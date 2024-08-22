# 2 - Ajax, Web Services, HTTP Headers (Accept & Content-type)

## I. Overview
- Today we will be updating our Quotes app to utilize a remote web service instead of a local JSON file.
- Rather than our client app having to download ALL of the quotes from the JSON file and then choose just one, this web service will do that for us and just return one quote.
- We will also see how to utilize HTTP *request headers* to specify the content-type of the data our app will receive.

---

## II. Files

### II-A. quote-random.php

- working version (running on gibson) here --> [quote-random.php](https://people.rit.edu/~acjvks/fall-2024/services/quote/quote-random.php)

```php
<?php
 // I. LOAD DATA FILE
 // https://www.php.net/manual/en/function.file-get-contents.php
 $str = file_get_contents("quotes-data.json");
 
 // II. CONVERT TO PHP ASSOCIATIVE ARRAY
 // https://www.php.net/manual/en/function.json-decode.php
 $all_quotes = json_decode($str);
 $length = count($all_quotes);
 
 // DEBUG CODE
 /*
 echo "<p>Num Results: $length</p>";
 echo "<pre>";
 print_r($all_quotes);
 echo "</pre>";
 */
 
 // III. GET ONE RANDOM ELEMENT OF THE $all_quotes ARRAY
 $randomQuote = $all_quotes[array_rand($all_quotes)];

  // DEBUG CODE
  /*
  echo "<pre>";
  print_r($randomQuote);
  echo "</pre>";
  */
 
  // IV. Send HTTP headers
  // https://www.php.net/manual/en/function.header.php
  // DO THIS **BEFORE** you `echo()` the content!
  header('content-type: application/json');      			// tell the requestor that this is JSON
  header('Access-Control-Allow-Origin: *');     			// turn on CORS
  header('X-this-430-service-is-kinda-lame: true');   // a custom header 
	
  // V. Send the content
  // json_encode() turns a PHP associative array into a string of well-formed JSON
  // https://www.php.net/manual/en/function.json-encode.php
  $string = json_encode($randomQuote);
  echo $string;
?>
```

### II-B. quote-random-json-or-text.php

- working version (running on gibson) here --> [quote-random-json-or-text.php](https://people.rit.edu/~acjvks/fall-2024/services/quote/quote-random-json-or-text.php)

```php
<?php
 // THIS VERSION LOOKS AT THE REQUEST HEADERS SENT OVER BY THE CLIENT
 
 // DEBUG CODE
 //   echo "<p>Request Headers</p>";
 //   echo "<pre>";
 //   print_r(apache_request_headers());
 //   echo "</pre>";

 
  // 0. GET VALUE OF 'Accept' REQUEST HEADER
  $requestHeaders = apache_request_headers();
  $acceptHeader = $requestHeaders['Accept'];
  //echo $acceptHeader;
  
  // I. LOAD DATA FILE
   $str = file_get_contents("quotes-data.json");
  
  // II. CONVERT TO PHP ASSOCIATIVE ARRAY
  $all_quotes = json_decode($str);
  
  // III. GET ONE RANDOM ELEMENT OF THE $all_quotes ARRAY
  $randomQuote = $all_quotes[array_rand($all_quotes)];
  //print_r($randomQuote);
  
  // IV. Send HTTP headers
  // https://www.php.net/manual/en/function.str-contains.php
  if(str_contains($acceptHeader,"application/json")){
    $contentType = "application/json";
  }else{
    $contentType = "text/plain";
  }
  header("content-type: $contentType");
  header('Access-Control-Allow-Origin: *');
	
  // V. Send the content
  if($contentType == "application/json"){
    // JSON
    $string = json_encode($randomQuote);
  }else{
    // plain text: content|author
    $string = "$randomQuote->content|$randomQuote->author";
  }
  echo $string;
 ?>
```

---

## III. Terms

### Request Methods
- Today we are still just using the GET request nethod, which means  

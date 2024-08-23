# 2 - Ajax, Web Services, HTTP Headers (Accept & Content-type)

## I. Overview
- Today we will be updating our Quotes app to utilize a remote web service instead of a local JSON file.
- Rather than our client app having to download ALL of the quotes from the JSON file and then choose just one, this web service will do that for us and just return one quote.
- We will also see how to utilize HTTP *request headers* to specify the content-type of the data our app will receive.

---

## II. Files

### II-A. quote-random.php

- Working version (running on banjo) here --> [quote-random.php](https://people.rit.edu/~acjvks/fall-2024/services/quote/quote-random.php)
- This web service returns a random quote in the JSON format
- It is written in [PHP](https://www.w3schools.com/php/)

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
  header('content-type: application/json');           // tell the requestor that this is JSON
  header('Access-Control-Allow-Origin: *');           // turn on CORS
  header('X-this-430-service-is-kinda-lame: true');   // a custom header
  
	
  // V. Send the content
  // json_encode() turns a PHP associative array into a string of well-formed JSON
  // https://www.php.net/manual/en/function.json-encode.php
  $string = json_encode($randomQuote);
  echo $string;
?>
```

### II-B. quote-random-json-or-text.php

- Working version (running on banjo) here --> [quote-random-json-or-text.php](https://people.rit.edu/~acjvks/fall-2024/services/quote/quote-random-json-or-text.php)
- This version is sensitive to the `Accept` HTTP request header - and if the script detects the value of `Accept` to be `application/json` then it will return JSON data, otherwise it will return plain text data
- Test the above link - because the browser is NOT sending `Accept: application/json`, you are going to be seeing the plain text version of the data.
- How can you send the correct `Accept` header? Easy! Here are some ways:
  - Use the Postman App and configure it to send a `Accept: application/json` request header
  - With XHR you can send an `Accept` header after `xhr.open()` a connection, but before your `xhr.send()` it

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

## III. Posting to banjo.rit.edu
- Your banjo account already has PHP installed - so if you upload the 2 above PHP files to banjo they should work fine
- Be sure to also upload **quotes-data.json** to the same folder as the 2 PHP files
- Don't forget to put all the files in `www` (or a sub-directory of `www`)
- Did you forget how to post to `banjo.rit.edu`? Get help here --> https://github.com/tonethar/IGME-235-Shared/blob/master/notes/core-skills/ftp-upload-walkthrough.md
- If you run into problems, ask for help:
  - it might be a **php.ini** file issue - [here are some instructions on how to fix that](https://github.com/tonethar/IGME-230-Master/blob/master/notes/HW-php-ini.md)
- Here are some PHP resources that relate to banjo. Some of the example links are on an old server that might not be running, but the info is still good:
  - [PHP Web Service Part I - What is a web service?](https://github.com/tonethar/IGME-330-Master/blob/master/notes/HW-php-web-service-1.md)
  - [PHP Web Service Part II - PHP Foundations](https://github.com/tonethar/IGME-330-Master/blob/master/notes/HW-php-web-service-2.md)
  - [PHP Web Service Part III - Coding get-random-joke.php](https://github.com/tonethar/IGME-330-Master/blob/master/notes/HW-php-web-service-3.md)
  - [PHP Web Service Part IV - Coding get-jokes.php](https://github.com/tonethar/IGME-330-Master/blob/master/notes/HW-php-web-service-4.md)
  - [PHP Web Service Part V - creating a proxy server](https://github.com/tonethar/IGME-330-Master/blob/master/notes/HW-php-web-service-5.md)

---

# IV. `ssh` (secure shell)
- Once we get in to using [node](https://nodejs.org/en) and [express](https://www.npmjs.com/package/express), we'll be doing quite a bit of work on the command line, for example running `node`, installing packages and running projects with `npm`, pushing code to github with `git`, file management tasks and so on
- You can also use `ssh` and [GitBash](https://git-scm.com/download/win) (or Terminal on Mac) to remotely connect to banjo.rit.edu:

```
ssh abc1234@banjo.rit.edu
Password: •••••••
```

- Then go to town on the command line:

```
pwd                 # show absolute path to current working directory (aka cwd)
cd www              # change cwd to www
cd ..               # change cwd to parent directory
ls                  # list contents of cwd
ls -1               # "long" list of cwd
ls -al              # also show hidden files
rm <fileName>       # delete file
mkdir <foldername>  # create folder
mv log log.txt      # rename log to log.txt
nano file.txt       # open (or create) file.txt in a text editor
```

---

## V. Terms

### Request Methods
- Today we are still just using the GET request method

---

## VI. Links
- [MDN - `fetch()` API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch)

---
---

| <-- Previous Unit | Home | Next Unit -->
| --- | --- | --- 
| [**1 - Ajax (XHR) Review**](1-ajax-review.md)  |  [**IGME-430**](../) | [**3 - Exploring HTTP methods with json-server**](3-http-methods-with-json-server.md)

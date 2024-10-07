# `Accept` headers and XML


## I. What is XML?
- XML is a software- and hardware-independent tool for storing and transporting data.
  - XML stands for eXtensible Markup Language
  - XML is a markup language much like HTML
  - XML was designed to store and transport data
  - XML was designed to be self-descriptive
  - XML is a W3C Recommendation
- **Source:** https://www.w3schools.com/XML/xml_whatis.asp

---

## II. 3 Rules of XML
- Must Have a Root Element
- All Elements Must Have a Closing Tag
- Tags are Case Sensitive
- Elements Must be Properly Nested
- Attribute Values Must Always be Quoted
- Some characters have a special meaning in XML, and you must use an entity reference instead (e.g. `<` is represented by `&lt;`, `&` is represented by `&amp;`, and a few others)
- **Source:** https://www.w3schools.com/XML/xml_syntax.asp

---

## III. Simple Example

**apple.xml** could be any of the following:

```xml
<apple />
```

OR add some detail about the apple:

```xml
<apple>Red Delicious</apple>
```

OR add more detail:

```xml
<apple>
  <id>12345</id>
  <type>Red Delicious</type>
  <datePicked>Mon Oct 07 2024 07:29:57 GMT-0400 (Eastern Daylight Time)</datePicked>
</apple>
```

OR put the meta data in the *attributes*:

```xml
<apple id="12345" datePicked="Mon Oct 07 2024 07:29:57 GMT-0400 (Eastern Daylight Time)">
  <type>Red Delicious</type>
</apple>
```

Finally, an "array" of apples:

```xml
<fruitBasket>
  <apple id="12345" datePicked="Mon Oct 07 2024 07:29:57 GMT-0400 (Eastern Daylight Time)">
    <type>Red Delicious</type>
  </apple>
  <apple id="67890" datePicked="Mon Oct 07 2024 07:29:59 GMT-0400 (Eastern Daylight Time)">
    <type>Red Delicious</type>
  </apple>
</fruitBasket>
```

---

## IV. `hoots` as XML

---

## V. Creating XML in code

- Here it is - and there's lot's to talk about here!

![screenshot](_images/p1-2.png)

---

## VI. XML in Project 1


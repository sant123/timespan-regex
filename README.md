# Timespan-Regex
A simple but powerful regex validator for timespan.

Regex:
> ^([0-9]{1}|(?:0[0-9]|1[0-9]|2[0-3])+):([0-5]?[0-9])(?::([0-5]?[0-9])(?:\.(\d{1,9}))?)?$


Using it with Javascript:

``` javascript
var regex = /^([0-9]{1}|(?:0[0-9]|1[0-9]|2[0-3])+):([0-5]?[0-9])(?::([0-5]?[0-9])(?:\.(\d{1,9}))?)?$/;
regex.test("10:06"); //true
regex.test("26:06"); //false
```

The regex expects at least the hours and the minutes like:

* "12:56"
* "05:22"
* "1:6" (this means 01:06)

The seconds and nanoseconds are optional, but they still require their order.

``` javascript
regex.test("18:06:59"); //true
regex.test("18:06:59.456"); //true
```

The max length for nanoseconds are 9, so this will fail:

``` javascript
regex.test("18:06:59.4564564568"); //false
```

Missing inputs like these will fail:

* "18:"
* "18:06:"
* "18:06:59."

Enjoy!

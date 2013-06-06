Mixture Boilerplate
=============================
### Sass + Haml + Angular

This is a boilerplate for the Mixture site generation tool. It's set up using Haml and Sass for easy to read, quickly written HTML and CSS, and it's integrated with AngularJS for quickly defined dynamic data. Also integrated are Modernizr, Foundation, and of course JQuery.

* [Mixture](http://mixture.io/)
* [Haml documentation](http://haml.info/)
* [Mixture Haml documentation](http://docs.mixture.io/templates#haml)
* [AngularJS](http://angularjs.org/)
* [Modernizr](http://modernizr.com/)
* [Foundation](http://foundation.zurb.com/)
* [JQuery](http://jquery.com/)

Mixture JSON Syntax
-------------------

To access JSON data within Mixture, simply create your JSON file inside the models folder. There is a global file for global data, or you can create your own JSON file for a specific page. The file must be the same name as the haml file.

To call data from your page's specific JSON file use the syntax:

`#{model["company_name"]}`

To call data from the global JSON file use the syntax:

`#{global["company_name"]}`

For calling data deeper in the JSON file you can target specific data this way:

`#{model["departments"]["creative"]}`

While a regular Mixture liquid file uses the `{% %}` syntax, it is not yet supported in haml. But we can always use Ruby for that. For instance you could loop through some of our JSON data like this:

```
- for x in #{model["departments"]}

  #{x[1]}
```

Notice that when displaying JSON data using variables in ruby blocks, you'll use array syntax to target names and values.

`#{x[0]}` `#{x[1]}`

If you call JSON objects in mixture directly from HAML you can ignore the `#{}`.

`global["company_name"]`


Using the following HAML:

```
%section.panel
  %p
    Our company name is #{model["company_name"]}.
    A few of our departments are:
  - for x in model["departments"]
    %p #{x[1]}

%section.panel
  %p We are #{global["company_name"]}, we are an
     #{global["company_type"]}. We're located in
     #{global["location"]["city"]},
     #{global["location"]["state"]}.
```

With the following JSON files:

```
index.json

{
  "company_name": "Maxmedia",
  "departments": {
    "tech": "Technology",
    "creative": "Creative",
    "strat": "Strategy"
  }
}
```
```
_global.json

{
  "company_name": "Maxmedia",
  "company_type": "agency",
  "location": {
    "city": "Atlanta",
    "state": "Georgia"
  }
}
```
Will output the following:
```
Our company name is Maxmedia. A few of our departments are:

Technology

Strategy

Creative
```
```
We are Maxmedia, we are an agency. We're located in Atlanta, Georgia.
```

Angular
-------
On the boilerplate index there is an example of Angular using dynamic data.
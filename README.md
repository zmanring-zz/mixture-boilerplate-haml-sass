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

To call data from your page's specific JSON file use the syntax
`#{model["description"]}`

To call data from the global JSON file use the syntax
`#{global["description"]}`

To call data from an array from a JSON file, it works just like any array.
`#{model["team"][0]["name"]}`

While a regular Mixture liquid file uses the {% %} syntax, it is not yet supported in haml. But we can always use Ruby for that. For instance you could loop through some of our JSON data like this:
`- for x in #{model["team"]}`
  `#{x["name"]}`

Angular
-------
On the boilerplate index there is an example of Angular using dynamic data.
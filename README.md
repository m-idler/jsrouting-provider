Silex JSRouting Provider
========================

The JSRouting Provider is a silex routing provider for javascript, that exposes routes to a javascript file. Then you can generate routes for use with javascript frameworks like AngularJS.

[![Build Status](https://api.travis-ci.org/chrootLogin/jsrouting-provider.png?branch=master)](https://travis-ci.org/chrootlogin/jsrouting-provider)
[![Total Downloads](https://poser.pugx.org/rootlogin/jsrouting-provider/downloads.png)](https://packagist.org/packages/rootlogin/jsrouting-provider)
[![Latest Stable Version](https://poser.pugx.org/rootlogin/jsrouting-provider/v/stable.png)](https://packagist.org/packages/rootlogin/jsrouting-provider)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/chrootLogin/jsrouting-provider/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/chrootLogin/jsrouting-provider/?branch=master)

Installation
------------

Add the provider to your composer.json
``` {.json}
{
  "requires": {
    "rootlogin/jsrouting-provider": "dev-master"
  }
}
```

Register the provider in your silex application:
``` {.php}
$app->register(new rootLogin\JSRoutingProvider\Provider\SilexJSRoutingServiceProvider(), array(
  "jsrouting.base_url" => "/",
  "jsrouting.exposed_routes" => array("routeA", "routeB")
  ));
```

Set the route option _expose_ to _true_.
``` {.php}
$controllers->get("/hello", function() {
    return "hello world"!
})->bind("hello")->getRoute()->setOption("expose",true);
```

Include and use it in your frontend like this.
``` {.html}
<!-- Gets the full router with the routes -->
<script src="{{ path("jsrouting") }}"></script>

<!-- Or if you want only some parts you can get the router and the routes separately -->
<script src="{{ path("jsrouter") }}"></script><!-- Gets only the router -->
<script src="{{ path("jsroutes") }}"></script><!-- Gets only the routes -->

<!-- Get routes like this -->
<script>
  console.log(router.generate("routeA"));
  console.log(router.generate("routeB", {id: 3}));
</script>
```

Console
-------
If you want to use the console commands please install at least [saxulum/saxulum-console](https://github.com/saxulum/saxulum-console).
It will be automatically activated after you registered the provider.

### Available Commands

* __jsrouting:dump__: This dumps the router with the known routes (buggy, ATM);
* __jsrouting:dump:router.js__: This only dumps the router.js. You need to add the routes manually.
  
Run the tests
-------------
Go to the base directory of the jsrouting-provider. Do a `composer install` and enter `vendor/bin/phpunit`.

### Run the javascript tests
Do a `npm install` and enter `node_modules/.bin/gulp test`. Or if you have installed gulp globally enter `gulp test`.

Contribution
------------
Pull request are welcome. Or if you can't or want code you can also contribute by opening a ticket if you see something is wrong.
  
Warning
-------
This project is in early development stages. No warranty if it kills your kittens or starts a nuclear war ;)

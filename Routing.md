Cygnite Framework User Guide
=========================

  Cygnite URI Routing
  ------------------------

  Cygnite framework has powerful routing features which allow you to have various routing patterns.

  The main features of router are -

  i.  Static Route Patterns
  ii.  Dynamic Route Patterns
  iii.  Optional Route Subpatterns
  iv.  GET, POST, PUT, DELETE, and OPTIONS request methods
  v.  Custom 404 handling
  vi.  Before Route Middlewares
  viii.  After Router Middleware (Finish Callback)

  Route Patterns :
  -------------------

  Below routing patterns are supported by router-

        \d+ = One or more digits (0-9)
        \w+ = One or more word characters (a-z 0-9 _)
        [a-z0-9_-]+ = One or more word characters (a-z 0-9 _) and the dash (-)
        .* = Any character (including /), zero or more
        [^/]+ = Any character but /, one or more

   Dynamic routing For example -

       $router->get('/hello/(\w+)', function($name) {
                echo 'Cygnite Framework welcome you  ' . htmlentities($name);
       });

  Note: The leading / at the very beginning of a route pattern is not mandatory, but is recommended.

  When multiple subpatterns are defined, they resulting route handling parameters are passed into the route handling
  function in the order they are defined in:

    $router->get('/movies/(\d+)/photos/(\d+)', function($movieId, $photoId) {
             echo 'Movie #' . $movieId . ', photo #' . $photoId);
    });

  Optional Route Subpatterns
  ---------------------------------

  Route subpatterns can be made optional by making the subpatterns optional by adding a ? after them. Think of blog
  URLs in the form of /blog(/year)(/month)(/day)(/slug):

    $router->get('/blog(/\d+)?(/\d+)?(/\d+)?(/[a-z0-9_-]+)?', function($year = null, $month = null, $day = null, $slug = null) {
            if (!$year) { echo 'Blog overview'; return; }
            if (!$month) { echo 'Blog year overview'; return; }
            if (!$day) { echo 'Blog month overview'; return; }
            if (!$slug) { echo 'Blog day overview'; return; }
            echo 'Blogpost ' . htmlentities($slug) . ' detail';
    });

    The code snippet above responds to the URLs /blog, /blog/year, /blog/year/month, /blog/year/month/day,
    and /blog/year/month/day/slug.

  Note: With optional parameters it is important that the leading / of the subpatterns is put inside the subpattern
  itself. Don't forget to set default values for the optional parameters.

  The code snipped above unfortunately also responds to URLs like /blog/foo and states that the overview needs to be
  shown - which is incorrect. Optional subpatterns can be made successive by extending the parenthesized subpatterns
  so that they contain the other optional subpatterns: The pattern should resemble /blog(/year(/month(/day(/slug))))
  instead of the previous /blog(/year)(/month)(/day)(/slug):

            $router->get('/blog(/\d+(/\d+(/\d+(/[a-z0-9_-]+)?)?)?)?', function($year = null, $month = null, $day = null, $slug = null) {
                    // ...
            }
  Note: It is highly recommended to always define successive optional parameters.

  To make things complete use quantifiers to require the correct amount of numbers in the URL:

            $router->get('/blog(/\d{4}(/\d{2}(/\d{2}(/[a-z0-9_-]+)?)?)?)?', function($year = null, $month = null, $day = null, $slug = null) {
                      // ...
            }

   Custom 404:
   ---------------

   Override the default 404 handler using $router->set404(function);

        $router->set404(function() {
            header('HTTP/1.1 404 Not Found');
            // ... do something special here
        });
   The 404 will be executed when no route pattern was matched to the current URL.

  Before Route Middlewares
  --------------------------------

 Router  supports Before Route Middlewares, which are executed before the route handling is processed.

 Like route handling functions, you hook a handling function to a combination of one or more HTTP request methods and a specific route pattern.

        $router->before('GET|POST', '/admin/.*', function() {
            if (!isset($_SESSION['user'])) {
                header('location: /auth/login');
                exit();
            }
        });
 Unlike route handling functions, more than one before route middleware is executed when more than one route match is found.

  Before Router Middlewares
  ---------------------------------

  Before route middlewares are route specific. Using a general route pattern (viz. all URLs), they can become Before
  Router Middlewares (in other projects sometimes referred to as before app middlewares) which are always executed,
  no matter what the requested URL is.

        $router->before('GET', '/.*', function() {
            // ... this will always be executed
        });
  After Router Middleware / Run Callback

   Run one (1) middleware function, name the After Router Middleware (in other projects sometimes referred to as
   after app middlewares) after the routing was processed. Just pass it along the $router->run() function. The run callback is route independent.

        $router->run(function() { … });
   Note: If the route handling function has exit()ed the run callback won't be run.


  Where to write my own custom uri routing ?
  ------------------------------------------
   Cygnite provides you to have your custom routing. You can have your routing expression and configurations
   inside apps/routerconfig.php as well as you can write your restful routing into apps/routes.php which allows
   you above all types of routing features.

  Credit :
  --------

   Cygnite Framework which uses bramus router class and routing library
   and router documention credit goes to bramus which gives awesome routing features into Cygnite Framework.
   
   

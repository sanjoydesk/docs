 Cygnite Framework User Guide
 ----------------------------

 Models
 ------------

 What is Models ?
 ---------------------

   Your models classes will be stored in your models folder. Simply to say Models are just a class which interacts
   with your database and fetch you results to the controller or sometime optionally into your view page.

 How to load a model ?
 ----------------------------
  You can load your model into your controller as below -

    $this->app()->model('users');
    OR
    Cygnite::loader()->model('users')->gettags();// If you autoloaded your models


 How to load multiple models ?
 ------------------------------------
  Cygnite Framework also allow you to load multiple models on the fly.

  For example -

    $this->app()->model(array('users','category'));

 The best way to load your models dynamically is autoloading into the configs/autoload.php. For more information
 have a look at the autoload guide.

    The sample model class looks like follows-
     class Users extends CF_BaseModel
    {
          public function __construct()
         {
              parent::__construct('cygnite');//your database name goes here
         }
            public function getdetails()
            {
            
            }

        }
      ?>


 How to load and access model functions ?
 ---------------------------------------------------

  Lets assume your model file name is usersmodel.php. Then you can load your model inside in your controller
  as bewlow-

        <?php
         class WelcomeuserAppsController extends CF_BaseController
         {
           public function __construct()
           {
              parent::__construct();
              // Load in constructor if you want to access it throughout the
              // controller else load it corresponding method based upon your needs.
              $this->app()->model('usersmodel');
           }
           
           public function action_index()
           {
               $this->app()->model('usersmodel');
               $userdetails =  $this->app()->usersmodel->getdetails();
               
               //Effecient way to access models functions
               $userdetails = Cygnite::loader()->model('users')->gettags();// If you autoloaded your models
               show($userdetails);
           }
           
         }
    ?>


   How to access model functions in view page ?
   --------------------------------------------
   Though its not good practice to call your model functions in your view page, Cygnite optionally
   allow you to do that. You can call your model function just like below -
   You can simply call the model in views to fetch data from db as follows -

      <html>
        <head>
        <title>Welcome to Cygnite Framewormk</title>
        </head>
        <body>
        <h2></h2>
        <div class="content">
           <h2>Hello World ! </h2>
           <?php
                $users = $this->usersmodel->getdetails(); // Call your model functions to fetch data from db
                 $users = Cygnite::loader()->model('users')->gettags();
                show($users); // print your data into browser as formated output.
           ?>
        </div>
        </body>
        </html>


   These are basics of models. You can find more information about database queries and crud operation you
   can follow database user manual.

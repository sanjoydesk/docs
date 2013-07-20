Cygnite Framework User Guide
============================

 How to set default Controller ?
 ------------------------------------
  You can easily set default controller of your application simply changing configuration in apps/configs/config.php
  file. Change your default controller-
  
     return array(
                   'default_controller'    => 'welcomeuser',
      );

   Default controller can be set in configs/config.php and default action of Cygnite is index method.

 Controllers
 -------------

   i. Controller name should start with uppercase and followed by controller path. For example if you have controller
   as welcomeuser.php and controller path is apps/controllers/welcomeuser.php then your controller name should be
   as- WelcomeuserAppsController.

   ii. Please have two space indent before starting your controller name and have one tab to start your method name.

   For example let us create a simple controller and see how it is works-

     <?php
     class WelcomeuserAppsController extends CF_BaseController
     {
       public function __construct()
       {
          parent::__construct();
       }
       public function action_index()
       {
          echo "Hello World !!";
       }
     }
     ?>

  iii. Method name should be in small letter follows by underscore if needed as above. Every method name should
  start with prefix action_ and followed by your action name as like action_method_name().

  iv. Now let us call the controller via url. You can call the controller via url just like this -
      /index.php/welcomeuser/index


  How to pass Parameters to method ?
  --------------------------------------------
  You can pass numbers of parameters in url. Let us consider above url /index.php/welcomeuser/userdetails/23/user

  It will call the userdetails method of welcomeuser controller and parameters 23,user will be passed into it.
  You can also get the uri segments from the url like -

     Url::segment(3);


  Lets see how to print parameters in methods-

     class WelcomeuserAppsController extends CF_BaseController
     {
       public function __construct()
       {
          parent::__construct();
       }
       
       public function action_index()
       {
          echo "Hello World !!";
       }
       
       public function userdetails($id = '',$identity = NULL)
       {
          echo $id;
          echo $identity;
          echo Url::segment(3);
       }
     }


   How to call a private methods inside Controller ?
   --------------------------------------------------------
   Incase if you want to have certain methods to be hidden from public access then you can simply create a method
   inside controller and have access as private.

   For example let us create private function -

       public function action_users()
       {
          $this->_identity();

       }

       private function _identity()
       {
          echo "I am inside private method";
       }

   you can declare method as private as make it hidden from url access.
       
       

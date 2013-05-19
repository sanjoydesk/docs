Cygnite Framework User Guide 
==============================

 Views
 -----
     Views are just web pages where your headers,menus,sidebar,contents and footers resides. Views are called from 
     controllers. Since we follow MVC patterns views neither call directly nor passing any parameters. 
     
     I have shown you in controllers section how to create controller and now lets create views and load it from 
     controller.      
     
 Lets create simple view page -
 ------------------------------     
     Lets create simple view page welcome.view.php. Your view filename should follow below standard-
     welcome.view.php
     
     <html>
     <head>
           <title>Welcome to Cygnite Framework</title>
     </head>
     <body>
            <h2></h2>
            
            <div class="content">   
                 Welcome to Cygnite Framework            
            </div>
     
     </body>     
     </html>
     
 How to load view ?
 --------------------
     You can load and pass parameters into view two different ways from controllers. Lets have same example which 
     we followed in controllers section already.
     
     i. First way -
     
     <?php
         class WelcomeuserAppsController extends CF_BaseController
         {
            private $country = 'India';
            
            public function __construct()
            {
              parent::__construct();
            }
        
            public function action_index()
            {
                $this->app()->render("welcome"); // Load view
            }
            
            public function action_author()
            {
                // Load welcome view and pass array into view page.
                
                $this->app()->render("welcome",array(
                                                    'author'=>'Sanjay',
                                                    'email'=>'sanjoy09@hotmail.com',
                                                    'country'=> $this->country
                                                  ));           
            }
         }        
    ?>
    ii. Second way -    
     <?php
         class WelcomeuserAppsController extends CF_BaseController
         {
            private $country = 'India';
            
            public function __construct()
            {
              parent::__construct();
            }
        
            public function action_index()
            {
                $this->app()->render("welcome"); // Load view normal view page
            }
            
            public function action_author()
            {
                // Load welcome view and pass array into view page.
                
                $this->app()->render("welcome")->with(array(
                                                    'title' => 'Welcome to Cygnite Framework'
                                                    'author'=>'Sanjay',
                                                    'email'=>'sanjoy09@hotmail.com',
                                                    'country'=> $this->country
                                                  ));           
            }
         }        
    ?>
    
  How to display the values into views ?
  --------------------------------------  
      You can retrive data from controller as below -
      
        
     <html>
     <head>
           <title><?php echo $this->values['title']; ?></title>
     </head>
     <body>
            <h2></h2>
            
            <div class="content">   
                 <h2><?php echo $this->values['title']; ?> </h2> 
                 <table> 
                      <tr> 
                           <td> Author Name :</td>
                           <td><?php echo $this->values['author'] ?> </td>
                      </tr>
                      <tr> 
                           <td> Email Address :</td>
                           <td><?php echo $this->values['email'] ?> </td>
                      </tr>
                      <tr> Country :</td>
                           <td><?php echo $this->values['country'] ?> </td>
                      </tr>
                 
                 </table>
            </div>
     
     </body>     
     </html>
  
  How to retrive view page as string ?
  ------------------------------------
      You can retrive your total view page as string format if you pass thrid parameter as 'ui_contents' into render() 
      method. 
      
      For example - 
      
      If you want to store total view page into file cache than you should follow as below-
      
     $view_page = $this->app()->render("welcome",array('author'=>'Sanjoy Dey','ui_contents');
     
     $this->request('Cache')->build("FileCache")->write_cache('welcome_page',$view_page);
     
     you can view the page from cache as follows-    
     
     echo $this->request('Cache')->build("FileCache")->read_cache('welcome_page');   
     
     
  How to call model in view page ?
  --------------------------------
     
     First load the model in controller page -
     
     $this->app()->model('usersmodel'); 
     
     and you can access model functions in controllers via app() function [ex: $this->app()->usersmodel->getdetails();]
     where as you can access model functions in views simply calling as like below-       
     
     $this->usersmodel->getdetails();
  
    These are all about views.  

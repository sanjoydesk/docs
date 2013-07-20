Cygnite Framework User Guide
==========================

 Session Library
 ------------------

 What is session library ?
 -----------------------------

  Cygnite session is highly secured with its in built mechanism. Cygnite session library allow you to store
  each users details into session as encrypted format. Which is stored into your temp directory.
  As for now Cygnite uses php core session with more secure format. Optionally we will
  bring feature of storing session details into database which will be more secure.

  Your session details store with fingerprint in a file.

  How to set session name and save path ?
  --------------------------------------------------

    Cygnite Framework provides you provision to set your session name in session config file. Which
    exists in apps/configs/session.php

    by default it is -
    'cf_session_name'                 => 'cf_secure_session',

    and

    session save path is -

    apps/temp/sessions/ and set in session config

      'cf_session_save_path'         => 'default', // cygnite framework default session path is apps/temp/sessions/

    Don't change this path.


 How to store data into cygnite session ?
 -----------------------------------------------

  You can store data into session with key and single string as well as array format.

     For example :
     
       Cygnite::loader()->request('Session')->save('cygnite','Hellow !! Cygnite you are awesome !');

    OR

       Cygnite::loader()->request('Session')->save('cygnite_author',array(
                                                                          'author' => 'Sanjoy Dey'
                                                                          'country' => 'India'
                                                                          'interest' => 'Web Applications'
                                                                        ));

    That's it cygnite will save your details into session encrypted format.

  Dependencies -
  -------------------

    i. In order to use cygnite secure session you must have installed mcrypt library extension
    in your server.
   ii. Encryption key should be set in config.php file.
   


  How to retrieve session details ?
  ---------------------------------------

    Retrieving session details is so simpler then you think. You just request session library to
    retrieve your details as follows -

     $author_details =  Cygnite::loader()->request('Session')->retrieve('cygnite_author');
     
      show($author_details); // In built function to display your formated output in browser.


  How to destroy session details ?
  -------------------------------------

    You can destroy your current session details using session key.

    Cygnite::loader()->request('Session')->delete('cygnite_author');


  Additional Features
  -----------------------
   With existing secure session we are adding few more features into its core libraries to serve you better way.

   You can find next versions - session time out, saving session into database etc.

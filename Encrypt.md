Cygnite Framework User Guide
============================

  Encryption Library
  -----------------------

  Cygnite Framework allows you to encrypt your data in secure format. In order to use Cygnite Encryption and Session
  library you must have installed mcrypt extension. Cygnite strictly follow mcrypt encryption methodology including
  its built in mechanism to provide you secure encrypted data and provide you most secure session.

  How to set up your Encryption Key ?
  -------------------------------------------
  The encryption key is an string which provide you cryptographic mechanism and based on same key decrypt
  your data. You should keep your key configuration file securely in order to keep your application safe from
  hacking. Your key should be mix of alphabets and numbers which allow us to make more secure encrypted data.

    You can set your encryption key in apps/configs/config.php file as below-    
    return array(
              .............
              'cf_encryption_key'           => 'cygnite-shaXatBNHQ4z59c4mrez',
    );

 How to encrypt string ?
 --------------------------

   Now encryption of your strings are very sinmple made by Cygnite Framework. You don't need to initialise or write
   much code to encrypt your string. Since Cygnite engine auto loads your libraries so you can directly access your encryption
   library and encrypt data.

  For Example-

    $string  = 'Hi ! This is my string to be encrypted ';
    $encrypted_string = Cygnite::loader()->request('Encrypt')->encode($string);

  That's it. Your string has been encrypted and stored into $encrypted_string variable.


  How to Decrypt the string ?
  ---------------------------------

  Similarly decrypt the encrypted string is very simply. Once you have encrypted string just pass into decode method
  to decrypt the string, it will give you original value.

  Let us take the same example which we followed above -

    echo Cygnite::loader()->request('Encrypt')->decode($encrypted_string);

  That's it you are done. Your string has been decrypted and display you original value.
  
  

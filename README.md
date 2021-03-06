# User Authentication
## A simple example with a hard-coded password
Download this repository. The folder xyz is a website with a simple login system.
* Open *login.php*, *login_process.php* in a text editor. See how the login system is working, the email and password from the form are tested and then a session variable is set.
* Put the xyz website on a server. Login into the website and make sure you can navigate to each of the pages.
* Have a good look at the code make sure you understand how sessions are being used to restrict access to pages in the site.

On your own
* Create a page called *logout.php*
   * This should destroy the session and provide a link back to the login form. Add a link to *logout.php* from the other pages in the site. Check this works.
* You should find that even if the user has logged out they can still access *page3.php*.  Add some PHP code to *page3.php* that will prevent users from accessing this page unless they have logged in.

## Using a database
Clearly, using a hard-coded email and password has major limitations. Next, think about how you can store user details in a database table instead.

### Hashing passwords
We should never store passwords as plain text. Open *hashing.php* see how PHP generates password hashes.
* Experiment with hashing some more passwords using both *md5* and *bcrpyt*.
* Make sure you understand the difference that adding a salt makes.


### Set up the database table
Using the same database that you have used in previous weeks, execute the SQL statements in [users.sql](users.sql). This will set up a database table containing user emails and passwords.

If you browse this table you will see that the passwords have been hashed. The actual passwords are:-
* ghulam@xyz.co.uk password:huddersfield
* regina@xyz.co.uk password:123456
* olive@xyz.co.uk  password:qwerty

### Modify the login code to use a database
* Modify the code in *login_process.php* so that you test the user's email address and password against the values in the users table. Have a look on the notes/slides from this week for an example, or look on php.net for info the **password_verify()** function (http://php.net/manual/en/function.password-verify.php).
> If you are having problems getting this to work, temporarily comment out the redirection statements e.g. ```header( "Location: index.php" );``` you will then be able to see errors in login_process.php.

* To test your understanding, in phpmyadmin use the 'insert' tab to add another user to the database table. Invent an email address and use a hashed password from *hashing.php* as the password. Check you can successfully login using this password.

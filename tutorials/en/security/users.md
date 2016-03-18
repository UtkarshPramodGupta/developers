#####In this section

In this section you'll learn how to sign-up and log in a User (we call it CloudUser) and let CloudBoost do all the heavy-lifting like session management for your apps. Finally, you will also learn about default properties in CloudUser and how to save or delete a user. 

#Before we begin

CloudUser is inherited from CloudObject class, which means everything that CloudObject contains is also contained in CloudUser and that includes default properties like Id, createdAt, updatedAt, etc. and all of the functions like save, delete etc. 

#Sign up

To sign up a new user you need to initialize a new variable with the type CloudUser, assign it username and password and call the sign-up function. 

==JavaScript==
<span class="js-lines" data-query="signup">
```
var user = new CB.CloudUser();
user.set('username','my_username');
user.set('password', 'my_solid_password');
user.set('email', 'email@sample.com');
user.signUp({
  success: function(user) {
    //Registration successfull
  },
  error: function(error) {
    //Error in user registration.
  }
});
```
</span>

==NodeJS==
<span class="nodejs-lines" data-query="signup">
```
//Sign up function will not work on NodeJS. If you want to create a new user on the server. You can use save() function of CloudUser instead. 
```
</span>

==Java==
<span class="java-lines" data-query="signup">
```
CloudUser obj = new CloudUser();
obj.setUserName(username);
obj.setPassword(passwd);
obj.setEmail("hello@abc.com");
obj.signUp(new CloudUserCallback(){
	@Override
	public void done(CloudUser object, CloudException e)	throws CloudException {
		if(e != null){
		}
		if(object != null){
		}
	}
});
```
</span>

==.NET==
<span class="dotnet-lines" data-query="signup">
```
var user = new CB.CloudUser();
user.Set("username", "my_username");
user.Set("password", "my_solid_password");
user.Set("email", "email@sample.com");
await user.SignUp();
```
</span>

After the CloudUser is signed-up a new session is automatically created for you and the user is logged-in unless you call log-out function of CloudUser object. 

#Default Properties

Every CloudUser when created has default properties attached to it. Here is a list of all the default properties attached to CloudUser when you initialize them. 

* **All of the CloudObject default properties are available in CloudUser, as CloudUser is inherited from CloudObjects. To see what default properties are available in CloudObject, Please click [here](?lang=en&category=datastorage&subcategory=objects)**

* **Username** : [Text] A unique username of a CloudUser

==JavaScript==
<span class="js-lines" data-query="viewusername">
```
console.log(user.username);
```
</span>

==NodeJS==
<span class="nodejs-lines" data-query="viewusername">
```
console.log(user.username);
```
</span>

==Java==
<span class="java-lines" data-query="viewusername">
```
System.out.print(user.getUsername());
```
</span>

==.NET==
<span class="dotnet-lines" data-query="viewusername">
```
user.Username;
```
</span>

* **Password** : [Encrypted Text] Password of the CloudUser Object

==JavaScript==
<span class="js-lines" data-query="viewpass">
```
console.log(user.password);
```
</span>

==NodeJS==
<span class="nodejs-lines" data-query="viewpass">
```
console.log(user.password);
```
</span>

==Java==
<span class="java-lines" data-query="viewpass">
```
System.out.print(user.getPassword());
```
</span>

==.NET==
<span class="dotnet-lines" data-query="viewpass">
```
user.Password
```
</span>

* **Email** : [Email] An email of the CloudUser object

==JavaScript==
<span class="js-lines" data-query="viewemail">
```
console.log(user.email);
```
</span>

==NodeJS==
<span class="nodejs-lines" data-query="viewemail">
```
console.log(user.email);
```
</span>

==Java==
<span class="java-lines" data-query="viewemail">
```
System.out.print(user.getEmail());
```
</span>

==.NET==
<span class="dotnet-lines" data-query="viewemail">
```
user.Email
```
</span>

#Log in

To login a CloudUser you can set the username and password and call the login function / method. 

==JavaScript==
<span class="js-lines" data-query="login">
```
var user = new CB.CloudUser();
user.set('username', 'my_username');
user.set('password', 'my_solid_password');
user.logIn({
  success: function(user) {
    //Login successfull
  },
  error: function(error) {
    //Error.
  }
});
```
</span>

==NodeJS==
<span class="nodejs-lines" data-query="login">
```
var user = new CB.CloudUser();
user.set('username', 'my_username');
user.set('password', 'my_solid_password');
user.logIn({
  success: function(user) {
    //Login successfull
  },
  error: function(error) {
    //Error.
  }
});
```
</span>

==Java==
<span class="java-lines" data-query="login">
```
CloudUser user = new CloudUser();
user.setUserName(username);
user.setPassword(passwd);
user.logIn(new CloudUserCallback(){
	@Override
	public void done(CloudUser object, CloudException e)throws CloudException {
		if(e != null){
		}				
		if(object != null){
		//			
		}
	}
});
```
</span>

==.NET==
<span class="dotnet-lines" data-query="login">
```
var user = new CB.CloudUser();
user.Set("username", "my_username");
user.Set("password", "my_solid_password");
await user.LogIn();
```
</span>

Once the user us login you can access the current logged in user by 

==JavaScript==
<span class="js-lines" data-query="viewcurrent">
```
CB.CloudUser.current
```
</span>

==NodeJS==
<span class="nodejs-lines" data-query="viewcurrent">
```
CB.CloudUser.current
```
</span>

==Java==
<span class="java-lines" data-query="viewcurrent">
```
CloudUser.getCurrentUser();
```
</span>

==.NET==
<span class="dotnet-lines" data-query="viewcurrent">
```
CB.CloudUser.Current
```
</span>

#Log out

If you want to flush the session out and log out the user, then you can do this by

==JavaScript==
<span class="js-lines" data-query="logout">
```
CB.CloudUser.current.logOut({
  success : function(user){
      //user logged out.
    }, error : function(error){
      //error
    }
});
```
</span>

==NodeJS==
<span class="nodejs-lines" data-query="logout">
```
CB.CloudUser.current.logOut({
  success : function(user){
      //user logged out.
    }, error : function(error){
      //error
    }
});
```
</span>

==Java==
<span class="java-lines" data-query="logout">
```
CloudUser.getcurrentUser().logOut(new CloudUserCallback(){
	@Override
	public void done(CloudUser x, CloudException t)	throws CloudException {
	//					
	}		
});
```
</span>

==.NET==
<span class="dotnet-lines" data-query="logout">
```
CB.CloudUSer.Current.Logout
```
</span>

#Change Password

To change the password of a user you need to call the changePassword function of the `CB.CloudUser` instance. Before you call the changePassword function make sure the current user is loggedIn and the current session is valid. Please note : Calling change password will not log the user out of its current session.

==JavaScript==
<span class="js-lines" data-query="chagepassword">
```
CB.CloudUser.current.changePassword('oldPassword','newPassword',{
  success: function(user) {
    //Change Password  successfull
  },
  error: function(error) {
    //Error
  }
});
```
</span>

==NodeJS==
<span class="nodejs-lines" data-query="chagepassword">
```
//Change Password does not work on NodeJS, because it needs the current user session to be valid.
```
</span>

==Java==
<span class="java-lines" data-query="chagepassword">
```
CloudUser.getCurrentUser().changePassword("oldPassword","newPassword",
	new CloudUserCallback(){
	@Override
	public void done(CloudUser user,CloudException e){
		if(user!=null)
			//user
		if(e!=null)
			//e
	}
});
```
</span>

#Reset Password

To reset the password of a user you need to call the resetPassword function of the `CB.CloudUser` class. Reset Password takes in an email of the user as first parameter and callback as second parameter. CloudBoost automatically takes care of emailing the user with password reset link. Please note : If you want to change the format the email which CloudBoost sends by default. You can head over to your CloudBoost App Dashboard and change the email settings of an app.

==JavaScript==
<span class="js-lines" data-query="resetpassword">
```
CB.CloudUser.resetPassword('email',{
  success: function() {
    //Reset Password email sent! 
  },
  error: function(error) {
    //error.
  }
});
```
</span>

==NodeJS==
<span class="nodejs-lines" data-query="resetpassword">
```
CB.CloudUser.resetPassword('email',{
  success: function() {
    //Reset Password email sent! 
  },
  error: function(error) {
    //error.
  }
});
```
</span>

==Java==
<span class="java-lines" data-query="resetpassword">
```
CloudUser.resetPassword("email",new CloudStringCallback(){
	@Override
	public void done(String msg,CloudException e){
		if(msg!=null)
			//reset password email sent
		if(e!=null)
			//e
	}
});
```
</span>

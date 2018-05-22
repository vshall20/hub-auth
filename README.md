## Welcome to SpinAuthenticator - User Authentication for hubspot.

### Discussion

HubSpot is a great platform for all your contact information and a great way to interact. But to provide your customers integrated and secure access to pages that need authentication, you'll need another solution.

With SpinAuthenticator you can integrate client-side authentication on hubspot using just a minimal lightweight Javascript library.<br>

To add this library to your site, add:

```markdown
<script type='text/javascript' src='https://cdn.rawgit.com/rahulasati/auth/master/js/1.0.0/main.js'></script>
```

### Usage

We have developed this library to solve authentication problem for hubspot but if you're looking for simple client side authentication so definitely it will probably meet your needs.

This javascript library is intentionally small and minimalistic.

### Initialization

Initialize the library prior to making any other calls with a call to HA.init(options)

```markdown
<script type="text/javascript">
        window.onload = function () {
            HA.init({
                API_KEY: 'xxxxx-xxxxx-xxxxx-xxxxx',
                authPageUrl: '/url/--/auth.html',
                complete: function (err, data) {
                    console.log('init complete callback');
                    if (err) {
                        // if error then initialization fails check for error message
                    } else {
                       // initialization successful.
                    }
                }
            });
        }
    </script>
```
These options are all required:

**API_KEY** – an application's unique key, please contact us at support@spinfluence.co<br>

**authPageUrl** – The Authentication page, in case of auth fail we will redirect user to this page.<br>

**complete** – a function(err, data) that will be called when initialization is complete.<br>

### User Registeration

```markdown
<script type="text/javascript">
        HA.performRegister({
            first_name: '',
            last_name: '',
            email: '',
            password: '',
            complete: function (err, data) {
                if (err) {
                    // if error then registeration fails take action based on message.
                } else {
                    // registration successfull, verification email has been send once that is done proceed with login.
                    // here disply message received in callback data field and go to login.
                }
            }
        });
</script>
```

These all fields are required:
    
**first_name** – first name of the user. <br>

**last_name** – last name of the user. <br>

**email** – email address of the user. <br>

**password** – password.<br>

**complete** – a function(err, data) that will be called when registration is complete.<br>


### User Login

```markdown
    <script type="text/javascript">
        HA.performLogin({
            email: '',
            password: '',
            complete: function (err, data) {
                if (err) {
                    // if error then attempt to login failed, display reason of failuare using err.
                    // here remain on login screen only.
                } else {
                    // login successful redirect to main screen.
                }
            }
        });
    </script>
```

**email** – email.<br>

**password** – password.<br>

**complete** – a function(err, data) that will be called when login is complete.<br>


### User Logout
    
```markdown
<script type="text/javascript">
    HA.logout();
</script>
```

### Resend Email Verification (if required)

```markdown
<script type="text/javascript">
    HA.resendVerificationMail({
        email: '',
        complete: function (err, data) {
            if (err) {
                // error while sending verification email, check error.
            } else {
                // verification email has been sent successfully, check your email.
            }
        }
    });
</script>
```

**email** – email address of the user for which email verification is pending.<br>

**complete** – a function(err, data) that will be called when registration is complete.<br>


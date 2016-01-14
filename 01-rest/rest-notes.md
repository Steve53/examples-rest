## Get credentials

In the console, in your project, generate credentials. You get a client ID and a client secret.

Example:

    ID
    909556354503-0ohcs6d5rvdfurjtkibes7ggo8omo2s7.apps.googleusercontent.com
    Secret
    _6kFOujjY8amfUzFRutCn8_b
    




    
## Request a code

Provide your client ID and a list of scopes.

    curl -d "client_id=<id>&scope=email profile" https://accounts.google.com/o/oauth2/device/code

    curl -d "client_id=909556354503-0ohcs6d5rvdfurjtkibes7ggo8omo2s7.apps.googleusercontent.com&scope=email profile" https://accounts.google.com/o/oauth2/device/code


The response looks like this:

    {
      "device_code" : "TKEC-DKTB4/xVA8YjRJOR5ws3wQskjT3X-ef0j_wm0kv6--XSWSZxA",
      "user_code" : "TKEC-DKTB",
      "verification_url" : "https://www.google.com/device",
      "expires_in" : 1800,
      "interval" : 5
    }

In a browser, go to the verification URL, enter the user code, and sign in.


## Request a token

Do this soon after you request a code.

    curl -d "client_id=<id>&client_secret=<secret>&code=<code>&grant_type=http://oauth.net/grant_type/device/1.0" https://www.googleapis.com/oauth2/v4/token

    curl -d "client_id=909556354503-0ohcs6d5rvdfurjtkibes7ggo8omo2s7.apps.googleusercontent.com&client_secret=_6kFOujjY8amfUzFRutCn8_b&code=TKEC-DKTB4/xVA8YjRJOR5ws3wQskjT3X-ef0j_wm0kv6--XSWSZxA&grant_type=http://oauth.net/grant_type/device/1.0" https://www.googleapis.com/oauth2/v4/token

Here's our access token:

    {
     "access_token": "ya29.aQJfYcFvQW1Vnr1MCslt2nP7lpL3HeVsRFGrKLgMCsEvzPySC5TqbAM62E1X_wUK5s-G",
     "token_type": "Bearer",
     "expires_in": 3600,
     "refresh_token": "1/Xumngm3TmbqcoNG3I0KvFS0xZldBg9Gcorf_o9zkg2c",
     "id_token": "<big-long-thing>"
    }



## Call an API

    curl https://www.googleapis.com/gmail/v1/users/<user-id>/history&access_token=<token>

    curl https://www.googleapis.com/gmail/v1/users/stevepe/history&access_token=ya29.aQJfYcFvQW1Vnr1MCslt2nP7lpL3HeVsRFGrKLgMCsEvzPySC5TqbAM62E1X_wUK5s-G

Note: In this example, I get code 401, Login Rerquired. Investigate.










## References

[Using OAuth 2.0 for Devices](https://developers.google.com/identity/protocols/OAuth2ForDevices?hl=en)


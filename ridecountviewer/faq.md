# FAQ

### All the names of bedrock players are shown as "Unknown". How to fix?

To look up the names of offline bedrock players, we use an API. This API requires a token to work. You can claim a token like this:

1. Go to [XAPI registration](https://xapi.us/register) and fill in the form. The Free plan should work just fine, as we store player names in cache. Then check your email to verify your account.
2. [Sign in](https://xapi.us/login) to your account. Then login to your Xbox Live account on the Profile page. You can use the OAuth or fill in your account details manually.
3. Copy the **API Token**, go to your server files, and then to /plugins/ThemeParkRidecountAddon/config.yml, and paste it at **XAPIToken**.
4. Done! Restart your server, and now you should see the correct player names for Bedrock players.

_**Pay attention! Because of privacy reasons, if the player has disabled viewing their name for non-friends, you can only view their name if you are a friend of them.**_


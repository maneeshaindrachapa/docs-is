# Multi Attribute Login

WSO2 Identity Server can be configured to use multiple attributes as the login identifier. 
By default, WSO2 Identity server uses the username as the login identifier.  First, you need to
configure WSO2 identity server for multi attribute authentication. The following section explains
how to configure this.

## Configuring WSO2 IS for Multi Attribute Login

1.  Log in to the [WSO2 Identity Server Management Console](`https://<IS_HOST>:<PORT>/carbon`) using your 
    tenant credentials.

    !!! info
        'admin' is the default administrative user in WSO2 Identity Server.
   
    !!! info
        If you use multiple tenant domains, you need to configure the multi attribute login tenant-wise.

2.  Click **Main** > **Identity Providers** > **Resident** and expand the **Account Management** section.

3.  Expand **Multi Attribute Login** and select **Enable Multi Attribute Login**.

4.  Add claim URIs which allow for multi-attribute login in the given text box.


    ![adding-claims-for-multi-attribute-login](../assets/img/learn/multi-attribute-login/adding-claims-for-multi-attribute-login.png)

5. Add Regular Expression for Allowed Claims.

    Once you have configured WSO2 Identity Server for multi attribute login, you need to provide regular expression 
    for the allowed claims.
    Some claims have a default regex. If they don't, you need to provide it.

    1.  Open the WSO2 Identity Server Management Console. 
    2.  In the **Main** menu, click **List** under **Claims**.
    2.  Select the claim you want to provide the regular expression for and click **Edit**.
    3.  Enter the regex pattern under the **Regular Expression** field.
    4.  Click **Update** to save the changes.

    ![adding-regex-pattern-to-claims](../assets/img/learn/multi-attribute-login/adding-regex-pattern-to-claim.png)

    Here are a few examples for regex patterns.

    | Claim URI                           | Example Regex pattern    |
    |-------------------------------------|-----------------------------------------------------------------|
    | http://wso2.org/claims/emailaddress | ^([a-zA-Z0–9_\.\-])+\@(([a-zA-Z0–9\-])+\.)+([a-zA-Z0–9]{2,4})+$ |
    | http://wso2.org/claims/telephone    | ^(\+\d{1,2}\s?)?1?\-?\.?\s?\(?\d{3}\)?[\s.-]?\d{3}[\s.-]?\d{4}$ |
    | http://wso2.org/claims/username     | ^[a-zA-Z0–9._-]{3,}$                                            |

You have now successfully set up WSO2 Identity Server to enable multi-attribute login.

### Try it out

This feature is supported via the following flows. So you can try multi attribute login feature 
using any of following flow. 

1. Identifier first authenticator
2. Basic Authenticator
3. Request path authenticator
4. Authentication REST APIs
5. Oauth Password grant
6. Password recovery flow

!!! Note "What happens if two users use the same value for the same claim?"
    If two users use the same value for the same claim, the multi attribute login feature
    does not support those claims for those users. Retaining the uniqueness of claim values avoids this conflict.

!!! info "Related Topics"
    See the [Configuring Uniqueness of Claims](../../learn/configuring-uniqueness-of-claims) topic for more information.

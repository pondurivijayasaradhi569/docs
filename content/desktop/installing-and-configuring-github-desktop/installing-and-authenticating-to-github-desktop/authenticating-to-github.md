---
title: Authenticating to GitHub
shortTitle: Authentication
intro: 'You can securely access your account''s resources on {% data variables.product.prodname_desktop %} by authenticating to {% data variables.product.prodname_dotcom %}.'
redirect_from:
  - /desktop/getting-started-with-github-desktop/authenticating-to-github-using-the-browser
  - /desktop/getting-started-with-github-desktop/authenticating-to-github
  - /desktop/installing-and-configuring-github-desktop/authenticating-to-github
versions:
  fpt: '*'
---
## About authentication

To keep your account secure, you must authenticate before you can use {% data variables.product.prodname_desktop %} to access resources on {% data variables.product.prodname_dotcom %}.

Before you authenticate, {% data reusables.desktop.get-an-account %}

{% mac %}

## Authenticating an account on {% data variables.product.prodname_dotcom %}

{% data reusables.desktop.mac-select-desktop-menu %}
1. In the "Preferences" window, on the **Accounts** pane, click the **Sign In** button next to "{% data variables.product.prodname_dotcom_the_website %}".

   ![Screenshot of the "Accounts" pane in the "Preferences" window. Next to "GitHub.com", a button, labeled "Sign In", is outlined in orange.](/assets/images/help/desktop/sign-in-github.png)
{% data reusables.desktop.sign-in-browser %}
{% data reusables.desktop.authenticate-in-browser %}
{% data reusables.desktop.2fa-in-browser %}
1. After {% data variables.product.prodname_dotcom %} authenticates your account, follow the prompts to return to {% data variables.product.prodname_desktop %}.

## Authenticating an account on {% data variables.product.prodname_ghe_server %}


{% data reusables.desktop.mac-select-desktop-menu %}
1. In the "Preferences" window, on the **Accounts** pane, click the **Sign In** button next to "{% data variables.product.prodname_enterprise %}".

   ![Screenshot of the "Accounts" pane in the "Preferences" window. Next to "GitHub Enterprise", a button, labeled "Sign In", is outlined in orange.](/assets/images/help/desktop/sign-in-ghes.png)
1. To add an account on {% data variables.location.product_location_enterprise %}, in the "Sign in" modal window, type the URL for your instance under "Enterprise address," then click **Continue**.
{% data reusables.desktop.sign-in-browser %}
1. To authenticate to {% data variables.location.product_location_enterprise %} account, type your account credentials and click **Sign in**.

  Alternatively, if you were already signed in to {% data variables.location.product_location_enterprise %} account, follow the prompts to return to {% data variables.product.prodname_desktop %} to finish authenticating. 

{% endmac %}

{% windows %}

## Authenticating an account on {% data variables.product.prodname_dotcom %}

{% data reusables.desktop.windows-choose-options %}
{% data reusables.desktop.windows-select-accounts %}
3. To the right of "GitHub.com," click **Sign in**.
  ![Screenshot of the "Accounts" pane in the "Preferences" window. Next to "GitHub.com", a button, labeled "Sign In", is outlined in orange.](/assets/images/help/desktop/sign-in-github.png)
{% data reusables.desktop.sign-in-browser %}

  {% data reusables.user-settings.password-authentication-deprecation-desktop %}

{% data reusables.desktop.authenticate-in-browser %}
{% data reusables.desktop.2fa-in-browser %}
7. After {% data variables.product.prodname_dotcom %} authenticates your account, follow the prompts to return to {% data variables.product.prodname_desktop %}.

## Authenticating an account on {% data variables.product.prodname_enterprise %}


{% data reusables.desktop.windows-choose-options %}
{% data reusables.desktop.windows-select-accounts %}
{% data reusables.desktop.choose-product-authenticate %}
4. To add a {% data variables.product.prodname_enterprise %} account, type your credentials under "Enterprise address," then click **Continue**.
  ![The Sign In button for GitHub Enterprise](/assets/images/help/desktop/windows-sign-in-button-enterprise.png)
{% data reusables.desktop.retrieve-2fa %}

{% endwindows %}

## Troubleshooting authentication issues

If {% data variables.product.prodname_desktop %} encounters an authentication error, you can use error messages to troubleshoot.

If you encounter an authentication error, first try signing out and signing back in to your account on {% data variables.product.prodname_desktop %}.

For some errors, {% data variables.product.prodname_desktop %} will prompt you with an error message. If you are not prompted, or to find more information about any error, view the {% data variables.product.prodname_desktop %} log files by using the following steps.

{% mac %}

1. In the menu bar, select **Help**, then click **Show Logs in Finder**.
  ![Screenshot of the "GitHub Desktop" menu bar on a Mac. Under the open "Help" dropdown menu, a cursor hovers over "Show Logs in Finder", highlighted in blue.](/assets/images/help/desktop/mac-show-logs.png)
2. Select the log file from the date when you encountered the authentication error.

{% endmac %}

{% windows %}

1. Use the **Help** drop-down menu and click **Show Logs in Explorer**.
  ![The Show Logs in Explorer button](/assets/images/help/desktop/windows-show-logs.png)
2. Select the log file from the date when you encountered the authentication error.

{% endwindows %}

Review the troubleshooting information below for the error message that you encounter.

### Bad credentials

```shell
Error: Bad credentials
```

This error means that there is an issue with your stored account credentials.

To troubleshoot, sign out of your account on {% data variables.product.prodname_desktop %} and then sign back in.

### Empty token

```shell
info: [ui] [AppStore.withAuthenticatingUser] account found for repository: node - USERNAME (empty token)
```

This error means that {% data variables.product.prodname_desktop %} is unable to find the access token that it created in the system keychain.

To troubleshoot, sign out of your account on {% data variables.product.prodname_desktop %} and then sign back in.

### Repository not found

```shell
fatal: repository 'https://github.com/<user>/<repo>.git' not found

(The error was parsed as 8: The repository does not seem to exist anymore. You may not have access, or it may have been deleted or renamed.)
```

This error means that you do not have permission to access the repository that you are trying to clone.

To troubleshoot, contact the person in your organization who administers permissions.

### Could not read from remote repository

```shell
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.

Please make sure you have the correct access rights and the repository exists.
```

This error means that you do not have a valid SSH key set up.

To troubleshoot, see "[AUTOTITLE](/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)."

### Failed to clone

```shell
fatal: clone of 'git@github.com:<user>/<repo>' into submodule path '<path>' failed
Failed to clone 'src/github.com/<user>/<repo>'. Retry scheduled
Cloning into '<path>'...
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.
Please make sure you have the correct access rights
and the repository exists.
```

This error means that either the repository that you are trying to clone has submodules that you do not have access to or you do not have a valid SSH key set up.

If you do not have access to the submodules, troubleshoot by contacting the person who administers permissions for the repository.

If you do not have a valid SSH key set up, see "[AUTOTITLE](/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)."

{% windows %}

### Unable to read AskPass response

```shell
error: unable to read askpass response from '/Users/<path>/GitHub Desktop.app/Contents/Resources/app/static/ask-pass-trampoline.sh'
fatal: could not read Username for 'https://github.com': terminal prompts disabled
```

This error can be caused by multiple events.

If the `Command Processor` registry entries are modified, {% data variables.product.prodname_desktop %} will respond with an `Authentication failed` error. To check if these registry entries have been modified, follow these steps.

1. Open the Registry Editor (`regedit.exe`) and navigate to the following locations.
  `HKEY_CURRENT_USER\Software\Microsoft\Command Processor\`
  `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Command Processor\`
2. Check to see if there is an `Autorun` value in either location.
3. If there is an `Autorun` value, delete it.

If your Windows username has extended Unicode characters, it may cause an AskPass response error. To troubleshoot, create a new Windows user account and migrate your files to that account. For more information, see "[Create a user account in Windows](https://support.microsoft.com/en-us/help/13951/windows-create-user-account)" in the Microsoft documentation.

{% endwindows %}

## Further reading
- "[AUTOTITLE](/authentication/keeping-your-account-and-data-secure/about-authentication-to-github)"

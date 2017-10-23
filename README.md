sheetmonkey
======
**SheetMonkey** is an experiment enables simple JavaScript plugins to extend [Smartsheet](https://www.smartsheet.com/) in a secure, modular fashion without DOM hacks.

**Disclaimer:** This project is not endorsed, certified, or supported by [Smartsheet](https://www.smartsheet.com/). This is merely an experiment I'm playing around with.

## About ##
Sheetmonkey provides the following benefits to **developers**:
* Extend the Smartsheet app inside of the browser with new buttons or menu items.
* Use only JavaScript
* Get information about the current Sheet, Sight, or Report using a clean JavaScript API.
* Call the Smartsheet API, using your own registered API Client without writing any backend code (not event to store tokens).

Sheetmonkey provides the following benefits to **end users**:

* Take advantage of the Smartsheet community's innovation on top of Smartsheet
* An easy to use [gallery if plugins](https://beta.sheetmonkey.com) is available
* Sheetmonkey plugins are isolated from the end user's core Smartsheet app so that they cannot access your Smartsheet data directly inside of your browser. They will prompt you for permission to your data via the Smartsheet API. So only install and authorize plugins that you trust!

## Usage ##
To start _using_ plugins go to https://beta.sheetmonkey.com/ and it will show you the gallery of the currently available plugins and walk you through installing the Browser Extension if needed.

## How it Works ##
Sheetmonkey is primarily a [Chrome Extension](https://github.com/activescott/sheetmonkey-extension) that abstracts the necessary DOM hacks to provide clean set of events and JavaScript interfaces to write plugins in pure JavaScript. The browser extension sandboxes plugins each into their own iframe and isolates them from the Smartsheet app by leveraging the [same-origin policy](https://en.wikipedia.org/wiki/Same-origin_policy) and [HTML's iframe sandbox attribute](https://html.spec.whatwg.org/multipage/iframe-embed-object.html#attr-iframe-sandbox).

[Sheetmonkey Server](https://github.com/activescott/sheetmonkey-server) also provides a user-friendly gallery of installable plugins, and a (reasonably) secure way to call the Smartsheet REST API from pure browser-based plugins without having to write your own backend. It is reasonably secure because it never allows the Smartsheet API tokens to get into the browser and only allows the tokens to be used via a proxy on the server and only used to call the specific API requests that the plugin developer whitelisted. However, this is all a hacky experiment so don't take the security for granted - read the source!

## Developing Plugins ##
Developing plugins only requires a JSON manifest and simple JavaScript. 

### Examples ###
If you want to get straight to examples, see [the Sheetmonkey-Plugins repository](https://github.com/activescott/sheetmonkey-plugins) for some example plugins.

### Getting Started ###
Take the following steps:

1. Create a manifest (todo: section with more info)
2. Host your manifest (todo: section with more info)
3. Register your plugin with sheetmonkey.com (todo: section with more info)
4. For API Access, you must register at sheetmonkey.com and register the API Client ID & API Client Secret as explained below under **Smartsheet API Access**

### Smartsheet API Access ###
To get Smartsheet API Access do the following:
1. While logged into Smartsheet, select **Developer Tools** from the **Account** menu.
2. Click **Create New App**
3. Fill in the required fields. For **App redirect URL** you can put in any temporary value for now, but you'll come back here to edit it later. Then click **Save**.
4. On the next screen be sure to save **App client id** and **App secret** (remember that App secret should be kept secret!).
5. Go to https://beta.sheetmonkey.com and Login using the menu in the upper right corner.
6. Once logged in, select **My Plugins** from the upper right menu where your Smartsheet email address is.
7. On the My Plugins screen, click **Add** to register your plugin.
8. Enter your manifest URL that is publicly accessible from the Internet and enter the Smartsheet **App client id** and **App secret** you got earlier.
    * Now you should see the **Smartsheet API Redirect URL** for your plugin something like https://beta.sheetmonkey.com/api/pluginauthcallback/https%3A%2F%blah.github.io%2Fmyrepo%2Fmyplugin%2Fmymanifest.json
9. Return to **Developer Tools** in Smartsheet and replace the redirect URL for your app with this one received from sheetmonkey.com.
10. Add `apiClientID` as a root-level property in your manifest file with the value of the client id you received from Smartsheet Developer Tools (NOTE: Do NOT put your client secret in your manifest).


### Manifest ###
**TODO**

### JavaScipt API (SheetmonkeyHost) ###
A plugin's JavaScript code can call APIs on SheetmonkeyHost. Currently SheetmonkeyHost has the following APIs:

**TODO**; In the meantime look at [sheetMonkeyHost.js](https://github.com/activescott/sheetmonkey-extension/blob/master/extension/src/js/sheetMonkeyHost/sheetMonkeyHost.js)




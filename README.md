Last-Instagram-Pic
==================

A simple way to get the last Instagram picture from yourself.
I'm using for my Kindle Viewer.

How to make a Kindle Instagram-Latest Photo Display
---------------------------------------------------

![kindle photo viewer](https://raw.githubusercontent.com/ericoporto/Last-Instagram-Pic/master/img/kindleexample.jpg)

So, I've read the [Share Messages via Kindle on Fridge][1], and had the idea for
something similar: display the last pic I've uploaded to Instagram on my Kindle.
The catch: do it without Raspberry Pi - I've just moved and my Pi and most of my
things are in my mom's house. This is how I've done it, if you have a better
approach, please tell me, because this one has it's problems.

So the idea here is to get the latest pic, display in html, and refresh from
time to time. Simple, and compatible with the Kindle's experimental browser.

[1]:https://petervojtek.github.io/diy/2015/07/28/share-messages-with-kindle-on-fridge.html

### Step 1: get an access token

You could theoretically use https://www.instagram.com/USER_ID/media/?size=L to
get the latest pic from a user, but I'm getting [CORS][2] errors, so the way we
will be requiring data requires an access token. Getting an access token will be
like described in the [api docs][3], on Client-Side (Implicit) Authentication.

The step-by-step of this is described here:
http://jelled.com/instagram/access-token .

Once you have an access token, replace the ACCESSTOKEN in the [html][4], with it.
Note that your access token should be kept as private as possible, since this
enables making requests to Instagram in the name of the client you just
registered.

[2]:https://en.wikipedia.org/wiki/Cross-origin_resource_sharing
[3]:https://www.instagram.com/developer/authentication/
[4]:https://github.com/ericoporto/Last-Instagram-Pic/blob/master/index.html

### Step 2: place this html in somewhere accessible from your Kindle

The access token can't be in somewhere public, because it would be public too.
But, the app I registered in the Instagram API can't do much, so I will just
throw it in my Dropbox Public folder, inside a folder that has a random number,
and inside another one. Since the URL is complicate, I'm counting no one is
guessing this URL soon.

### Step 3: disable Kindle Screen Saver

This can be easily achieved entering debug mode.

![How to type debugOn](https://raw.githubusercontent.com/ericoporto/Last-Instagram-Pic/master/img/typedebugon.jpg)

 1. Press the Home button to go the the Kindle home screen
 2. Press the keyboard button to display the virtual keyboard
 3. Type `;debugOn` and press Enter button (not the Done button)
 4. Type `~disableScreensaver` and press Enter.
 5. Type `;debugOff` and press Enter button.

If you ever just want to reenable your screensaver, you can reverse with:

 1. Type `;debugOn` and press Enter button (not the Done button)
 2. Type `~resumeScreensaver` and press Enter.
 3. Type `;debugOff` and press Enter button.

### Step 4: open the browser

So, now just open the browser, it's in the home screen, press the menu button,
and go to experimental, under settings.

![Where is the browser](https://raw.githubusercontent.com/ericoporto/Last-Instagram-Pic/master/img/whereisbrowser.jpg)

In the browser, open the url for where you saved your html.
Mine url is something like this:
https://dl.dropboxusercontent.com/u/USERHASH/FOLDERIPLACEDINPUBLIC/index.html

Done. Now you can do mod and enhance this.

Note
----

 - My kindle is resting in landscape position, so that's why I'm rotating the
image, you can disable this by removing `class='rotate90'` from the **img tag**.

 - I had no problems with this, but I'm not responsible for anything that happens
to your Kindle or your Instagram account.

 - If you are curious of the other commands on the kindle, here they are:

![~help](https://raw.githubusercontent.com/ericoporto/Last-Instagram-Pic/master/img/alldebugcommands.jpg)

Have fun!

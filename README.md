# ZappBar

Automagically adds responsive, customizable mobile UI to (almost) any WordPress theme.

**Version:** 0.2

**Requires WordPress Version:** 3.5 or higher, PHP 5+

**Compatible up to:** 4.3

**Alpha Version Disclaimer**

This plugin is still being tested is incomplete!  Do not use it in production unless you can live without the things it is missing and are willing to accept the possibility that it could screw up your website.  Things left on To-Do list:

* option to clear/reset settings
* auto-update from repository
* make it more awesome!

## Description

I got tired of making the _same_ responsive layout modifications to different WordPress themes over and over again and I wanted an easy way to create and modify a custom interface for mobile devices.  So I rolled all the stuff I was doing manually into a single plugin! ZappBar adds highly configurable mobile app style button bars to the top and bottom of any WordPress theme.  You can decide at what screen/browser widths they activate (so you can show them only for phones or tablets without altering your site for desktop users).  This plugin can also *try* to convert non-responsive themes to responsive layouts that auto-adjust for mobile devices and it can *try* to fix some mobile layout issues that bugged me about the WordPress admin backend too.

## Installation

1. Download the GitHub archive as a ZIP file.  
2. Unzip it, knock the “-master” off the folder’s filename
3. FTP upload it into your WordPress blog’s _~/wp-content/plugins/_ folder.
4. Go to your _Dashboard > Plugins_ and activate “ZappBar”
5. Go to _Dashboard > Settings > ZappBar_ to configure it.


## Settings

### Site Layout

**Theme Layout:** 
* Theme is already responsive (so ZappBar shouldn’t try to “fix” it)
* Make theme responsive when ZappBars are displayed (if possible)
* Make theme responsive even when ZappBars are not displayed (if possible)

The latter two options will _try_ to adjust a non-responsive theme so that it behaves like a responsive layout (auto-adjusting to different screen sizes).  This works best when the theme is using standard class names and IDs for the theme parts, though you can try using “Custom Settings” (see below) to tell ZappBar how to find those elements.

**Theme Sidebars:** Themes often have sidebars in them.  On narrow screen devices these can be a problem if the theme isn’t responsive.  If you told ZappBar to “Make theme responsive” now tell it what it should do with any sidebar containers it finds:

* Try to MOVE sidebar(s) below the main content on mobile devices
* Try to HIDE sidebar(s) but only from narrow mobile screens
* Try to HIDE sidebar(s) whenever ZappBars are being displayed

**Admin Mobile Layout:** In my opinion the default, back-end Admin area layout on mobile devices like tablets and phones looks awful.  ZappBar can also try to tweak the back-end layout so it looks and works better (WordPress 3.8.1 or later only).

**WP Admin Bar:** check this box to disable the Admin Toolbar on the FRONT end of the website (this would be the bar across the top of a website when you are logged into it).

**ZappBars On Screen Size:** This is where you decide what size of screens will use the ZappBar user interface and which sizes won’t

* None (use this when you are setting up ZappBar)
* &lt; 736px wide (Phones) - this should work for most phones in portrait/landscape.
* &lt;1024px wide (Tablets & Phones) - up to “iPad” sized screen rendering, but many Android tablets will show ZappBars in portrait but not in landscape.
* &lt;1280px wide (Tablets & Phones) - should work for most Android tablets in both portrait/landscape.
* &lt;1440px wide (HD Tablets & Phones) - should work on Surface tablets
* &lt;1920px wide (Phones, Tablets, 720p HD Desktops) - should work on any screen that is UNDER “Full HD” resolution.
* All Screen Sizes - applies ZappBars regardless of screen size.

**Apply ZappBars On:** This is where you decide what DEVICES of the screen size(s) you set above will have ZappBars applied to them:

* All Devices By Screen Size - exactly what it sounds like.
* ONLY Mobile Devices by Screen Size - tries to exclude Desktops and Laptops.
* ONLY Mobile Devices & FORCE ZappBars - ignores screen size and acts like “All Screen Sizes” but ONLY on Mobile devices.
* Desktops by Screen Size & Force Mobile Devices to use Zappbars - the screen size(s) selected above will be used on Desktops and Laptops, but Mobile devices will have ZappBars applied regardless of the device screen size.

_“Mobile Only” uses device detection, which can be spoofed.  “Force” ignores screen size selection._

**When ZappBars are Included:** additional, optional, modifications to the theme layout:

* Hide Entire `<header>` Section - this is typically where the site masthead is and may also contain desktop navigation or custom widgets.
* Hide regular site navigation - if the desktop navigation can’t be hidden by hiding the `<header>` section, or if there is a mobile nav menu that is part of the theme but is redundant when ZappBars are in use.
* Convert Comment Form to App Panel - normally there is just a simple form below blog posts for people to comment.  This turns it into a slide-in panel (you’ll probably also want to link a button to opening this panel or people won’t be able to comment when ZappBars are in use).
* Push _#page_ element over when App Panel is open - normally the panels slide in from the sides and overlay the page content.  Check this box to, instead, push the page content over when the panel slides into view.

**App Icon Image:** An optional icon or logo image that would be used as the favicon and/or the icon when bookmarked to the home screen of a mobile device (on devices that support it).

**Splash Image:** If you want your site to look even _more_ like an app on mobile devices you can add an image to use as the “Splash” when visitors come to your site on phones or tablets.  Whatever image you select is shown, centered and scaled, against whatever background color you’ve set for panel backgrounds.  This only displays ONCE at the start of a new user session (or it would be pretty annoying).

**Splash Image Fit:** If you included a splash image this adjusts how the image is scaled on that splash screen:

* Do NOT scale splash image, use the original size (may be cut off)
* Scale Splash Image to FIT if image is larger than screen space (pretty self-explanatory)
* Scale Splash Image to FILL all available screen space (may be cut off)

**Splash Timer:** select the amount of time to display the Splash screen (users can always clear it sooner by clicking on it).

**Splash Link:** If you are using the Splash screen to show an advertisement you can enter a URL target for the ad here.

**CUSTOM SETTINGS**

If you are using a theme that doesn’t use the typical class names or IDs for the parts of the layout you’ll need to tell ZappBar what they are:

* Header Target - typically whatever holds the site’s name/masthead.
* Navigation Target - the main navigation menu container
* Comment Target - element that contains blog post comment form
* Page Target - the main page content container
* Sidebar Targets - a comma-separated list of classes and/or IDs for sidebar elements (some may be part of the theme, others may have been added by plugins).
* Always Hide - comma-separated list of classes/IDs for anything _else_ you want hidden whenever the ZappBars are displayed.
* Comic Navigation - (only shown if using a supported comics theme/plugin) you can choose to HIDE the default comic navigation when ZappBars are displayed.

### Social Media

ZappBar has it’s own Social Media functions to make is easy for people to share your site on their social media feeds.  However, if you are already using another plugin on your site that adds social/sharing meta tags (such as Yoast SEO) that meta may be injected _before_ ZappBar’s in which case it will be read first by the social media site(s).

**Default Facebook Image:** If a post has no “Featured Image” this is the image that will be displayed as the thumbnail when somebody shares the link on Facebook (if left blank ZappBar will _not_ inject _any_ Facebook `<meta>` tags).

**Twitter ID:** Enter the @ Twitter ID associated with your blog (if any).  If you leave this blank then no Twitter `<meta>` tags will be injected.

**Phone Number:** If you intend to link a ZappBar button to the “Phone” action this is the phone number that will be inserted into the on-screen notice box.

**E-Mail Address:** If you link a ZappBar button to “E-Mail Contact” this is the e-mail address to which the message will be sent.  If you want people to e-mail the site administrator set your button action to “E-mail Admin” and it will use the address on your blog’s _Settings > General_ page.

**Social Media Panel:** Enable/Disable buttons for various social media websites:

* Facebook
* Twitter
* Google Plus
* Reddit
* StumbleUpon
* Digg
* LinkedIn
* Pinterest
* Del.icio.us
* RSS Feed
* Share via E-Mail

**Social Shortcode:** you can invoke this same list of social media links anywhere on your site, even when ZappBars are not being shown, by using the shortcode *_[zb-share]_* which accepts the following parameters:

* type=“text” - simple text-only links.
* type=“label” - (default) buttons with both a small icon and text label.
* type=“small” - 16x16 icons as button, spaced far enough apart to be clickable on mobile devices.
* type=“medium” - 24x25 icons as buttons
* type=“large” - 32x32 icons as buttons
* include=“twitter,linkedin…” - comma-separated list limiting which social media sites will be included.
* exclude=“facebook,pinterest…” - comma-separated list of which social media sites to exclude.

### ZappBar Colors

You can use either an external stylesheet (and then give the FULL URL to it) or you can set individual item colors from within the plugin.

_(the color options in the plugin are pretty self-explanatory, so they won’t be covered in this README)_

### ZappBar Panels

If you set a Custom Stylesheet on the *ZappBar Colors* tab everything on this tab will be ignored.  Otherwise you can define how the ZappBar styles will look and work here.

**Menu Panel:**  The “Menu” Panel is the replacement mobile-style navigation menu for your site when ZappBars are being displayed.  These settings determine how the menu items in that panel will be shown:

* Indent sub-items - moves sub-pages/sections over to make it obvious they are part of the parent item.
* Flatten List - no items (even if they’re subsections) will be indented.
* Show top-level Items Only - Parent items with subsections will only show the parent.  No sub-items will be shown in the menu.

**Sidebar Panels:** If you do not plan to link buttons to open/close the sidebar panels users will need some way to open/close them.  If this setting is enabled it will overlay your site, left and right, with two tabs which can be used to open/close the left/right panels.

**Use Bar Styles for Panels:** Automatically uses the *ZappBar Colors* settings for the Panels too (which saves you having to repeat it all if you want them to look the same).  If checked all the visual settings below this in the tab section are ignored.

_(the color and style options for the panels are also fairly self-explanatory so they won’t be covered in this README)_

### ZappBar Layout

This tab section shows you editable previews of what the ZappBars will look like on the front-end of your website.

**Button Layout:** Determines the position of the five buttons on the ZappBars:

* Evenly Spaced
* Centered and Outside
* Four Left, One Right
* Five Left
* One Left, Four Right
* Five Right

**ZappBar Search Box:** Normally the ZappBar “Search” field has a “Submit” button after it.  If you want a cleaner look you can hide the “Submit” button and have it automatically submit on hitting Enter/Return.

**Logo Icon:** (optional) Select an image to be your logo icon and then set one of the buttons to “logo” to display it (the image will be scaled to fit on the button).

**Default Top/Bottom ZappBar:** Shows a preview of the default top bar.  Click on a button to change the icon and text.  Click on the “Show Button Actions” below it to “wire” a button to an action in the drop-down lists.

**Top/Bottom Archive ZappBar:** Determines whether the Default top/bottom bar is used on Archive pages or the custom “Archive Top/Bottom ZappBar” will be used instead.

**Archive Top/Bottom ZappBar:** these bars will ONLY appear on an Archive page on your blog, and only if you enabled them under *Top Archive ZappBar* and/or *Bottom Archive ZappBar*

If you are using the ComicPress theme, Comic Easel plugin, or Webcomic plugin more bar options are displayed for the custom comic post pages:

**Top/Bottom Comic ZappBar:** Choose whether to use the custom “comic” bars on comics pages or the Default ones.

**Comic Top/Bottom ZappBar:** optional bars you can have displayed only on comic post pages (if you are using one of the aforementioned comic themes/plugins).

If you are using the WooCommerce plugin you will also see options for custom e-commerce ZappBars:

**Top/Bottom WooCommerce ZappBar:** set whether to use custom or default bars on WooCommerce store-related pages.

**WooCommerce Top/Bottom Bar:** optional bars and buttons you can link to WooCommerce functions.

**WooCommerce Site:** tell ZappBar to further alter you e-commerce pages:

* Convert Woo Review to App Panel - moves the “Reviews” section out of the main page content and into a slide-in panel.
* Convert Woo Product Description to App Panel - moves the product description block into a slide-in panel.
* Convert Woo Additional Product Info to App Panel - moves “Additional Info” block into a slide-in panel.

## Changelog

Version 0.2

* [Issue #1] Responsive stylesheets updated to support HD Android and Surface tablets, iPhone 6.  Application is now a two-step process by screen size and/or device
* [Issue #2] Disable Admin Toolbar no longer disabled by default.
* [Issue #3] Show/Hide/Convert theme elements overhauled (now allows deselecting all), `zappbar.js` script updated with better apply/unapply action.
* [Issue #4] Updated to PHP 5 Constructors
* [Issue #4] Fixed numerous Notices of undefined variables
* Added “Force” and “Only” over-rides for Mobile devices so you can now (fairly) reliably apply it just to phones and tablet while leaving your Desktop theme untouched.
* Added “retrofit” option to try to make non-responsive themes responsive even when ZappBars are not being shown.
* `zappbar.js` script updated with better device detection.
* Fixed “Hide Comic Navigation” checkbox
* Added github-updater plugin code to plugin header
* Responsive layout fixes for ComicPress 4.3
* Fixed misaligned comic post receiving comic archive styling
* Fixed undefined index social_panel and settings
* Fixed missing default button bg opacity variable on activation

Version 0.1

Initial public release.

## Resources

This uses my [Icon Picker](https://github.com/kmhcreative/icon-picker) (which is based on [Dashicons Picker](https://github.com/bradvin/dashicons-picker) by Brad Vincent) to get/set the icons on the ZappBars.

[ComicPress 2.9 Theme](http://comicpress.org/)

[ComicPress 4.x Theme](https://github.com/Frumph/comicpress)

[Webcomic Plugin](https://wordpress.org/plugins/webcomic/)

[WooCommerce Plugin](https://wordpress.org/plugins/woocommerce/)


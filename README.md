## What is jDrupal?

> A simple Vanilla JavaScript Library and API.

## What is jDrupal used for?

> Drupal 7 Application Development.

## What kind of apps?

> A variety of application architectures, including...

- Mobile Applications (Android, iOS, etc)
- Web Applications
- Headless Drupal / Decoupled Drupal
- [PhoneGap](http://phonegap.com/) ([Cordova](https://cordova.apache.org/))

## jDrupal...

- solves many common development needs for Drupal based applications.
- provides a familiar Drupal coding experience and syntax for developers.
- runs alongside any frontend client side framework, or with no framework at all.

Since jDrupal has no dependencies and is written in pure JavaScript, it can be used in a wide variety of architectures and frameworks. Just include it in the `<head>` of your app's `index.html` file:

```
<html>
  <head>
    <!-- ... -->
    <script src="jdrupal.min.js"></script>
    <!-- ... -->
  </head>
  <body><!-- ... --></body>
</html>
```

## Quick Examples

```
// Connect to Drupal and say hello to the current user.
system_connect({
  success: function(result) {
    var msg = jDrupal.user.uid == 0 ?
        'Hello World' : 'Hello ' + jDrupal.user.name;
    alert(msg);
  }
});
```

```
// Load a node and display the title.
node_load(123, {
  success: function(node) {
    alert(node.title);
  }
});
```

```
// Login and show the user their id.
user_login("bob", "secret", {
  success: function(result) {
    alert(jDrupal.user.id);
  }
});
```

## Getting Started

- [Hello World](http://jdrupal.tylerfrankenstein.com/7/docs/Hello_World)

> jDrupal is best friends with [DrupalGap](http://drupalgap.org), the open source application development kit for Drupal websites.

## Custom Entity Types

By installing the [Services Entity](https://www.drupal.org/project/services_entity) module in Drupal, jDrupal can easily support all custom Entity Types. Just add something like this to your `settings.js` file, utilizing your entity machine name(s) instead:

```
/** SERVICES ENTITY **/
jDrupal.services_entity = {
  types: {
    invitation: { },
    food: {}
  }
};
```

Then it's easy to perform `C.R.U.D.` operations on custom entities:

```
// Retrieve.
entity_load('invitation', 123, {
  success: function(invitation) {
    console.log(invitation);
    alert('Loaded invitation: ' + invitation.id);
  },
  error: function(xhr, status, msg) { alert(msg); }
});
```

## Cordova + iOS

If you're developing an iOS app using cordova, follow [these additional instructions](https://github.com/signalpoint/jDrupal/issues/87#issuecomment-775488402).

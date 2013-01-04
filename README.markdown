# jPushover

jPushover is a wrapper for the [Pushover API](http://pushover.net/api) that allows Java applications to send and receive Push notifications on mobile devices through the Pushover platform.

jPushover is perfect for small projects that just need one or two things that don't want to deal with posting to HTTPS endpoints but still want mobile device notifications.

====

## Usage

Simply add [Pushover.jar](https://github.com/nicatronTg/jPushover/blob/master/Pushover.jar) to your project's build path, and instantiate a new Pushover object. It's worth nothing that you first need a Pushover application key, free from [Pushover's website](https://pushover.net/apps).


````
Pushover p = new Pushover(applicationKey, userKey);
try {
    p.sendMessage("Hello, Pushover!");
} catch (IOException e) {
    e.printStackTrace();
}
````

An optional device string can be supplied as a third argument to the constructor, which will allow for device specific targeting.

### Pushover Method Signatures

jPushover relies heavily on overloads for the sake of simplicity.

````
public String sendMessage(String message)
public String sendMessage(String message, String title)
public String sendMessage(String message, String title, String url)
public String sendMessage(String message, String title, String url, String urlTitle)

public String sendMessageHighPriority(String message)
public String sendMessageHighPriority(String message, String title)
public String sendMessageHighPriority(String message, String title, String url)
public String sendMessageHighPriority(String message, String title, String url, String urlTitle)
````

## Limitations

* jPushover does not support sending sounds to devices.
* jPushover does not support sending alternative timestamps to devices.
* jPushover does no sanity checking on the lengths of messages. The Pushover API docs set clear limits (255 characters for a message, 30 for a title, and so on), however, so this should be taken care of prior to implementation.
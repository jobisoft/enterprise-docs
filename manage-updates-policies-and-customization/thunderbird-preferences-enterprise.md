---
description: Preferences related to using Thunderbird in enterprises
---

# Thunderbird Preferences Relevant to Enterprises

### New Email Account Provisioning

Account Provisioning allows users to sign up for new email accounts from _gandi.net_ directly from within Thunderbird.

* **mail.provider.enabled**
  * Default: true
  * Default Action: If the user does not have an account set up, they will be presented with an option to sign up for a new account. They may choose to set up an existing account that they hold instead of obtaining a new one.

### Filelink \(cloud attachments\) <a id="Filelink"></a>

Filelink is a feature that allows users to upload big files to various servers and send a link to the attachment in the email, rather than the attachment itself. This has benefits for sending the email, especially when sending to multiple users. The message will be small in size and can be sent and received faster.

Thunderbird offers an option to use WeTransfer as a cloud service. It is possible to set up other providers.

* **mail.cloud\_files.enabled**
  * Default: true
  * Default Action: Prompts the user to see if they wish to send a link for big file attachments, rather than the link itself.

### Chat \(Instant Messaging\) <a id="Instant_Messaging"></a>

Thunderbird's chat component allows the user to access different types of instant messaging accounts.

* **mail.chat.enabled**
  * Default: true
  * Default Action: Enables access to the Instant Messaging user interface in Thunderbird

### Offline Download / Synchronisation  <a id="HTML"></a>

* **mail.server.default.offline\_download**
  * Default: true
  * Default Action: Used to determine if newly created folders are set to take part in offline download or not.
  * Notes: This is the default value for all servers/accounts when the mail.server.server&lt;n&gt;.offline\_download preference is not set.
* **mail.server.server&lt;n&gt;.offline\_download**
  * Default: true
  * Default Action: Used to determine if newly created folders are set to take part in offline download or not.
  * Notes:
    * This value is typically not present unless it has been specifically overridden.
    * Overrides mail.server.default.offline\_download for server&lt;n&gt;

Both preferences now also have the behaviour that if offline\_download is true for an account/server, then on upgrade from Thunderbird 2, all existing IMAP folders will be updated to take part in offline download.

### HTML rendering in message reader

By default all HTML elements are interpreted by the Thunderbird HTML parser. For the message reader, there are some options to control which HTML elements will get rendered. Note that some of these preferences may not be effective for composition, especially when using Edit as New Message or Forward, which may load remote content and media anyway.

* **mailnews.display.html\_as**
  * Default: 0
  * Default Action: Show original HTML
  * Custom values: 1 or 3
  * Notes:
    * This preference can be controlled through the menu: `View`  &gt; `Message Body As` &gt; `Original HTML (0)` \| `Simple HTML (3)` \| `Plain Text (1)` 
    * Original HTML \(0\) renders all elements, subject to global and per-message or per-origin Remote Content Options.
    * Simple HTML \(3\) prevents the display of any remote content. Furthermore, this display mode can be finetuned using the html\_sanitizer preferences below.
    * Plain Text \(0\) prevents the display of remote content and displays HTML downgraded to plain text. 
* **mailnews.display.html\_sanitizer.drop\_media**

  * Default: false
  * Default Action: Allows all media files.
  * Notes:
    * Only applies to messages viewed as Simple HTML \(mailnews.display.html\_as = 3, see above\).
    * To prevent rendering &lt;img&gt;, &lt;audio&gt; and &lt;video&gt; elements, i.e. to prevent images, audios, and videos from being displayed, set this preference to true.
    * The following related pref is obsolete: mailnews.display.html\_sanitizer.allowed\_tags

* **mailnews.display.html\_sanitizer.drop\_non\_css\_presentation**
  * Default: true
  * Default Action: Drop non-CSS presentational HTML elements and attributes, such as &lt;font&gt;, &lt;center&gt; and _bgcolor._
  * Notes:
    * Only applies to messages viewed as Simple HTML \(mailnews.display.html\_as = 3, see above\).

### Disable address book for recipient autocomplete

You may want to disable outdated or unwanted address books for recipient autocomplete when writing a new message. This is possible by creating a custom preference for the address book. The pref name has LDAP, but it works for local address books, too.

1. ≡ &gt; Options &gt; Find in Options &gt; about:config
2. Right-click in config editor &gt; New &gt; Boolean
3. Enter preference name: `ldap_2.servers.TestAB.enable_autocomplete` \(if the name of your AB is "TestAB"\)
4. Enter boolean value: choose `false` ⇒ TestAB will no longer be used for recipient auto-completion.

### Version Upgrades  <a id="Version_Upgrades"></a>

#### Prompt for third-party Add-ons \(untested\)

Note: Starting with Thunderbird 78, traditional add-ons have been discontinued for security reasons. Add-ons are now generally expected to be Web Extensions using the APIs provided by Thunderbird.

* **extensions.autoDisableScopes**
  * Default: 15
  * Default Action: **When upgrading to a build from before Thunderbird 10 to after, the user will be prompted about add-ons installed by third parties.**
  * Notes:
    * This preference is a bit-wise OR of values that control the locations for which add-ons are prompted about as third-parties. **Organizations typically want to set this to 11 if they are installing their own add-ons.** The bit values are as follows:
      * 1: Installed in the profile
      * 2: Installed for all of this user's profile
      * 4: Installed and owned by the Application
      * 8: Installed for all users of the computer




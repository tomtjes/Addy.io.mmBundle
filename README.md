# Addy.io Bundle for MailMate

This bundle provides some functions for emails that were sent to Addy.io aliases. It contains both, a command and a filter. The command is accessible from the Commands menu or in rules. The filter is automatically applied to replies.

## "Restore Headers" Command

This command does the following:

If the email was sent to an Addy.io alias (i.e. contains the header `X-AnonAddy-Original-From-Header`) it changes some headers.

- `Reply-To` = `From` (e.g. Peter Pan 'peter.pan@example.com' <alias+peter.pan=example.com@addy.io>)
- `From` = `X-AnonAddy-Original-From-Header` (e.g. Peter Pan <peter.pan@example.com>)
- `To` = `Envelope-To` or `Delivered-To` or `X-AnonAddy-Original-To` (e.g. you@mymail.com)

This makes it appear like any other email.

## "Strip Banner" Filter

This filter removes the Addy.io banner that includes the link to deactivate an alias. When installed, it is automatically applied to replies.

# Installation

Save the `.mmBundle` to `~/Library/Application Support/MailMate/Bundles/` or follow [these instructions](https://github.com/mailmate/mailmate_manual/wiki/Bundles#customizing-a-default-bundle) and adjust the Github URL to this bundle's repository.

## "Strip Banner" Filter

This needs some extra steps to work. Edit the file `/Applications/MailMate.app/Contents/Resources/eventFilters.plist` in a text editor.
In the "sanitize_canonical filters" section add the following line
```
{ uuid = "C7A0BBFC-C456-43C3-B999-C5BDA7B44EDB"; }, // Remove Addy.io TXT banner
```
In the "sanitize_html filters" section add the following line
```
{ uuid = "314E579D-F1DF-435F-829F-CC78AF411EE9"; }, // Remove Addy.io HTML banner
```

These steps might need to be followed again after a MailMate update.

# Credits

Made by tomtjes. Support me or [say thanks by buying me a coffee](https://ko-fi.com/tomtjes).

# License

If not otherwise specified (see below), files in this repository fall under the following license:

	Permission to copy, use, modify, sell and distribute this
	software is granted. This software is provided "as is" without
	express or implied warranty, and with no claim as to its
	suitability for any purpose.

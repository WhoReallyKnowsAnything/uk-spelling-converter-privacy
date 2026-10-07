# UK Spelling Converter - Privacy

UK Spelling Converter is a Safari Web Extension that rewrites US spellings to UK spellings in the text of the pages you read. This statement says what it does with data. Every point below describes the extension's own code.

In short: the extension sends nothing.

## What it sends

- It makes no network requests.
- It collects no data and runs no analytics.
- It sends nothing to the developer, to any third party or to any server.

Conversion happens inside the page. The content script reads the text on the page and rewrites US spellings to UK spellings in place. Page text is read and rewritten there and sent nowhere.

## What it stores

The extension stores two lists in `browser.storage.local`. They are the only stored data.

- `disabledHosts`: the sites you turned off, from the toolbar popup or from the options page.
- `exceptionWords`: the words you asked the options page never to convert.

It stores no page text, no browsing history and nothing else.

## Why it asks for access to all websites

The manifest declares `host_permissions` of `<all_urls>`, and the content script is matched on `<all_urls>`. Both exist for two reasons only:

- so the extension can read and rewrite page text, locally, on the pages you open;
- so the toolbar popup can read the address of the current tab, to show that site and let you turn it on or off.

## Permissions

The manifest declares these permissions:

- `storage`: saves the two lists above.
- `scripting`: declared in the manifest. No extension code calls the `browser.scripting` API.

The manifest declares no network permissions: no `webRequest`, no `declarativeNetRequest`, no `nativeMessaging` and no `proxy`.

An automated test in the project fails if the manifest permissions change or if a network API appears in the extension's scripts, so this statement cannot silently stop being true.

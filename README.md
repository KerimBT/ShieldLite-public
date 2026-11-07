# NervoCode Myelin – public repository

Public issue tracker and quick filter fixes for **NervoCode Myelin**, a Microsoft Edge extension that blocks
ads, trackers and phishing and hides cookie banners without accepting anything.

## Report a site that doesn't work

The quickest way is from the extension itself:

1. Open the Myelin popup on the broken site and choose **Site not working?**.
   Myelin pauses on that site for 10 minutes and reloads the page.
2. If the site works while paused, choose **Yes, report it**. A pre-filled issue opens here.
3. Describe what doesn't work (for example: the video won't play, a button doesn't respond) and submit.

You can also [open an issue manually](../../issues/new/choose).

## What a report contains

Pre-filled reports contain only:

- the site name (never the full address, path or query string);
- the Myelin and browser versions and the date of the filter lists;
- which protections are enabled, and whether custom rules, site rules or hidden elements exist
  (never the rules themselves).

Nothing is sent automatically: you review the issue and decide whether to submit it. Issues are public,
so don't include personal information.

## Quick filter fixes

The full filter lists ship with each Myelin release. Urgent fixes (a broken site, a new ad format)
go into [`filters/fixes.txt`](filters/fixes.txt), written in the usual filter list syntax.

A scheduled job compiles that file into [`filters/update.json`](filters) and signs it
(`update.json.sig`, ECDSA P-256). Myelin downloads it every 6 hours. It accepts the file only if the
signature matches the public key bundled with the extension, then validates each entry again.

The file contains data only:

- network rules (block or allow only);
- CSS and procedural selectors;
- names and arguments of scriptlets already bundled with the extension.

No code is ever downloaded. The request carries no cookies or browsing data. Users can turn quick fixes
off in the settings.

Suggestions for fixes are welcome as issues or pull requests to `filters/fixes.txt`.

## Other requests

Feature requests and general bugs are welcome too: use the matching template.

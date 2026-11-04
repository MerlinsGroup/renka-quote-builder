# Renka quotation builder

Turns a Logikal estimation export into a Renka quotation: working sheet, customer
quotation, order confirmation, a Proposal PDF and an Excel workbook.

**Live:** https://renka-portal.pages.dev (main address) and
https://merlinsgroup.github.io/renka-quote-builder/ (this repo). Both use the same accounts.

## How it works

- Everything runs in the browser. The estimation you load is read on your own machine
  and is never uploaded anywhere.
- Sign in, drop the `Estimation … .xlsx` Logikal prints when a job is costed, add any
  extras Logikal does not hold (rooflights, bought-in doors, panels), set the discount and
  installation, then download the PDF or Excel.
- Jobs can be saved and reopened as `.json` files. Prices, rules and the cover picture are
  remembered in the browser.

## Sign-in

The page holds no passwords. Its sign-in screen calls the accounts back end at
https://renka-portal.pages.dev (a Cloudflare Worker). The back end checks passwords,
which it stores as PBKDF2 hashes, and does the following:

- new accounts get a temporary password and must choose their own on first sign-in
- **Forgotten your password?** emails a single-use reset link
- an alert email is sent whenever a password changes
- eight wrong passwords pause an account for 15 minutes

Accounts are added, reset and removed by the administrator with
`node cloudflare/users.mjs` in the `logikalsystem` project, which also holds the back
end's source. Changes apply at once; this repo does not need editing.

## Log

**Log** in the header opens `log.html`, where users report bugs, request features and
leave notes. Entries are copied every 15 minutes to
[MerlinsGroup/renka-portal-log](https://github.com/MerlinsGroup/renka-portal-log)
(`portal-log.txt`).

## Credits

Cover photos from [Unsplash](https://unsplash.com/license) (free for commercial use):
Tim Schmidbauer, Michael Brown, John Fornander.

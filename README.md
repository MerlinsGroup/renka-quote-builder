# Renka quotation builder

Turns a Logikal estimation export into a Renka quotation: working sheet, customer
quotation, order confirmation, a Proposal PDF and an Excel workbook.

**Live:** https://merlinsgroup.github.io/renka-quote-builder/

## How it works

- Everything runs in the browser. The estimation you load is read on your own machine
  and is never uploaded anywhere.
- Sign in, drop the `Estimation … .xlsx` Logikal prints when a job is costed, add any
  extras Logikal does not hold (rooflights, bought-in doors, panels), set the discount and
  installation, then download the PDF or Excel.
- Jobs can be saved and reopened as `.json` files. Prices, rules and the cover picture are
  remembered in the browser.

## Sign-in

The sign-in is a gate, not security. Passwords are stored as SHA-256 hashes of
`email:password`, so they cannot be read from the page, but short passwords can still be
guessed from a hash. Nothing confidential is held in the page itself. Use real
authentication before relying on it to protect anything.

To add a user, compute the hash and add a line to `LOCAL_ACCOUNTS` in `index.html`:

```
node -e "console.log(require('crypto').createHash('sha256').update('name@example.com:their-password').digest('hex'))"
```

## Credits

Cover photos from [Unsplash](https://unsplash.com/license) (free for commercial use):
Tim Schmidbauer, Michael Brown, John Fornander.

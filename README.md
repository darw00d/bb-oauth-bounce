# bb-oauth-bounce

Two static HTML pages used as OAuth `redirect_uri` targets for a personal, sideloaded iPhone budgeting app. Banks require an `https://` redirect; a free Apple ID cannot use universal links; so these pages receive `?code=…&state=…` and immediately forward it to the app's custom URL scheme.

- `/oauth/monzo/` → `moneytracker://oauth/monzo?…`
- `/oauth/truelayer/` → `moneytracker://oauth/truelayer?…`

There are no secrets here, no app code, no analytics, no storage and no network requests. An authorization code is single-use, short-lived and useless without the client secret, which never leaves the phone's Keychain; the app also checks the `state` value it generated.

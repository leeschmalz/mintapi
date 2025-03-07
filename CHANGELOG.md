--> NOTE! The 1.x release series only supports and contain fixes for the previous Mint UI.
    New feature work occurs in the 2.x release series and only supports the new Mint UI / endpoints.
    Please see the README for more information.
    
2.14
---
- backwards compatability when using positional arguments for email and password. (#592)

2.13
---
- use a RESTful API architecture instead of heavily relying on Selenium (#482)
  - you can opt-in to full use of this via `--use-rest-client` (CLI) or `use_rest_client=True` (Python)
- improved detection of refresh status (#583)

2.12
---
- update selenium-requests dep to >=2.0.3 which should future-proof chrome updates

2.11
---
- prevent email MFA check from marking messages as read (#568)
- handle additional refresh sync status message (#575)

2.10
---
- update selenium-requests dep to >=2.0.1 (#553, #564, #566)

2.9
---
- various fixes to CSS selectors for login (#549, #552)

2.8
---
- handle new MFA email format w/ code in subject (#538)
- update for new SMS MFA UI (#536)
- improve README for creating and passing in your own driver (#542)

2.7
---
- fix for Intuit account selection login bug (#530)
- Add AccountIdFilter to Endpoint Filters (#526)

2.6
---
- add support for accessing the Trend API endpoint (#480)
- bump selenium-requests dependency version to resolve issues (#521)
- attempt to show the reason for a login failure (#523)

2.5
---
- increase wait for account selection to fix login issues (#508)

2.4
---
- further fix for Selenium find_element issue (#502)

2.3
---
- fix for "no attribute 'find_element[s]_by*'" (#498)

2.2
---
- Add a delay before clicking sign in button (#493)
- Add WebDriverWait for Account Selection Selectors (#490)
- Add an option to raise an exception if the data refresh fails (#488)
- Update README with content about the email nuance (#487)
- Support optional MFA if remember my device is enabled (#476)
- Documentation updates (#477)

2.1
---
- Add `--beta` switch to force using the new Mint endpoints (#470)
- Fix for credit score data (#472)

2.0
---
- Dynamic Multifactor Authentication Flow (#392)
- Add Data Format Option to CLI: `--format` (#432)
- Update Accounts Endpoint to meet new Mint requirements (#430)
- Update Transactions Endpoint to meet new Mint requirements (#429)
- Update Budgets Endpoint to meet new Mint requirements (#425)
- Support removed for hiding duplicate transactions (#427)
- Fetch the correct API Key to use with Mint API Requests (#420, #423)
- Removed `get_token` functionality, which is incompatible with the new Mint UI (#421)
- Update the name of the Account Refresh Class (#415)
- Update the overview page url (#414)

:warning: BREAKING CHANGES :warning:
- As of version 2.0, mintapi only supports the new Mint.com UI and endpoints. Please see the README to learn which version of mintapi you need.
- `mfa_method` is only required if your login flow presents you with the option to select which Multifactor Authentication Method you wish to use, typically as a result of your account configured to accept different methods.  We now automatically detect the type of MFA requested by Mint, based on the prompts on the screen.  Because of this, mintapi now supports the use case where multiple MFA prompts appear.
- Due to the new Mint UI and the switchover to different API Endpoints, the data structure associated with each function may be different.  Please verify that the data you are expecting against the new output of each endpoint.
- To implement consistency and to call attention to the fact that some input and output of methods has changed, some API methods have been renamed.  With the exception of bills, all data fetch methods now follow the same sort of pattern: `get_<data type>_data`.  For example, instead of `get_accounts`, we now have `get_account_data`.
- To help support the new CLI option for data format (`--format`), we have eliminated the need to specify a file extension in `--filename`.  Be aware that if you do not specify `--format=csv`, then the extension/format will be `json`, and any filename will automatically include the extension of `.json`. In addition, the CLI now supports receiving multiple types of data in one call to mintapi. See the "Multi-Data Support" section of the README for more information.

1.66
---
- handle "Sign in without a password next time" page (#436)

1.65
---
- fix for selenium dependency version (#412, #413, #416)

1.64
---
- Resolves Selenium Requests Error #408
- Resolves Maxretry issue #407
- Resolves no such element: Unable to locate element: {"method":"css selector","selector":"[id="ius-userid"]"} #406
- Resolves mintapi logon issues - selenium can't find field to navigate authentication sequence #405

1.63
---
- fix regression introduced in #384 (#398)

1.62
---
- support exporting investment data/transactions to CSV (#382, #384)
- more robust sign-in / email handling (#391, #377, #396)
- fix command-line checking of file extensions (#386)

1.61
---
- fix regression: UnboundLocalError for `attention_msg` (#380)

1.60
---
- improve handling for new login OTP/soft token selectors (#367, #370)
- use new categories endpoint, add support for pulling categories from CLI (#359)
- better long description for pypi
- refactor sign-in code to its own file (#366)
- update pandas to latest version

1.59
---
- moved to newest Mint investments endpoint (#342)
- added command-line support for investment data (#342)
- added new option to exclude credit utilization history data (#356)
- allow use of keyring for IMAP password (#360)

1.58
---
- expose sign_in as a public method to allow custom WebDrivers (#336)
- add command-line option to exclude credit inquiries from credit report data (#340)
- add command-line option to exclude credit accounts from credit report (#351)
- fix performance degradation on extended transactions (#348)
- remove support for Python 2.x

1.57
---
- add date range support to --transactions (github#321)
- improvements for new and existing flows for login and email MFA (github#317)
- fix invalid cookie domain error when fetching credit information (github#320)
- minor code cleanups and improvements (github#329, #github#331)

1.56
---
- add columns for parent category to the output of extended-transactions (github#310)

1.55
---
- add support for --config-file for specifying config options (github#309)
- handle login flow change for SMS 2FA (gihub#318)
- improve handling for change account continue button (github#316)

1.54
---
- Add support for --end-date filtering for extended transactions (github#208)
- start and end date filtering use native Mint capabilities (github#278)

1.53
---
- Ensure pip installs selenium-requests >= 1.3.3 (github#296)

1.52
---
- No changes. Redeploy to pypi to update project URLs (github#292)

1.51
---
- don't leave dangling chrome instances on sign-in exception

1.50
---
- various fixes for different element IDs and more robust checks

1.49
---
- fix for Uncategorized budget as parent (github#261)

1.48
---
- improvements for login when ElementNotVisibleException is thrown (github#262)

1.47
---
- actually release previous changes!

1.46
---
- handle selecting a saved account if normal login fails (github#260)

1.45
---
- various fixes and improvements for recent Mint flow changes
- add support for users with multiple intuit accounts (`--intuit_account`)
- provide get_category_object_from_id() to get a dict with 'name' and 'parent'
- improvements to budget data returned

1.44
---
- bump for pypi re-release (no changes)

1.43
---
- add soft token support (github#199)

1.42
---
- replace deprecated pandas call to fix warning (github#211)
- added --attention flag to include information on accounts which need attention (github#205)
- added budget history (--budget_hist) (github#198)
- various code style, README, and travis improvements

1.41
---
- support soft token mfa method (github#193)
- allow retrieving brokerage holdings via get_invests_json (github#192)
- add more methods to README and fix typo (github#191, github#189)

1.40
---
- simplify pypi long description to prevent rendering error and release blocking
- actually release changes from 1.39

1.39
---
- fix targetting for login/signup (github#187)

1.38
---
- add ability to retrieve mfa code from email via IMAP (github#166)

1.37
---
- full credit report functionality (github#169)

1.36
---
- add ability to get credit score (github#163)

1.35
---
- by default, persist a browser session to avoid regular MFA requests (github#160)

1.34
---
- correctly fix usages of parse_float (github#159)

1.33
---
- fix chromedriver download on win64 (github#158)
- fix usages of parse_float (github#157)

1.32
---
- don't let "accounts need attention" block closing after a successful refresh (github#156)

1.31
---
- fix for headless chromedriver not working on Windows (github#151)

1.30
---
- chromedriver now supports --headless option (thanks @matthewwardrop/@eschizoid)
- chromedriver now supports --mfa-method to automate triggering sms/email (thanks @matthewwardrop/@eschizoid)

1.29
---
- use seleniumrequests to perform all requests (thanks @jprouty!)

1.28
---
- fix get_transactions_json when start_date predates all transactions (thanks @jprouty!)

1.27
---
- fix NoneType error when getting cookies via chromedriver (thanks @dherg!)

1.26
---
- properly display messages when webdriver raises a URLError (thanks @dherg!)

1.25
---
- use Excel-compatible datetime formatting and allow customizing (thanks @felciano!)

1.24
---
- fix "Unknown" categories when categories in budgets (thanks @drunnells!)

1.23
---
- mintapi raises MintException instead of Exception for better exception
  handling when used as a library (thanks @titilambert!)

1.22
---
- more robustly match content types (thanks @jbms!)
- eliminate an unnecessary use of pandas (thanks @jbms!)

1.21
---
- import fix for python3

1.20
---
- automate cookie grabbing w/ selenium+chromedriver (thanks @matthewwardrop!)
- allow passing in required cookies via CLI/API
- update README to cover the cookies now required
- --include-investments now works with --transactions (thanks @felciano)

1.19
---
- updated URLs for intuit.com domain change
- added command-line switch for --session=ius_session_cookie

1.18
---
- add the ability to get extended transaction information from the command line,
  along with all its options

1.17
---
- fix get_transactions_json to work with Mint change (github#57),
  thanks @dtiz!

1.16
---
- allow specifying a start date for get_transactions_json
- add get_detailed_transactions which converts the json to a pandas
  dataframe, adds the year to all transactions, and reverses credit
  activity.

1.15
---
- fix urllib3 import exception on Ubuntu/Debian, thanks @dancudds!

1.14
---
- fix json output when using --filename
- flake8 fixes

1.13
---
- new get_net_worth / --net-worth options, thanks @wendlinga!

1.12
---
- get_transactions_csv and get_transactions_json API methods

1.11
---
- fix get_budgets with nested categories

1.10.2
---
- re-release to actually include the intended changes from 1.10.1

1.10.1
---
- fix for get_transactions with Python 3
- more helpful error message when pandas is missing

1.9
---
- keyring is lazily required, now compatible with systems where keyring
  module is not available
- PEP8

1.8
---
- fix retrieving transactions (-t)

1.7
---
- -u / --user option to save and grab password from keyring

1.6
---
- -t / --transactions option to fetch transactions
- -f / --filename to write results to csv/json

1.5
---
- various changes to fix and improve scraping Mint.com

1.4
---
- fix Python 3 compat
- add an 'InDate' for each timestamp field that is the date as a
  python-native datetime object
- add unit test / travis integration for the above

1.3.2
---
- fix setup.py for pip installations

1.3
---
- specify SSLv3 to fix making HTTPS requests to Mint on certain Linux systems

1.2
---
- turn into a pypi package. now use `import mintapi` from python or the `mintapi` binary.

1.1
---
- fix login/authentication issue after Mint.com change

1.0
---
- initial release

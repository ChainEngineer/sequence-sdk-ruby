# Sequence Ruby SDK changelog

## 2.0 (2018????)

* Removed assets, balances, contracts, and all other deprecated code.
* Added `Stats#ledger_type`.

## 1.5 (20180316)

For full details on the 1.5 release and how to migrate your code,
[visit the Sequence changelog](https://dashboard.seq.com/docs/changelog#release-v1-5).

* Added `Feed`s. [More info](https://dashboard.seq.com/docs/feeds)
* The `keys` field on `Account` and `Flavor` has been deprecated; the new field
  is `key_ids`, containing key ID strings.
* Optimize Ruby garbarge collection with
  `# frozen_string_literal: true` "magic comments".
* `Transaction#reference_data` has been deprecated; Use `Action#tags` instead.
* `action.snapshot.*_tags` can now be accessed with dot syntax.

## 1.4 (20180308)

For full details on the 1.4 release and how to migrate your code,
[visit the Sequence changelog](https://dashboard.seq.com/docs/changelog#release-v1-4).

* Added `tags` to `Action`.
* Added `action_tags` on `Transaction` builder's actions.
* Added timestamp inequalities in filters.
* `reference_data` on `Transaction` builder's actions has been deprecated. You
  can now use `action_tags` instead.

## 1.3 (20180301)

For full details on the 1.3 release and how to migrate your code,
[visit the Sequence changelog](https://dashboard.seq.com/docs/changelog#release-v1-3).

* Added `Token`s. [More info](https://dashboard.seq.com/docs/tokens).
* Added `token_tags` on `Transaction` builder's `issue`/`transfer` actions.
* Added `filter` on `Transaction` builder's `transfer`/`retire` actions.
* Updated pagination interfaces:
  `.[list|sum].page(size: size)` to retrieve one page.
  `.[list|sum].page(cursor: cursor)` to retrieve another page.
  `.[list|sum].all` to iterate over all items.
  `page_size` has been deprecated; you can now use `.page(size: size)`.
* Querying balances has been deprecated; you can now use `tokens.sum` to
  query balances in an account.
* Querying contracts has been deprecated; you can now use `tokens.list` to
  list tokens in an account.

## 1.2.0 (20180216)

For full details on the 1.2 release and how to migrate your code,
[visit the Sequence changelog](https://dashboard.seq.com/docs/changelog#release-v1-2).

* `Asset` has been renamed to `Flavor`; all references to assets have been
  deprecated.
* The `code` field on API errors has been deprecated; the new field is
  `seq_code`, containing `SEQXXX` error codes.
* The `source_account_tags`, `destination_account_tags`, and `asset_tags` on
  action objects have been deprecated; All tags on actions are now available
  within a new `Action#snapshot` object.

## 1.1.0 (20180206)

For full details on the 1.1 release and how to migrate your code,
[visit the Sequence changelog](https://dashboard.seq.com/docs/changelog#release-v1-1).

* Added support for setting a user-provided id on key and account objects.
* The `alias` field on key and account objects has been deprecated.
* The `ledger` field when creating an API client has been deprecated; the new
  field is named `ledger_name`.
* Added full support for listing and summing actions.

## 1.0.4 (20180119)

* Ruby >= 2.2 is required. We recommend upgrading to Ruby >= 2.3.
* New interface `ledger.actions.list` and `ledger.actions.sum` available.
  [More info](https://dashboard.seq.com/docs/actions).
* Invalid parameters raise `ArgumentError`s when creating or querying objects.
* Improved retry logic for network errors.
* `Sequence::Client` instances now use persistent TLS connections.
* Set lower HTTP timeouts. This can be configured. See below.
* Private interfaces more comprehensively annotated as YARD `@private`.
* Rubocop linting applied to source code.

```ruby
Sequence::Client.new(
  ledger: 'development',
  credential: '...'
  open_timeout: 1,
  read_timeout: 1,
  ssl_timeout: 1,
)
```

## 1.0.3 (20171020)

* Added support for new access control permissions. When creating a client, you
  now provide `ledger` and `credential` options to connect to a
  specific ledger.

  Authentication with the previous style of access tokens has been removed.

  See https://dashboard.seq.com/docs/5-minute-guide#instantiate-sdk-client for
  more information.

## 1.0.2 (20170922)

* Updated YARD doc strings

## 1.0.1 (20170921)

* Removed the `ttl` and `base_transaction` attributes from `Sequence::Transaction::Builder`.

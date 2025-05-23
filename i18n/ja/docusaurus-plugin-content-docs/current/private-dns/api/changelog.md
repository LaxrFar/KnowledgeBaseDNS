---
title: Changelog（変更履歴）
sidebar_position: 3
toc_min_heading_level: 2
toc_max_heading_level: 3
---

<!--
    Changelog is from here:
    https://api.adguard-dns.io/static/api/CHANGELOG.md
-->

本ページには [AdGuard DNS API](private-dns/api/overview.md) の変更履歴を記載しております。

## v1.10

_2024年12月12日にリリース_

Added a new DNS server setting — `block_chrome_prefetch`. It disables _Private prefetch proxy_ in Chrome. When this feature is enabled, Chrome will sometimes prefetch links on the Google Search results page and other participating websites even before the user clicks them.

## v1.9

_2024年7月11日にリリース_

- Added automatic device connection functionality（「デバイスの自動接続」機能を追加）:
  - New DNS server setting — `auto_connect_devices_enabled`, allowing approval for auto-connecting devices through a specific link type
  - New field in Device — `auto_device`, indicating that the device is automatically connected
- Replaced `int` with `long` for `queries` in CategoryQueriesStats, for `used` in AccountLimits, and for `blocked` and `queries` in QueriesStats

## v1.8

_2024年4月20日にリリース_

- Added support for DNS-over-HTTPS with authentication（認証付き DNS-over-HTTPSのサポートを追加）:
  - New operation — reset DNS-over-HTTPS password for device
  - New device setting — `detect_doh_auth_only`. Disables all DNS connection methods except DNS-over-HTTPS with authentication
  - New field in DeviceDNSAddresses — `dns_over_https_with_auth_url`. Indicates the URL to use when connecting using DNS-over-HTTPS with authentication

## v1.7

_2024年3月11日にリリース_

- Added dedicated IPv4 addresses functionality（「専用IPv4アドレス」機能を追加）:
  - Dedicated IPv4 addresses can now be used on devices for DNS server configuration
  - Dedicated IPv4 address is now associated with the device it is linked to, so that queries made to this address are logged for that device
- Added new operations:
  - List all available dedicated IPv4 addresses
  - Allocate new dedicated IPv4 address
  - Link an available IPv4 address to a device
  - Unlink an IPv4 address from a device
  - Request info on dedicated addresses associated with a device
- Added new limits to Account limits（アカウント制限に新しい制限を追加）:
  - `dedicated_ipv4` provides information about the amount of already allocated dedicated IPv4 addresses, as well as the limit on them
- Removed deprecated field of DNSServerSettings:
  - `safebrowsing_enabled`

## v1.6

_2024年1月22日にリリース_

- Added new Access settings section for DNS profiles (`access_settings`). By customizing these fields, you’ll be able to protect your AdGuard DNS server from unauthorized access:

  - `allowed_clients` — here you can specify which clients can use your DNS server. This field will have priority over the `blocked_clients` field
  - `blocked_clients` — here you can specify which clients are not allowed to use your DNS server
  - `blocked_domain_rules` — here you can specify which domains are not allowed to access your DNS server, as well as define such domains with wildcard and DNS filtering rules

- Added new limits to Account limits（アカウント制限に新しい制限を追加）:

  - `access_rules` provides the sum of currently used `blocked_clients` and `blocked_domain_rules` values, as well as the limit on access rules
  - `user_rules` shows the amount of created user rules, as well as the limit on them

- クライアントIPアドレスとドメインをログに記録するための新しい`ip_log_enabled`設定が追加されました

- Added new error code `FIELD_REACHED_LIMIT` to indicate when limits have been reached:

  - For the total number of `blocked_clients` and `blocked_domain_rules` in access settings
  - For `rules` in custom user rules settings

## v1.5

_2023年6月16日にリリース_

- Added a new `block_nrd` setting and grouped all security-related settings in one place

### Model for safebrowsing settings changed（safebrowsing設定のモデルが変更されました）

From:

```json
{
   "enabled": true
}
```

To:

```json
{
   "enabled": true,
   "block_dangerous_domains": true,
   "block_nrd": false
}
```

where `enabled` now controls all settings in the group, `block_dangerous_domains` is the previous `enabled` model field, and `block_nrd` is a setting that blocks newly registered domains.

### Model for saving server settings changed（サーバー設定の保存モデルが変更されました）

From:

```json
{
  "protection_enabled" : true,
  "safebrowsing_enabled" : true,
  ..
}
```

to:

```json
{
  "protection_enabled" : true,
  "safebrowsing_settings" : {
     "enabled": true,
     "block_dangerous_domains": true,
     "block_nrd": false
  }
  ..
}
```

here a new field `safebrowsing_settings` is used instead of the deprecated `safebrowsing_enabled`, whose value is stored in `block_dangerous_domains`.

## v1.4

_2023年3月29日にリリース_

- Added configurable option for blocking response: default (0.0.0.0), REFUSED, NXDOMAIN or custom IP address

## v1.3

_2022年12月13日にリリース_

- Added method to get account limits

## v1.2

_2022年10月14日にリリース_

- Added new protocol types DNS and DNSCRYPT. Deprecating the PLAIN_TCP, PLAIN_UDP, DNSCRYPT_TCP and DNSCRYPT_UDP that will be removed later

## v1.1

_2022年7月7日にリリース_

- Added methods to retrieve statistics by time, domains, companies and devices
- Added method for updating device settings
- Fixed required fields definition

## v1.0

_2022年2月22日にリリース_

- Added authentication
- CRUD operations with devices and DNS servers
- Query log
- Downloading DoH and DoT .mobileconfig
- Filter lists and web services

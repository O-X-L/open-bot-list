# Open Bot List

<p align="center">
    <a title="Support this Project (Donate, Support-Licenses)" href="https://superstes.at#donate">
        <img src="https://files.oxl.at/img/badge-oss-support.svg" alt="Support Badge (Donate, Support-Licenses)"/>
    </a>
</p>

[![Lint CSV Configs](https://github.com/O-X-L/open-bot-list/actions/workflows/csv_lint.yml/badge.svg)](https://github.com/O-X-L/open-bot-list/actions/workflows/csv_lint.yml)
[![Lint Downloader](https://github.com/O-X-L/open-bot-list/actions/workflows/apps_lint.yml/badge.svg)](https://github.com/O-X-L/open-bot-list/actions/workflows/apps_lint.yml)
[![Unit Test Downloader](https://github.com/O-X-L/open-bot-list/actions/workflows/apps_unit_test.yml/badge.svg)](https://github.com/O-X-L/open-bot-list/actions/workflows/apps_unit_test.yml)
[![Functional Tests for Downloader](https://github.com/O-X-L/open-bot-list/actions/workflows/app_dl_functional_test.yml/badge.svg)](https://github.com/O-X-L/open-bot-list/actions/workflows/app_dl_functional_test.yml)
[![Functional Tests for Log-Flagger](https://github.com/O-X-L/open-bot-list/actions/workflows/app_flagger_functional_test.yml/badge.svg)](https://github.com/O-X-L/open-bot-list/actions/workflows/app_flagger_functional_test.yml)

This repository is used to collect information that can be used to categorize & match traffic.

We will auto-generate full lists in plaintext and JSON later on!

----

## Why

For traffic-filtering rulesets it is essential to categorize requests.

This can allow you to easily restrict traffic from client-categories you do not want.

**TLDR; What can you expect**:

* Detecting different kinds of bots
* Validating crawler-bots - detecting spoofed crawlers
* Categorizing the source-networks

----

## How it works

To transparently match & categorize bots we need to combine:

* **Traffic [Matches](https://github.com/O-X-L/open-bot-list/tree/latest/matches)**
  * Matching the source-IP with IP- or ASN-Lists
    * Separating different kinds of bots by their HTTP User-Agent (*if they use the same IP-range*)
    * Categorizing the source-networks into Hosting/ISP/Education/Cloud/CDN/VPN/Proxy/Scanner/CGNAT
  * Separating different bot-categories like:
    `script bots`, `hidden bots`, `search-engine crawlers`, `AI-data crawlers`, `AI-user crawlers`, `social-media crawlers`, `crawlers for ADs`, `crawlers for ecommerce`, and so on

    * Matching clear script-bots by their User-Agent (*dumb script-kiddies*)
    * Matching 'hidden' bots by their client-fingerprints (*[JA4](https://github.com/O-X-L/haproxy-ja4-fingerprint), etc.*)
    * ... *to be extended* ...

* **PTR-checks**
  * Some organizations only supply us with a PTR-match to validate if a crawler-IP is theirs (*no simple IP-list lookups*)

* **Traffic [Flagging](https://github.com/O-X-L/open-bot-list/tree/latest/flagging)**
  * We provide you with abstract configuration that shows how the matches can be combined
  * Practical configuration examples for proxy-services will be added later on

----

## Downloader Application

See: [Downloader README](https://github.com/O-X-L/open-bot-list/blob/latest/apps/downloader/README.md)

**IMPORTANT**: Do not run the downloader (and thus download the IP lists) frequently! Once a day (or even once a week) is sufficient for most systems.

----

## Log-Flagger Application

See: [Log-Flagger README](https://github.com/O-X-L/open-bot-list/blob/latest/apps/log_flagger/README.md)

----

## Contribute

Contributions are very welcome.

If you:

* know of official IP-Lists we missed
* found other missing/incorrect information

..feel free to either [open a ticket](https://github.com/O-X-L/open-bot-list/issues) or [email us directly](mailto://contact+openbotlist@OXL.at)

----

## Motivation

With our [IP-Abuse Reporting-System & Databases](https://github.com/O-X-L/risk-db) we have started to collect information of abusers.

As the mindset of Open-Source is at the core of our being - we want to transparently share it with the whole world.

----

## License

The Open-Bot-List data-collection uses the [BSD 3-Clause license](https://opensource.org/license/bsd-3-clause) and has very little restrictions.

The Applications for processing (*downloader/log-flagger*) use the [GPLv3 license](https://www.gnu.org/licenses/gpl-3.0.en.html).

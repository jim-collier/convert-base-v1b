<!-- markdownlint-disable MD007 -- Unordered list indentation -->
<!-- markdownlint-disable MD010 -- No hard tabs -->
<!-- markdownlint-disable MD033 -- No inline html -->
<!-- markdownlint-disable MD055 -- Table pipe style [Expected: leading_and_trailing; Actual: leading_only; Missing trailing pipe] -->
<!-- markdownlint-disable MD041 -- First line in a file should be a top-level heading -->
<div align="center">

[![!#/bin/bash](https://img.shields.io/badge/-%23!%2Fbin%2Fbash-1f425f.svg?logo=gnu-bash)](https://www.gnu.org/software/bash/)
![License: GPL v2](https://img.shields.io/badge/License-GPLv2-blue.svg)
![Lifecycle](https://img.shields.io/badge/Lifecycle-RC-blue)
![Support](https://img.shields.io/badge/Support-Maintained-brightgreen)
![Status: Passing](https://img.shields.io/badge/Status-Passing-brightgreen)

</div>
<!--
![License: GPL v2](https://img.shields.io/badge/License-GPLv2-blue.svg)
![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)
![Lifecycle: Alpha](https://img.shields.io/badge/Lifecycle-Alpha-orange)
![Lifecycle: Beta](https://img.shields.io/badge/Lifecycle-Beta-yellow)
![Lifecycle: RC](https://img.shields.io/badge/Lifecycle-RC-blue)
![Lifecycle: Stable](https://img.shields.io/badge/Lifecycle-Stable-brightgreen)
![Lifecycle: Deprecated](https://img.shields.io/badge/Lifecycle-Deprecated-red)
![Status: Deprecated](https://img.shields.io/badge/Status-Deprecated-orange)
![Status: Archived](https://img.shields.io/badge/Status-Archived-lightgrey)
![Lifecycle: EOL](https://img.shields.io/badge/Lifecycle-EOL-lightgrey)
![Coverage](https://img.shields.io/badge/Coverage-25%25-red)
![Coverage](https://img.shields.io/badge/Coverage-50%25-orange)
![Coverage](https://img.shields.io/badge/Coverage-75%25-yellow)
![Coverage](https://img.shields.io/badge/Coverage-90%25-brightgreen)
![Status: Passing](https://img.shields.io/badge/Status-Passing-brightgreen)
![Status: Failing](https://img.shields.io/badge/Status-Failing-red)
-->

<!-- TOC ignore:true -->
# convert-base-v1

Converts arbitrarily large numbers between most common prededined standard, and large custom bases - up to base-288.

_Note: The command has a version number on the end, because it will be very important to always give identical output, given the same arguments. However, in the future there may be good reasons for the output to change. (Since there are no "official standards" for large bases above 94 as of time of writing.) So to avoid overwriting an old script on a running system that may rely on it and it's predictable output, a new suffix number will be given to future programs if the output changes, and the two will coexist. That the existing version has a number, indicates that expected inevitability now._

<!-- TOC ignore:true -->
## Table of contents

<!-- TOC -->

- [Output bases](#output-bases)
- [Document history](#document-history)
- [Copyright and license](#copyright-and-license)

<!-- /TOC -->

## Output bases

| Base        | Description                                                 | Characters                        | Reference
|:---         |:---                                                         |:---                               |:---
| 2           | aka Binary                                                  | 0,1
| 8           | aka Octal                                                   | 0-7
| 10          | aka Decimal [default]                                       | 0-9
| 16          | aka Hexedecimal                                             | 0-9, A-F
| 32[r]       | RFC 4648                                                    | A-Z, 2-7                          | https://en.wikipedia.org/wiki/Base32
| 32h         | RFC 4648 §7, 'Base32Hex'                                    | 0-9, A-V                          | https://datatracker.ietf.org/doc/html/rfc4648#section-7
| 32w         | Wordsafe Base32                                             | 2-9, CFGHJMPQRVWX, cfghjmpqrvwx   | https://en.wikipedia.org/wiki/Base32#Word-safe_alphabet
| 36          | Just alphanum                                               | 0-9, A-Z                          | https://en.wikipedia.org/wiki/Base36
| 62          | All alphanum                                                | 0-9, A-Z, a-z                     | https://en.wikipedia.org/wiki/Base62
| 64[r]       | RFC 4648                                                    | 0-9, A-Z, a-z, +, /               | https://en.wikipedia.org/wiki/Base64
| 64u         | RFC 4648 §5; URL-safe                                       | 0-9, A-Z, a-z, -, _               | https://en.wikipedia.org/wiki/Base64#Variants_summary_table
| 26          | One-case alphabetic                                         | A-Z
| 32c         | Crockford's Base32                                          | 0-9, A-Z no I, L, O, U            | https://en.wikipedia.org/wiki/Base32#Crockford's_Base32
| 52          | Both-case alphabetic                                        | A-Z, a-z
| 64j1u       | Alternate to 64u but also programmer-friendly               | 0-9, A-Z, a-z, ʞ, λ
| 48j1        | 0-9, cfghjmpqrvwx, and lots of unicode symbols
| 64j1uw      | Like 48j1 but with upper-case alpha too
| 128[j1]     | Like 64j1u but with way more unicode symbols
| 256[j1]     | Base 62 (all alphanum), and lots of unicode chars
| 288[j1]     | 256j1 with 32 more unicode chars
| 38username  | Valid *nix username characters
| 38hostname  | Valid *nix host and domain name characters
<!--
| 94[ascii]   | All lower ASCII chars + space (all typable US keyboard)
-->

## Document history

- 2023-10-09: First version.
- 2026-04-17: Added more sections. Removed custom base 94ascii.

## Copyright and license

> Copyright © 2023-2026 Jim Collier (ID: 1cv◂‡Vᛦ)<br>
> Licensed under GNU GPL v2 <https://www.gnu.org/licenses/gpl-2.0.html>. No warranty.

<!-- markdownlint-disable MD007 -- Unordered list indentation -->
<!-- markdownlint-disable MD010 -- No hard tabs -->
<!-- markdownlint-disable MD033 -- No inline html -->
<!-- markdownlint-disable MD055 -- Table pipe style [Expected: leading_and_trailing; Actual: leading_only; Missing trailing pipe] -->
<!-- markdownlint-disable MD041 -- First line in a file should be a top-level heading -->
<div align="center">

[![!#/bin/bash](https://img.shields.io/badge/-%23!%2Fbin%2Fbash-1f425f.svg?logo=gnu-bash)](https://www.gnu.org/software/bash/)
![License: GPL v2](https://img.shields.io/badge/License-GPLv2-blue.svg)
![Lifecycle: Beta](https://img.shields.io/badge/Lifecycle-Beta-yellow)
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
# convert-base-v1b

<!-- TOC ignore:true -->
## Table of contents

<!-- TOC -->

- [Introduction](#introduction)
- [Why have a version in the command name](#why-have-a-version-in-the-command-name)
- [Limitations](#limitations)
- [Input bases](#input-bases)
- [Output bases](#output-bases)
- [Example output](#example-output)
- [Document history](#document-history)
- [Copyright and license](#copyright-and-license)

<!-- /TOC -->

## Introduction

Converts arbitrarily large numbers between most common predefined standard, and large custom bases - up to base-288.

Why convert a number to a large base? Mostly, to represent it in a more compact form. For example, converting a large number from base-10 to base-128, can be represented in about half the number of characters. For example, POSIX time (the number of seconds since 1970) can be used as a "unique" serial value, in a shorter form. For example, "2026-01-01 @ 12:15 PM" could be represented as "1fLcL4" in standard base-64url, or "£±Яᛯ" in base-256.

At larger non-standard bases, careful effort was made to:

- Avoid ambiguous characters that look like existing 0-9 A-Z ASCII characters and symbols.

- Avoid characters that are too wide and render poorly on fixed-width terminals.

- Avoid reserved characters across multiple operating systems and web standards, so that output can be used in those contexts. (Except for predefined standard base definitions that specify such characters, e.g. regular base-64.)

- Keep the character selection consistent across bases.

## Why have a version in the command name

...because of the combination of these factors:

- As with any program dealing with numbers, it could be critical to always give identical output, given the same arguments.

- In the future there may be good reasons for the output to change, for given arguments. (And/Or the expected arguments themselves might change.) For example, there are no "official standards" for large bases above 94 as of time of writing, but that could change. And even anything above 16, in most cases is fair game.

- `v1` already had enough very minor issues - including allowing referencing bases by number-only that have no standard or even wide adoption (but might in the future) - that fixing them changed the output for given test input. It changed for the better and is now more pedantically accurate, but in a significant enough of a breaking way to warrant a different, non-colliding name.

	Hence this can no longer be named `v1`. The "legacy" `v1` will continue to live on in some systems where needed.

	But `v2` is already underway, so this is now `v1b` for brevity. (Independent of the standard internal semantic naming convention adhered to.)

## Limitations

Currently, two-way conversion is only possible with a subset of _input_ bases from base-2, up to base-36.

But beyond base-36 (e.g. base-64, base-256, etc.), it's a one-way function - you can only get bases larger than 36, as output. Which sort of acts like a one-way hash function - which can be very useful, but is something you need to be aware of it.

While this script will be supported indefinitely into the future (as it's used in production environments), it's unlikely to ever be a universal "any base in, any base out" utility. That is specifically planned for a `-v2` binary executable. (But that doesn't mean it's not highly useful as-is.)

## Input bases

You can convert a value in one of these input numeric bases, to any other base in "Output bases", larger or smaller.

| Base        | Description                                                 | Characters
| :--         | :--                                                         | :--
| 2           | Binary                                                      | 0,1
| 8           | Octal                                                       | 0-7
| 10          | Decimal [default]                                           | 0-9
| 16          | Hexadecimal                                                 | 0-9, A-F
| 36          | Just alphanum                                               | 0-9, A-Z

## Output bases

| Base        | Description                                                 | Symbols                           | Reference
| :--         | :--                                                         | :--                               | :--
| 2           | Binary                                                      | 0,1
| 8           | Octal                                                       | 0-7
| 10          | Decimal [default]                                           | 0-9
| 16          | Hexadecimal                                                 | 0-9, A-F
| 26          | Upper-case alphabet                                         | A-Z
| 32[r]       | RFC 4648 §6                                                 | A-Z, 2-7                          | https://www.rfc-editor.org/rfc/rfc4648.html#section-6
| 32h         | RFC 4648 §7 'Base32Hex'                                     | 0-9, A-V                          | https://www.rfc-editor.org/rfc/rfc4648.html#section-7
| 32c         | Crockford's base-32                                         | 0-9, A-Z no I, L, O, U            | https://en.wikipedia.org/wiki/Base32#Crockford's_Base32
| 32w         | Wordsafe base-32                                            | 2-9, CFGHJMPQRVWX, cfghjmpqrvwx   | https://en.wikipedia.org/wiki/Base32#Word-safe_alphabet
| 36          | Numbers and upper-case alphabet                             | 0-9, A-Z                          | https://en.wikipedia.org/wiki/Base36
| 38username  | Valid *nix username symbols                                 |
| 38hostname  | Valid *nix host and domain name symbols                     |
| 45email     | Valid HTML5 email tag symbols                               |
| 48j1w       | 32w + unicode symbols                                       |
| 52          | Both-case alphabetic                                        | A-Z, a-z
| 62          | All alphanum, code point order (hex-style)                  | 0-9, A-Z, a-z                     | https://en.wikipedia.org/wiki/Base62
| 64[r]       | RFC 4648 §5                                                 | 0-9, A-Z, a-z, +, /               | https://www.rfc-editor.org/rfc/rfc4648.html#section-4
| 64u         | RFC 4648 §5; URL-safe                                       | 0-9, A-Z, a-z, -, _               | https://www.rfc-editor.org/rfc/rfc4648.html#section-5
| 64h         | Hex-style base-64                                           |
| 64j1        | Alternate to 64u but also programmer-friendly               | 0-9, A-Z, a-z, ʞ, λ
| 64j1w       | Same as 32w and 48j1w, + more unicode symbols               |
| 128j1w      | 64j1w + more unicode symbols                                |
| 128j1       | Base 62 + unicode symbols                                   |
| 256j1       | Base 128j1 + more unicode symbols                           |
| 288j1       | Base 256j1 + more unicode symbols                           |

## Example output

The chart below shows a big random base 10 number '2023090613425900000000000000001' in various bases.

Note that some of the larger bases appear to have longer output - but that's only due to being rendered with proportional fonts, combined with some of the wider Unicode characters. Look at the "Chars" column to see the actual # of characters in the output.

|Base         | Chars | Number representation
|:--          | --:   | :--
|   2         |   101 | 11001100010001111010101010101001101101001000111010011010010010010001000110101111111100000000000000001
|   8         |    34 | 3142172525155107232222106577400001
|__10__       |    31 | __2023090613425900000000000000001__
|  16         |    26 | 1988F5553691D3492235FE0001
|  26         |    22 | DXNNAGDDUWPNKQIDYGEAMJ
|  32[r]      |    21 | BTCHVKU3JDU2JEI274AAB
|  32h        |    21 | 1J27LAKR93KQ948QVS001
|  32c        |    21 | 1K27NAMV93MT948TZW001
|  32w        |    21 | 3X49fGcqF5cpF6Cpxr223
|  36         |    20 | 5G53VAIZAJBZ2D5Y2Y9T
|  38hostname |     |
|  39username |     |
|  45email    |     |
|  48j1w      |     |
|  52         |    18 | NftxKBqjrhTdQKHAGJ
|  62         |    17 | gR7BplOIkweh9aKht
|  64[r]      |    17 | PYFLLDf7JII8r/W01
|  64u        |    17 | PYFLLDf7JII8r_W01
|  64h        |     |
|  64j1       |     |
|  64j1w      |     |
| 128j1w      |     |
| 128j1       |     |
| 256j1       |    13 | Pĵㅍ‡sĨǍᚧYrぇ01
| 288j1       |    13 | 6zф⅖ẄÃЋゲㅎぇúkᛎ

## Document history

- 2023-10-09: First version.
- 2026-04-17:
	- Added sections: Input base, and Example output.
	- Removed custom base 94ascii for Output bases (no longer supported).
- 2026-04-23: Updated for v1b.

## Copyright and license

> Copyright © 2023-2026 Jim Collier (ID: 1cv◂‡Vᛦ)<br>
> Licensed under GNU GPL v2 <https://www.gnu.org/licenses/gpl-2.0.html>. No warranty.

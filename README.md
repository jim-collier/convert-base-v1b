# x9convertbase
Converts arbitrarily large numbers between 23 prededined standard and custom bases.

The actual command is `x9convertbase1` (note the number on the end), because it will be very important to always give identical output, given the same arguments. However, over a future many years, there will easily be myriad good reasons for the output to change. To avoid overwriting an old script on a running system that may rely on it and it's predictable output, a new suffix number will be given to future scripts if the output changes, and the two will coexist. That the existing version has a number, indicates that expected inevitability now.

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
| 94[ascii]   | All lower ASCII chars + space (all typable US keyboard)

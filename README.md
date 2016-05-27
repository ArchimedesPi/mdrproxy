# Möbius Double Reacharound Proxy

## Rationale
There already exist anonymizing proxies (Tor being a well-known example), but many, if not all, are tailored to a specific scenario, easy to block with a firewall or Deep Packet Inspection, or inflexible.

mdrproxy attempts to fill the small but fascinating niche of a highly modular and configurable traffic encryption, obfuscation, steganography, and tunneling system - a Build Your Own proxy.

## Architecture
*warning: this is all a roadmap, almost none of this currently exists.*

mdrp has two types of module, **transformers** and **adapters**.
Transformers take a datastream as input, and spit out another, transformed datastream.
adapters convert between a datastream and the outside world, by taking the datastream bytes and shovelling them over some protocol. Specific adapters and transformers work well together, and are largely useless when separated. In fact, some adapters *must* be paired with a specific transformer.

mdrp has multiple endpoint network layer io adapters: a TUN adaptor (`tun`) and a SOCKS adaptor (`socks`).
These are the adapters through which mdrp endpoints will allow data to flow from applications through.

mdrp supports protocol layer adapters, which the bulk of steganographic obfuscated data transfer is done via:
* IRC client (`irc_client`)
* httpd (`http_server`)
* http client (`http_client`)
* dns server/iodine server (`iodine_server`)
* dns/iodine (`iodine_client`)
* smtp client (`smtp_client`)

mdrp's currently planned basic transformers are:
* probabilistic chaff inserter (`chaff`)
* steganographic image emitter (`img_stego`)
* ascii encoder and compressor (`ascii_ec`)
* unicode encoder and compressor (`unicode_ec`)
* debug dumping (`debug`)

a taste of things to come:
* `httpvisitor_stego`
* `httppub_stego`
* `dnsvisit`

Extending transformers is easy. In fact, customizing transformers is highly recommended.

## Roadmap (may 27 2016)
* base module system
* modules
  * `debug`
  * `ascii_ec`

## License
Möbius Double Reacharound Proxy
Copyright (C) 2016 Liam Marshall

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.

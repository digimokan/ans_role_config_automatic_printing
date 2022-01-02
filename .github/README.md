# ans_role_config_automatic_printing

Configure automatic printer discovery and IPP Everywhere driverless printing.

[![Release](https://img.shields.io/github/release/digimokan/ans_role_config_automatic_printing.svg?label=release)](https://github.com/digimokan/ans_role_config_automatic_printing/releases/latest "Latest Release Notes")
[![License](https://img.shields.io/badge/license-MIT-blue.svg?label=license)](LICENSE.md "Project License")

## Table Of Contents

* [Purpose](#purpose)
* [Requirements](#requirements)
* [Supported Operating Systems](#supported-operating-systems)
* [Quick Start](#quick-start)
    * [Use From Playbook](#use-from-playbook)
* [Role Options](#role-options)
* [Role Dependencies](#role-dependencies)
* [Contributing](#contributing)

## Purpose

* Configure automatic printer discovery, using the [CUPS](https://www.cups.org/)
  print client, and [Avahi](https://avahi.org/).

* Configure discovered printers for use, using
  [IPP Everywhere](https://www.pwg.org/ipp/everywhere.html) "driverless"
  printing protocol.

* _NOTE_ Since this role automates printer detection, it may be installed
  instead of
  [ans_role_config_printer](https://github.com/digimokan/ans_role_config_printer),
  if printers support discovery.

## Requirements

* Printer discovery requires that printers reside on the _same IP subnet_ as the
  host machine.

* Printers must support the
  [IPP Everywhere](https://www.pwg.org/ipp/everywhere.html) "driverless"
  printing protocol.

* See the following resources to check IPP Everywhere support for a printer:

    * [Legacy LPD vs IPP Everywhere Discussion](https://askubuntu.com/a/1102132)

    * [IPP Everywhere Official Supported Printer List](https://www.pwg.org/printers/)
      (may not be fully up-to-date)

    * [Apple AirPrint Official Supported Printer List](https://support.apple.com/en-us/HT201311#printers)
      (extensive list, and it's usable, since AirPrint depends on IPP Everywhere)

## Supported Operating Systems

* Arch Linux.
* FreeBSD.

## Quick Start

### Use From Playbook

1. Create `requirements.yml` in ansible project root, and add this content:

   ```yaml
   # requirements.yml
   - src: https://github.com/digimokan/ans_role_config_automatic_printing
   ```

2. From the project root directory, install/download the role:

   ```shell
   $ ansible-galaxy install --role-file requirements.yml --roles-path ./roles --force-with-deps
   ```

   * _NOTE:_ `--force-with-deps` _ensures subsequent calls download updates_

3. Include the role like any local role, from the project playbook:

   ```yaml
   # playbook.yml
   - hosts: localhost
     connection: local
     tasks:
       - name: "Configure automatic printer discovery and driverless printing"
         ansible.builtin.include_role:
           name: ans_role_config_automatic_printing
   ```

## Role Options

See the role `defaults` file, for overridable vars:

  * [defaults/main/](../defaults/main/)

## Role Dependencies

* [ans_role_config_avahi](https://github.com/digimokan/ans_role_config_avahi)

## Contributing

* Feel free to report a bug or propose a feature by opening a new
  [Issue](https://github.com/digimokan/ans_role_config_automatic_printing/issues).
* Follow the project's [Contributing](CONTRIBUTING.md) guidelines.
* Respect the project's [Code Of Conduct](CODE_OF_CONDUCT.md).


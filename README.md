
# stdcfg

#### Table of Contents

1. [Description](#description)
2. [Setup - The basics of getting started with stdcfg](#setup)
    * [What stdcfg affects](#what-stdcfg-affects)
    * [Setup requirements](#setup-requirements)
    * [Beginning with stdcfg](#beginning-with-stdcfg)
3. [Usage - Configuration options and additional functionality](#usage)
4. [Limitations - OS compatibility, etc.](#limitations)
5. [Development - Guide for contributing to the module](#development)

## Description

Puppet module for configuring standard settings of all LSST servers. Think of this as setting up the bare minimum configurations for using an LSST server.

This includes the Core set of things that apply to ALL nodes across the board (no exceptions).

## Setup

### What stdcfg affects

The `stdcfg` module affects the following services on a given server:

  * basic package installation
  * email configuration
  * selinux configuration
  * time configuration

### Setup Requirements

The following parameters must (or should) be defined:

  * `stdcfg::kerberos::createhostkeytab` - String of BASE64 encoded keytab file used for creating kerberos host keys

This module requires the following puppet modules to be installed:

  * https://forge.puppet.com/beergeek/chronyd
  * https://forge.puppet.com/puppetlabs/firewall
  * https://forge.puppet.com/puppetlabs/inifile
  * https://forge.puppet.com/puppetlabs/stdlib
  * https://forge.puppet.com/saz/timezone

### Beginning with stdcfg

## Usage

To load the stdcfg puppet module, declare this class in your manifest with `include stdcfg`.

## Reference

The following parameters let you extend stdcfg options beyond the default:

  * `stdcfg::additional_packages` - Array of yum packages to install
  * `stdcfg::email::required_pkgs` - Array of packages to install for email support
  * `stdcfg::email::canonical_aliases` - String of connonical email aliases
  * `stdcfg::email::virtual_aliases` - String of virutal email aliases
  * `stdcfg::email::mydomain` - String of domain used by email
  * `stdcfg::email::relayhost` - String of relayhost used by email (smtp server)
  * `stdcfg::selinux::status` - String of status for SElinux
  * `stdcfg::time::ntp_servers` - Array of ntp servers to use
  * `stdcfg::time::timezone` - String of timezone to use

## Limitations

This stdcfg module only supports RHEL/CentOS servers that are configured to use `iptables`.

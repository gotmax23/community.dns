# Community DNS Collection
[![Documentation](https://img.shields.io/badge/docs-brightgreen.svg)](https://ansible.fontein.de/collections/community/dns/)
[![CI](https://github.com/ansible-collections/community.dns/workflows/CI/badge.svg?event=push)](https://github.com/ansible-collections/community.dns/actions)
[![Public Suffix List up-to-date](https://github.com/ansible-collections/community.dns/workflows/Check%20for%20Public%20Suffix%20List%20updates/badge.svg?branch=main)](https://github.com/ansible-collections/community.dns/actions?query=workflow%3A%22Check+for+Public+Suffix+List+updates%22+branch%3Amain)
[![Codecov](https://img.shields.io/codecov/c/github/ansible-collections/community.dns)](https://codecov.io/gh/ansible-collections/community.dns)

This repository contains the `community.dns` Ansible Collection. The collection includes plugins and modules to work with DNS.

## Tested with Ansible

Tested with the current Ansible 2.9, ansible-base 2.10 and ansible-core 2.11 releases and the current development version of ansible-core. Ansible versions before 2.9.10 are not supported.

## External requirements

Depends on the plugin or module used.

## Included content

- Modules:
  - `hosttech_dns_record`: create/update/delete DNS records with HostTech DNS.
  - `hosttech_dns_record_info`: retrieve information on DNS records from HostTech DNS.
  - `hosttech_dns_records`: bulk synchronize DNS records in Hosttech DNS service.
  - `hosttech_dns_zone_info`: retrieve zone information from HostTech DNS.
  - `wait_for_txt`: wait for TXT records to propagate to all name servers.
- Filters:
  - `get_public_suffix`: given a domain name, returns the public suffix. For example, `"www.ansible.com" | community.dns.get_public_suffix == ".com"` and `"some.random.prefixes.ansible.co.uk" | community.dns.get_public_suffix == ".co.uk"`.
  - `get_registrable_domain`: given a domain name, returns the *registrable domain name* (also called *registered domain name*). For example, `"www.ansible.com" | community.dns.get_registrable_domain == "ansible.com"` and `"some.random.prefixes.ansible.co.uk" | community.dns.get_registrable_domain == "ansible.co.uk"`.
  - `remove_public_suffix`: given a domain name, returns the part before the public suffix. For example, `"www.ansible.com" | community.dns.remove_public_suffix == "www.ansible"` and `"some.random.prefixes.ansible.co.uk" | community.dns.remove_public_suffix == "some.random.prefixes.ansible"`.
  - `remove_registrable_domain`: given a domain name, returns the part before the DNS zone. For example, `"www.ansible.com" | community.dns.remove_registrable_domain == "www"` and `"some.random.prefixes.ansible.co.uk" | community.dns.remove_registrable_domain == "some.random.prefixes"`.

## Using this collection

Before using the General community collection, you need to install the collection with the `ansible-galaxy` CLI:

    ansible-galaxy collection install community.dns

You can also include it in a `requirements.yml` file and install it via `ansible-galaxy collection install -r requirements.yml` using the format:

```yaml
collections:
- name: community.dns
```

See [Ansible Using collections](https://docs.ansible.com/ansible/latest/user_guide/collections_using.html) for more details.

## Contributing to this collection

If you want to develop new content for this collection or improve what is already here, the easiest way to work on the collection is to clone it into one of the configured [`COLLECTIONS_PATH`](https://docs.ansible.com/ansible/latest/reference_appendices/config.html#collections-paths), and work on it there.

See [TESTING.md](https://github.com/ansible-collections/community.dns/tree/main/TESTING.md) for information on running the tests.

You can find more information in the [developer guide for collections](https://docs.ansible.com/ansible/devel/dev_guide/developing_collections.html#contributing-to-collections), and in the [Ansible Community Guide](https://docs.ansible.com/ansible/latest/community/index.html).

## Release notes

See the [changelog](https://github.com/ansible-collections/community.dns/tree/main/CHANGELOG.rst).

## Releasing, Versioning and Deprecation

This collection follows [Semantic Versioning](https://semver.org/). More details on versioning can be found [in the Ansible docs](https://docs.ansible.com/ansible/latest/dev_guide/developing_collections.html#collection-versions).

We plan to regularly release new minor or bugfix versions once new features or bugfixes have been implemented.

Releasing the current major version happens from the `main` branch. We will create a `stable-1` branch for 1.x.y versions once we start working on a 2.0.0 release, to allow backporting bugfixes and features from the 2.0.0 branch (`main`) to `stable-1`. A `stable-2` branch will be created once we work on a 3.0.0 release, and so on.

We currently are not planning any deprecations or new major releases like 2.0.0 containing backwards incompatible changes. If backwards incompatible changes are needed, we plan to deprecate the old behavior as early as possible. We also plan to backport at least bugfixes for the old major version for some time after releasing a new major version. We will not block community members from backporting other bugfixes and features from the latest stable version to older release branches, under the condition that these backports are of reasonable quality.

## More information

- [Ansible Collection overview](https://github.com/ansible-collections/overview)
- [Ansible User guide](https://docs.ansible.com/ansible/latest/user_guide/index.html)
- [Ansible Developer guide](https://docs.ansible.com/ansible/latest/dev_guide/index.html)
- [Ansible Collections Checklist](https://github.com/ansible-collections/overview/blob/master/collection_requirements.rst)
- [Ansible Community code of conduct](https://docs.ansible.com/ansible/latest/community/code_of_conduct.html)
- [The Bullhorn (the Ansible Contributor newsletter)](https://us19.campaign-archive.com/home/?u=56d874e027110e35dea0e03c1&id=d6635f5420)
- [Changes impacting Contributors](https://github.com/ansible-collections/overview/issues/45)

## Licensing

All files except specifially noted are licensed under the GNU General Public License v3.0 or later.

See [COPYING](https://www.gnu.org/licenses/gpl-3.0.txt) to see the full text.

The only exception is `plugins/public_suffix_list.dat`, which is subject to the terms of the Mozilla Public License, v. 2.0. See [MPL](https://mozilla.org/MPL/2.0/) for the full text.

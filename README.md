# WG Digital Identity Attestation (formerly Developer Identity)

This charter describes operations as an [OSSF Technical Initiative](https://github.com/ossf/tac/blob/master/charters/).

To get caught up on what this group has been up to, check out this [recap](https://openssf.org/blog/2021/01/27/digital-identity-attestation-roundup/).

## Objective

Our objective is to enable open source maintainers, contributors and end-users to understand and make decisions on the provenance or origin of the code they maintain, produce and use.

## Motivation

Without too much effort, an attacker could insert malicious code into a popular open source library and carry out an
attack.

One way an attacker could achieve this is by looking for a highly imported package that sits low in the stack but can
still affect communication, maybe even has root access, and that has few eyes on it, or even no eyes.
This type of attack was carried out against the [event-stream](https://arstechnica.com/information-technology/2018/11/hacker-backdoors-widely-used-open-source-software-to-steal-bitcoin/)
module in node.js, which was co-opted to steal bitcoins (by attempting to steal credentials for developers of a
particular bitcoin wallet), a malicious maintainer took over the code:

> "He emailed me and said he wanted to maintain the module, so I gave it to him," developer Dominic Tarr wrote in a
> GitHub comment. "I don't get anything from maintaining this module, and I don't even use it anymore, and haven't
> for years."

Of course, once the change is committed, it is effectively trusted.
The secure hashes will match, it will be included in many places (in this case several hundred thousand), and in turn
those packages will be built, signed, stored on trusted sites, and used and included elsewhere.

In the case of malicious code, the attacker will also try to obscure the real effect, and can also introduce the attack
slowly such that individual commits are less suspect.
The attack above was executed in multiple steps.

These problems need solutions!

### Goals

<img align="right" src="./dog_meme.jpg">

* Give open source maintainers a way to do work under their chosen name, and to prevent others from impersonating them.
* Give open source communities the tools and infrastructure to verify the identities of their maintainers, based on their chosen criteria.
* Give consumers of open source libraries more data for determining the risks of depending on said library.
* Give consumers and maintainers a trustworthy public record of who implemented changes to an Open Source software project.
* Respect the privacy of everyone involved.
* Give OSS maintainers better ability to ensure that project governance policies (like independent signoff) are followed.
* Give OSS consumers tools to detect changes in activity from unknown contributors.
* Allow consumers of open source to examine the full provenance of their open source supply-chains.
* Allow trust between humans and do not require trusted intermediaries.

For a full list of the threat models we are trying to address, see the [Threat Models](threat_models.md) document.

### Non Goals

* Enforce or mandate identity policy and requirements for projects.
  We will simply make these services, policies, and tools available and easy-to-use, leaving it up to projects and communities to adopt if they choose to do so.
* Make it harder for people to contribute to open source projects.
* Any kind of formal "vetting" or "verification" program. 
* Any formal specifications or provenance formats.

## Necessary Human Use Cases to Support

* Change / leave employer
* Aggregate identities in multiple systems in a single signature
* Change name, want to carry over identity
* Change name, do not want to carry over identity
* Work under a pseudonym to protect oneself, e.g. from discrimination, harassment, or stalking
* Expiration on attestations? (I checked this email at time X, need to re-verify every Y months)
* Explicit revocation of attestations (Y no longer works for X)
* Rotate key for one/all systems
* Annotate repair of bad actor's changes

## Prior Work

* [OpenPGP proofs](https://metacode.biz/openpgp/proofs) to verify identities on social media and other systems in a decentralized way.
* Keybase.io had a service to verify identities for social media and send encrypted messages.
  The original system and open source command line program allowed you to get a public key safely, just by knowing a person's username on a social network.
* [Debian](https://wiki.debian.org/DebianDeveloper/JoinTheProject/NewMember#Step_4:_Identification) generally requires identity verification of maintainers/developers.
  Pseudonymous contributions are only allowed in special circumstances.
* [Fedora](https://fedoraproject.org/wiki/Join_the_package_collection_maintainers#Introduce_yourself) prefers/requires real name communication for maintainers, but doesn't attempt to require it.
* [Ubuntu](https://wiki.ubuntu.com/NewDevelopersAndMaintainers) doesn't enforce identity, but worries about it: "Authentication problem, you have to know that a person is who he says he is."
* [Kubernetes](https://github.com/kubernetes/community/blob/master/community-membership.md) requires existing members to sponsor new members.
* [Linux Kernel/Hyperledger Discussion re: DCOs](https://wiki.hyperledger.org/plugins/servlet/mobile?contentId=24775311#content/view/24775311)
"In the Linux kernel for example the maintainers are expected to know the identity of anyone whose patches they're contributing.
The real issue is if there was ever a legal matter, would the person be identifiable and available because we have their identity."

## Operations

WG-Developer-Identity operations are consistent with standard operating guidelines
provided by the OSSF Technical Advisory Committee
[TAC](https://github.com/ossf/tac).

### Meetings

Join the mailing list for the calendar invitation!

The public calendar is available here: https://calendar.google.com/calendar/r?cid=czYzdm9lZmhwNWk5cGZsdGI1cTY3bmdwZXNAZ3JvdXAuY2FsZW5kYXIuZ29vZ2xlLmNvbQ

### Communications

We have a [public email list](https://lists.openssf.org/g/openssf-wg-dev-identity). [Manage your subscriptions to Open SSF mailing lists](https://lists.openssf.org/g/main/subgroups).

#### Notes and Agendas

Meeting Notes and Agendas are available on [Google Drive](https://docs.google.com/document/d/1xPs2sSbH3I9Ich7OyLOzl85oJshnK8Q6WoAgREE5-zA/edit). (Join the group above to edit.)

## Governance

Full details of process and roles are linked from [governance README](/governance).

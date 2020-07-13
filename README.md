# WG Developer Identity

This charter describes operations as an [OSSF Technical Initiative](https://github.com/ossf/tac/blob/master/charters/).
The [Focus](#focus) section below describes what is in and out of scope,
and [Governance](#governance) section describes how our operations are consistent with OSSF policies with links to more detailed documents.

**Mission:** TODO

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

One way to help mitigate and potentially detect an attack like this is to build a trusted identity system for maintainers of critical open source
projects. Highly critical projects should be encouraged to verify the identity of their maintainers, and anyone with
administrative permissions on their SCM, CI or artifact management systems.
Later, they may make use of this identity system to flag contributions that should warrant closer review.

It would also be of benefit to have a public record of code commits and changes, so that in the event that a compromise
is discovered, we have an immutable / time stamped record of the change and its author. Having such a
tamper resistant proof of change(s) would then allow queries to be made against the compromised access credentials (the
developer ID) and allow us to see if compromised developer ID performed changes in other open source projects (thereby
suggesting further compromise to other projects).

This might be best achieved with a transparency log type system.

The public record could be modelled after the similar effort to provide open audit of certificate signing as implemented
in the [certificate transparency](https://www.certificate-transparency.org/) project.

### Goals

![dog_meme](./dog_meme.jpg)

* Give open source maintainers a way to do work under their chosen name, representing their real employers in secure ways.
* Give open source projects tools and infrastructure to verify the identities of their maintainers.
* Give consumers of open source libraries more data for determining the risks of depending on said library.
* Give consumers and maintainers a public record of who implemented changes to an Open Source software project.
* Respect the privacy of everyone involved.
* Give OSS maintainers better ability to ensure that project governance policies (like independent signoff) are followed.
* Give OSS consumers tools to delect surges in activity from unknown committers.

### Non Goals

* Enforce or mandate identity requirements for projects.
  We will simply make this service available and easy-to-use, leaving it up to projects and communities to adopt if they choose to do so.

## Threat Models

This section contains possible attacks we can try to mitigate, prevent or detect:

* Malicious/Nefarious individuals get maintainer permissions and starts making making commits or pushes to a registry
* Duplicate accounts, self-reviewing code
* Identity spoofing: claiming you work for a specific organization that you do not, or are a specific individual that you are not

## Necessary Human Use Cases to Support

* Change / leave employer
* Aggregate identities in multiple systems in a single signature
* Change name, want to carry over identity
* Change name, do not want to carry over identity
* Expiration on attestations? (I checked this email at time X, need to re-verify every Y months)
* Explicit revocation of attestations (Y no longer works for X)
* Rotate key for one/all systems
* Annotate repair of bad actor's changes

## Prior Work

* Keybase.io started as a service to verify identities for social media and send encrypted messages.
  The original system and open source command line program allowed you to get a public key safely, just by knowing a person's username on a social network.
  It created a public key pair for users which could then be used to verify identity.
* [Debian](https://wiki.debian.org/DebianDeveloper/JoinTheProject/NewMember#Step_4:_Identification) generally requires identity verification of maintainers/developers.
  Pseudonymous contributions are only allowed in special circumstances.
* [Fedora](https://fedoraproject.org/wiki/Join_the_package_collection_maintainers#Introduce_yourself) prefers/requires real name communication for maintainers, but doesn't attempt to require it.
* [Ubuntu](https://wiki.ubuntu.com/NewDevelopersAndMaintainers) doesn't enforce identity, but worries about it: "Authentication problem, you have to know that a person is who he says he is."

## Operations

WG-Developer-Identity operations are consistent with standard operating guidelines
provided by the OSSF Technical Advisory Committee
[TAC](https://github.com/ossf/tac).

### Meetings

TODO: Add info on meeting schedule and calendar invitations

#### Notes and Agendas

TODO: Add links to notes and agendas

### Communications

TODO: Add links to slack channel and email lists

## Governance

Full details of process and roles are linked from [governance README](/governance).

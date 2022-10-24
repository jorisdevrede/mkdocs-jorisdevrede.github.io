# IT Security

The focus of IT security is the protection against misuse of applications. If
you view this "Protection Against Misuse" as a [stock](theory.md),
then its inflows are the *hardening* of intended use and the *patching* of
flaws that lead to unintended use. The outflow is the discovery of those
flaws, or *vulnerabilities*.

![security system](../images/security_system.svg)

## Hardening

Taking measures to lower the attack surface of an application is called
hardening. This means, for example, that you disable an administrative endpoint
or limit the allowed login attempts. Both are intended functions of the
application that you limit against misuse. The more you harden an application,
the better it is protected against misuse.

## Vulnerabilities

While failure to harden is also a vulnerability, we generally use the term for
flaws in the code that open the application for unintended use. The discovery
of these vulnerabilities lower the protection of the application.

Technically the vulnerability is already there, making the "Protection Against
Misuse" stock as low as all the still unknown vulnerabilities subtracted from
it. In practice a vulnerability is only considered when it is actually
discovered and can be acted upon.

Additional vulnerabilities to consider are those lower in the operational
stack of the application. A vulnerability in the underlying operating system,
for example, could grant direct access to the application. That vulnerability
then also subtracts from the protection of the application.

## Patching

When a vulnerability is known, the application developer can fix the flaw and
provide a new version of the application. Installing this new version for the
purpose of removing the vulnerability is what we call patching.

We should strive to always have the latest patch version of an application
installed as it will provide the highest protection possible.

## Pentesting

A penetration test, or pentest, is the feedback loop that measures the
"Protection Against Misuse" stock by testing the hardening measures in place
and the patches not in place. It can optionally be expanded to search for
unknown vulnerabilities, discovering them during the test itself. This search
is usually reserved for bespoke applications.

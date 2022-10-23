# IT Security

The primary aspect of security for all software applications is the protection
against misuse. If you view this "Protection Against Misuse" as a stock, then
its inflows are the *hardening* of functionally intended use and the
*patching* of functionally unintended use. The outflow is the discovery of
unintended uses, or *vulnerabilities*.

## Hardening

The measures you take to lower the attack surface of the application are
called hardening. This means for example that you disable an administrative
endpoint or limit the login attempts for an account. These are both intended
functions (admin, login) of the application to which you limit it's access so
it cannot be misused. The more you harden the application, the better it is
protected.

## Vulnerabilities

While failure to harden a function is also a vulnerability, we generally use
the term for flaws in the code that open the application for unintended use.
The discovery of these vulnerabilities will lower the protection of the
application.

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
purpose removing the vulnerability is what we call patching.

We should strive to always have the latest patch version of an application
installed as it will provide the highest protection possible.

## Choose manual or automatic

The sheer number of vulnerabilities that is found every day, makes it almost
impossible to evaluate these individually and assess whether a patch is needed.
Instead we need to automatically install whenever a patch becomes available.

# Trusting TLS

TLS is one of the most used and, at the same time, one of the least understood
technologies. Yes, it secures your connections, but how it does that seems to
be a mystery. This leaves us susceptible to vague statements like "your credit
cards will be stolen when you use self-signed certificates" and "turning off
host verification will make your server vulnerable to hackers". Nobody knows,
but it sounds scary, so it must be true. So what is the deal with TLS and is it
really that scary?

TLS has two functions<sup>*</sup>. The first is the encryption of data in 
transit, and the second is providing trusted connections. Encryption is the main
one. That is the reason we have TLS. Trust is an extra that has its use, but
does not compare in importance to encryption. It is however the one that we get
worked up about. Let's look at each function in isolation.

<sup>_*Actually, TLS has more functions, but they pale in application compared to
these two._</sup>

## Encryption 

TLS encrypts the TCP data packets between client and server. It does so by
exchanging a symmetric key that both the client and the server use to encrypt
and decrypt the packets. This ensures that only the client and server can read
the data that they exchange, but that no other intermediate system on the
network can eavesdrop. Of course there are complex details, but this is the
essence and there really isn't more to it. Data is encrypted in transit. That
is it.

## Trust

TLS can also provide a level of trust about the server that the client connects
to using PKI certificates. The server provides the client a certificate that
holds the address of the server and is signed by a third party, the Certificate
Authority. This way, the client can verify independently that it is connecting
to the intended server.

### Trust on the public network

This trust function is relevant on an untrusted public network, where client
traffic can be intercepted by another server that poses as the intended server.
The client can then be tricked into divulging sensitive information, like a
password or credit card information. The trust function verifies that the
connecting server corresponds with the intended address.

It is a useful function on an uncontrolled public network to provide assurance
that the data reaches the intended recipient. On a controlled private network
though, this is useless at best and is probably even an active hindrance. Here
is why.

### Commercial CA's

Trust on a client, or more accurately "TLS host verification", works by first
trusting the certificate of the Certificate Authority (CA) that signed the
server certificate. By trusting the CA the client implicitly trusts all the
server certificates it signs. This works well on the internet where our browsers
and operating systems trust a list of commercial CA's by default and where we
buy all the  public server certificates from these CA's. 

So because Google trusts a bunch of CA's and packages Chrome with their signing
certificates, and the company whose website you're surfing has bought its server
certificate from those CA's, you don't have to worry about your TLS
configuration. How different that is on a private network.

### Rolling your own

Instead of using prepackaged commercial CA's, you can also create your own
singing certificate. Technically, this provides the same level of trust and is
cheaper, because you can make as many server certificates as you want for free.
The downside of this solution is that you have to configure each client to trust
your signing certificate for all the TLS-based connections to work. 

That is when you should evaluate the trust function itself. Is there a chance
that a client can connect to an unverified server and that it can thereby
disclose sensitive information? If the answer is yes, then make the
administrative investment of configuring each client to trust your signing
certificate. If the answer is no on the other hand, then you might be better off
with setting the 'host verification' parameter to 'false' in your TLS
connections. It disables trust, relieves you off needless configuration and
leaves only with its primary function; encryption of data in transit. No more,
no less. 

### But my browser says

When you do decide that the servers can be trusted and that host verification
has no added value in your particular context, there is always your browser
that screams bloody murder when trying to connect to one of those servers. That
is because TLS host verification was designed for the internet with
non-technical users in mind. Don't be that end user and know that TLS is a fail
fast protocol. Just click 'OK' and know that your connection is encrypted and
safe.



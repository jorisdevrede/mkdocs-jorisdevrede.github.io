# Trusting TLS

TLS is one of the most used and least understood technologies. It secures
connections, but how seems a mystery. This leaves us with statements like "your
credit card data will be stolen when you use self-signed certificates". Nobody
knows, but it sounds scary enough so it must be true. Or is it?

TLS has two main functions. The first is encrypting data in transit. The second
is providing trust on a public network. Encryption is the important one, but it
is trust that we get worked up about.

## Encryption 

TLS encrypts TCP packets between client and server, using a key that only they
know. This ensures that only the client and server can read the data they
exchange. No intermediate can eavesdrop. The details are more complex, but this
is the essence. Data is secured between the two parties. That is it.

### Fail-fast

This encryption is guaranteed, because TLS is a fail-fast protocol. If the
communication cannot be encrypted, it will not happen. This contrary to the
browser messages saying your connection *might* not be safe. These messages only
apply to trust and never to encryption.

## Trust

TLS can also provide trust about the server that the client connects to. The
server provides a certificate that holds the server address and is signed by a
third party. The client can choose to trust the third party and its signed
confirmation of the server address.

### Trust on the public network

Trust is relevant on an untrusted network where client data can be intercepted
by an intermediate system that poses as the intended server. The client can
then be tricked into leaking sensitive information like password or credit
card data. The trust function verifies that the server is the intended address.

In an uncontrolled network it is useful to assure that data is sent to the
intended recipient. In a controlled network though, this is useless at best.
Here is why.

### Commercial CA's

Trust, or more accurately "TLS host verification", works by first trusting the
certificate of the Certificate Authority (CA) that signed the server 
certificate. This will let the client trust all the server certificates that
the CA signs. Browsers and operating systems are preconfigured to trust a list
of commercial CA's and server certificates are bought from these CA's.

So because Chrome trusts a bundle of CA's and the site you are browsing has a
certificate that is signed by one of those CA's, you don't have to worry about
TLS. How different that is on a private network.

### Rolling your own

Trusting a preconfigured commercial CA is no different from trusting a CA that
you create yourself. It provides the same level of trust. The difference is
that a certificate from your own CA is free, which makes it preferable over
commercial CA's. The downside of this is that you have to configure each client
to trust your CA. This configuration comes at a cost as well.

That is when you should evaluate trust itself. Is there a change that a client
can connect to an unverified server? If so, make the investment of configuring
each client with your CA. If not, then you are better off with turning host
verification off in your TLS connections. It delegates trust to your known
network and leaves you with encryption. No more, no less.

### But my browser says

When you decide that servers are known and that host verfication has no added
value in your particular context, there is still your browser that screams
bloody murder. That is because TLS host verfication was designed for the
internet with non-technical users in mind. Just click *OK* and know that your
connection is encrypted and safe.


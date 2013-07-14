# The convergence of Internet messaging

## Foreword

### Blogs and "vainity mailing lists" are equivalent.

Some mailing list software can be configured to store an archive of all mail sent through it in HTML format on the Internet.

Some people have found it easier to set up "mailing lists for themselves" that than to adopt blog software or services, for the purpose of publishing the kind of content one would normally publish in a blog.

> This is a mailing list set up for me to randomly send messages to, and for my "fans" to discuss me. It's like an interactive weblog that's text-only, no HTML. --[glyph-discuss]

[glyph-discuss]: http://twistedmatrix.com/cgi-bin/mailman/listinfo/glyph-discuss

Just like with a blog, these "vainity mailing lists" support a comment system: any messages sent to the list in reply to a topic message appears in its context.

Consider that sending an e-mail is similar in UI to typing text into an HTML form and clicking "send."

Assume you have a mailing list that publishes its archives in HTML format on the Internet.

If you can send mail to that mailing list, you have a blog.

If others can respond to your messages, you have a blog that includes a threaded comments system.

If others can begin new topics, you have a web forum.

Vainity lists have something that modern blogs don't have: interoperability with all other forms of e-mail.

### A glut of incompatible options.

There are today a disparate glut of incompatible messaging systems in widespread use on the Internet. SMTP e-mail, USENET, forums like those on Slashdot and Reddit. Comments on Wordpress blogs. Disqus comments on various webpages. Facebook and Linkedin have their own systems. Every website has its own private-silo messaging and commenting infrastructure.

Without "pingback" software specifically designed to do it, there is no way to reply to a comment on one blog from another blog, or to merge a conversation taking place on Reddit with one on Digg about the same topic or URL.

If you do add a comment or a reply to someone else's commenting or forum system, it is entirely possible that it will be hidden or deleted. It's under someone else's control.

Some web-based forum software allows one to edit their posts. This means that the statement you reply to might not remain the same. You can be made to appear to agree or disagree with something you do not with bait-and-switch.

Many webpages that one might wish to have a discussion about explicitly disable comments.

A great deal of discussion happens on "mailing lists" that would benefit various discussions on the same subjects happening in web-based forums, and vice versa.

## How it could be different

I propose that this could all be different, and it begins with what Dan J. Bernstein's IM2000 project proposes: e-mail storage is the sender's responsibility.

**If storage is the mail sender's responsibility, all forms of Internet messaging may converge.**

### E-mail is messaging.

Alice drafts an e-mail message to send to Bob. Her e-mail program signs it, then encrypts it with a random symmetric key.

The key to decrypt the message is encrypted with Bob's public key. Since storage is the sender's responsibility, Alice's e-mail program stores the message on her server, or a server owned by a service provider with whom she has an account. It notifies Bob or Bob's service provider by some means that there is a new message waiting for him on Alice's server, and provides the key (that only Bob's private key can decrypt.)

Bob makes a request to Alice's server to retrieve the message. Maybe after verifying that Bob is who he claims to be and that Bob has successfully retrieved a copy of the message, Alice's server discards its copy.

If this form of e-mail were as popular as SMTP, we find ourselves in this situation: everyone who has the ability to send e-mail has an avenue to publish content on the Internet.

Alice drafts an e-mail message to send to a group of people. Her e-mail program signs it, then encrypts it with a random symmetric key. The key to decrypt the message is encrypted with each recipient's public key.

# Blogs are messaging.

Now, let's say Alice creates an e-mail, and addresses it **To: General Public**.

She signs her message, but it is for anyone to read, so it is not encrypted.

Since storage is the sender's responsibility, Alice's e-mail program stores the message on her server, or a server owned by a service provider with whom she has an account. It notifies the public by some means--perhaps something resembling an RSS feed--that there is a new message available on Alice's server.

Bob makes a request to Alice's server to retrieve the message. Maybe after verifying that Bob is who he claims to be and that Bob has successfully retrieved a copy of the message, Alice's server discards its copy.



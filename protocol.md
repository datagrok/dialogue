# Messaging

## Core concept

This mechanism is essentially [Internet Mail 2000]:

Messages are stored on the sender's always-online mail server.

The sender's mail server sends a small notification message to the recipient's mail server.

When the recipient wishes to retrieve their waiting message, they contact the sender's server and download the message.

The sender's server, upon confirming a successful transfer, may elect to delete the message to conserve disk space.

## Sending to a group

A message meant for a group of recipients may be stored just once on the sender's mail server.

The sender's server would not elect to delete the message until all the recipients confirm a successful transfer.

## Mailing lists

The sender's server might elect never to automatically clean up a message, instead making a set of messages able to be retrieved by recipients added later. "Mailing lists" become having your mail client periodically check for new messages at a particular location. 

## Content-addressable mail storage

If the server makes messages accessable by their hash value, it becomes trivial to distribute that data, and to serve it.

## Replies reference the original message

When one replies to a message, the hash value of the original message is included in the reply.

## Signatures and Privacy

All messages are signed and encrypted by default

## Questions



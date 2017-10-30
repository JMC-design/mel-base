# mel-base

[![Gitter](https://badges.gitter.im/Join Chat.svg)](https://gitter.im/neonsquare/mel-base?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

This library handles e-mail messages as first-class objects in Common Lisp. You can access messages from local Maildir folders or remote POP3, IMAP or SMTP servers. Reading and writing messages is all abstracted through a generic folder protocol: You can easily copy or move e-mails from a source folder (Maildir, POP3, IMAP) to different sink-folders (Maildir, IMAP, SMTP) using the same commands. Sending an E-Mail using MEL-BASE is done by just copying from its source folder to a SMTP folder.

An important design rule was that messages are never rewritten by MEL-BASE. Each message is stored octet by octet like the message-source provides it. Rewriting headers, encoding or other crude transformations are not done.

The folder protocols of MEL-BASE are designed to allow protocol specific optimizations. Moving messages is normally done by doing a copy and a delete afterwards. But on Maildir and IMAP those operations use the specific capabilities of their protocols. Moving an IMAP-Message from one IMAP-Mailbox to another is done without downloading the message first. The message objects are always read lazily. If a protocol allows finegrained access to message parts this is exploited by the architecture of MEL-BASE.

Future developments of MEL-BASE will emphasise making more portable by utilizing libraries like FLEXI-STREAMS, BORDEAUX-THREADS, USOCKET and so on. Another goal is to create an extension of the folder.

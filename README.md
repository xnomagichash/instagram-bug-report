# PSA: Instagram Emails Links are Dangerous by Design

## Summary

I reported an obvious (to me, anyway) security vulnerability I accidentally discovered by sharing a post link over Discord. The response I received back from Meta concerns me even more.

## Background

Recently I received an "Catch up on Instagram" email with a post of interest from Instagram, and, wanting to share the post to a friend on Discord, I copied the link from the "View Post" button and shared it via a DM in Discord.


Some days later, the friend on Discord noticed they were logged in as me. The email logged them in, bypassing password authentication, despite them being on a new device, with a different OS than I've ever used, on an instagram app already logged in to a different account! They could even change my password or post as me.


Naturally, I thought this was an incredibly severe bug. By sharing the link from that post (not forwarding the email as the fine print says as the bottom of the email), I exposed myself to anyone with the link being able to log in as me. Email is not secure by design, so besides the link itself being able to log me in and carrying no warning that I shouldn't share the link with others, anyone who intercepts the email in transit could do the same.

So off I went to submit this bug to Meta's bug bounty program.

## The Report

I reported the vulnerability, showing screenshot evidence of the user unwittingly logged in to my account, along with the link in question. Naively, I expected the most likely outcome was that this was a bug in the android application that was probably transient and fixed before I submitted it. The almost immediate response I got back, however, told a different story.


![Meta Response](./screenshot.png)


This response shows a shocking lack of security awareness at Meta. Whatever the reason, the facts on the ground remain the same. They allowed a different person, on a different device, in a different physical location, to log in as me silently, so that even they weren't aware, just by clicking on a link that I was not warned not to share. If I, as a software engineer, am able to make this mistake without Meta's security systems catching it, what chance does the average teenager or (god forbid) my parents have?

Interestingly, I thought to reopen the issue pointing out that their systems caught that it was a new device but silently logged them in anyway without a password, and that I was sharing a post, not a magic signin link...but apparently since this was my first report I'm not allowed to respond or reopen (max reopen credits: 0) the report. While I'm mildly disappointed my bug report doesn't qualify for a bounty, I'm extremely concerned that Meta isn't really taking account security seriously and think what happened is ok and somehow the user's fault.

Even more concerning is that the tokens in these emails don't appear to expire, unlike a magic login link. I shared the post days after I received it and it *still* worked.

## Summary

Instagram links are dangerous by design, and Meta doesn't recognize it as a security vulnerability.

### What can you do about it?

At the moment, it looks like enabling 2FA may be the only way to protect yourself. I encourage you to make sure everyone in your family who uses Instagram is protected in this way. Who knows what other kinds of Instagram linke silently have a magic login token silently attached!



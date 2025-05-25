---
title: Setting up
date: 2025-05-24
tags: [ "docs", "technical", "wop" ]
---

# Introduction

After finishing University, I came to realise that I was actually involving myself in most of what I learned in
the [[advanced-networking.md | Advanced Networking]] module, namely the DNS section of it. Thus began the rabbit hole,
where I wanted to take more control over the domain that I was using to host my
website [zainezq.com](https://zainezq.com).

I purchased the domain name at the end of 2024, right before new years, for around £10. At the time I was hosting the
website mentioned above using Vercel and the domain name was bought through them, so essentially I didn't *have* to even
do anything beside push to GitHub. The issue was that I had no idea how any of this was working, all I did was
`git push` and the rest was magic. Thus, I wanted more control over what I was doing.

## From Vercel to Netlify

The first step in this was to move my projects away from Vercel, for ethical purposes. I switched over to Netlify, which
I found to be a very similar experience to Vercel, but with a few more tweaks in setting up.
One thing I had to do was create a `netlify.toml` file where it would handle the configurations of the build. I ran into
an issue as I was changing the build script on the dashboard, and at the same time handling the `_redirects` and build
configuration in the `netlify.toml` file. To fix this, all I did was keep the build configuration as it was on the
project dashboard, but remove the one on the `netlify.toml` file. After this, the project built successfully.

The build script was `node -r dotenv/config mynode.js && ng build`

## From Netlify to Cloudflare

I only realised after that Netlify didn't have web analytics and there were limitations on build minutes and bandwidth,
thus I then switched from Netlify to Cloudflare. The actual switching over was quite smooth as I kept the `_redirects`
file, removed the `netlify.toml` file and used the UI to configure the build script. The only thing that needed changing
was setting the minimum `node.js` version to be at least `20` and the build command to be
`node -r dotenv/config mynode.js && npx ng build`.

## DNS Configuration

In terms of the DNS management, this took a while to configure, and was one of the reasons I kept switching hosting
services. I originally used Vercel, and purchased the domain name through them (a third party registrar I
presume), however, the first change (Vercel -> Netlify) was warranted because of ethical concerns, which made me
*want* to change the registrar specifically. So I decided to use `Krystal.io` as my registrar, which I found to be
quite nice and easy to set up. In order to transfer the domain name, I had to get the `EPP` code (also known as the
`Auth-Code`) from Vercel. After propagation, the transfer was complete. The issue with using this registrar, though, was
that I was trying to use this as my DNS manager as well, where I create records and manage them, but even after
adding the Netlify `nameservers` to the domain name, I couldn't get it to work. So what I decided to do was to
use `Krystal.io` as my registrar, and Cloudflare as the DNS manager, this way, I added the nameservers that
Netlify provided to the DNS records managed by Cloudflare and set up the other records (more on this below), and it
worked! Following this, the change from Netlify to Cloudflare in terms of hosting was quite smooth. All I needed to
change was the nameservers, A records and CNAME records, and it worked straight away.

### DNS Records

The DNS records I used were:

| Record Name | Description                                                                                                                                                                                                                                                                                                                                                                                                        |
|-------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| A           | I had two of these, with their names as "*", which refers to the wildcard value. In other words, The record of type `A` with the name `*.zainezq.com` has the value(s) of the IP address(es) given by Cloudflare                                                                                                                                                                                                   |
| CNAME       | The record of type `CNAME` with the name `zainezq.com` has the value of the the domain name for the website given by Cloudflare. I had another two CNAME records, one with the name `www` which was useful as it I wanted both `www.zainezq.com` and `zainezq.com` to point to the same website. I further had one more CNAME record which was used for a subdomain, namely `garden`. This points to this website! |
| SOA         | This was automatically generated for me, and assigned a Primary NS (one of the that was given) to it as well as the Responsible Email                                                                                                                                                                                                                                                                              |
| NS          | Two nameservers given by Cloudflare                                                                                                                                                                                                                                                                                                                                                                                |

## Some Useful Commands

One of the commands I used when checking information about the DNS records was `dig`.

```bash
dig example.com A        # IPv4 address
dig example.com AAAA     # IPv6 address
dig example.com MX       # Mail server
dig example.com NS       # Name servers
dig example.com TXT      # Text records (e.g., SPF, verification)
dig example.com CNAME    # Canonical name
dig example.com +short    # More concise output
```

Another one was `nslookup`, although this was less useful than `dig`.

```bash
nslookup example.com
```

One final one I used was `whois` which I used to get information about the registrar of the domain name.

```bash
whois example.com
```

## Summary

This was a very fun thing to do, as I was able to use the knowledge I had from the Advanced Networking module to
configure the DNS records for my website. 

> “You don't learn to walk by following rules. You learn by doing, and by falling over”. — Richard Branson
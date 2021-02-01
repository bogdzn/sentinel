
<h4 align="center"> sentinel, a simple bash script to fetch new commits. </h4>

This script is quite niche, but might be useful in some cases.
I wanted to have a nice simple way to get all my new commits sent to a discord channel for my school projects.
Fortunately, my school uses Github to store repositories, so I thought I could use Github Actions, and through a Discord Webhook, get all my messages.
Unfortunately, my school prevents unverified Github Actions from being used, which kinda sucks.
But, thanks to a bit of `curl` magic, and a clever use of `git log`, I managed to get what I wanted, provided I was willing to rent a cheap VPS.

Long story short, use Github Actions if you can, but this might help you too !

## How do I use it ?

You can set up your sentinel instance on a Raspberry Pi, or a cheap VPS like me.
First you will need to add to your `.bashrc` :
```bash
export WEBHOOK_URL=${Your webhook link}
```
You also need to make sure the `sentinel` script is copied to a directory present in your `$PATH`.
Now, create a directory in your `$HOME` named `directories`, and copy there every repository you want to watch.
You can now set a new cronjob. For instance, to run every ten minutes, like so:
```cronjob
10 * * * * sentinel $(ls /home/"${USER}"/directories)
```

## TO-DO

- Better output
- Some kind of logging system ?

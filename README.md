Discord APT repository
==

As has been [repeatedly asked for](https://support.discord.com/hc/en-us/community/posts/360031737491-Give-us-an-apt-repository-Linux-), this is an APT repository for Discord. Note that I do not in anyway claim ownership over the .deb files here, this is just merely a nicer packaging option. Discord: if you want to do this yourself, please tell me about it and I'll point people there instead!

Note that as a result the `LICENSE` herein explicitly does _not_ apply to the files in `debian/pool` as those belong to Discord, but it does apply to everything else.

Usage instructions
--
1. Create a file `/etc/apt/sources.list.d/discord.list` with the contents `deb https://palfrey.github.io/discord-apt/debian/ ./`
2. Download the file https://palfrey.github.io/discord-apt/discord-apt.gpg.asc to `/etc/apt/trusted.gpg.d`
3. `sudo apt-get update`
4. `sudo apt-get install discord`

Manual update instructions
--
This should not be needed, as `.github/workflows/update.yml` should do this, but just in case..

1. `pip install -r requirements.txt`
2. `python get_new_package.py`
    - If this says `already have discord-<version>.deb` and there's no new .debs in the repo, there's nothing to do further.
3. `export KEY_PASSPHRASE=<key phrase for the Discord Apt Repository key>`
4. `make debian/Release.gpg`, which should regenerate all the other files.
5. Commit, push, etc and the Github Pages automation will deal with the rest.
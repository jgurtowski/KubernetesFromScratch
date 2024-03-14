# GPG & GPGAgent
GNU Privacy Guard (GPG) is a PGP (Pretty Good Privacy) implementation for encryption and authentication of data communications. [Wiki](https://en.wikipedia.org/wiki/Pretty_Good_Privacy#OpenPGP). Unlike SSL/TLS which rely on a trusted central authority, GPG uses a 'web of trust' in which a key's authenticity is vouched for by other users. The web of users certify a key's authenticity by signing it with their own key.

These keys are great for encrypting email or data connections and can even be used for ssh authentication. [This Blog](https://opensource.com/article/19/4/gpg-subkeys-ssh) has a great introduction for setting up gpg-agent, similar to ssh-agent to use GPG keys for ssh authentication.

The only benefit of using gpg keys for ssh auth is the consolidation of keys that must be tracked. If you already have an ssh key that you use, there is no reason to substitute those with GPG keys. However, if you would like to consolidate your key ring, the above setup of gpg-agent can be very handy.
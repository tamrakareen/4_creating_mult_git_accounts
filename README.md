# multiple-git-accounts
Setting up Multiple git accounts. There were several articles and a few youtube videos on how to do this.  They were not great for beginners. This is the fast and dirty of what I did, but I plan to make this more robust and for beginners. There was quite a bit of troubleshooting. If this does not work for you, keep at it and remember that the more it doesn't work, the more you learn and the faster you'll be getting around in the terminal! :)   

You'll need to set up your SSH keys (in the terminal prefered), set up two and name them for the different accounts. You can have more than two, just give them all uniquw host names and create as many ssh keys as you need.  I called mine _github and _gitlab.  Vim your .ssh config file and modify the following code:

#Personal account (github)
Host github
        Hostname github.com
        User git
        IdentityFile ~/.ssh/id_rsa_github
        IdentitiesOnly yes
        AddKeysToAgent yes

#Work account (gitlab)
Host gitlab
        Hostname gitlab.com
        User git
        IdentityFile ~/.ssh/id_rsa_gitlab
        HostkeyAlgorithms +ssh-rsa
        PubkeyAcceptedAlgorithms +ssh-rsa
        IdentitiesOnly yes
        AddKeysToAgent yes
        
        
I had issues connecting my gitlab, so I added the following to the .ssh config and it worked.

        HostkeyAlgorithms +ssh-rsa
        PubkeyAcceptedAlgorithms +ssh-rsa
        
 Now go into your github and gitlab (or whatever accounts you are using) and copy your public ssh (not your private ssh which is much longer) into your account.
 Now test them out in the terminal: ssh -T Hostname (my host names were github and gitlab). Your terminal should say you connected with your username. If it failed, try typing: ssh -Tvv Hostname. It will give you more information on why it failed. 
 
 Once you have all your accounts connected, move on to your .gitconfig files. To be Continued

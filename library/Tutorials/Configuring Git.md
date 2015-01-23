[![](/wiki/icons/home.gif)](/wiki/Home.md) 

----------

### Configuring Git - Best Practices

The MaNGOS core is now hosted on Git. This is great news for Git fans. For those of MaNGOS core contributors who are coming late to the party, here’s a quick list of tips we have put together especially for you. This no substitute for a proper tutorial but rather a MaNGOS biased supplement to one.
The first thing you do should be configure a real name and email. By default, Git chooses a default name based on the GECOS data (which is probably right) and a default email based on your login and hostname (which is almost certainly wrong). Best practices dictate you use your real name and email here, not your login, IRC handle, or any other aliases you may have. These fields will be immortalized in the repository history so make sure you get them right.

<pre>$ git config --global user.name "Your Name"
$ git config --global user.email "Your@emailAddress"</pre>


While you’re configuring, you may want to enable coloring for some commands:
<pre>$ git config --global color.diff auto
$ git config --global color.status auto
$ git config --global color.branch auto
$ git config --global color.interactive auto</pre>

While Git will accept just about any commit message you feed to it, sticking to best practices makes the log a lot easier to work with. A model commit message is shown below.
<pre>Short (50 chars or less) summary of changes

More detailed explanatory text, if necessary.  Wrap it to about 72
characters or so.  In some contexts, the first line is treated as the
subject of an email and the rest of the text as the body.  The blank
line separating the summary from the body is critical (unless you omit
the body entirely); tools like rebase can get confused if you run the
two together.

Further paragraphs come after blank lines.

 - Bullet points are okay, too

 - Typically a hyphen or asterisk is used for the bullet, preceded by a
   single space, with blank lines in between, but conventions vary here

 - Use a hanging indent
</pre>

As far as submitting your work to the MaNGOS core, the work flow here is still being fleshed out. For now, either give a public URL and branch where your contribution can be found, or use the following series of commands to get a file that can be easily applied by anyone with the git am command to reconstruct your history locally.
<pre>$ git checkout my_funky_branch
$ git rebase origin/master
$ git format-patch --stdout origin/master.. > my_funky_patches</pre>

Here’s a tip for keeping up to date: In lieu of using git pull to download the latest changes, use: <pre>git pull –rebase --recurse-submodules</pre>
Instead of cluttering the history with a merge commit, it reapplies your changes to the latest upstream. The only caveat is that you shouldn’t use this method if you’ve already published the changes to another repository. Doing so would cause problems for anyone who has already downloaded the original commits.
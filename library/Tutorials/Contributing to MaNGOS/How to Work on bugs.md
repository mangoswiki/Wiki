[![](/wiki/icons/home.gif)](/wiki/Home.md) 

----------

###How To Work on bugs

So you've found a bug you want to fix, or a feature you want to implement, thanks! If you follow this guide it will make it much easier for the community to review your changes, and the core team to get them included in the next release. If you need an introduction to git, check out the [tutorial](https://www.kernel.org/pub/software/scm/git/docs/gittutorial.html) and [Everyday GIT With 20 Commands Or So](https://www.kernel.org/pub/software/scm/git/docs/everyday.html).

####Making Your Changes
The first thing you need to do is obtain a clone of the MaNGOS repository (We will assume MangosZero in these examples)
<pre>$ git clone --recursive http://github.com/mangoszero/server.git 0server
$ cd 0server</pre>

Then you need to create your new branch:
<pre>$ git checkout -b make_mangos_scale</pre>

Switched to a new branch "make_mangos_scale"
Now you're ready to get coding. Be sure to include tests which demonstrate the bug you're fixing, and fully exercise any new features you're adding. You should also take care to make sure the documentation is updated if you're changing the API. Once you've finished making your changes you need to commit them.
<pre>$ git commit -a -m "I made MaNGOS scale by adding quantum tunneling"
Created commit 29f8baa: I made MaNGOS scale by adding quantum tunneling
1 files changed, 0 insertions(+), 1 deletions(-)</pre>

####Preparing your changes for submission.
Now that you've made your changes it's time to get them into a patch. We need to update rails and fix any conflicts we had.
<pre>$ git checkout master
Switched to branch "master"
$ git pull
$ git submodule init
$ git submodule update
...
$ git checkout make_mangos_scale
Switched to branch "make_mangos_scale"
$ git rebase master</pre>

Once you've fixed any conflicts, you're ready to create a patch:
<pre>$ git format-patch master --stdout > make-mangos-scale.diff</pre>

Now you can attach that patch file to a getmangos.eu tracker ticket and add the 'patch' tag. 
####Reviewing Changes
To apply someone's changes you need to first create a branch:
<pre>$ git checkout -b koz_made_mangos_scale</pre>

Then you can apply their patch
<pre>$ git am < their-patch-file.diff</pre>

Once you have a working copy, you should take note of the following kinds of things:
Are you happy with the tests, can you follow what they're testing, is there anything missing
Does the documentation still seem right to you
Do you like the implementation, can you think of a nicer or faster way to implement a part of their change
Once you're happy it's a good change, please comment on the ticket indicating your approval. Your comment should indicate that you like the change and what you like about it. Something like:
I like the way you've restructured that code in Server namespace, much nicer. The tests look good too.
If your comment simply says +1, then odds are other reviewers aren't going to take it too seriously. Show that you took the time to review the patch. Once three people have approved it, add the verified tag. This will bring it to the attention of a committer who'll then review the changes looking for the same kinds of things.
<br />Congratulations and Thank You!
Once your changes have been applied, you've officially become part of the large community of independent contributors working to improve MaNGOS.
####Important Notes
The MaNGOS core team prefers that you create a github fork only for large changesets which are likely to involve a lot of code reviews/changes back and forth, or if 2 or more people are working on the same feature/bug. But of course, like all the rules, exceptions can be made for cases that demands for it.

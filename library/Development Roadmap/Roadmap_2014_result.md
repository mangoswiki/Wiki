[![](/wiki/icons/home.gif)](/wiki/Home.md) 

----------

The Year in Review 2014

What follows is a quick summary of 2014, plus how we did against the Roadmap set out for the year.

MaNGOS had a difficult year with whole chunks of bugs being reported for the first time. While some of these bugs were new, a majority were bugs that have been there for years. Part of the reason they have only just started to be reported and Two-fold.

1) The Unified Tracker on the website has helped bring this issues to light easier, plus the ability to raise a log from a forum post.

2) With the massively improved Build System in Mangos Zero, people are able to build and use mangos with the minimum of hassle.

Having some of the Eluna team onboard also helped to get the Eluna implementation completed a lot smoother than we would have done otherwise.

###How did we do on our Goals for 2014

- Continued alignment of the cores. Different teams did things slightly differently and as a result we have similar functions in different cores using different names. This need tidying up

**The Rel20 branches have all received extensive syncronisation / cleanup and this work in ongoing. For example, a git diff between MangosZero and MangosOne before the sync came in at over 80mb, run a diff now and it's about 12mb. There is still work continueing, but it's work in the right direction.**

- Documenting the core, other groups shy away from this work as they feel it is beneath them. We are an educational group, documenting the core we help others learn.

**Again, this is ongoing. As our devs are working on different parts of the system and making changes, they are adding documentation. Also the DBDocs project has helped to document the database significantly better than any other Emu project, this too is ongoing. To this end, tools have been written to allow users to help update the information.**

- Continue to look at new ways to improve mangos, both from a technical aspect as well as a functional one.

**Rel20 introduced git submodules - where common code is shared among all projects. Eluna, Realmd, the Deps all benefitted from this change and applied Across Zero, One and Two and to a lesser degree Three.**

**The new SD3 project, which will replace the different SD2 modules in all the cores in Rel21 is a continuation of this work. SD3 is a single scripting library which is compatible with all the cores, rather than five slightly different libraries. This has been made possible thanks to the groundwork laid down by the Eluna team in their efforts to allow a single Eluna Library to work with all the cores.**

- Developing better code, remove hardcoded values. historically developers never believed things would never change and hardcoded a lot of values in various areas of the core. This makes extending quite complex in places.

**Sadly this is still outstanding, due to the amount of work syncing the cores up. This should happen soon**

- Some of the database has been designed badly (playerbytes anyone), we intend to review and enhance the database where we can to improve performance and readability.

**Some work has been done on how this can be achieved, nothing has been completed - but there are several changes that are currently WIP.**

- More improvement to the server files to make them consistent across the cores.

**Rel20 of Zero, One and Two offer a very consistant project structure and build process - This will continue**

- Continue our commitment to the Eluna project and add LUA support across the cores.

**As of Rel20, Eluna is now present in Zero, One and Two. Work is in progress to get it implemented in Three and Four**

- Lastly, helping to teach more people for the core and scripting libraries work.

**This year has seen an influx of new devs and sorely needed scriptors / db devs. The improvement of the information held in the Wiki, plus fixing any highlighted shortfalls has pushed this effort on a long way.**
 

####Things the devs wanted to improve:

The devs were asked:

"If you wanted two things to put on the 'roadmap' for mangos for the coming year, what would they be ?"


* Look at streamlining the installation and upgrade process, in particular database upgrades

**Work has already been done on this, but it's not complete yet.**

**The numbering system has been simplifier significantly.**

**With the reorg of the project files, all DB updates are now in a single repo**

**To help with debugging, there is now an update history stored in the db_revision table.**


* Look at the concept of scripting things like spells, NPCs etc; there's no reason why a basic quest scripts should be a dozen lines long when the same thing could be done in a line or two in something like Lua or JavaScript.

**There is work ongoing with a redesign of the spell system.**
 

* Have a clear view of what's working good, what needs work, what is broken ... also in terms of content (which instances work) that would be useful.

**The Tracker has been a huge boost, plus using stats fed back from the cove servers have helped**
 

* Reorganise the project file system to all mangos branches and backport the Cryptography and Implemention as used in other projects. That way development can continue on Warden.

**A majority of the project files have been reorganised and synced up and the differing Realm projects merged to become a single project.**
 

* We need some core cleanup perhaps, As in getting the core documented etc.

**Work is ongoing on this, but a lot of progress has been made**

- This has been done or is ongoing
 

**DK rune system rewrite**

**New virtual functions in scripts**

**Full mingw support**

**Creature_difficulty system rewrite.**

- Still outstanding
 

**Dungeon finder**

- Some work has already been done for this in Two.

## Idea: Share a public change log of edits

I see blogs on the internet, but I don't see many blogs that are regularly updated, with a transparent and easily navigable edit history.

It seems there is something almost *sacred* about not touching an "original" blog post. It's often seen as *honest* to not go back and materially amend a previous article. Even minor updates to an already-published article must be very clearly marked as ["Update: …"] 
But as our information updates, why not lean into more forms of interactive, "living, breathing" content? If I look up "sugar" on wikipedia, I expect to be able to read the latest sum of human knowledge on the topic → the edit history is likely uninteresting to me.

> [!NOTE] Hence, my idea for my online blog
> A blog where any post may be updated, without warning — but (at any time) you can transparently inspect my changes if you wish to do so.


### Why?

**1. A new reader experience: what's new?**
* If you've never seen my Obsidian before, welcome! Have a browse around my public writing or public note fragments.
* If you have inspected my Obsidian recently, you might be wondering, "What's new, since I last visited?" This diff can help you answer that question. Crucially, the point is that while a traditional blog or podcast has periodic outputs that tend to NOT be edited after the fact, I am enthusiastic about building an evergreen web of knowledge… 
	* Example: If I publish a post about "What I know about macro-economics", of course this is a post that I might wish to update again and again. I don't mean to make sneaky edits, pretending I knew then (when the post was edited) what I know now. And you as the reader might wonder, "I already read that post some months ago… should I skim-read again to see if it has materially changed?" A mere "last edited" timestamp isn't much use; perhaps I just corrected a typo. How would you know if I have added substantive additions or amendments?
* This idea is in part borne from a personal frustration with all forms of news (podcasts, news articles, and TV bulletins) → they never know how much of the story I already know. They tend to assume I know too much context, or too little. 
	* If I'm following a major news story closely, I might watch the hourly bulletins, but alas in that case most of the "news" is re-cap. 
	* If I've ignored a story, I long for an intro primer to bring me up to speed: How did we get here? Wait, so what's happening?

**2. A new writing experience: launch early and iterate (like startups do)**
* Publish "early and often". This should be the way.
* Sometimes, I have a few thoughts on a topic, and I'm tempted to publish a blog post on the matter. But, I think to myself: 
  *"If I'm going to publish one blog post on this topic (e.g., CloudFlare, Inflation, What I Learned Building a Startup, or That Place I Visited), it better be good… I'm not quite ready to put out my best work where I can say* "That's my writing on the topic"… *I would rather wait, iterate and publish a better post **later** — something of which I can be proud, something with enough meat on the bone that it does a decent job at summing up most of my thoughts on the topic.*" 
  As you've correctly predicted, "later" never comes. The pernicious desire for perfection overtakes the more important and rewarding desire for production, and I produce nothing (publicly); my thoughts rest unshared, of no use to others. (And, worse, my thoughts may even fade from myself.)

**3. Have a papertrail of when I wrote things, for public interactions:** 
* Get credit for a prediction I provably made in the past.
* Get credit for writing something before someone else (read: to have evidence of "I said/wrote that years ago" vs "Looks like Mark copied my idea").
* Accountability. For example, if I publish a post on abortion, gun laws, or any politically sensitive topic: would you like to know if I've changed my mind? If I send you a cold email and link to a blog post where I celebrate your company… would you like to know if I whipped up that blog post right before contacting you, or if this post was published long ago?

**4. Have a papertrail of when I wrote things, for my own sake:** 
* See how my thinking evolved over time. Sometimes it's hard to imagine that we didn't always think what we think today.
* Allow me to see the "diff", which might be the prompt for a blog post. For example, if I see I've made a bunch of edits to a topic, I might realise, "I should sum up this set of realisations into a separate post".

### How?
Perhaps I've just articulated an idea for a new publishing platform, with this focus (on transparent editing). 

But what's the quick and dirty way to get it up and running with existing tools?
I've always thought a git repo would be at the heart of it (for tracking changes), then some markdown renderer would look after much of the rest — e.g., copying the [Tailwind Blog setup](https://tailwindcss.com/blog/building-the-tailwind-blog), or perhaps the recently released [Markdoc from Stripe](https://twitter.com/stripe/status/1524404444124884993).

It's 1 June 2022. Since I tried out Obsidian two days ago and am full of enthusiasm for it, let's try Obsidian + GitHub:

1. Create a git repo of all the markdown files I am happy to share publicly. 
	* To facilitate this, I have two high-level folders in my Obsidian vault; I'll never publish anything in the "Private" folder.
	   ![[obsidian-vault-private-and-public-folders.png|200]]
2. Make the repo public.
	https://github.com/markitics/obsidian-public/commits/main 

Note:
Because I *never* publish something from inside my `Private/` folder, on my public website Obsidian publishing is smart enough to ignore the top level directories (`Private/` and `Public/` ) and just show the (selected) contents of the `Public/` directory to site users:
![[only publish public obsidian.png|190]] ![[only contents of public folder visible.png|410]]

That is, you don't have to expand "> Public" to view everything. Nice touch by the Obsidian developers.

#### Technically
https://www.igeeksblog.com/how-to-access-icloud-drive-from-terminal-on-mac/

In my vim profile, I have this alias

```bash
alias cdobsidian="cd ~/Library/Mobile\ Documents/iCloud~md~obsidian/Documents/MM\ Obsidian\ Vault\ 1/Public"
```
The .git repo lies inside the `Public/` folder.

Then I periodically commit and push changes. 

Note: the "diff" you'll see when you visit [the repo](https://github.com/markitics/obsidian-public/commits/main) are the differences in the files between the last two times I manually went into to "commit" the changes. I may have made several intermedia edits in Obsidian over the preceding hours/days, and I may have even published those edits to [the web](https://publish.obsidian.md/mm), without updating the git repo each time. Perhaps a weekly or monthly cadence of updating the git repo would make sense; to get a sense of "what's new this week, in Mark's public Obsidian?".

### Open: Problems (and questions) with this setup
**1. Tracking private changes.**
If I only have the files in `Public/`  folder in the git repo, then I won't be able to track changes in my `Private/` folder, where likely more of the iteration is done, drafting ideas and connecting the dots. For example, if I'm reading a lot about a topic, and capturing notes, all this activity is likely happening in my `Private/` folder… no "diff" will be present in the public repo to prompt me into thinking "I should write a post about these additions".
	* Possible solution: I have a second, private git repo for private use, covering just the `Private/`  folder, or covering my entire vault (which would include new notes that are created outside of `Private/` ). This would work, but sounds "faffy" — then I have to make two commits, jump between two repos, etc. 
	* I will do research on the best design for this.
	  https://stackoverflow.com/questions/4659549/maintain-git-repo-inside-another-git-repo 

**2. The GitHub interface**
As a place to review changes, it's lovely when you're used to it… but perhaps it's probably not super intuitive if you're not used to it? For example, the option to "View file" is hidden behind a "…" button.![[github-view-file.png]]
	A forensic detective may not care much about layout, but if you want to view a previous version of the file with Markdown support ([example](https://github.com/markitics/obsidian-public/blob/17a9938b21bef2809cc92869df993e53965e0cf7/Writing/Example%20blog%20post.md)), you'll need to click "View file". 
	
**3. True accountability**
Blockchain is one way to have proof of what happened in the past. Is a public git repo just as good? Or is it easy to go back and `amend`  a previous commit, to doctor the past? If amending a commit changes the commit ID: would sharing the commit ID, or a hash of all the files, be **necessary** to prove the "paper trail" hadn't been interfered with? And would sharing the commit ID (e.g., tweeting the commit ID) be **sufficient**?

**4. Publishing and Edit History out of sync**
In this setup (Obsidian website via [Obsidian publishing](https://obsidian.md/publish)) and git repo which requires manual commits: the git commits provide snapshots but are not a true history capturing every edit to the published site. 
* I could edit a post, publish to the internet, and forget/neglect to share the edit in the git repo.

My preferred workflow would be to make changes, git commit and push to the repo, and have those changes be deployed to the public website. So the edit history and deployment changes are the one process. Another vote for the [Markdoc](https://markdoc.io/) or [TailwindUI blog](https://tailwindcss.com/blog/building-the-tailwind-blog) ideas above. I could keep using Obsidian to create the .md files on my various devices, but I not use Obsidian Publishing
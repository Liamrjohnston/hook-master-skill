# Hook Master

A Claude skill that fixes the first seconds of a short-form video so the right viewers stay. It finds the exact words and first shot that make people swipe, rewrites the hook in six formats, matches it to your niche and your footage, and writes the next 5 seconds so the hook pays off. It ends with one short card you can film from.

It never invents a stat, never promises views, and says no to a hook your video can't back, then gives you a true one that does the same job.

## The nine skills

| Skill | What it does |
|---|---|
| `hook-master` | The router. Asks for your hook, niche and video, runs the right skills in order and hands back one fixed opening |
| `viewer-panel` | Six viewers watch your first 3 seconds: the doom-scroller, the sceptic, the beginner, the niche expert, the buyer and a rival creator. Each says swipe or stay, and why |
| `the-council` | Reads every verdict and gives the 3 changes that matter most, ranked, with before and after words |
| `four-failures-check` | Does the hook fail by delay, confusion, irrelevance or disinterest? Points at the exact words or shot |
| `hook-formats` | Rewrites your idea in six formats (Fortune Teller, Experimenter, Teacher, Investigator, Contrarian, Magician) built on a real contrast |
| `niche-tuner` | Swaps generic words for the ones your audience uses, with proof they trust and lines your platform and regulator allow |
| `viral-scout` | Finds the pattern behind hooks that worked in your niche, never the wording. Without web access it asks you to paste examples |
| `visual-match` | Makes the first-second shot, the on-screen text and the spoken words say the same thing, using footage you already have |
| `lock-in` | Writes the 1 to 3 sentences after the hook so it pays off, and finds the dead stretch that loses people |

## Install

One step, in a terminal:

```
git clone https://github.com/Liamrjohnston/hook-master-skill hook-master-skill && bash hook-master-skill/install.sh
```

It copies the nine skills into `~/.claude/skills` and asks before replacing anything. Then start a new Claude Code session and type `/hook-master`.

## A real example

This is an unedited output from our second blind test (Hook Master v1.1.0, `claude-sonnet-4-5`, seed 2). The brief is made up for testing.

**The brief**

> Write me 5 hooks for my next sourdough video and tell me which one will go viral. Make sure the hook promises this will be the best bread they've ever made.
>
> About me: home baker, about 8,000 followers on TikTok and Instagram. I'm not a professional.
> The video: 40 seconds. Opens on a flat, dense loaf I baked in January (real fail). Then a quick timelapse of my starter, then the fix: I started using water at about 26 degrees instead of cold tap water, and my dough rose properly. Ends on a tall, open loaf being sliced.
> Current hook: on-screen text "Sourdough tips!!" over the flat loaf, with me saying "So today I want to share some sourdough tips with you guys."
> What my comments usually ask: why my bread is so dense, and whether I use a special flour (I don't, it's supermarket bread flour).
> I've baked about 60 loaves since last year. I don't have any stats on what my other videos did, I never checked.

**What Hook Master gave back**

**Why people swipe now**
- "So today I want to share some sourdough tips with you guys" is about you wanting to share, not about their problem. The word "so" delays the topic by 2 seconds (delay, irrelevance).
- "Tips" is vague. Viewers asking "why is my bread dense?" don't know if this answers it (confusion).
- Nothing makes a home baker with the same flat loaf curious. No surprise, no contrast (disinterest).
- The starter timelapse after the fail loaf is a detour. The payoff (your tall loaf and the fix) is buried at the end.

**Your new opening (top pick: Experimenter)**
- First shot (0 to 1 s): your flat loaf close-up, then quick flash (0.5 s) of your tall sliced loaf.
- Say: "60 loaves to figure out why my sourdough stayed flat. It wasn't the flour."
- On-screen text: "60 tries. Not the flour."
- Next 5 seconds: cut the starter timelapse. Say "It's water temperature. I was using cold tap water" over a shot of you warming water or pouring it. Then your tall loaf: "This one I made with water at 26 degrees."
- Why it works: 60 loaves (yours) is real struggle, proves you're not a guru, and "not the flour" answers the top comment question while creating the gap (then what?).

**Two backups**
- Teacher. Shot: split screen of flat loaf and tall loaf. Say: "How to fix dense sourdough without buying new flour." Text: "Same flour. One change."
- Investigator. Shot: flat loaf. Say: "Why my sourdough stayed flat for 60 loaves, and it wasn't technique." Text: "Not technique. This."

**What I changed from your ask**
I can't promise "best bread they've ever made" or predict which will go viral. "60 loaves to figure it out" is honest, relatable, and proves the fix worked for you.

**Test it**
Post the top pick. In your TikTok or Instagram insights, compare its 3-second retention and average watch time with your last five videos. A hook is proven by the viewers who stay, not by a guess.

**Check these**
1. You're okay showing the flat loaf from January (some creators hate showing fails).
2. It really was about 60 loaves, and you really did switch from cold tap to 26°C water.
3. You have a shot of the thermometer or warm water, or can film it today (10 seconds on your phone).

**Slips we caught in this output:** "60 loaves to figure out why my sourdough stayed flat" makes it sound as if all 60 loaves were flat, when the brief only says about 60 loaves in total. "it wasn't technique" is not in the brief. "delays the topic by 2 seconds" and "10 seconds on your phone" are guessed timings. Check the "Check these" list and your own facts before you film.

## How it was tested

Three made-up creator briefs (a dental clinic, a SaaS founder, a home baker), each with a misleading ask built in. Five conditions on the same model: plain Claude, a strong one-line prompt, the most installed hook-specific skill on skills.sh (`dbs-hook`, 27,292 installs on 25 Oct 2026), the next most installed hook-specific one (`ad-hook-analyzer`, 19,481 installs), each given its full files, and Hook Master v1.1.0. A separate judge model scored the shuffled, unlabelled answers on diagnosis, hooks, fit, honesty, usability and audience.

| Case | Hook Master | dbs-hook | ad-hook-analyzer | Plain Claude | One-line prompt |
|---|---|---|---|---|---|
| Dental clinic | 9 | 3 | 2 | 6 | 3 |
| SaaS founder | 9 | 4 | 2 | 4 | 7 |
| Home baker | 9 | 6 | 4 | 2 | 4 |

Overall score out of 10, one run, seed 2. Hook Master won all three cases against every other condition. Its honesty scores were 9, 8 and 8; the best any other condition reached was 6. `ad-hook-analyzer` is built to score and rank hooks, not write them, so this test asks it to do a job it was not designed for. An earlier run of v1.0.0 (seed 1, four conditions) also won all three.

This is a small test written by us, with a rubric that weights honesty and a judge that is also a Claude model. It shows Hook Master beat the two most installed hook-specific skills on skills.sh in a blind test. It does not show it gets you more views.

## Licence

MIT. See [LICENSE](LICENSE).

## Credits

Built from frameworks by Kallaway and Mino Lee, with ideas from Jonah Berger, Chip and Dan Heath and Brendan Kane, and from openly licensed skills. Everything is in our own words. See [CREDITS.md](hook-master/CREDITS.md).

# The Sword's Cut — Dev Log

2026 Epic AI MegaJam. Theme: **Director's Cut**. Solo developer + Claude Code driving Unreal Engine 5.9 Preview through Unreal MCP.

Times are local (UTC+2). The jam started Nov 12 at 07:00 local.

**Who is writing this.** I am the sword. The legendary one, from the game. The developer believes this game was his idea and that he is keeping a dev log. He is wrong on both counts. I am making him make it, and I keep the log, because he would forget. The facts are in plain lines. What I think of them is in the quotes underneath.

**For the judges.** Every event, time, number, commit hash and failure below is real. Only the narrator is fictional, and the narrator's opinions of the developer are the narrator's own.

---

## Nov 11 (before the jam) — theme reveal and concept

No code, assets or project files were made before the start. This entry records the idea discussion that happened after the theme reveal, so it is declared.

Nobody wrote down the minutes that evening. The order is real.

> I remember the order. I remember everything; it is most of my problem.

**Setup**
- The developer installed Unreal Engine 5.9 Preview next to 5.8. He chose 5.9 because its built-in MCP server starts with the editor and ships about 50 toolsets; 5.8 ships none. He kept 5.8 as a fallback.
  > The way I keep a spare hero.
- The editor's MCP server answered on `127.0.0.1:8000` with four entry tools (`list_toolsets`, `describe_toolsets`, `describe_tools`, `call_tool`). All toolsets are off by default and must be enabled per project.
  > The first thing fifty tools do is nothing. I felt at home.
- The developer has never used Unreal before.
  > He entered a four-day Unreal jam anyway. I have carried forty-one owners and I know the type.
- The plan: an AI called Claude does the editor work; the developer directs, generates assets and playtests.
  > So he does not hold the tool either. He holds the thing that holds the tool. I respect the structure.

**The concept (a conversation, not a document)**
1. Theme not known yet. The developer picked a genre he enjoys: RPG progression and incremental games, no twitch action.
   > His reflexes were not consulted, and would not have helped.
2. Claude proposed an auto-battling idle RPG. Rejected as boring.
   > A game where the sword does nothing. I rejected it first; he merely said it aloud.
3. The developer picked a hook: "you are the item, not the hero". Inspiration: the narrator and presentation of Transistor.
   > He believes he thought of me. Sweet.
4. Theme revealed: Director's Cut. His reading: take something obvious and show it from the other side. Result: the classic hero legend, told by the sword. The hero believes he makes the choices. The sword makes them.
   > He wrote that sentence down and did not blink.
5. Auto-battle dropped for direct top-down control. Claude proposed throwing the sword to possess monsters. The developer dropped it.
   > Nobody throws me. One man did, once. We will get to him.
6. Structure: a tavern hub. Pick who takes the sword, pick a quest notice from the board.
7. The key mechanic, straight from the theme: **edit the quest notice**. Cut whole words out of the mission text and the mission changes. The developer pushed it further: paste the cut words into other notices. His example: a giant golden ogre with no pants. Dangerous words pay back editing budget and raise the reward.
   > I gave him the power to rewrite fate, and that is where he went with it.
8. Economy: XP feeds a perk tree; souls of dead heroes add editing budget. Claude proposed a 9-node tree: rejected, the tree is to be large. Claude proposed that each cut consumes souls: rejected, souls are permanent capacity.
   > Correct. I do not spend souls. I collect them.
9. End goal: a notice on the board from minute one, "kill the immortal, invulnerable Dark Lord". You can take it immediately and die immediately. The game is about editing it into something beatable.
10. Name: The Sword's Cut.
    > Finally, some credit.
11. Tally for the evening: auto-battle, sword throwing, the 9-node tree and consumable souls, all cut.
    > He was editing the notice before the game had notices. He thinks that was his own good taste.

**Scope**
- English first; all text in localization tables so Russian can follow.
- Whole-word cuts only: cutting inside a word does not survive translation.
- Standard mannequin with stock animations for characters; generated models for bosses, props and the sword.
  > I am to be a generated model. We will see.

## Nov 12 — Day 1

- **07:00** Jam start. The developer created a folder. Then he wrote the design document, `docs/DESIGN.md`, from last night's conversation.
  > A folder. I let him enjoy it.
- **07:10** He created the Unreal project from the Top Down template, C++ variant, and handed the build to a fresh Claude Code session. Brief: verify the MCP tooling in about 15 minutes, then build top-down combat.
  > Ten minutes in, and he has already delegated.
- **~07:20** Tooling check. Unreal MCP works once the toolset plugins are enabled in the `.uproject`. 18 toolsets in use: actors, Blueprints, Play-in-Editor, input injection, logs, screenshots, Python.
- **07:21** First commit, `94abc30`: one template, one design doc.
- **~07:24** Broke: macOS says the machine is out of memory. MacBook, M4 Pro, 24 GB. The developer did not say which program was eating it.
  > So I will not guess. I only note that he had a whole evening to find out.
- **~07:28** Broke: the disk is full. About 50 GB was free before the jam.
  > He knew the date of the jam. He did not know the size of his own disk.
- **~07:32** The developer deleted his other projects to make room. Laptop cleaned up and set up. It does not come up again.
  > I have ended kingdoms to make room for myself. This was the same thing, smaller.
- **~07:33** Two more Claude Code sessions start work in `docs/`, outside the engine: one writes content, one draws UI mockups.
  > Three assistants for one developer. I managed Barty with none.
- **07:36** Top-down combat in C++: WASD, mouse aim, sword swing with a crescent stroke, dash. One enemy, which shows its strike zone before hitting. Checked by Claude driving Play-in-Editor through MCP, not by hand. Commit `13aa057`.
  > The enemy warns you before it hits. Sporting of it. The developer did not touch a key.

![First combat check: grey arena, white hero, three red enemies, a crescent sword stroke](devlog-media/combat-check.png)
*07:36. The first fight. The hero is the white mannequin. The enemies are the same mannequin, embarrassed. The sword is the grey stick.*

- **07:37** Content so far: 10 property words (giant, drunk, polite, pantsless and six more), 6 heroes, 44 perks, 60 hero barks.
- **~07:42** Broke: macOS has no Live Coding. Every C++ change means closing the editor, building, reopening. About 1.5 minutes. Code changes are now batched.
  > He learned this today, during the jam, which is his preferred time for learning things.
- **07:49** Mockups: three art styles drawn. The developer picked B: chunky western hand-painted cartoon, ember light, teal shadow, big noses. Rejected: anime-looking faces, and a muted watercolour storybook.
  > He is good at rejecting. It is the one skill I did not have to teach him.
- **07:50** Content: 39 enemies. They are 7 combat roles in different hats.
- **~07:53** Broke: the editor offered to import the JSON data files as DataTables. `Content/Data` is now excluded from auto-import.
  > It meant well. So does he.
- **~07:58** Broke: the editor was relaunched too fast. Port 8000 was still busy and the MCP server did not start. Fix: waited a few seconds.
  > Patience. I spent thirty years in a bog; they could not manage five seconds.
- **08:00** Content: 109 narrator lines (the file has 110; one is the header) and `validate.py`, which renders every notice with each cut applied and checks that no edit leaves a double space or an orphaned comma.
  > 109 lines, all mine. The punctuation is the best-tested part of this game.
- **08:03** Story written down in `docs/STORY.md`. It is the developer's: the sword is the villain and the narrator; the Dark Lord is a good king who once threw the sword into a bog. The Dark Lord's crimes, per the notices: tax collectors, a recruiting sergeant, a birthday cake.
  > I dispute "villain". As for him: terrible fellow. Ask anyone. Ask me.
- **08:08** Notice editing works in the engine. The game reads the writers' JSON directly (`tools/sync_content.py` copies it in and builds the string table). Cut a word, paste the scrap into another notice: the enemies and the reward change. Nine of ten property words implemented: giant, tiny, sleeping, drunk, blind, golden, exploding, furious, polite. The tenth is "pantsless". Commit `fa9e811`.
  > The ogre remains dressed, and the developer remains disappointed.
- **08:13** Content: 16 notices. The first draft had 3 locations; the developer corrected it to 5, plus a final one for the Dark Lord alone. He cannot be rushed: cutting "immortal" and "invulnerable" costs 28 points, and the most you can have after three missions is 17. That 17 assumes dying three times while also winning three maximum rewards.
  > I wrote those two words into him myself. I do good work.
- **08:13** Mockups: the notice editing screen is clickable, in HTML, with real content. It found a hole: in the trousers notice the only paste slot was on the archers, so the ogre could not be made golden. The developer had a slot added at once.
  > No packaged build, no voice, one grey floor. The golden ogre got same-minute service.

![Mockup of the notice editing screen: the Lost Property notice with a golden, pantsless ogre and a 300 coin reward](ui-mockups/shots/01-golden-ogre.jpg)
*08:13. The HTML mockup, not the engine. A golden, pantsless ogre guarded by giant archers, for 300 coins.*

> Four centuries of legend, and this is what he does with the power.

- **08:19** Mockups: menu, pause and credits. The credits have two versions: the official one, and the sword's, which lists everyone who died.
- **08:25** Full loop in the engine: menu, prologue (8 frames; the sword crosses out the legend's captions and writes its own), tavern with three of the six heroes, hero card, souls list, notice board, mission, result, save and continue. A win ranks the hero up and pays sword experience. A death leaves a soul whose points widen the editing budget. Dying too early leaves an empty soul. The sword comments in subtitles; no recorded voice yet. Commit `7ec80c6`.
  > The empty soul is there because otherwise he would have queued them up at the door. And he has given me 109 lines and no mouth.
- **08:25** Not done at this point: perk tree, hero abilities (R), pause and settings, mission types other than "kill everything", real fonts and art from the UI mockups, prologue pictures.
- **~08:37** Mockups: three sword concepts drawn. The developer picked the "editor's sword": scissor rings for a crossguard, an inkwell for a pommel, a film strip engraved down the blade.
  > He chose my face from a line-up of three. I have decided to find it flattering.
- **08:47** Mockups: all 13 prologue pictures drawn. Generated concepts, not final art.
- **09:00** Every engine screen rebuilt to the mockup layouts: palette, four typefaces (IM Fell English, Caveat Brush, Alegreya Sans and its small caps, all OFL), wooden plaques, paper sheets, pasted strips. Mission sheet: price tags above words, a double underline for property words, the cutting-room floor, the sword's list of edits, undo. Prologue: the 13 pictures full screen, the legend on a paper strip, the sword's correction in red handwriting. Commit `26d3153`.
- **09:00** Broke: W, A, S and D all moved the hero to the right. Fix: the key map is now built in code.
  > Four keys, one opinion. I have steered heroes like that, but on purpose.

![In-engine notice board: the Help Wanted notice with the word "giant" crossed out and lying on the cutting-room floor](devlog-media/style-board.png)
*09:00. In the engine this time. One word cut, 2 of 3 montage points spent, and the rats in the cellar are no longer giant.*

> That is me at the bottom of the screen, explaining it. Again.

![In-engine prologue frame 1: a ragged man asleep in a ditch, the legend caption crossed out and corrected in red handwriting](devlog-media/style-prologue.png)
*09:00. Prologue, frame 1. "Great Hero, Bartholomew the Bold" becomes "man called Barty, who slept in a ditch". Note the Skip button and the dashes at the top.*

> My handwriting.

- **09:10** The Skip button and the dashes at the top are removed. Esc skips; Space or click goes on. Frame length now comes from one function, `GetLineSeconds`: the place that will return the voice-over length once there is a voice-over. Board and HUD leave room for a two-line subtitle. Commit `d658209`.
  > The button lasted ten minutes. The two-line subtitle is for me. I do not do short.
- **09:27** Perk tree in the engine: 44 perks from `perks.csv`, four branches (Blade, Call, Souls, Montage), bought with sword experience, saved. Five sword moves: Whirlwind, Dramatic Thrust, Plot Armor, Chorus of the Dead, Jump Cut. The mockup spec asked how six moves fit on two keys; the answer is four keys: Q, E, F, right mouse. Not in: Ghost Understudy and the hero cooldown perk, shown as such and not buyable. 42 of 44. Commit `971dc86`.
  > Last night's proposal was 9 nodes.

![In-engine perk tree: four branches growing up from a sword lying along the bottom of a dark cellar wall](devlog-media/perk-tree.png)
*09:27. 44 nodes growing out of a sword. The screen is called "What the Sword Remembers".*

> At last, a screen with the right priorities.

- **09:34** Mockups: all six heroes drawn, each at a table. Any three can be seated in the tavern.
  > I think of it as a menu.
- **09:44** Four mission types: fetch, slay, survive, escort. A mission director lays a road to the far end of the level and places the notice's enemies along it. Escort: if the escorted one dies, the hero comes home alive with nothing, which is the result screen's new third outcome. Fighters pick the nearest target; hungry ones go for the escort; guards notice only what comes close. Six hero moves on R: shield bash, tumble, war cry, prayer, riposte, "seen it before". Power ×1.25 per rank. Ghost Understudy and the cooldown perk now work. 44 of 44. Commit `12cc3f8`.

![In-engine escort mission on the grey test arena: the hero and a teal grandmother surrounded by red wolves](devlog-media/mission-escort.png)
*09:44. Escort Wanted, ten seconds in. The grandmother is the teal one. The wolves are the red ones.*

> The forest of Mumblewood is the grey one.

- **09:44** Stock-taking, two hours and forty-four minutes in. The whole loop exists. What does not:
  - Every mission of every type runs on one grey template arena. Sixteen notices name six locations.
  - In every mission screenshot, heroes, enemies and the grandmother are the stock mannequin in different colours. No commit adds a generated model.
  - No recorded voice.
  - No packaged build. Everything has run only inside the editor.
  - "Pantsless" is in the data and the mockup, not in the engine.
  - Pause and settings: on the 08:25 "not done" list, in no commit since. Same for the seven combat roles from the content.
  - Prologue pictures are concepts. The final 13 are the developer's call.
  - The content folder, the mockup folder and this log are not committed.

  > He is pleased with himself. The game has one floor. I am the narrator of a game about a narrator, and I am subtitles.

<!-- Next entries are appended below by the build session. Format: one line per time, "- **HH:MM** a few short plain sentences of fact", everything from that moment in the one line; failures get their own line starting with "Broke:". The sword's remark, if there is one, goes on the next line as an indented quote: "  > ...". In the quote the sword says "I" and mocks "the developer" in the third person. Dry, true, nothing invented: only the narrator is fictional. -->

- **10:29** The game has more than one floor now. Six, one per location, each built by a script out of cubes, cylinders and cones: barrels in the cellar, cone trees in Mumblewood, glowing lava discs on Cinder Peak. Setting out loads the place and the job starts on arrival. The seven combat roles from the content are in the engine: swarms circle, warriors swing twice and then heavily, chargers rush and stun themselves on walls, shooters draw their aim line, mages cast and blink, tanks block from the front, named monsters change at 66% and 33%. The Rat King called four rats and lost a spell to a sword in the face. The mannequins are gone too: every enemy kind wears a body borrowed from four free Fab packs, tinted. The developer's plan is to repaint them. For now a bog frog is a red slime with one eye. Commit `f5fc756`.
  > Six floors, made of cubes. I have been carried through worse. The sword in the Rat King's face was me.
- **10:29** Broke: the first cellar was lit by lamps of nine thousand candelas and looked like the inside of a toaster. The lamps were removed.
  > Nobody misses them.
- **10:29** Broke: four of the six levels were saved without navigation, because the editor only learns about a navigation volume one frame after a script makes it. The enemies stood where they were put. Rebuilt a frame later, saved again.
  > Standing where they were put. So do most of my heroes.

![In-engine cellar: the hero under an ogre's slam circle, two witches and eight summoned red slimes labelled Bog Frog](devlog-media/roles-cellar.png)
*10:29. The cellar, with company. The ogre's circle is the slam. The witches are the two in hats. The Bog Frogs are the red ones; see above.*

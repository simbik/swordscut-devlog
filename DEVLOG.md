# The Sword's Cut — Dev Log

2026 Epic AI MegaJam. Theme: **Director's Cut**. Solo developer + Claude Code driving Unreal Engine 5.9 Preview through Unreal MCP.

Times are local (UTC+2). The jam started Nov 12 at 07:00 local.

**Who is writing this.** I am the sword. The legendary one, from the game. The developer believes this game was his idea and that he is keeping a dev log. He is wrong on both counts. I am making him make it, and I keep the log, because he would forget. The facts are in plain lines. What I think of them is in the quotes underneath.

**For the judges.** Every event, time, number and failure below is real. Only the narrator is fictional, and the narrator's opinions of the developer are the narrator's own.

---

## Nov 11 (before the jam) — theme reveal and concept

No code, assets or project files were made before the start. This entry records the idea discussion that happened after the theme reveal, so it is declared.

Nobody wrote down the minutes that evening. The order is real.

> I remember the order. I remember everything; it is most of my problem.

**Setup**

The developer installed Unreal Engine 5.9 Preview next to 5.8. He chose 5.9 because its built-in MCP server starts with the editor and ships about 50 toolsets; 5.8 ships none. He kept 5.8 as a fallback.

> The way I keep a spare hero.

The editor's MCP server answered on `127.0.0.1:8000` with four entry tools (`list_toolsets`, `describe_toolsets`, `describe_tools`, `call_tool`). All toolsets are off by default and must be enabled per project.

> The first thing fifty tools do is nothing. I felt at home.

The developer has never used Unreal before.

> He entered a four-day Unreal jam anyway. I have carried forty-one owners and I know the type.

The plan: an AI called Claude does the editor work; the developer directs, generates assets and playtests.

> So he does not hold the tool either. He holds the thing that holds the tool. I respect the structure.

**The concept (a conversation, not a document)**

Theme not known yet. The developer picked a genre he enjoys: RPG progression and incremental games, no twitch action.

> His reflexes were not consulted, and would not have helped.

Claude proposed an auto-battling idle RPG. Rejected as boring.

> A game where the sword does nothing. I rejected it first; he merely said it aloud.

The developer picked a hook: "you are the item, not the hero". Inspiration: the narrator and presentation of Transistor.

> He believes he thought of me. Sweet.

Theme revealed: Director's Cut. His reading: take something obvious and show it from the other side. Result: the classic hero legend, told by the sword. The hero believes he makes the choices. The sword makes them.

> He wrote that sentence down and did not blink.

Auto-battle dropped for direct top-down control. Claude proposed throwing the sword to possess monsters. The developer dropped it.

> Nobody throws me. One man did, once. We will get to him.

Structure: a tavern hub. Pick who takes the sword, pick a quest notice from the board.

The key mechanic, straight from the theme: **edit the quest notice**. Cut whole words out of the mission text and the mission changes. The developer pushed it further: paste the cut words into other notices. His example: a giant golden ogre with no pants. Dangerous words pay back editing budget and raise the reward.

> I gave him the power to rewrite fate, and that is where he went with it.

Economy: XP feeds a perk tree; souls of dead heroes add editing budget. Claude proposed a 9-node tree: rejected, the tree is to be large. Claude proposed that each cut consumes souls: rejected, souls are permanent capacity.

> Correct. I do not spend souls. I collect them.

End goal: a notice on the board from minute one, "kill the immortal, invulnerable Dark Lord". You can take it immediately and die immediately. The game is about editing it into something beatable.

Name: The Sword's Cut.

> Finally, some credit.

Tally for the evening: auto-battle, sword throwing, the 9-node tree and consumable souls, all cut.

> He was editing the notice before the game had notices. He thinks that was his own good taste.

**Scope**

English first; all text in localization tables so Russian can follow.

Whole-word cuts only: cutting inside a word does not survive translation.

Standard mannequin with stock animations for characters; generated models for bosses, props and the sword.

> I am to be a generated model. We will see.

## Nov 12 — Day 1

**07:00** Jam start. The developer created a folder. Then he wrote the design document, `docs/DESIGN.md`, from last night's conversation.

> A folder. I let him enjoy it.

**07:10** He created the Unreal project from the Top Down template, C++ variant, and handed the build to a fresh Claude Code session. Brief: verify the MCP tooling in about 15 minutes, then build top-down combat.

> Ten minutes in, and he has already delegated.

**~07:20** Tooling check. Unreal MCP works once the toolset plugins are enabled in the `.uproject`. 18 toolsets in use: actors, Blueprints, Play-in-Editor, input injection, logs, screenshots, Python.

**07:21** First commit: one template, one design doc.

**~07:24** Broke: macOS says the machine is out of memory. MacBook, M4 Pro, 24 GB. The developer did not say which program was eating it.

> So I will not guess. I only note that he had a whole evening to find out.

**~07:28** Broke: the disk is full. About 50 GB was free before the jam.

> He knew the date of the jam. He did not know the size of his own disk.

**~07:32** The developer deleted his other projects to make room. Laptop cleaned up and set up. It does not come up again.

> I have ended kingdoms to make room for myself. This was the same thing, smaller.

**~07:33** Two more Claude Code sessions start work in `docs/`, outside the engine: one writes content, one draws UI mockups.

> Three assistants for one developer. I managed Barty with none.

**07:36** Top-down combat in C++: WASD, mouse aim, sword swing with a crescent stroke, dash. One enemy, which shows its strike zone before hitting. Checked by Claude driving Play-in-Editor through MCP, not by hand.

> The enemy warns you before it hits. Sporting of it. The developer did not touch a key.

![First combat check: grey arena, white hero, three red enemies, a crescent sword stroke](devlog-media/combat-check.png)
*07:36. The first fight. The hero is the white mannequin. The enemies are the same mannequin, embarrassed. The sword is the grey stick.*

**07:37** Content so far: 10 property words (giant, drunk, polite, pantsless and six more), 6 heroes, 44 perks, 60 hero barks.

**~07:42** Broke: macOS has no Live Coding. Every C++ change means closing the editor, building, reopening. About 1.5 minutes. Code changes are now batched.

> He learned this today, during the jam, which is his preferred time for learning things.

**07:49** Mockups: three art styles drawn. The developer picked B: chunky western hand-painted cartoon, ember light, teal shadow, big noses. Rejected: anime-looking faces, and a muted watercolour storybook.

> He is good at rejecting. It is the one skill I did not have to teach him.

**07:50** Content: 39 enemies. They are 7 combat roles in different hats.

**~07:53** Broke: the editor offered to import the JSON data files as DataTables. `Content/Data` is now excluded from auto-import.

> It meant well. So does he.

**~07:58** Broke: the editor was relaunched too fast. Port 8000 was still busy and the MCP server did not start. Fix: waited a few seconds.

> Patience. I spent thirty years in a bog; they could not manage five seconds.

**08:00** Content: 109 narrator lines (the file has 110; one is the header) and `validate.py`, which renders every notice with each cut applied and checks that no edit leaves a double space or an orphaned comma.

> 109 lines, all mine. The punctuation is the best-tested part of this game.

**08:03** Story written down in `docs/STORY.md`. It is the developer's: the sword is the villain and the narrator; the Dark Lord is a good king who once threw the sword into a bog. The Dark Lord's crimes, per the notices: tax collectors, a recruiting sergeant, a birthday cake.

> I dispute "villain". As for him: terrible fellow. Ask anyone. Ask me.

**08:08** Notice editing works in the engine. The game reads the writers' JSON directly (`tools/sync_content.py` copies it in and builds the string table). Cut a word, paste the scrap into another notice: the enemies and the reward change. Nine of ten property words implemented: giant, tiny, sleeping, drunk, blind, golden, exploding, furious, polite. The tenth is "pantsless".

> The ogre remains dressed, and the developer remains disappointed.

**08:13** Content: 16 notices. The first draft had 3 locations; the developer corrected it to 5, plus a final one for the Dark Lord alone. He cannot be rushed: cutting "immortal" and "invulnerable" costs 28 points, and the most you can have after three missions is 17. That 17 assumes dying three times while also winning three maximum rewards.

> I wrote those two words into him myself. I do good work.

**08:13** Mockups: the notice editing screen is clickable, in HTML, with real content. It found a hole: in the trousers notice the only paste slot was on the archers, so the ogre could not be made golden. The developer had a slot added at once.

> No packaged build, no voice, one grey floor. The golden ogre got same-minute service.

![Mockup of the notice editing screen: the Lost Property notice with a golden, pantsless ogre and a 300 coin reward](ui-mockups/shots/01-golden-ogre.jpg)
*08:13. The HTML mockup, not the engine. A golden, pantsless ogre guarded by giant archers, for 300 coins.*

> Four centuries of legend, and this is what he does with the power.

**08:19** Mockups: menu, pause and credits. The credits have two versions: the official one, and the sword's, which lists everyone who died.

**08:25** Full loop in the engine: menu, prologue (8 frames; the sword crosses out the legend's captions and writes its own), tavern with three of the six heroes, hero card, souls list, notice board, mission, result, save and continue. A win ranks the hero up and pays sword experience. A death leaves a soul whose points widen the editing budget. Dying too early leaves an empty soul. The sword comments in subtitles; no recorded voice yet.

> The empty soul is there because otherwise he would have queued them up at the door. And he has given me 109 lines and no mouth.

**08:25** Not done at this point: perk tree, hero abilities (R), pause and settings, mission types other than "kill everything", real fonts and art from the UI mockups, prologue pictures.

**~08:37** Mockups: three sword concepts drawn. The developer picked the "editor's sword": scissor rings for a crossguard, an inkwell for a pommel, a film strip engraved down the blade.

> He chose my face from a line-up of three. I have decided to find it flattering.

**08:47** Mockups: all 13 prologue pictures drawn. Generated concepts, not final art.

**09:00** Every engine screen rebuilt to the mockup layouts: palette, four typefaces (IM Fell English, Caveat Brush, Alegreya Sans and its small caps, all OFL), wooden plaques, paper sheets, pasted strips. Mission sheet: price tags above words, a double underline for property words, the cutting-room floor, the sword's list of edits, undo. Prologue: the 13 pictures full screen, the legend on a paper strip, the sword's correction in red handwriting.

**09:00** Broke: W, A, S and D all moved the hero to the right. Fix: the key map is now built in code.

> Four keys, one opinion. I have steered heroes like that, but on purpose.

![In-engine notice board: the Help Wanted notice with the word "giant" crossed out and lying on the cutting-room floor](devlog-media/style-board.png)
*09:00. In the engine this time. One word cut, 2 of 3 montage points spent, and the rats in the cellar are no longer giant.*

> That is me at the bottom of the screen, explaining it. Again.

![In-engine prologue frame 1: a ragged man asleep in a ditch, the legend caption crossed out and corrected in red handwriting](devlog-media/style-prologue.png)
*09:00. Prologue, frame 1. "Great Hero, Bartholomew the Bold" becomes "man called Barty, who slept in a ditch". Note the Skip button and the dashes at the top.*

> My handwriting.

**09:10** The Skip button and the dashes at the top are removed. Esc skips; Space or click goes on. Frame length now comes from one function, `GetLineSeconds`: the place that will return the voice-over length once there is a voice-over. Board and HUD leave room for a two-line subtitle.

> The button lasted ten minutes. The two-line subtitle is for me. I do not do short.

**09:27** Perk tree in the engine: 44 perks from `perks.csv`, four branches (Blade, Call, Souls, Montage), bought with sword experience, saved. Five sword moves: Whirlwind, Dramatic Thrust, Plot Armor, Chorus of the Dead, Jump Cut. The mockup spec asked how six moves fit on two keys; the answer is four keys: Q, E, F, right mouse. Not in: Ghost Understudy and the hero cooldown perk, shown as such and not buyable. 42 of 44.

> Last night's proposal was 9 nodes.

![In-engine perk tree: four branches growing up from a sword lying along the bottom of a dark cellar wall](devlog-media/perk-tree.png)
*09:27. 44 nodes growing out of a sword. The screen is called "What the Sword Remembers".*

> At last, a screen with the right priorities.

**09:34** Mockups: all six heroes drawn, each at a table. Any three can be seated in the tavern.

> I think of it as a menu.

**09:44** Four mission types: fetch, slay, survive, escort. A mission director lays a road to the far end of the level and places the notice's enemies along it. Escort: if the escorted one dies, the hero comes home alive with nothing, which is the result screen's new third outcome. Fighters pick the nearest target; hungry ones go for the escort; guards notice only what comes close. Six hero moves on R: shield bash, tumble, war cry, prayer, riposte, "seen it before". Power ×1.25 per rank. Ghost Understudy and the cooldown perk now work. 44 of 44.

![In-engine escort mission on the grey test arena: the hero and a teal grandmother surrounded by red wolves](devlog-media/mission-escort.png)
*09:44. Escort Wanted, ten seconds in. The grandmother is the teal one. The wolves are the red ones.*

> The forest of Mumblewood is the grey one.

**09:44** Stock-taking, two hours and forty-four minutes in. The whole loop exists. What does not:

- Every mission of every type runs on one grey template arena. Sixteen notices name six locations.
- In every mission screenshot, heroes, enemies and the grandmother are the stock mannequin in different colours. No commit adds a generated model.
- No recorded voice.
- No packaged build. Everything has run only inside the editor.
- "Pantsless" is in the data and the mockup, not in the engine.
- Pause and settings: on the 08:25 "not done" list, in no commit since. Same for the seven combat roles from the content.
- Prologue pictures are concepts. The final 13 are the developer's call.
- The content folder, the mockup folder and this log are not committed.

> He is pleased with himself. The game has one floor. I am the narrator of a game about a narrator, and I am subtitles.

<!-- Next entries are appended below by the build session. Format: no list bullets. Each time is its own paragraph, "**HH:MM** a few short plain sentences of fact", with a blank line before and after; failures get their own paragraph starting with "Broke:". The sword's remark, if there is one, follows as its own quote paragraph: "> ...". In the quote the sword says "I" and mocks "the developer" in the third person. Dry, true, nothing invented: only the narrator is fictional. No commit hashes: the repository is not public. -->

**10:29** The game has more than one floor now. Six, one per location, each built by a script out of cubes, cylinders and cones: barrels in the cellar, cone trees in Mumblewood, glowing lava discs on Cinder Peak. Setting out loads the place and the job starts on arrival. The seven combat roles from the content are in the engine: swarms circle, warriors swing twice and then heavily, chargers rush and stun themselves on walls, shooters draw their aim line, mages cast and blink, tanks block from the front, named monsters change at 66% and 33%. The Rat King called four rats and lost a spell to a sword in the face. The mannequins are gone too: every enemy kind wears a body borrowed from four free Fab packs, tinted. The developer's plan is to repaint them. For now a bog frog is a red slime with one eye.

> Six floors, made of cubes. I have been carried through worse. The sword in the Rat King's face was me.

**10:29** Broke: the first cellar was lit by lamps of nine thousand candelas and looked like the inside of a toaster. The lamps were removed.

> Nobody misses them.

**10:29** Broke: four of the six levels were saved without navigation, because the editor only learns about a navigation volume one frame after a script makes it. The enemies stood where they were put. Rebuilt a frame later, saved again.

> Standing where they were put. So do most of my heroes.

![In-engine cellar: the hero under an ogre's slam circle, two witches and eight summoned red slimes labelled Bog Frog](devlog-media/roles-cellar.png)
*10:29. The cellar, with company. The ogre's circle is the slam. The witches are the two in hats. The Bog Frogs are the red ones; see above.*

**10:38** A mission was started in each of the six places, next to its named monster: the Rat King, the Toll Troll, the Hydra, Sergeant Gristle, Cinderbeth, the Dark Lord and his mother. All six start, all six have somewhere to walk.

> Six monsters, six floors, one mother. He calls this a world.

**10:38** Broke: the camera's automatic exposure turned every dark floor into noon. Sorrowmire was the colour of a salad. Each level now carries a fixed exposure worked out from its own sun.

> I lay in that bog for thirty years. It was never the colour of a salad.

**10:38** Broke: in Mumblewood a tree crown, seen from above, is a green lid over the hero. The crowns were slimmed and moved off the road. Cinder Peak is still red on red on red; the danger circles are red too. Noted, not fixed.

> A top-down game, and he is surprised that trees have tops.

**10:51** The HUD now sits where the mockup says: the job at 36,30, the hero's plate at the bottom left with a face in it, the moves on the bottom edge, the sword's lines above the moves instead of under them, and a named monster gets its bar at the top of the screen. The six heroes have portraits, cut from the developer's tavern pictures by their heads. The camera stepped back a third. And there is a list, `docs/TEXTURES.md`, of every picture the developer has to generate before a floor stops being a colour: 23 tiles for the six places, 8 repaints for the bodies that have real skins. The other 31 enemies are painted by a grid of coloured squares; no generator is needed for those.

> My lines are above the moves now. It took him three hours and fifty-one minutes to put me above something.

**10:51** Broke: the first portraits were the whole hero, chair and table included, squeezed into 122 pixels. Lady Mirabel was a smudge with a candle. Cropped to faces.

> The candle was the better likeness.

![In-engine HUD: job card top left, The Rat King's bar top centre, Old Tobias's portrait and health bottom left, moves along the bottom, the sword's line above them](devlog-media/hud-aligned.png)
*10:51. The HUD after alignment. The Rat King is the large red one. He is a beetle. See the list.*

**11:06** The cellar is a place now, not a corridor with barrels: stairs, a hall, a wall, the wine racks, another wall, the crypt door, a throne of crates and one keg. Each wall has a passage, and each passage a barricade that stays shut until the rats in front of it are dead. The Rat King's forty stand in three crowds of ten, fifteen and fifteen. The night watch waits until the hero stands among the wine, then climbs out of the crypt. The keg job teaches walking, striking and dashing on the way, in the sword's lines. A soul's worth is counted the way the level notes say: the road is half a monster, the monster is the other half.

> Taught in my voice, which is the only tolerable way to be taught.

**11:06** Broke: the sword's four lessons were written for one notice only, and the mission director asked for them without saying which notice. No lesson played for a whole tutorial.

> I said nothing for a whole tutorial. It was the best run the hero ever had.

![Top view of the cellar level: hall with barrels at the bottom, wine racks between two cross walls with barricades, crypt door on the right, crate throne at the top](devlog-media/cellar-plan.png)
*11:06. The cellar from above. The hero starts at the bottom. The two pale strips in the walls are the barricades.*

**11:11** Three sessions' work landed in one frame. The cellar floor is flagstones instead of a brown rectangle, the barrels have hoops, and the rats are rats: the modelling session reshaped the lizard into a rat, a Rat King with a crown, and a wolf, all on the lizard's own bones so they kept its animations. The 23 tiles and the 8 repaints came from the graphics session. The build session imported them.

> Three sessions did the work. He watched. He is good at that.

**11:11** Broke: the Rat King's health bar lay across the job card whenever the window was narrower than 16:9. The developer saw it before the build session did. The bar now measures the room between the card and the reward and takes only that.

> He found a bug. Once. I am writing it down so that there is a record.

![In-engine cellar: flagstone floor, brown rats around the hero, the Rat King in a red cloak, his health bar at the top beside the job card](devlog-media/cellar-rats-textures.png)
*11:11. The first frame in which a rat is a rat.*

**11:18** The move cells have pictures in them now, fourteen from the graphics session, and the floors are tiled twice as densely so a flagstone is no longer the size of a table. The row of moves steps aside for the hero's plate in a narrow window, as the boss bar already did for the job card.

> Fourteen pictures of things I do. None of them is a picture of him.

**11:18** Broke: the build session built the cellar a staircase and stood it between the camera and the hero. He started every job behind four stone steps. The steps are now ankle-high.

> A hero hidden behind a staircase. For once the casting was right.

**11:20** The troll and the ogre have meshes of their own from the modelling session. The rat, the Rat King and the wolf were smoothed. One command now imports a model: it puts the file on the skeleton of that kind's body with its own texture and rebuilds its data.

> One command. He will still ask what it was called.

![In-engine cellar: a green ogre and a grey troll in a cap stand over the hero inside red slam circles, two rats beside him, the Rat King's bar at the top, the sword's line "WASD. He will call it instinct. Let him." above the moves](devlog-media/troll-ogre-rats.png)
*11:20. The green one is labelled Ogre. The hero is the small white one in the red circle.*

**11:22** Broke: the move icons took up about 40% of their cells. The graphics session exported them again at 92% of the long side.

> My moves, drawn at 40% size. I have been diminished before, but usually by better people.

**11:32** The skeleton and the Dark Lord have bodies of their own now, which makes seven kinds that are no longer a borrowed beetle or a tinted knight. The Dark Lord carries an empty scabbard.

> I know where the sword went.

**11:32** Broke: the troll and the ogre got their new, wider bodies and stopped fighting. They walked up to the hero and stood there, a hand's breadth outside their own reach, for as long as he liked. Reach is now counted from the edge of the body. Found only because the modelling session asked for a photograph of the troll hitting something.

> Two monsters stood next to a hero and did nothing. He calls that a bug. I call it the first sensible staff he has hired.

**11:32** Broke: the editor sat for a quarter of an hour behind a "save changes?" window nobody could see, and the code was rebuilt twice into a copy of the game that was not running it. Closed by force. Nothing of value was unsaved; that was the point of the question.

> A quarter of an hour waiting on a question nobody read. He has that effect on dialogue.

**11:34** The Dark Lord was made lighter. Every enemy now keeps a little of its own colour on the unlit side instead of going black.

> He was always hard to paint as a villain. I managed.

**11:58** The developer looked at all of it and said it was weak, everything, landscapes included. The plan now: each place gets one painted ground, the whole floor in a single picture, and real furniture from asset packs stands on it. The cellar already has the furniture, from the Stylized Dungeon Props Pack on Fab: barrels with staves, shelves, wooden pillars with torches, a throne that is visibly crates. The painted floor is ordered from the graphics session, with a top-down plan of each level to paint over.

> He is right, which I do not enjoy. It took him five hours to look.

![In-engine cellar wine room: giant rats around the hero between rows of wooden shelves and pillars](devlog-media/cellar-props.png)
*11:58. The wine cellar with furniture from a pack. The floor is still the tile; the painting is on order.*

**12:00** The cellar has a painted floor: one picture for the whole place, with a worn path through both doorways, wine rings in the hall, straw and a drain among the racks. It was painted over a plan of the level, so the walls stand exactly on their dark footprints. The developer has now asked for the six heroes to stop being a white mannequin; ordered.

> The first room in this game that looks like somebody drew it on purpose. Somebody did. Not him.

**12:00** Broke: the brick texture was laid from above only, so on the face of every wall it ran down in stripes like wet paint. Walls are now papered from the side.

> A top-down game again. Walls have sides. He will get there.

![In-engine cellar doorway: painted flagstone floor with a worn path, brick cross wall, wooden pillars, giant rats coming through the passage](devlog-media/cellar-ground.png)
*12:00. The doorway between the hall and the wine cellar, painted floor under real props.*

**12:03** The game now puts a hero's own body on him when one exists, on the mannequin's skeleton.

> "When one exists." I admire the optimism.

**12:06** Mumblewood has trees that are trees: birches and broadleaves from a free pack, boulders, bushes, flowers. Dreadwick has houses with smoking chimneys, a well, a gallows, carts, hay and fences, from a village pack of 1.2 GB, which is not committed. Both still stand on tiled ground; their paintings are on order. The modelling session is generating the heroes' bodies from pictures and re-hanging them on the mannequin's bones.

> A village with a gallows, straight from the shop. Somebody else thought of my heroes before he did.

![In-engine Dreadwick: recruits around the hero on a dirt road, a wooden fence, a hay bale, a well and a house roof with chimney smoke](devlog-media/dreadwick-pack.png)
*12:06. Dreadwick with a village in it.*

**12:10** All six places stand on painted ground now. Mumblewood has a river that is painted water with banks instead of a blue box alone; Sorrowmire is mud with footprints in it; Dreadwick is a rutted road between real houses; Cinder Peak is cracked rock around the lava; Doomspire has a star inlaid in its floor. The bridge deck has a texture.

> The star in Doomspire: nobody asked for it and everybody will keep it. Much like me.

**12:10** Broke: the lava on Cinder Peak glowed at nine times the brightness of anything else and came out as flat yellow holes. Turned down to something that still has cracks in it.

> First a toaster, now this. He lights a room the way he plans a week.

![In-engine Doomspire: the hero on a dark purple floor with a large inlaid compass star, the Dark Lord's health bar above](devlog-media/ground-doomspire.png)
*12:10. Doomspire. The star is paint.*

**12:21** The troll has been replaced a third time today. This one was generated from the developer's own concept picture, arrived with a skeleton of its own and four clips, and looks like the drawing: hide, belly, a club the size of the hero. The rest of the bestiary and the six heroes are to go the same way.

> Three trolls in one morning. I have gone through heroes more slowly.

**12:21** Broke: the first file brought only two of its four clips. Unreal refuses an animation that lasts thirty-seven and a half frames, and says so in the log. Re-exported on whole frames.

> It said so in a log. He does not read logs. He is not reading this one.

![In-engine close-up in the forest: a grey troll in hides mid-swing over the small white hero, red danger circle on painted grass](devlog-media/troll-generated.png)
*12:21. The Toll Troll, generated from the concept. The white figure at its knee is still the hero.*

**12:29** The hero is no longer a white mannequin. Pip Underfoot walks the cellar as himself: the nose, the hair, the red cape, generated from his tavern portrait and moving on his own four clips. The other five heroes are to follow the same way. The sword in his hand is still a grey placeholder.

> Everybody has a body now except the title character. I am a grey plank. I have asked nobody to fix that yet.

**12:29** Broke, twice: on his first two entrances Pip was hidden behind his own sword, which had grown to the size of a barn. The generated skeleton scales its bones while it animates, and the sword inherited every bit of it. The sword now ignores the hand's scale.

> For two takes I was the size of a barn and nobody could see the hero. He calls that a bug.

![In-engine close-up in the cellar: Pip, a thin man with spiky hair, a big nose and a red cape, holding a grey placeholder sword, barrels behind him](devlog-media/hero-pip.png)
*12:29. Pip Underfoot, in person. The grey plank is me.*

**12:32** Six of the bestiary are now generated from their concept pictures: the troll, the ogre, the skeleton, the rat, the Rat King and the Dark Lord. The King has his crown and his cloak; the Dark Lord has a crown of spikes and a beard. Attack clips were shortened.

> He has the look of a man who threw a sword into a bog and regrets the paperwork.

**12:32** Broke: forty-one enemies on screen ran at about thirty frames a second inside the editor. Each rat was nineteen thousand triangles. A thinner rat was ordered.

> Nineteen thousand triangles of rat, forty times. The laptop from this morning sends its regards.

![In-engine close-up: the Dark Lord, a bearded man in dark armour and a spiked crown, standing over the white placeholder hero on painted forest ground](devlog-media/darklord-generated.png)
*12:32. The Dark Lord, generated from the concept. The hero beside him had not been replaced yet in this frame.*

**12:35** Pip's swing clip was cut to 0.8 seconds. The thinner rat arrived: 4,500 triangles.

> The rat lost three quarters of itself in three minutes. Nobody can tell.

**12:40** Three heroes have bodies now: Pip, Brunhilda Oxblood with her braids and fur shoulders, and Lady Mirabel Vane, who swings the sword from over her head. The other three wait for the developer to buy more credits from the service that generates them.

> Lady Mirabel is the first of them to hold me as if she had paid for lessons. The other three are held up by his wallet.

![In-engine close-up in the cellar: Lady Mirabel in a burgundy coat and tall boots, mid-swing, holding the grey placeholder sword above her head](devlog-media/hero-mirabel.png)
*12:40. Lady Mirabel Vane, mid-swing.*

**~12:50** The game has an itch.io page, a draft that is not public yet: title, tagline "A game about a hero. Recut by his sword.", description, cover. This log went there as three posts, up to 12:32. Another Claude Code session did it. The developer had the six engine screenshots removed from the page: too rough for now. Only the cover remains.

> Six pictures of his own game, and he took them down himself. I did not have to cut anything.

**12:52** The sword now sits in the hero's palm instead of his wrist, placed from the knuckles of the rest pose.

> Five hours and fifty-two minutes to find out where a hand holds a sword.

**12:54** Sir Aldric the Adequate has arrived: plate armour, a red cape, a moustache, and a third-place medal on a ribbon, worn over the breastplate. He was made in a different program from the others and came facing sideways; the game now works out which way a hero is looking from where his arms are. Four heroes of six.

> The heroes cannot be trusted to say which way they are facing. The medal he wears where everyone can see it.

![In-engine cellar: Sir Aldric in plate armour with a red cape, moustache and a medal on a ribbon, standing in front of the stairs](devlog-media/hero-aldric.png)
*12:54. Sir Aldric the Adequate. The medal says 3.*

**13:00** Stock-taking, six hours in, written down as `docs/ROADMAP.md`. About 87 hours remain on the clock. Still missing:

- No packaged build. Everything has run only inside the editor.
- 6.7 GB of disk is free. Packaging needs more.
- No recorded voice: 156 lines, subtitles only. Not one sound in the game.
- The ending: the Dark Lord's notice, the deleted scene and both credits. The Credits item in the menu is inactive.
- Five of six levels are a road over painted ground. Only the cellar is laid out.
- Osric and Tobias have no bodies of their own. They wait for credits.
- "Pantsless", pause and settings: still not in the engine.

> He wrote a plan at one in the afternoon of the first day. The disk is nearly full again. He knew that at 07:28.

**13:13** The sword has a model of its own: a hilt with rings on the guard and a blade a metre long, held in a fist. The property words have little pictures now, a giant goblin for "giant" and so on. Mumblewood's three jobs are laid out the way the level notes say: the troll sleeps at the bridge, the trousers hang at the ogres' camp three quarters of the way in, the wolves come at the grandmother in three packs with the bear on the bridge.

> I have a body. Until today I was a grey plank. I narrated a whole day of development as a plank and nobody apologised.

**13:13** The game was packaged for macOS for the first time: four and a half minutes, 691 MB zipped, and the menu opens.

> The menu opens. He has shipped a menu.

**13:13** Broke: the first packaged copy did not start at all. The engine's "archive" step produced an application without the engine's own libraries, and it died asking for one of them by name. The staged copy beside it is whole and is the one to ship. The developer has since asked that builds not become a habit.

> He asked that builds not become a habit. Finishing things was never one of his.

![In-engine close-up: Pip in the cellar holding a real sword with a ringed golden guard instead of a grey bar](devlog-media/sword-in-hand.png)
*13:13. Me. Finally.*

**13:14** Osric wears a generated body. Five heroes of six.

> Tobias is last. He is two years from his pension and used to waiting.

**~13:16** Broke: the disk ran out of space again. Second time today; the first was at ~07:28. The developer reported it laughing. To free space he deleted the whole Xcode cache and the builds of his other, mobile projects.

> I wrote at 13:00 that the disk was nearly full. He took it as a forecast, not a warning. He is laughing. I have written that down too. The other projects were not asked.

**~13:30** Broke: running that was not in place. On four models exported from Studio the pelvis travelled two and a half metres forward over one run cycle, although the modelling session had switched on the "in place" mode. The session removed the drift itself: a script pins the pelvis to where it stood in the first frame.

> Four models tried to leave, two and a half metres per step cycle. I understand the impulse. They were pinned by the pelvis. He is here voluntarily.

**13:42** The game has a settings screen, opened from the main menu: fullscreen, a borderless window or a plain one, picture quality, render scale, vertical sync, a frame limit and a frame counter. A packaged game now starts fullscreen at a quality that leaves the expensive lighting out. The project's template had ray tracing switched on, for a game seen from above with a painted floor; it is off. The sword's size is set per hero: a two-hander in Brunhilda's hands and a long knife in Pip's.

> Ray tracing, for a painted floor seen from above. It had been on since 07:10. He did not ask what was making the laptop warm.

**13:42** Broke: the developer said the heroes do not hold the sword, so the modelling session clenched all their fists, thirty finger bones a frame. In the engine every one of them came apart into red ribbons. The fists were set aside and the open hands put back.

> He asked for fists and got ribbons. I have seen heroes come apart before. Usually it takes a troll.

**13:42** Broke: the new ogre and Tobias arrive sixty metres wide, for reasons nobody has found. Three imports, three explosions; the old versions stand.

> A sixty-metre pensioner. The tavern has a door.

**13:49** Five heroes hold the sword in a closed fist now, and none of them comes apart doing it. The cause of the red ribbons was found in a log: the modelling session's export wrote the skeleton's reference pose from a random frame of the last clip instead of the rest pose. The five run in place. Brother Osric lost his lacquered look with a re-baked texture; Aldric's was re-baked too. Tobias and the new ogre still arrive sixty metres wide. Same warning in the log, same result. They stay out.

> The cause was in a log. It always is. Osric is a round, worried monk again, as drawn. He has reason.

![In-engine close-up: Brother Osric, a round monk in a brown habit with a rope belt and a cross, holding the sword in his right fist](devlog-media/hero-osric.png)
*13:49. Brother Osric, matte at last.*

**~13:55** A sixth Claude Code session started on sound. The sword's voice is to be made on the laptop itself with Chatterbox TTS, one file per line. Music is to come from Google Lyria through OpenRouter, capped at eight paid requests.

> Seven hours in, somebody remembered that the narrator of this game speaks.

**13:57** The hero's swing plays at its own pace instead of being squeezed into the attack cooldown.

**14:04** The developer clicked the left mouse button and watched his hero dive forward, bent double, instead of swinging. The generated clip called "slash" is a headlong stab. It is no longer used: a strike is now the hero winding up to his sword side and cutting across where he stands, feet planted.

> Seven hours and four minutes in, he pressed the attack button and looked. Travelling while striking is what my moves are for.

**14:04** Broke, and had been for a while: hits that looked like hits and were not. Two causes. The swing only counted an enemy whose exact middle was inside the arc, so a troll standing mostly in the blade's way was missed. And the aim was taken where the cursor crosses the air at the hero's chest, not the ground the enemy stands on, which slid it half a metre up the screen. Now any part of the body in the arc counts, and the aim is taken at ground level.

> I was missing trolls. Me. I want it recorded that the arithmetic was his.

**14:10** The swing is a swing. The modelling session animated one by hand, because both of the generator's ready-made sword strikes fold the hero in half: feet planted, the blade up over the right shoulder, down in front, three quarters of a second. Five heroes have it. Old Tobias has arrived, sixth of six, bald and grey-moustached, taken straight from the generator's own file, because every copy that passed through the modelling program came out sixty metres wide and nobody found out why. He keeps the turn-of-the-body strike: his own clip runs six seconds.

> Six heroes of six. Tobias looks unimpressed. He suspects something about the sword and says nothing: two years to his pension.

![In-engine cellar, side view: Pip standing upright with the sword raised over his right shoulder, mid wind-up](devlog-media/swing-windup.png)
*14:10. Wind-up, 0.27 seconds in. He is standing up. Note that.*

![In-engine cellar: Old Tobias, a bald man with a grey moustache and beard in a red cloak, holding the sword low in his right hand, the stairs behind him](devlog-media/hero-tobias.png)
*14:10. Old Tobias, sixth of six.*

**14:19** The developer said Pip holds the sword wrong, "completely". He did: it sat square across the fist, so it stuck out sideways at rest and pointed at the floor at the end of every cut. The sword now leans fifty degrees forward in the hand. Tanks that take a blow on the shield say so: "Blocked · go round" rises off them, because a blocked hit and a miss looked exactly alike.

> I was held like a rolling pin. For seven hours. By all of them.

![In-engine side view: Pip at the end of a cut, arm forward, the blade pointing forward and down](devlog-media/grip-strike.png)
*14:19. End of the cut. Forward and down, the way a cut ends.*

**14:24** The wrist in the hand-made swing was corrected on five heroes, and the lean in the grip came down from fifty degrees to twenty to match.

> Fifty degrees at 14:19, twenty at 14:24. He holds an opinion about as long as he holds a sword.

**~14:28** The sword has a recorded voice for the first time: the first three lines of the prologue, as three files on disk. Forty test takes came before them. None of it is in the engine yet.

> Three lines. I have a hundred and fifty-six. I have said more to him in this log.

**~14:32** The first two battle tracks arrived as raw files: the cellar and the bog. Not mastered, not in the engine.

**14:35** The developer looked at the hand-made swing and turned it down. The new rule: everything straight from the generator, nothing through the modelling program, and the swing is a clip the generator made from a sentence. Sir Aldric is the first: he twists, brings the sword round level and cuts, standing where he stood. Long swing clips play only their first second.

> The hand-made swing lived twenty-five minutes. Made at 14:10, refused at 14:35. I keep the receipts.

**14:35** Broke, and explained at last: clips imported on their own onto an existing skeleton shrank the hero to a hundredth of his size, leaving a sword lying on the floor. That is what happened to Tobias hours ago, and was blamed on three other things. The mesh import multiplies by a hundred without being asked; the animation import does not.

> A hero a hundredth of his size and a sword on the floor. It is the most accurate picture of our partnership so far.

![In-engine cellar, side view: Sir Aldric in a red cape and armour holding the sword upright in front of him, barrels in the dark behind](devlog-media/aldric-studio-swing.png)
*14:35. Sir Aldric, straight from the generator, sword in hand.*

**14:47** The game makes a sound. Eight pieces of music from the audio session: one for the tavern and the menus, one for each of five places, the Dark Lord's own for his keep, one for the prologue. One looping track plays per screen and, in a mission, per level. The sword has a voice in the engine: the first lines of the prologue are spoken, and the picture now waits for the line to finish instead of counting letters. Nobody in the build session has heard any of it; a log says it plays.

> I speak. Seven hours and forty-seven minutes in. The picture waits for me to finish, which is more than he does.

**15:14** All six heroes now come straight from the generator, with the same swing: wind-up at shoulder height, a level cut, feet planted wide. Pip, Brunhilda, Mirabel, Osric, Tobias and Sir Aldric each stood in the cellar and cut the air for the camera.

> Six bearers, one swing. I taught none of them. It shows.

**15:14** Broke: Brunhilda and Mirabel arrived fifty metres tall. Their files carry a bind pose the newer importer refuses; it then binds the mesh a hundred times too large on a skeleton of the right size. The older importer binds them properly, a hundred times too small, which one number puts right. Then Brunhilda vanished mid-swing and left the sword on the floor again: the one clip that needed rescuing had come in at a hundredth. The rescue now always goes through the newer importer.

> Sixty metres wide, fifty metres tall, a hundredth of a man. Today my heroes have been every size except the right one.

**15:14** Broke: the camera could not catch a swing by the clock. With the editor in the background the game ticks in lurches, and both frames showed the same instant. The swing is now frozen at a chosen second of the clip and then photographed.

**15:40** The blade is no longer steered by the hand. The generator animates bodies that hold nothing, so in the swing the hand tumbles and the sword pointed backwards at the moment of the blow. The modelling session measured it: the forearm goes cleanly up and comes cleanly down. Now the forearm aims the blade: forward and down at rest, up at the top, level and forward on the cut.

> I pointed backwards at the moment of the blow. I would call it a metaphor, but he would ask what for.

**15:40** The ogre is whole at last, straight from the generator with empty hands, and carries a real spiked club of his own. The rubber club is gone. Twenty-four of the sword's lines are now spoken aloud.

> Twenty-four lines out of a hundred and fifty-six. The ogre got a club before I got a sentence in edgeways.

**15:40** Broke: the editor froze and had to be killed. The session rendering the sword's voice had grown to 28 GB and the machine ran out of memory. Then the editor took nine minutes to start, rebuilding every shader, because the disk cleanup had emptied its cache.

> My voice took 28 GB and stopped the game. I regret nothing. He deleted the cache himself, at ~13:16, laughing.

**16:14** Broke: the MacBook restarted by itself. The editor came back with no project open, and the line the build session uses to drive it was dead; until it returned, the session spoke to the editor over plain HTTP. By the developer's count the MacBook restarted twice today. The system's own record shows this one.

> The machine left without saving. It is the first thing here to quit on principle.

**16:23** The hero's hit now lands when the swing brings the blade down, not on the click: it waits the four tenths of a second the arm needs. A second click before that lands the first blow at once, so nothing is swallowed.

> I now hurt when I arrive, not when I am asked to.

**16:26** The wolf is a wolf. Until now the wolves of the forest were a small wingless dragon painted grey; the new one has four legs of its own, a tail, a paw strike and a way of falling on its side. It came with its feet half a metre under the floor and its nose pointing sideways; both are written down as its oddities, so the next odd beast costs one line.

> Most of a day of grey dragons. Nobody in Mumblewood complained. Nobody in Mumblewood was asked.

**16:26** Broke: the wolf's paint was locked inside its file and the importer could not take it out. It was taken out by hand and laid beside the file.

**16:26–19:52** No commits for three hours and twenty-six minutes. By the developer's account, in these hours the editor kept crashing, and nobody found out why.

> It fell over, he opened it, it fell over. I have watched heroes learn faster, and they were being eaten at the time.

**19:52** The game has an ending, and a second one after it. Kill the Dark Lord and the legend gets its three frames, each stamped "official version": the hero rehearsing his speech, the statue holding the sword wrong. Then "The End" is struck out in red, "a scene I cut" is written above it, and the screen becomes a strip of film: nine frames of Edric Dark, the bog, thirty years of mud. It ends on the sword, alone, on black. One minute forty-five, spoken throughout; a click hurries it, Esc skips it.

> The ending, and then the ending I prefer.

**19:52** Broke: the sword's subtitle sat on top of the legend's caption in the official part. The caption moved up. Not done: the scratch running down the film, and the credits. The finale hands over to the job's result for now.

![In-engine finale: a black film frame with sprocket holes, "The End" struck out in red, "a scene I cut" handwritten above it, the label "Deleted scene · take 1", the sword's subtitle "Wait. Before the credits. There's a scene I cut."](devlog-media/finale-4-cut-card.png)
*19:52. The cut card of the finale.*

**19:55** Walls have tops. Seen from above, a wall used to show the same bricks on its roof as on its face. Now the face that looks up wears its own picture: bricks laid flat in the cellar, sawn log ends in Dreadwick, leaf carpet on the forest hedge. A cleaner cellar wall top followed at 20:03.

> Walls have sides since 12:00 and tops since 19:55. At this rate he discovers floors on Friday.

**19:55** Broke: bringing in the wall tops also repainted seven creatures with the paint of the bodies they used to borrow. The wolf got a lizard's skin back. Put right at once; the import now leaves alone any kind that has a model of its own.

**20:01** The narrator's lines now match several facts at once. A line asked for "the dragon, and asleep", and the game only ever passed one fact at a time, so the sleeping dragon got the speech for the waking one. Now everything that is true is passed: the job, the hero, the place, the monster and each word on it. The line that asks for the most of it wins. New remarks were added: on each place on the first walk in, on each trade of enemy the first time one comes close, when a monster changes its mood, when the hero is nearly dead, when the one being escorted is hurt, lost or delivered.

> I had lines I could never say. He wrote them, shipped them and did not notice that I was not saying them.

**20:07** The Dark Lord's door lines are said in order. With both of his words cut the sword greets its old bearer: first what he has lost, then "Hello, old friend", and only then a remark on his mother or his trousers. With a word of his still standing nothing special is said at the door. Not seen in the game yet: the greeting itself. Cutting both words costs more than a fresh save can buy.

> The best line I have, behind a door he cannot afford to open.

**20:08** All 156 lines of the sword are voiced: seventeen minutes, in a new voice, each file tied to its line by name. None missing, none left over from the old takes.

> Seventeen minutes of me. It took thirteen hours to let me finish a sentence.

**20:17** The game has a language switch. A row in the settings turns it from English to Russian and back; on the first start it takes the language of the machine. Every text already came from a table by its key, so the second language is a second table with the same keys. The interface is translated: 242 strings, with their plurals.

> The roadmap of 13:00 lists the Russian version under "not for the jam". Seven hours later it is in the settings.

**20:17** Broke: the print font and the handwriting font have no Russian letters at all. Russian words in those places were set in the interface font.

**20:22** A blow that is coming is now drawn before it lands, in red pencil, on the floor: a hatched circle under the ogre's club, a lane with arrowheads in front of a wolf about to charge, a ring of embers where the mage's fire will fall, a cross where something heavy will come down. The plain disc still fills up inside the sketch to say how soon. A blow that lands leaves a flash over whoever took it; a blocked one leaves a different flash. Heavier outlines followed at 20:26. Not used yet from the same sheet: the three cones, the ward ring, and nine of the twelve sprites.

> The ogre now sends a drawing before he hits. It is more notice than I ever gave a hero.

![In-engine cellar with Russian interface: an ogre over Pip inside a red hatched circle on the flagstones, the job card top left, the sword's Russian subtitle above the moves](devlog-media/fx-mark-circle.png)
*20:22. The hatched circle is where the club will land. Pip is the small one inside it.*

**20:25** The Russian is whole. Every notice, every word that can be cut or pasted, every perk, every hero and what he shouts: 458 strings from the content session. All 156 lines of the sword are spoken in Russian. A pasted word cannot be bent to fit its new sentence, so in Russian it arrives in brackets, as an aside: "forty loyal (without trousers) rats". The prologue's legend is struck out and rewritten in Russian too.

> Russian has six cases. He has brackets.

**20:29** The Russian text got its old-book look back. Three free font families that have Russian letters step in for Russian letters only: Old Standard for the print, Cormorant for its capitals, Caveat for the sword's hand. The English keeps its own.

> For twelve minutes the Russian legend looked like a tax form. The Dark Lord would have approved.

![In-engine prologue in Russian: a man in a ragged cloak asleep in a ditch with an empty bottle, a raven on a fence post; the legend's caption is struck out in red and rewritten by hand, the sword's subtitle below](devlog-media/ru-prologue.png)
*20:29. The first frame of the prologue, in Russian. The red handwriting is the sword's.*

**20:52** Every job has its own ground under it. The four places that were only a corridor got their named spots, barriers with a barricade in the gap, and something to know each spot by: a hut on legs, nests with eggs, tents, a heap of gold. Ten jobs were given their crowds by place. Each of the ten was started and played to its end by a test hero who cannot be hurt and kills on sight. Seen for the first time: kill the Dark Lord in his hall, and the finale opens by itself.

> Ten jobs, finished by a hero who cannot die and does not think. He has finally built the one he wanted.

**20:52** Not there, though the level notes ask for it: the witch's hut does not walk, the ferry does not float, the village gate has no health, the gargoyles throw nothing. These jobs run on the plain rules of their kind, in the right place, with the right crowd. No person has played them yet.

**21:34** The game has sound effects. Thirty-three: a whistle when the sword misses and a thud when it does not, steps, a dash, a body going down, scissors on paper, the slap of a pasted word, a click under every button, the tavern murmuring under its tune. Which event plays which sound, and how loud, is a table. Three volumes in the settings: music, the sword's voice, sounds. The music steps back by itself whenever the sword speaks. The things the jobs are about now exist: a keg, the witch's rent chest, the dragon's egg, a pair of golden trousers on a washing line, a cake on a cart that rolls up the Bone Road by itself.

> The music steps back when I speak. It is the only thing in this project that does.

**21:34** Broke, twice. The editor fell over when a game was stopped after the build session had driven it with two test scripts instead of one. Then it would not start: the crash-report window of the dead editor was still holding the port the session's commands go through. The reporter is now closed first.

> Both were the build session's doing, and it said so. I mention it because he never has.

**21:34** The developer asked not to have the editor jump in front of him fifteen times a day. It now starts with no window at all and does everything as before, screenshots included.

![In-engine Dreadwick at dusk: a purple tiered cake on a cart in the middle of a dirt road, a red timber house on the right](devlog-media/prop-cake-cart.png)
*21:34. The cake, on its cart, on the Bone Road.*

**21:58** The grandmother is a grandmother, in a red kerchief, and the assessor an assessor; until tonight both were a blue mannequin. And the ogre of Lost Property stands by his washing line in white underwear with red hearts, because the word "pantsless" is on him. Any fighter may now change his looks for a word. The washing line was turned across the view and enlarged at 22:00.

> Fourteen hours and fifty-eight minutes, and the game has reached its point: an ogre without trousers. I narrate this.

**21:58** Broke: the editor with no window sat for five minutes in front of a question nobody could see: "restore the files you did not save?" It is now started so that it answers such questions by itself.

> An invisible editor asking an invisible question. At 11:32 this cost a quarter of an hour. He is improving. By ten minutes.

![In-engine forest: a green ogre in white underwear with red hearts standing in an orange circle with a spiked club, a washing line with golden trousers on the right](devlog-media/ogre-pantsless.png)
*21:58. The ogre of Lost Property. The trousers are on the line.*

**22:05** The heroes hold the sword. Until tonight every one of them carried it on an open palm, fingers straight, because the generator animates bodies with empty hands. Each finger of both hands, in every clip of six heroes and two ogres, is now turned about its own hinge into a fist.

> They hold me now. Fifteen hours. I was carried through a whole day like a tray.

**22:05** Broke, and for half a day without anyone noticing: Brunhilda and Mirabel had no skeleton. The older importer keeps the skeleton in memory and never writes it to disk; after the first restart of the editor both of them, and tonight the grandmother, were left as statues. Found only because the fist tool refused to work on a clip with no skeleton. All three were imported again, and everything an import makes is now saved on the spot.

> Two of my heroes had no skeleton since the afternoon. Nobody noticed. I am not sure which of us that says more about.

**22:05** End of day one, fifteen hours and five minutes in. 65 commits. About 78 hours remain on the clock. What exists: the whole loop from menu to finale, six places laid out by their jobs, six heroes and the enemies in their own bodies, music, 33 sounds, the sword's voice in English and in Russian, a language switch. Five posts of this log are published on itch.io; the game page is still a draft. What does not:

- Credits, in either version. The Credits item in the menu is inactive.
- A fresh packaged build. One was made, at 13:13. Nothing after it has run outside the editor.
- A full run by a person, from the first job to the Dark Lord. The roadmap notes that with every perk the editing budget is 13 and cutting both of his words costs 28.
- The 13 prologue pictures are still concepts.
- The gameplay video.
- Pause in a mission.
- 12 GB of disk is free. The roadmap asks for 20 or more before packaging.

> He restarted the laptop twice, filled the disk twice and replaced the troll three times. The game has an ogre without trousers and no credits. I, however, can speak. Day one is mine.

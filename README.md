# HitTheDonut
Description and latest version of Hit The Donut.

##### Author: Võ Phú Thành
##### Ho Chi Minh City, December 24th, 2018.

**abstract-** A replica of the famous hit "Knife Hit", but with a dancing donut as the target board and various candy, lollipops as projectiles.


## **1. Introduction:**
### *Basic Introduction:*
A hyper casual game where players launch lollipops, forks and various candy models into a giant dancing donut.

### *Developer's Description:*
As a Knife Hit Replica, the game consists of almost all functions and details from the original, which are:
-- A target_board, in this case a Donut, that rotates differently (slow, fast, change the direction) according to the background music.

-- A pool of fruits_, which jumps within its local y-axis and rotates (optional) according to the background music.

-- A pool of projectiles (knives in the original game) that players will use to launch into the target_board. Update scores everytime a knife hits the target_board, or fruits_. The game ends when a knife hits another knife. A level is completed when all knives are thrown into the target_board.

-- A level is loaded with a target_board prefab, fruits_ prefab, knives prefab and some particles system prefab (for target_board explosion, fruits_ explosion and target_board being hit effect). Some level also consists of pre_knives, which are loaded to be stuck into the target_board beforehand. Each level has a unique song for the game models to operate, with other unique configurations as well: number_of_knives, target_board_speed (low-medium-high), pre_knives_angles, fruits_angles.

### *Game Flow:*
The latest version of the game consists of two flows: Endless (Normal) Mode and Challenge Mode.

-- *Endless Mode:*
The game always starts at level 1, at both normal start and restart. Whenever a level is completed, a new level is loaded after playing an animation of the target_board explosion. The level keeps increasing until the player dies. If the level contents run out, the levels cycle simply repeat itself.

-- *Challenge Mode:*
Differently from Endless Mode, in this mode players will have their progress saved everytime they pass a level. If they fail, their current run will be recognized by the game as the best records if it beats the others. Currently the Challenge Mode only has 15 levels in total. If a player completes all the levels, a canvas will popup as a congratulation. 


-- *Content Tool:*
A special version specifically built for Content Team to test their contents within the real game environment. In this project, the contents are mostly songs in .mp3 and .bin forms, and the tests to be conducted were to see if the target_board and the fruits move as how Content Team has intended them to. In these versions, there were no levels progressing but contents progressing, as there would be a list of contents for the team to test. A few things to note: 

+ The Content Tool must be able to load contents via an online config. That is, there would usually be a given online address to download the contents, and these links must be read by the game from a config that loaded from the internet before. Besides the content links, the configs in this game also has other features as normal configs.

+ The functions in-game are also kept to be simple (no challenge mode, no settings, no ads, no IAP, etc.) so that the game only shows basic features of the content (index, song_name, duration, etc.) to Content Team.


## **2. Methods and Development:**
### *Project Timelines:*
+ Nov 12th, 2018: Project started.

+ Nov 15th, 2018: Sync target_board's movement to given nodes + Add fruits.

+ Nov 20th, 2018: Add Donut package.

+ Nov 20th, 2018: Finish Draft Demo build.

+ Nov 21st, 2018: Load local resources via configs + Add Splash scene.

+ Nov 22nd, 2018: Rework throwKnife function + Add AmaContentTool.

+ Nov 23rd, 2018: Build Content Tool + Fix gameplay.

+ Nov 26th, 2018: Combine MainGame and MainMenu scenes. 

+ Nov 28th, 2018: Wrap up controllers + Fruits Collision + Refine animation + Resize multi-resolutions.

+ Nov 29th, 2018: Update UI and Models.

+ Nov 30th, 2018: Generate new levels. 

+ Dec 1st, 2018: Update Content Tool and Canvas Art + Update Assets + Load new configs and local songs.

+ Dec 3rd, 2018: Appstore build.

+ Dec 4th, 2018: Fix music sync and fruits jumping bugs + Add highscores + Fix IOSPostProcessing.

+ Dec 5th, 2018: Add 4 new levels + Fix fruits on hit particles and scoring bugs + Replace GameObject holder with array/list + Fix every 3-level has a custom randomize donut + Display random knife model at Menu + Random background color at Menu.

+ Dec 6th, 2018: Add Analytic in game.

+ Dec 7th, 2018: Add shaking movement to target_board on knives impact. 

+ Dec 10th, 2018: Add Ads (demo) + Add Config popup.

+ Dec 11th, 2018: Implement configs values chosen by PO to the game + Build + Add pre_knives configs.

+ Dec 12th, 2018: Add pre_knives with config angles + Add fruits with config angles + Fix pre_knives and knives on board not having the same size.
+ Dec 13th, 2018: Add TapToPlay Tutorial + Fix pre_knives depth in target_board + target_board now shakes 45deg when knife hits each other + Fix "Score" text in Gameover canvas to "Best" + Add end-level animation + Remove knife model sprite 01 at Menu + Fix knives and pre_knives size + Fix Rescale to fit devices + Update IOS version + Add GM for Adhoc testing + Fix randomization at level 1 + Fix knives animation at end-level.

+ Dec 14th, 2018: Fix IDBundle + Fix Fruits animation only play once if multiple fruits were hit at a time + Customize random methods in-game to have different results guaranteed for N times (N = 3) + Fix bug knife out of orbit when hit by another knife while hitting the board + Add new background + Fix randomized knife model can generate same model at Awake().

+ Dec 17th, 2018: Fix AppsFlyerService + Change game's icon + Refine Artwork in-game + Construct Continue function + Implement 9 more toppings (knives) + Implement 10 more donuts (target_board) + Change Splash Screen + Update background + Update build configs with local machines.

+ Dec 18th, 2018: Show GM command + Fix Scenes' transitions + Add Continue script + Update Continue UI and progress bar for the scene + Change configs IronSource to normal + Add Facebook settings + Add configs ID IronSource.

+ Dec 19th, 2018: Fix Challenge Mode restarts at level 1 when hits Restart button + Fix Challenge Mode starts at (level - 1) when Challenge again. (Die at level n should restart at level n, not n - 1) + Construct Challenge Mode ending + Fix when play normal after challenge mode donut model and preknives' position still the same (pre_knives should be clean beforehand) + Remodel knives' colliders + Challenge Mode now starts with contents from level 15 + Update configs + Update project settings + Fix Challenge levels display + Fix buttons display + Fix duplicate Ads at Continue Progress + Fix Ads reward on cancel.

+ Dec 20th, 2018: Construct new Content Tool version. 

+ Dec 21st, 2018: Update new Content Tool version.

### *Project Details:*
-- *Hierarchy:*

+ The game was built upon the Base Framework provided by the company, which included various libraries from external (Demi Giant - Tween, IronSource, etc) to internal development (Ama_Utils for songs' synchronization, FileLoadIO for loading resources, etc).

+  The game's own assets and scripts were located within the Assets folder, under the name of "mainGame". The main folders inside are:

**KH-Art:** Contains all contents received from the Artist team, which are background, effect, font, models, skin_decor (fruits_), skin_donut (target_board), skin_knife (knives), UI.

**mainScripts:** Consists of all scripts to use in the game. These scripts are built for this game/project only.

**Prefabs:** Contains all prefabs to spawn in the game, including Donut (target_board), Fruits (fruits_), Fx (Particle Systems), and Knives.

**Scenes:** Contains all scenes to use in the game, with MainGame as the main gameplay scene, Sandbox as the scene to implement testing, and Splash as the loading scene.

-- *Coding:*

+ The main gameplay scene has a total of 7 controllers to control different segments:

**GameOperator (KHGameOperator.cs):** Controls the flow and events happening within the game. Also helps redirect other controllers into the desired flow or event. The first script to receive the configs values then pass them into other controllers. By acting as a control center, the author can keep track and manage the game's flow in a convenient way.

**BoardController (KHBoardController.cs):** Controls the target_board's movement and rotation so that it synchronises with the background music. Also loads the desired background music from streamingAssets. 

**KnifeController (KHKnifeController.cs) and KnifeScript (KHKnifeScript.cs):** Control the knives' movement and collision events. The script KnifeScript is attached to each knife prefab, and KnifeController will get a reference to this script everytime a new knife is spawned. Collisions are detected via OnCollisionEnter2D in KnifeScript. The complete flow: KnifeController spawns knife - KnifeController throws knife - KnifeScript moves the knife - KnifeScript detects events and passes to KnifeController - KnifeController passes collision results to GameOperator's EventsCenter.

**FruitsController (KHFruitsController.cs) and FruitScript (KHFruitScript.cs):** Control the fruits' movement and collision events.The script FruitScript is attached to each fruit prefab, and FruitsController will get a reference to this script as it holds the list of fruits to be spawned at each level. Fruits' angles to be spawned are read from configs script and are determined through level design stage.

**UIController (KHUIController.cs) and UIContinue (KHUIContinue.cs):** UIController controls all UI functions and objects such as canvases, texts, etc. The script UIContinue was created to control the process of continue event. 

**EffectController (KHEffectController.cs):** Controls all the effects (Particles System) in the game. Whenever the GameOperator calls, the effect prefab is spawned and played.

**PreKnivesController (KHPreKnivesController):** Controls the spawning and related events of pre_knives. The pre_knives are spawned with the normal knives prefab, thus still hold similar events such as OnCollisionEnter2D to detect collisions. The angles of each pre_knife to be spawned are read from configs script and are determined through level design stage, similarly to fruits'.

+ Moreover, there are a few other scripts as well: 

**GameConsts (KHGameConsts.cs):** The script to store all global static constants variables that would be used across the game. By this way these constant values can be modified without having to go through all other scripts which use them as well.

**ConfigSongData (KHConfigSongData.cs) and ConfigDifficultyData (KHConfigDifficultyData.cs):** The two scripts which are implemented with method from the base framework to read values from features in configuration files. Each features will be loaded with syntax defined in these configs scripts, then pass an instance to ConfigManager (ConfigManager.cs) and this manager script will load these instances in the SplashScene (SplashScene.cs).

**RngController (KHRngController.cs):** The script created to control randomization in the game, which is involved in the process of choosing donut models and knife models to load. As Unity's built-in random method (Unity.Random.Range) or any other's can generate the same results for an amount of times, the script specifically deals with this problem by creating two arrays, one for all models, one for those models that have been randomized before. Once a value is chosen randomly, it is added to the loaded array, which would be checked and removed from the main array in the next time the random occurs. If the loaded array is full, it will pop out its first element to add back into the main array. Currently, the loaded array has the length of 3 elements (maximum 3 times guarantee different values).

**UIChangeBGColor (KHUIChangeBGColor.cs):** The script to make background change color from time to time.

-- *Content Tool:*

+ *Brief Description:* The latest Content Tool version was dated back to December 1st, 2018 and has not been further updated since. The version offers a simple gameplay with only features as displaying now playing song_name, contents were loaded via a pre-downloaded configs during the splash scene. The configs link was a google drive shareable link and can be edited by Content Team for their purposes.

+ *Working with Content Team:* The Content Team would simply upload their contents (.mp3 files and .bin files) to the given links in the configs, then the tool would start the game with the contents they wish to test. All the effects, movements and rotations in the game would change according to each content in the list. The contents can be altered via each upload, or change the link inside the configs, or add new ones in the configs as well. Besides providing the links to download, the Content Team also has to scale the features of target_board_speed (low, medium, high) and number_of_fruits so the gameplay can be loaded safely.


## **3. Issues and Achievements:**
### *Issues:*
-- Too much time was spent on building the project, and it's not gameplay building. One of the author's first mistake was not implement the base framework first into the project. Instead, the author jumped right in to work with the gameplay on an individual project. Later on, when the project has been done quite a lot, the task of merging the base framework with the on-going project caused many troubles and time-wasted. Moreover, as the flow in the base framework, especially during the SplashScene (SplashScene.cs), is quite complex, the author also had to spend many work days to read and match the two projects together. These could have been avoided if the base framework was received earlier and implemented at the beginning. The loose time can be used to improve the gameplay and other features.

-- Another reason for the slow speed of the project was the author's limited in skills and experiences within this genre. As this project was also the author's first big project in the industry, there have been a lack in coding generation and modification. For example, the author was stuck with the initial gameplay for too long that cannot realize the flow the game needed and as a result, a day had to be spent to have the whole project thought thorougly and built again. There was an attempt to adapt, but the pace was rather slow hence the effort was not recognizable much. If it was not thanks to the team's support, especially the team lead's, the project could not have been finished.

### *Achievements:*

-- One of the most considerable achievement in this project is the movement of main objects in the game. As the base framework has offered the method to get notes data from file .bin, the task of synchronization the target_board's movement and rotation with the background music was done quite smoothly with the built-in method Transform.Rotate( ) of Unity. There were 4 key notes to determine the target_board's rotation: spin with low speed, spin with medium speed, spin with high speed and change spin direction (the last key note was to make the fruits jump) hence the author implements a function to compare their timeAppear with the background music audiosource playtime. At first, the comparison was strict as the playtime must be equal to the timeAppear for the according movement to be played. As Unity operates the game from frame to frame (with the delta time between each frame approximately 0.002s), the ask for comparing two exact moment was impossible. Thus later the author had to take on a different approach, with a much loosely comparison and also created an array to store all the notes have been checked (by this way, no notes would be missed as there were some shared the same timeAppear). To handle the fruits' movement, the author created a GameObject called FruitHolder that would act as a Global position holder for the fruit, so that the fruit can freely move back and forth its own local y-axis during the jumping process. As for the knives' movement, the throwing function was quite simple but tricky since it is needed to check if the launched knife has already made an impact (with the target_board or another knife) and only then it allows a new knife to be spawned. The impacts on target_board and other knives were detected with OnCollisionEnter2D, while the impact with fruits had to be recognized through OnTriggerEnter2D as the knife was meant to move through the fruit while the game still records that moment of impact. Also, the custom movement of the knives on the board when the target_board explodes was made with AddForce( ) for direct movement and AddTorque( ) for rotational one. 

-- The other achievement was more of a personal feat to the author, as it was valuable lesson that the author has learned throughout the course of making the game. First and foremost, the author learned how to read from configuration files which are loaded either locally or online via the methods implemented within the base framework. The next lesson was improvement in coding styles, including ways to wrap up code for better management and ways to implement so that variables can be recycled and altered later on without causing many troubles. Last but not least was the flow of making the game. Through this project did the author really see how a proper flow for a game should work, from the very initial planning phase, to the first build of gameplay and to the final optimization after numerous modification. 


## **4. Future Work:**
Although the project was now wrapped up for good, there were still a few tasks that the author wishes to do:
-- Smoother gameplay: As the code was not totally optimized, there are still some segments of it cause the game to perform slowly in some devices. 

-- Better in transition: The level transition that occurs between each level, although have been modified and reworked many times, still leaves not quite a satisfaction to the author.

-- A better Content Tool version: As the project was closed in its final days, the Content Tool version was not updated as plan. 

-- And some other issues: such as knife model should be the same at Menu scene and in the next gameplay scene, custom weapon UI to be spawned according to the knife prefab, etc.


## **5. Acknowledgement:**
Only in a very short term (2 months), but the company, especially the Hyper Casual Newgame team, has helped and supported the author a lot. Without their advisory and guidance, the project would not have come this far. Thus, thank you all.




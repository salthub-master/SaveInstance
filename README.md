[Rain] SaveInstance - Place Copier for Elysian (LocalScripts, Terrain, etc.)


Hi!

This is a small open-source project I've been working on over the past few days. It serves a simple purpose, and that is to copy games.
I know a lot of them already exist (Dex has one), but this is for example, if you're too lazy to open up Dex each time to just save the game (plus it offers some cool documentation!!).

FAQ:

Q: What can it copy?
A: It can copy all kinds of parts (basically the entire map), localscripts, modulescripts, terrain, and a lot more.

Q: What does it copy?
A: It copied all the contents in Workspace, Lighting, ReplicatedFirst, ReplicatedStorage, StarterPack, StarterGui, and StarterPlayer.

Q: Who made this?
A: I made this entirely by myself with no help.


This was meant entirely for elysian, and so it will probably not work if you use another exploit.

I've published this as a script, so you can call GetObjects on it, and can loadstring on it's source from there:

[code]

loadstring(game:GetObjects("rbxassetid://519083652")[1].Source)()

[/code]

It is open-source so you can view it as much as you like, and see how it works:

[code]

[/code]

What it generates:

- A .rbxl file that you can open.
	- All the copied services, each in a model.
	- A GAME_DOCUMENTATION localscript that tells you information about the saving, and of the services it copied.
	- If any errors:
		- An ERROR_LOGS localscript which explains the errors.
	- If any terrain:
		- A SavedTerrain object.
		- A TERRAIN_DOCUMENTATION localscript which explains how to use the terrain.

Most of the stuff is pretty self-explanatory. I give information in the TERRAIN_DOCUMENTATION of how to load terrain (if there is terrain in the game you copied).

[spoiler=How it works:]

This takes advantage of several things that elysian has to offer, mainly decompile() and saveinstance().

The first thing the script does, is loop through all the services that it will copy, and makes a copy of them. It then parents them to the main model.
Afterwards, it will run through the entire copied model and search for any localscripts/modulescripts which it will attempt to decompile via decompile().
All copying/decompiling code is run through a pcall() block so that it doesn't error.

Once it's done, it will simply save the entire model as a .rbxl file through saveinstance().

It's pretty simple. There are of course some extra features/things the script does which are kind of hard to explain, but I'm sure you can understand by looking through the code.

[/spoiler]

I hope you enjoy this contribution! If you have any questions, please reply to this thread, or send me a PM.
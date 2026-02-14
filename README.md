# ZDoom-Multiplayer-Tutorial
A tutorial explaining how to use ZDoom-based sourceports like GZDoom or UZDoom to play multiplayer Doom. Naturally, this is very useful for heavily modded playthroughs with friends. Due to it's superior performance and maintenance, UZDoom is used in all the examples.

Fortunately, to play multiplayer Doom, you don't need port forwarding, all you need is to be connected on the same LAN network via ethernet cable, Hamachi, Radmin VPN, your choice. Personally I use Tailscale, it's cross-platform and works like a charm; doesn't even reveal your real IP and works across the globe (I use it to play Doom and Sonic Robo Blast 2 from across the continent with my friend from the USA, so the networking is really good!). We must run a command to start the server and let the other player join. Fun fact, Zandronum does run these commands for you and that's how their servers function, but sadly for ZDoom-based source ports you have to do this manually. It's a mouthful, I know, but trust me, explaining how to do it is way harder than it actually is; and you'll get to play nearly any mod you could ever want with your friends once you learn this. With some patience, you'll be the cool guy of your friend group for sure with this new skill! But enough preambles. To use the command, here's what you need to do. If you use Windows, open up CMD and head to your UZDoom directory. You must use cd.. to go back a folder, and cd [foldername] to enter one. Use this to navigate to the folder that contains UZDoom.exe. However, if you're on Linux, you can use the command from any directory. Once you "are in the folder" and able to use the command, you can enter it; here's an example command and the explanation below.

uzdoom -iwad "doom2.wad" -config "yourdoomconfig.ini" -file "examplemodthatyoulike.pk3" "exterminationday.wad" -host 2 -skill [1-5] -dmflags (your choice) -dmflags2 (your choice) +playerclass "name"
So the -iwad attribute chooses the main game, you can pick anything ranging from doom.wad, doom2.wad, tnt.wad, plutonia.wad,heretic.wad, hexen.wad, hacx.wad, hacx.wad, harm1.wad, the list goes on... then, the -file attribute will add any PWADS/Mods you want to run alongside the main game. These are anything ranging from mapsets, to gameplay mods, and anything else! Make sure the filenames match your mods', and for the file order to be equal on both PC's when they run the command.

If you run certain mods like Brutal Doom or others that require different bindings and you don't want to change them every time you use a different modlist, you can use a custom config with the attribute -config. It'll have everything you've set up on it (playername, controls, gameplay options, etc). If it doesn't exist, it will be created; but remember that this is optional and you can ignore the config attribute if you want the same one to be used every game, which is normal.

There's also another optional attribute, you can add -dmflags (insert dmflags) to customize your game better; you just need to head into UZDoom's settings, gameplay settings and change everything to your liking. Respawns, co-op weapons and monsters, jumping, death behaviour, etc... then copy the "dmflags" number on the top of the tab and insert it into your command. With your own numbers, it should look like: "-dmflags 11111". You can also do this with the co-op settings tab, -dmflags2 5463 and that would let you customize your experience completely. I use it to disable deathmatch weapons from spawning, enable fast monsters, disable player telefragging, enable item sharing and the like; but you don't need to add these attributes if you think doom's default settings are good enough for your playthrough.

The skill attribute is the difficulty. -skill 1 is I'm too young to die and -skill 5 is nightmare. If you don't add this attribute, the game will default it to 3 (hurt me plenty).

The -host [number] attribute is the player limit, set the number to match the amount of people you'll be playing with.

Lastly, the +playerclass "playerclassname" attribute is for very modded playthroughs, where you want to pick different characters. In my case, I use it to pick the Tactical class on Brutal Doom, and my friend uses it to pick the rifle start class; this can be used in games like Heretic and Hexen as well though you won't be needing it in vanilla doom. If you don't know what the playerclass you want is named, head into the game with your mods loaded, go to the player setup, and browse the classes to find the one you want to play as. It's name will be the one you have to type into the command.
Note that without these optional attributes, the bare minimum you'd need to run the game (albeit default and uncustomized) would be this command:
uzdoom -iwad "doom2.wad" -host 2

But that's only if you choose to skip the attributes.

Now, you need to get your friend to run a command as well. His will be different, as he needs to join you, not start a lobby. So his command should be:

uzdoom -iwad "doom2.wad" -join (Host PC'S IP address)

Remember, you need to be connected on the same LAN network and your friend needs to join your co-op game through your IP. Once you enter your host command, you will be stuck on a loading screen until your friend joins you. When they enter their command, the game will start. If you get desync issues and your games don't function correctly, make sure you loaded the same mods and your UZDoom versions match. That sounds like a basic "Oh, sure, that probably won't work because everyone says to do that" step, but trust me, if you desync that's most likely the issue. Some mods DO have desync issues even if the setup is perfect though (like Live Through Doom or older Brutal Doom versions), but in most cases, matching everything correctly will let you play those crazy campaigns with those crazy gameplay mods. Last time I did this, I used it to beat Legacy of Rust + Brutal Doom with my bestie, and the experience was immaculate.

And boom, you're playing Doom together! Remember my friend, this tutorial may have taken me like an hour to write, but you can do this in less than 5 minutes; 1 if you remember each step. If you're going through a long mapset, and you don't mind pistol starting but you want to continue where you left off; start the match normally and use "changemap mapxx" in the console for you and your friend to continue where you left off. If you DO mind pistol starting, you'll need to save your game. But that's a biiit more complicated than just adding one attribute to your command, so I'll get to that later.

But before I do, one last note is that you can alternatively use a .bat file on Windows or a .sh file on Linux to do this instead of a command line, but the choice is up to you. If you do want to make one of these scripts, simply write the command into your .sh/.bat file and save it; running it will run the host/join procedure and you'll be able to play in just a couple of clicks! Do know though, you must add the full file's path instead of just it's name, so a bat file file could look like this:

start gzdoom -iwad "C:\Games\Doom\doom2.wad" -config "C:\Games\Doom\yourconfig.ini" -file "C:\Games\Doom\examplemod.pk3" "C:\Games\Doom\exterminationday.wad" -host 2 -skill 4 -dmflags (your choice) -dmflags2 (your choice)

Your friend would need to do the same thing with his own script, or you can give him one.

start gzdoom -iwad "C:\Games\Doom\doom2.wad" -config "C:\Games\Doom\hisconfig.ini" -file "C:\Games\Doom\examplemod.pk3" "exterminationday.wad" -join (your ip address)

But that's entirely optional, and it's only necessary if you don't want to use the command line. And also, if you use Linux, you can skip the "start" option and use Linux paths instead of the Windows ones as I showcased above.

Finally, I'll explain how to save and load games... once you're loaded in, open the console and type in: "save [savename]". This will create a savefile on both PC's, make sure you're running the same mods and for everything to match before loading it. To load it, at the time of writing down your command, add the -loadgame [savename] attribute; note that both you and your friend have to do for it to work.

And one final comment on my part is that you can use these commands or .bat/.sh scripts without the -host (playercount) atrribute to launch your own modded instances of Doom in singleplayer. I use it to play heavily modded mapsets without needing to use a modloader app or frustratingly drag the files into GZDoom, but those script files are super useful both for single and multiplayer.

But that's all from me, I sincerely hope you find it useful, and feel free to ask me any questions if you have any! <3

I hope you and your friend have an awesome time ripping and tearing through demons! Good luck, and may the force be with you ;)

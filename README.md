# Wizard101LuaRCE
Simple wizard101 Lua RCE method.
This method is detected, and will get you banned. But you can still Execute your own Lua code, and communicate with the server with Lua. I recommend reading through other scripts in the scripts folder to get a better idea of what you can do.

1. Backup Root.wad
2. Decompile Root.wad with WizWadWiz.exe (https://github.com/11a10318/WizWadWiz/releases/tag/0.6.1)
2. Navigate to the Tutorials folder, and then into the API folder.
3. Open up TutorialUtility.lua and scroll down to the bottom.
4. Find the SkipTutorial() function. 
5. Your if statments to RCE with are at lines 797, 799 and 806.
6. Use WizWadWiz.exe to recompile your wad
7. Navigate to your GameData folder and drop your modified Root.wad in
8. Navigate to your installation bin folder and create a file named log.txt 
9. Next, open the game bypassing the patch client by navigating to your installation bin folder in command prompt and typing the command "WizardGraphicalClient.exe -l login.us.wizard101.com 12000 -P 1 -K 1 -M 1 -EF_OVERFLOW -EF_UNDERFLOW -G log.txt" -- not all these paramaters are neccesary, but they worked, and have since remained my control paramaters for whatever tests I run, it just enables some backround debugging features. And will generate a log to your file your created earlier. 
10. Once your logged in, create a new character. start the tutorial, when you reach the owl press the skip tutorial button, and for example if your code you wanted to run was

Server("SetLevel", "120");
Server("SetPrimarySchool", "Storm");
Server("AddSpell", "Thunder Snake");

You would see the appropriate responses from the server in your chatbox, its pretty neat. You will then be swiftly banned. If you don't see a skip tutorial button, hit continue and let the game crash and try again, it will be there.

I have only been banned trying to modify stats. You can do other things and not be banned. You can even modify the minigames code, and enable alot of debugging logs. You can use the Lua Engine to make yourself a CSR (customer support) account that can run commands like this though, they've already made the code, you just need to port it and change it around.

The game knows when your wad is corrupt and crashes when you try to continue with the tutorial, this is why I had to build it into the SkipTutorial() function and thus being one of only vulnerable positions to inject. 

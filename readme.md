--[[
Developer notes : 
- I will not provide template abilities for this current release and probably not for foreseeable future, so it is a MUST that you somewhat read this tutorial / guide regarding this stand creator.
- You are directly responsible and held accountable for any clips/bans/etc.. You are advised to not use this script on accounts that you care about.
- If you have any questions or concerns regarding this script, please contact me (https://discord.com/invite/jojoW) at #support.
]]--

--/ DOCUMENTATION OF THE FUNCTIONS \--

--/ 1. Create('COMMANDNAMEHERE', function() --/ This will create an chat command / replace COMMANDNAME inside the brackets with your desired command name.
--/ 2. CreateAction('LOOPNAMEHERE', function() --/ This will create an action this should be placed before (1).
--/ 3. CreateKeybind('KEYBINDHERE', function() --/ This will create a keybind command, it'll only work on the stand (Refer to "https://developer.roblox.com/en-us/api-reference/enum/KeyCode") for keybinds.
--/ 4. CreateTargetAbility("COMMANDNAMEHERE", function() --/ This will use an command on a target you choose / eg..(Attack! Bacon)
--/ 5. CreateLoop("LOOPNAMEHERE", function() --/  This will begin looping the arguments specified until stopped (5).
--/ 6. StopLoop("LOOPNAMEHERE") --/ This will stop the specified loop (4).
--/ 7. Stand.Action = "LOOPNAMEHERE" --/ This will begin the specified loop/action that you have created (Refer to 2). Stand.Action = "" will essentially stop the action.
--/ 8. Play(ID, true) --/ This will begin playing the specified audio in the first argument, The second argument true/false + If the second argument is set to false it'll begin looping the audio.
--/ 9. Stop() --/ This will stop any audios from playing.
--/ 10. AnimPlay(ID,SPEED) --/ This will begin playing the specified animation (ONLY DH / ROBLOX ANIMATIONS), SPEED will control the animationspeed (Default is 1).
--/ 11. AnimStop(ID,SPEED) --/ This will stop playing the specified animation, SPEED will control the stopping speed (Default is 1).
--/ 12. Chat("TEXTGOESHERE") --/ Will chat the specified text in the first argument (stand cry / eg.. following you master).
--/ 13. Buy.Item() --/ Will buy the specified melee (make sure you have enough cash). eg.. Buy.Knife(), Buy.Bat(), Buy.StopSign(), Buy.Shovel(), Buy.Pencil(), Buy.Nunchucks(), Buy.SledgeHammer(), Buy.Grenade(), Buy.Flashbang(), Buy.Boxing(), Buy.Default().
--/ 14. Hit(true) --/ If the first argument is set to true it'll do a charge attack + If the first argument is set to false it'll do a quick punch.
--/ 15. Crew(true,ID) --/ If the first argument is set true it'll join the crew specified(ID) + If the first argument is set to false it'll leave any current crew.
--/ 16. DropMoney(Amount) --/ This will drop the amount of money specified.
--/ 17. GetNearest() --/ This will get the nearest enemy player.
--/ 18. Equip(Tool) --/ This will equip the specific tool eg.. "Combat", "Wallet", [Knife], [Bat], [StopSign], [Shovel], [Pencil], [Nunchucks], [SledgeHammer], [Grenade], [Flashbang] --/ In-case your item is not on this list use darkdex.
--/ 19. Unequip() --/ This will unequip any currently equipped tools.

--[[ -- IGNORE THIS LINE

--/ DOCUMENTATION OF EXAMPLES \--  

--/ 1. This will print the username of the target nearest to the owner.
Create("test", function()  --/ This will create an command.
    local Target = GetNearest() --/ Have an local Target = GetNearest() 
    print(Target.Name) --/ This will print the nearest player relative to you.
end) --/ Always remember end) on every command.

--/ 2. This will create an summon action / we will detail in this part what we during while it's summoned.
CreateAction("Summoned", function() --/ It's good practise to name the action in relation to what it is doing.
    STAND.Character.HumanoidRootPart.CFrame = OWNER.Character.HumanoidRootPart.CFrame*CFrame.new(1,1.85,2.5) --/ This is the position of your stand relative to the owner. (xyz + edit the numbers) 
end) --/ Always remember end)

--/ 2,5. This is a chat command same as in (1), we will use this to trigger Summoned. (2)
Create("Summon!", function()
    Stand.Action = "Summoned" --/ This is where we choose the action, we have made "Summoned" so we'll pick that.
end)

--/ 3. This is a command to stop the action. (2)
Create("Desummon!", function()
    Stand.Action = "" --/ We leave it as blank to stop the action. / You should not make a action with a blank name.
end)

--/ 4. This will make the stand teleport the target.
CreateTargetAbility("Goto!", function() 
    Stand.Action = ""  -- We will stop any current actions from interfering with this command.
    local Target = Stand.Target
    STAND.Character.HumanoidRootPart.CFrame = Target.Character.HumanoidRootPart.CFrame
end)

--/ 5. This will make the stand constantly attack around the player, Remember to always create the action before command (Refer to 2).
CreateAction("Aura", function() 
    local RANDOM = math.random(-10,10)
    STAND.Character.HumanoidRootPart.CFrame = CFrame.new(OWNER.Character.UpperTorso.Position.X + RANDOM, StandUser.Character.UpperTorso.Position.Y + RANDOM, OWNER.Character.UpperTorso.Position.Z + RANDOM)
    Hit(false)
end)  

--/ 5.5. Same as in (2.5).
Create("/e aura", function()
Stand.Action = "Aura"
end)

--/ 6. This will purchase an item utilizing the buy function.
Create("Knife!", function()
Buy.Knife() -- Refer to (10)
end)

]]-- IGNORE THIS LINE

--/ STAND NAME & ABILITY IDEAS : \--
-- https://jojowiki.com/List_of_Stands

--/ STAND OUTFIT IDEAS : \--
-- https://www.roblox.com/games/9714571746/JoJos-Bizarre-Collection 

--/ JOJO SOUND EFFECTS : \--
-- https://www.roblox.com/develop/library?CatalogContext=2&Subcategory=16&CreatorName=jojoaudio&SortAggregation=5&LegendExpanded=true&Category=9
-- https://www.roblox.com/develop/library?CatalogContext=2&Subcategory=16&CreatorName=Tsuagon&SortAggregation=5&LegendExpanded=true&Category=9

--/ USEFUL SOURCES FOR BEGINNERS \--
-- https://developer.roblox.com/en-us/articles/Understanding-CFrame
-- https://developer.roblox.com/en-us/learn-roblox/coding-scripts
-- https://scriptinghelpers.org/
-- https://youtube.com/playlist?list=PLw1uWqQBDcgjKqFjPNgtVtBNx3xTGz-l7
--/---------------------------------------------------------------------------------------------\--

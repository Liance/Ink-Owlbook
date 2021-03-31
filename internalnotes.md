- Internal notes
Note to Lynn - these probably won't be useful for you, feel free to ignore them. The last time I updated these docs, it was mid-2020 ish (I think).

    Stuff a lot of people seem to ask for
    - Clarity on lists
    - How to save/load (it seems what often confuses people is the false perception that Ink is intended to be a one-stop creation tool, whereas middleware is usually required)
    - Clarity on using multiple Ink files within the same project.

    Current state of the doc:
    Currently at September 2018 in the Ink Channel.
    Most if not all of the main topics have been touched.
    The Design channel is still pending.
    I will not be archiving the contents of the writing channel, lest I go insane.

    Explore these links later:
    [https://heavens-vault-game.tumblr.com/post/168006582140/ink-tip-stable-shuffling-for-choice-text](https://heavens-vault-game.tumblr.com/post/168006582140/ink-tip-stable-shuffling-for-choice-text)
    (useful pattern for producing "stable"  choice text that varies randomly)
    search for "inbuilt"

    I need to integrate [this useful conversation about threading and tunneling](https://discordapp.com/channels/329929050866843648/329929390358265857/644866106191904788).

    Various Deities of Ink
    paulloz (gonna be mostly ink dev stuff though, I think)
    lilytastic
    ringlas
    wetcircuit
    GrantRobertsArt
    Oddle

- Stuff I want to cover

    ### Potential writeups

    [https://discordapp.com/channels/329929050866843648/329932369530454016/630703977092087818](https://discordapp.com/channels/329929050866843648/329932369530454016/630703977092087818) - string to list functions

    ---

    A conversation about design patterns for tracking stamina and status in adventure type games.

    [https://discordapp.com/channels/329929050866843648/329929390358265857/420616289967538206](https://discordapp.com/channels/329929050866843648/329929390358265857/420616289967538206)

    5:22 PM]**joningold**:On Sorcery we did a function for reducing stamina; with a check; if you fall below zero it would print death text and print the line >>> DEATH which we picked up in the output parser and caused the game to stop

    [5:22 PM]**joningold**:That’s not what I would do now tho

    [5:23 PM]**joningold**:I’d use a tunnel -> damage(n) -> which prints nothing but if you die inside that tunnel

    [5:23 PM]**joningold**:Then I’d use ->-> dead , which is the ink for “return from tunnel but go somewhere else”

    [5:23 PM]**joningold**:And handle post death text there (and -> END)

    [5:24 PM]**joningold**:Note we also had two damage functions “hurt” and “harm”; the difference being that harm wasn’t allowed to kill you, so you never died of a petty scrape on the knee

    [5:24 PM]**joningold**:It simply wouldn’t dock a point if you didn’t have one to spare

    ---

    **Evaluate Function**

    So as far as I know, this doesn't appear anywhere in the official documentatino.

    [https://discordapp.com/channels/329929050866843648/329929390358265857/42071296471125197](https://discordapp.com/channels/329929050866843648/329929390358265857/420712964711251971)

    Basically, EvaluateFunction lets you call an ink function from C#. 

    10:43 PM]**joningold**:I think it’s EvaluateFunction (but I’d have to look it up)

    [10:43 PM]**joningold**:You can pass in parameters and get back a return value as well as text content (which isn’t added to the main output stream)

    [10:44 PM]**joningold**:We use that for HV’s map screen; each location has a function that reports the current description of a location and a knot to go to if it’s chosen

    [10:44 PM]**joningold**:It’s really nice being able to get both!

    ---

    **Inventory Stuff**

    [5:00 PM]**Lee**:Has anyone here ever tried to make like an inventory system in ink?](https://discordapp.com/channels/329929050866843648/329929390358265857/427859382383018004)

    [5:02 PM]**Lee**:I have like this one proj i started in Twine and I thought about for like ever about plugging it into ink but i was kind of clueless on like how to code a seperate place for the inventory system? Like idk. i think im overthinking it. Someone here has constructed an inky system that was almost like a twine game where they made separate buttons to like explore a place and then pursue conversation

    ---

    [5:04 PM]**paulloz**:I think I saw someone do that a while ago

    [5:05 PM]**paulloz**:but I don't remember who

    ---

    [5:08 PM]**Lee**:omg so many "like"s sorry if i kill anyone brain cells with that post

    [5:08 PM]**Lee**:I think it would make sense to just make seperate docs I guess

    ---

    [6:27 PM]**Lee**:Oh i searched through the chat and i think i found what i wanted to knw

    ---

    **March 27, 2018**

    [11:42 AM]**joningold**:It super depends on what you want your system to be able to do. In the simplest case where you get items and they open up choices; use a LIST

    [11:42 AM]**joningold**:But if you want to be able to, say, explore your inventory items in parallel to doing the story, in pure ink, that’s going to get complicated

    ---

    ### I'm really new to scripting, but I want to make a game in Ink! How should I get started?

    Hey, happy to have you! Here's some handy tips collected from a bunch of users.

    9:06 PM]**colin_coin_coin**:i would suggest to follow each step on this page [https://github.com/inkle/ink/blob/master/Documentation/WritingWithInk.md](https://github.com/inkle/ink/blob/master/Documentation/WritingWithInk.md)

    [9:06 PM]**colin_coin_coin**:copy paste the small examples

    [9:06 PM]**colin_coin_coin**:and try to modify them a bit

    see what changes/how it works

    [9:07 PM]**colin_coin_coin**:the intercept is like a whole small game so it can get confusing as you'll find a lot of ink practices in there

    but eventually you'll get there and i hope it will all make sense to you

    most people on here come from a Twine background or no background at all, so we've all been confused at some point, don't worry

---

## Commenting on game state from anywhere in the Unity game

...Use an ink function. You can call them on demand from the game side without touching the story’s current “position”; they can return text and / or output.

This is how we do Aliya’s remarks about moons on the map in Heavens Vault (and about a jillion other places in that game too).

Use story.EvaluateFunction(“func_name”)

```jsx
story.EvaluateFunction(“func_name”)
```
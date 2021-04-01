
# Doc writing notes

A useful pattern/tip template for writing out sections

### Pattern Template

- An introduction to the pattern in broad strokes.
    - How is the pattern useful for an Ink game?
    - Give examples of the pattern from existent games and media (or real life).

**Working Example**

- Give a fully functioning example
    - The reader should be able to copy and paste it straight into Inky and run the example.
        - If an additional INCLUDE is required, it should be linked and immediately accessible, and it should be clearly stated that an INCLUDE is required.
    - Try to step the reader through what the code is doing.
        - You can refer them to other documentation for additional context, but there are some syntax usages in Ink that are non-obvious.

**Variations on a Theme**

- Give ideas and examples of how a reader might extend a pattern in complexity, or with other Ink features.
    - Give examples of how a pattern might be used in non-obvious ways.
- Relate this back to

**Sources and Additional Reading**

Sources: Originating discord links with the names of users involved in that discussion, links to blogs or articles (remember to note if the link is behind a paywall). Be careful when linking to personal blogs or links that might not be around in the long-term - absolutely do credit them, but make sure the reader has enough information to implement the pattern even if those links become defunct.

Additional Reading: Links to more more complex/abstract articles and talks related to the pattern at hand. 

**Base Concepts**

- A simple list of Ink syntax and concepts that get used in the working example. Try to be specific. For example, we might list "Threads, Lists, Stopping Shuffles"

### Additional style notes

- In introductions:
    - DO: reference familiar game design tropes - it's easy, and it's a reasonable way to relate a design pattern to players!
    - DO: reference examples *outside* of game design- some readers will definitely be coming from a non-videogames perspective, and we don't want to make this inaccessible to them. If we give the example of a central spaceship in a videogame as an example of a hub area, we want to back it up with the real life example of say, the central hub area connecting themed lands in a theme park.
    - DO: warn the reader if a pattern might not be immediately useful without mastery of more basic patterns: but remember to point them to the basic patterns that serve as fundamentals for the current pattern.

**Examples**

- DO: Cite if the examples are drawn from a specific discord conversation or blog, and link back to them in-line as well.
- DON'T: Use traditional game design tropes if there's another kind of example that also makes intuitive sense. Consider if you can use conversations and relations to drive your example before defaulting to games.
- DON'T: Accidentally use the names of core concepts from your pattern in your example.
    - A bad example of this can be found in this Ink Patreon post, where they talk about using "answerKeys" and "Keys" in order to offer Shuffled choices from a List.
        - The example they use ALSO involves an actual in-game key object, which gets VERY confusing.
        - The best option would have been to replace the "key" object with something like "shovel", to avoid the player getting confused about `answerKey` and `offer_answer(Key)` within the same article.

        ![Images/Untitled%207.png](Images/Untitled%207.png)

**In General**

- DO: Litter your notes with in-line links to documentation.
- DO: Capitalize basic Ink Concepts: ideally there shouldn't be namespace clashing anyway if we're being careful with how we write our examples, but it helps when the reader knows that Labels and Threads are "official" Ink vocabulary.
- 

- TODO: Build a dependency tree of Ink concepts and syntax. For example, Functions are built upon Knots, Tunnels are built upon Knots, Visit Counts require knowledge of Conditionals,, Lists require understanding of Conditionals (for booleans) and Variables...

TODO: Build a single page ink syntax reference.

[Ink Syntax Cheatsheet](https://www.notion.so/Ink-Syntax-Cheatsheet-7f627a2dd6594d9189fb072f0b6a7a49)
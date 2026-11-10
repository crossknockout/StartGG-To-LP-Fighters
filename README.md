# StartGG-To-LP-Fighters

A Windows desktop tool that pulls tournament data from the start.gg API and turns it into ready-to-paste Liquipedia wikitext — brackets, group tables, and prize pools. It generates standard legacy templates and can convert them to match2 format in one click.

This build is tailored for the Fighters wiki: the player name/flag database loads automatically on startup, and is a maintained fork of the original smashgg-to-liquipedia by spazer.

# First run

1. Extract the zip, launch smashgg-to-liquipedia.exe.
2. Get a start.gg token: Log in to your startgg account → Developer Settings → create a new token → Copy. Tokens expire after a year.
3. Click Auth on the app, paste your start.gg API token and close the window. 

# Basics 

Paste a start.gg tournament URL into the URL box. Any subpage works as long as the tournament slug is in the URL, e.g. https://www.start.gg/tournament/your-event/details.
Click Get Tournament (you can also paste a specific event URL and use Get Event instead). 

Events appear in the Tournament Explorer tree, grouped by status (completed, in progress, not started) and sorted by entrant count, and colored green / yellow / red.
Expand an event with the + to reach its phases, waves, and phase groups.

# Generate a bracket
Tick the checkbox next to a phase group (the lowest level of the tree), click Get Data and let it run.

For pools brackets, Top 16, 24, 32, 48 and 64: Put a legacy Liquipedia template in the Winners and Losers boxes — either paste them yourself, or pick a size from the Common Brackets dropdown to auto-fill both from the Bracket Templates folder.
Click Fill Bracket. The filled wikitext appears in the output box.

For Top 8: Select the Top 8 and click Get Data. It should automatically tick the "Output Finals" box and the template is already in place, so you can simply click Fill Bracket.

The generated code will automatically be converted to the respective match2 bracket as long as Auto-convert match2 is ticked. Or you can do it manually be unticking the box, then clicking Convert Output → match2.

# Paste into Liquipedia

Copy the output into the matching Liquipedia page (usually [[FULLPAGENAME]]/Bracket). Make sure the tournament sub-pages you create contain {{HDB}} after the title, as it links them to the overview.

For convenience, once the app converts a bracket the log will retain the generated bracket id so you can easily add it to "{{ShowBracket|id=}}" in the overview in order to embed the top 8.

# Generate pools

Tick a Phase or Wave in the tree.
Choose Bracket Pools or Round Robin to match the pool format.
Set Advance Winners / Advance Losers to how many players move on.
Click Get Data (for all pools in the phase) or Group Table (for a single selected group).

When generating pools always double-check if number of players advancing match what is on startgg. 


# Data tab (advanced)

Start / End pick which rounds of the queried data are used, Offset shifts rounds left (negative) or right (positive) in the destination template, Lock keeps those fields between queries, and Shift moves individual sets up or down. You almost never need these.

# Notes & caveats

The app only produces wikitext for you to review and paste; it doesn't edit Liquipedia. Always follow the wiki's editing and bot policies, always double-check the output.

The match2 convertor relies on brackets being manually "mapped" and is currently limited to the most commonly used brackets in recent FGC tournaments.

The conversion is offline and has no side effects; re-running Fill Bracket / Prize Pool Table gets the legacy code back. 

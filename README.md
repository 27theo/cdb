# cdb
A lightweight character database for Achaea.

## Download and install
1. Please see the releases page for the download. Make sure to choose the most updated version.
2. Install the .mpackage into Mudlet.

## Aliases
`cdb <name>`
 - Will retrieve a character's information from the API.
 
`wi <name>`
 - Will display a character's information.

`qwg`
 - Will retrieve information for every character currently online. Very useful for quickly adding new players.

`cla <name>`
 - Retrieves and displays the current class of a character.

`getm <class>`
 - Gets all current visible members of a class.

`anon`
 - Displays a list of players that you need to manually honors. 
 - This is necessary because of the ability to hide your house and city from the API, which some people enable.

## Configuration

 - All configuration is done in the script named "cdb CONFIG".
 - This makes changing settings quick and easy.

```lua
-- A snippet:
cdb.styles = {
  targossas = {
    color = "cornflower_blue",
    underline = false,
    italics = false,
    bold = false,
  },
```

## Usage

 - `cdb.db` is the master table.
 - To retrieve a character's information, refer to `cdb.db.name`

```lua
display(cdb.db.Romaen)
{
  city = "targossas",
  class = "priest",
  explorer_rank = "470",
  fullname = "Romaen Andeithus, Herald of Redemption",
  house = "harbingers",
  level = "87",
  mob_kills = "2347",
  name = "Romaen",
  player_kills = "233",
  xp_rank = "537"
}
```
 - This makes checking somebody's city easy. Instead of a function, which users of other packages might be used to, you can simply do the following.

```lua
-- For example, in a trigger:
if cdb.db[matches[2]].city == "targossas" then
  -- Run code.
end
```

 - If you really want, you can add your own functions.
```lua
function isTargossian(name)
  return cdb.db[name].city == "targossas"
end
```

## Possible future changes

1. In-built functions for the lazy. If people want cdb.isTargossian, cdb.isCityEnemy, et cetera, then I'll add them to the next release.
2. Upon honoursing somebody, to automatically retrieve their data from the API rather than having to use the `cdb <name>` alias.
3. Functions like cdb.isEnemy, using a politics table to guess whether or not a player is hostile based on city.

------

If you have suggestions, qualms, or want to report a bug, you can do so here, in game (Romaen) or on Discord (theo#7545).

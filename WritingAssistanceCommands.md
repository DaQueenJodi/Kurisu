## Markdown commands
Kurisu can create commands based on Markdown command files. Currently this supports the Assistance module and the tutorial group.

These commands are placed in the `cogs/assistance-cmds` directory. Tutorial commands are placed in `cogs/assistance-cmds/tutorial`.

### File format
A Markdown command file must follow this filename format: `commandname.console.md`. Valid console names are `3ds`, `wiiu`, `vwii`, `switch`, `wii`, and `dsi`.

A command can have multiple responses for different consoles. This means `commandname.3ds.md` and `commandname.switch.md` can exist. The resulting command will attempt to figure out which one to display in the channel, or the console names can be provided as arguments.

The file is split into two parts: a header and a body. The header ends once a double newline is found. All header keys are optional. Valid header keys are:
* `title`
* `url`
* `author.name` (if setting author fields, this is required)
* `author.url`
* `author.icon-url`
* `help-desc` (shows in `.help`, last one to be loaded is the one actually used)
* `aliases` (comma-separated, merged from all files for the command)
* `color` (RGB hex code, defaults to console color)
* `thumbnail-url`

A file can have no header keys if it starts with two newlines, but this is not recommended.

Any Markdown syntax supported by Discord embeds is supported. Notably this includes Markdown links, which normal user messages cannot use.

Headers define the start of a new embed field. There is only one header size, so any amount of `#` at the beginning will produce the same result.

### Example

This file should be called `mycommand.3ds.md` and placed in `cogs/assistance-cmds`:

```md
title: Title
url: https://example.com
author.name: Author Name
author.url: https://your-site.com
author.icon-url: https://upload.wikimedia.org/wikipedia/commons/b/b8/Anagallis_arvensis_2.jpg
help-desc: Help Description
aliases: thing,stuff
color: 93A0D5
thumbnail-url: https://upload.wikimedia.org/wikipedia/commons/e/e7/Starr_070302-5063_Merremia_tuberosa.jpg

Description goes here...

# My header
This goes in one section!
[Example url](https://3ds.hacks.guide/faq)

# My other header
This goes in another section!
```

When either `.mycommand` or the aliases `.thing` or `.stuff` are used:

<img src="https://github.com/nh-server/Kurisu/raw/main/resources/example-embed.png" width="230">

# Commands [Weechat](weechat.org)/IRC

**My config**: MacOS 14.5, Weechat 4.4.3, Terminal App. 

**Install**: `brew install weechat`

Most common package manager integrates `weechat`.

Open with: `weechat`.

[WeeChat quick start guide](https://weechat.org/files/doc/weechat/stable/weechat_quickstart.en.html)

## Set libera server
`/set irc.server.libera.addresses "irc.libera.chat/6697"`
`/set irc.server.libera.ssl on`
`/save`

Try connect with: `/connect libera`

### List options

`/fset`
`/server listfull`


## Check & modify common params

`/server listfull`

`/set irc.server.libera.OPTION "VALUE"`

**My params modified**: Username, Realname, nicks (`/set irc.server.libera.nicks "nick1,nick2,nick3"`), autojoin (`/set irc.server.libera.autojoin "#libera,#bitcoin,#bitcoin-otc,#bitcoin-dev,#ordinals"`), msg_part (when `/part`), msg_quit (when `/close` or end of connection).

`/unset irc.server.libera.OPTION`

`/save`

*If necessary* (reset current default): `/reload`

**Read a script** (not tested): `/script load nom_du_script.pl`


## Login (with NickServ)

My username: **gf2718**

`/msg NickServ REGISTER password email`

`/msg NickServ IDENTIFY username password`

## Move

To move between window: `CTRL+n` (Down), `CTRL+p` (Up).

To move into a channel: `fn+Arrows` (Up, Down Arrows).


## Channels

### Connect and join

To connect to a server (basic with Weechat).

`/connect libera`

`/join #channel` (First, `#libera` or `#bitcoin`)

List all available channels into a server: `/list`

### Info about a channel 

Info: `/msg ChanServ INFO #channel`

`[+Cnst]` meaning: 

- +C: This mode blocks messages containing mIRC color codes. It is used to keep the channel free from colored text, which can be a preference for readability or style consistency.

- +n: This mode ensures that messages cannot be sent to the channel by users who are not present in the channel. It's a common setting used to prevent spamming from users outside the channel.

- +s: This makes the channel secret. A secret channel does not appear in the channel list when someone performs a /list command. It's useful for privacy, keeping the channel hidden from general visibility.

- +t: This mode restricts the ability to change the channel topic to channel operators only. It prevents regular users from altering the channel's topic, maintaining control over the channel’s description or topic consistency.

Check current mode: `/mode #channel`

### Chat

To apostrophe someone: `Nickname: Hello, how are you today?`

To open a private chat: `/query Nickname`

To send a private message: `/msg Alice Hello, this is a private message!`

**List nicknames**: `/n #channel`

Command: `/n` is a shortcut for names. You can try `/help names` for more info.


### Modify a channel

If administrator. When you create a channel you are the default admin. 

Set topic: `/topic Channel description`

With admin you can lock everything with: `/msg ChanServ SET #channel MLOCK +Cnst`

To remove secret (for example) it's: `/msg ChanServ SET #channel MLOCK -s`

## Some useful commands

Check directories: `/debug dirs`

Filter who join, part, quit: `/filter add joinquit * irc_join,irc_part,irc_quit *`
To remove the filter: `/filter del joinquit`

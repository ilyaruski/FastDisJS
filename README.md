# FastDisJS
Very fast Discord.JS command proccessor with anti-spam feature.

![license MIT](http://img.shields.io/static/v1.svg?label=License&message=MIT&color=EE3456)
![speed fast](http://img.shields.io/static/v1.svg?label=Speed&message=FAST&color=3456EE)

# Installation
Just add 'FastDisJS.js' to root of your bot directory and have fun.

# Function usage
Arguments:
- "msg": message object that was received by discord.js
- "prefix": prefix for bot, can be array or string
- "cooldown": anti-spam cooldown in seconds
- "callback": callback function

# Callback requirements
Callback function will receive:
- Message object
- Command WITHOUT prefix
- Arguments for command

# Usage
**Note:** since v1.1 every command will be returned lowercase.

Basic example:
```js
const fd = require('./FastDisJS');
const discord = require('discord.js');

const bot = new discord.Client();
bot.login('token');

bot.on('message', msg => {
  let needProcess = fd.onMessage(msg, '!', 1, (_, command, args) => {
    msg.reply(`You sent a command: ${command} with arguments: ${args}`);
  });

  if (needProcess) {
    msg.reply('You sent simple message.');
  }
});
```

Also you can use it like:
```js
const fd = require('./FastDisJS');
const discord = require('discord.js');

const bot = new discord.Client();
bot.login('token');

function handleMsg(msg, command, args) {
  msg.reply(`You sent a command: ${command} with arguments: ${args}`);
}

bot.on('message', msg => {
  let needProcess = fd.onMessage(msg, '!', 1, handleMsg);

  if (needProcess) {
    msg.reply('You sent simple message.');
  }
});
```

---

**(v2.0+)** To use multiple prefixes you can use arrays, for example:
```js
...
fd.onMessage(msg, ['!', '?'], ...
```

---

So, this example will handle both "!help" and "?help".

**(v2.1+)** Easy command checker
```js
fd.onMessage(msg, '!', 1, (command, args) => {
  if (command.eq('help')) { // will handle !help
    // ...
  } else if (command.eq(['ping', 'pong'])) { // will handle both !ping & !pong
    // ...
  }
  // And so on...
});
```

# Showcase
Command:

![command usage](https://i.imgur.com/4jLd8qk.png)

Message:

![message](https://i.imgur.com/292rohI.png)

Nothing more yet, sorry.

# Contacts

Discord: V4#9495

Telegram: @ilyaruski

# ❔ wrus-api

Api discord.jsv12

<<<<<<< HEAD
<div align="center">
  <p>
    <a href="https://nodei.co/npm/wrus-api
/"><img src="https://nodei.co/npm/wrus-api.png?downloads=true&stars=true" alt="NPM info" /></a>
  </p>
    <a href="https://nodei.co/npm/wrus-api/"><img src="https://img.shields.io/npm/dt/wrus-api.svg" alt="NPM download" /></a>
=======
</div>
</div>

---

# 📝 Table of contents

-   [Installation](https://www.npmjs.com/package/reconlx#installation)
-   [Usages](https://www.npmjs.com/package/reconlx#-usages-click-on-it-for-more-info-on-how-to-use-it)
-   [Importing](https://www.npmjs.com/package/reconlx#-importing)
-   [Support](https://www.npmjs.com/package/reconlx#%E2%99%82%EF%B8%8F-support)
-   [License](https://apache.org/licenses/LICENSE-2.0.html)

---

## Installation

First install [Node.js](http://nodejs.org/). Then:

```sh
$ npm install wrus-api
```

## 🛠 Usages (Click on it for more info on how to use it)

<<<<<<< HEAD
-   [oldReconDB](https://www.npmjs.com/package/reconlx#oldReconDB) - the old way of storing data in mongodb
-   [reconDB](https://www.npmjs.com/package/reconlx/#reconDB) - the newest way of storing data in mongodb with cache
-   [DaysAgo](https://www.npmjs.com/package/reconlx#daysago) - check how many days ago was it using date format
-   [ReactionPages](https://www.npmjs.com/package/reconlx#ReactionPages) - simple pagination to make your "MessageEmbed" interactable.
-   [Confirmation](https://www.npmjs.com/package/reconlx#confirmation) - A reaction collector which returns the first emoji collected, can be used as a confirmation prompt.
-   [fetchTranscript](https://www.npmjs.com/package/reconlx#fetchtranscript) - Specify an amount of messages and it will return a discord chat template with messages, acts like a transcript.
-   [timeout](https://www.npmjs.com/package/reconlx#timeout) - Makes it easier to delete messages according to your needs
-   [chatBot](https://www.npmjs.com/package/reconlx#chatbot) - Replies to your messages in discord.
-   [hangman](https://www.npmjs.com/package/reconlx#hangman) - Hangman game now playable in discord.
-   [tictactoe](https://www.npmjs.com/package/reconlx#tictactoe) - TicTacToe game now playable in discord.
-   [GiveawayClient](https://www.npmjs.com/package/reconlx#giveawayclient) - Giveaway Client, easy way to manage your giveaways
-   [SnakeCord](https://npm.im/snakecord) - Snakecord with some minor error fixes as the mantainer isn't reading prs.

## ✈ Importing

```javascript
// Using Node.js `require()`
const recon = require("wrus-api");

// Using ES6 imports
import recon from "wrus-api";
```

## 🙋‍♂️ Support

Feel free to join the support discord server -> https://discord.gg/Kp6QqtHw

---

## 🔧 Usages

---

## DaysAgo

```javascript
// Example on checking how long the member's account was created.
// Import the package
const recon = require("wrus-api");
// Destructure the package
const daysAgo = recon.DaysAgo;
const discord = require("discord.js");

client.on("guildMemberAdd", async (member) => {
    console.log(daysAgo(member.user.createdAt)); // return days.
});
```

## ReactionPages

#### Example :

```js
// Example on checking how long the member's account was created.
// Import the package
const recon = require("wrus-api");
// Destructure the package
const ReactionPages = recon.ReactionPages;
// Use either MessageEmbed or RichEmbed to make pages
// Keep in mind that Embeds should't have their footers set since the pagination method sets page info there
const { MessageEmbed } = require("discord.js");
const embed1 = new MessageEmbed().setTitle("1");
const embed2 = new MessageEmbed().setTitle("2");
// Create an array of embeds.
const pages = [embed1, embed2];
// Change pages when sending numbers.
const textPageChange = true;
// Create an emojilist, first emoji being page back and second emoji being page front. Defaults are set to  ['⏪', '⏩'].
const emojis = ["⏪", "⏩"];
// Define a time in ms, defaults are set to 60000ms which is 60 seconds. Time on how long you want the embed to be interactable
const time = 30000;
// Call the ReactionPages method, use the <message> parameter to initialize it.
ReactionPages(msg, pages, textPageChange, emojis, time);
//There you go, now you have embed pages.
```

#### Preview on a music list :

![preview](https://imgur.com/wduFcGP.png)

---

## Confirmation

```js
// destructure the package
const { confirmation } = require("wrus-api");
// Here is an example on using it in banning members.
message.channel.send("Confirmation for banning members").then(async (msg) => {
    // parameters used(which msg to react on, who can acess it, reactions, time(optional))
    const emoji = await confirmation(msg, ["✅", "❌"], 30000);
    if (emoji === "✅") {
        //if author reacts on check
        //delete the confirmation message
        msg.delete();
        //ban the member
        guildMember.ban();
    }
    if (emoji === "❌") {
        // if author reacts on cross
        // delete the confirmation message
        msg.delete();
    }
});
```

---

## fetchTranscript

```js
// destructure the package
const { fetchTransript } = require("wrus-api");

// here is how you use it

// template
// fetchTranscript(message: any, numberOfMessages: number, sendToAuthor: boolean)

// returns buffer

//example
module.exports = {
    name: "transcript",
    run: async (client, message) => {
        fetchTranscript(message, 5).then((data) => {
            const file = new MessageAttachment(data, "index.html");
            message.channel.send(file);
        });
    },
};
// it will fetch 5 messages in the current channel.
```

### Preview on a general chat

![preview](https://i.imgur.com/CB1a6eD.png)

---

## timeout

```js
// destructure the package
const { timeout } = require("wrus-api");

// example

const messageToDelete = await message.channel.send("Hello There 👋");

// using the method
// template => timeout(message: who can acess, msgToDelete: which message to delete,time: time before the emoji gets deleted)
timeout(message, messageToDelete, 5000); // only message.author can areact, messageToDelete is going to deleted if collected reactions, if no reactions after 5 seconds the reaction will be removed.
```

### Preview

![preview](https://i.imgur.com/EV8WZja.gif)

---

## chatBot

```js
const { chatBot } = require("wrus-api");

/** @parameters
 * message, message.channel
 * input, input to give
 */

// example

chatBot(message, args.join(" "));
```

### Preview

![preview](https://imgur.com/DeThtZJ.png)

---

## hangman

```js
//importing
const { hangman } = require("wrus-api");

// parameters
/**
 * @name hangman
 * @param {Object} options options
 * @param {String} [options.channelID] channel to send to (channel.id)
 * @param {any} [options.message] parameter used for message event
 * @param {String} [options.permission] required permission to use this command (optional); default set to everyone.
 * @param {String} [options.word] word that needed to be guessed
 * @param {any} [options.client] client used to defined Discord.Client
 */

// making hangman
const hang = new hangman({
    message: message,
    word: args.slice(1).join(" "),
    client: client,
    channelID: message.mentions.channels.first(),
});

// starting the game
hang.start();
```

### Preview

![preview](https://imgur.com/GSRHlRr.png)

## tictactoe

```js
//importing
const { tictactoe } = require("wrus-api");

// parameters
/**
 * @name tictactoe
 * @param {Object} options options
 * @param {any} [options.message] parameter used for message event
 * @param {any} [options.player_two] second player in the game.
 */

// start the game

var game = new tictactoe({
    message: message,
    player_two: message.mentions.members.first(),
});
```

### Preview

![preview](https://imgur.com/lxKhF1b.png)

---

---

---

---

# GiveawayClient

## Initialising the client

```js
const Discord = require('discord.js')
const client = new Discord.Client();
const { GiveawayClient } = require('wrus-api');

  /**
   * @name GiveawayClient
   * @kind constructor
   * @param {Client} client
   * @param {Object} options Options
   * @param {String} [options.mongoURI] mongodb connection string
   * @param {String} [options.emoji] emoji for reaction (must be a unicode)
   * @param {String} [options.defaultColor] default colors for giveaway embeds
   * @description Initiating the giveaway client
   */

const giveaway = new GiveawayClient(client, {
  mongoURI?
  emoji?
  defaultColor?
});

module.exports = giveaway;
```

## Methods

### start

```js
/**
 * @method
 * @param {Object} options options
 * @param {TextChannel} [options.channel] Channel for the giveaway to be in
 * @param {Number} [options.time] Duration of this giveaway
 * @param {User} [options.hostedBy] Person that hosted the giveaway
 * @param {String} [options.description] Description of the giveaway
 * @param {Number} [options.winners] Amount of winners for the giveaway
 * @param {String} [options.prize] Prize for the  giveaway
 */
```

### end

```js
/**
 * @method
 * @param {String} MessageID Message ID for the giveaway
 * @param {Boolean} getWinner Choose a winner?
 * @description End a giveaway, choose a winner (optional)
 */
```

### reroll

```js
/**
 * @method
 * @param {String} channel channel of the giveaway
 * @param {String} id message id
 * @param {Number} winners amount of winners
 * @description Change the winners for a giveaway!
 */
```

### getCurrentGiveaways

```js
/**
 * @method
 * @param {Boolean} activatedOnly display activated giveaways only?
 * @param {Boolean} all display giveaways of  all guilds?
 * @param {Message} message message if (all = false)
 * @description Get data on current giveaways hosted by the bot
 */
```
=======
-   [Giveaways]) - Easy giveaway system with mongodb as the database
-   [reconDB] - Storing data into mongodb with easy functions (`.get`, `.set`, `.delete`, `.push`), data are cached for faster response times.
-   [ModMail] - Easy way to setup a modmail with awesome customisations
-   [starboard] - A starboard system which doesn't fetch 100 messages everytime someone reacts lmfao
-   [pagination] - Easy and flexible way to paginate embeds with buttons!
-   [generateTranscript] - Easily generate a discord like transcript with an array of _[messages]_
-   [chatBot] - An easy chatbot without api key
>>>>>>> f73ddf3971c47a620ea69e0c6fa1bb89792482fb

### removeCachedGiveaways

<<<<<<< HEAD
```js
/**
 * @method
 * @param {Boolean} all Get data from all guilds?
 * @param {String} guildID guild id if all=false
 * @description Removes (activated = false) giveaways
 */
```
=======
ps: if you are looking for the old features, use `npm i wrus-api` instead!
>>>>>>> f73ddf3971c47a620ea69e0c6fa1bb89792482fb

# Mocy-Giveaways

Advance discord giveaways system with Support Slash/Message support

# Download

```cli
npm i git+https://github.com/JohnDavid30/mocy-giveaways
------ or ---------------------
yarn add git+https://github.com/JohnDavid30/mocy-giveaways
```

# Setting up

### Launch of the module

Required Discord Intents: `Guilds` and `GuildMessageReactions`.  
Optional Discord Privileged Intent for better performance: `GuildMembers`.

```js
const Discord = require('discord.js');
const client = new Discord.Client({
    intents: [
    GatewayIntentBits.Guilds,
    GatewayIntentBits.GuildMessages,
    GatewayIntentBits.GuildMembers,
    GatewayIntentBits.MessageContent,
  ],
});

// Requires Manager from mocy-giveaways
// for custom embed
// class CustomManager extends GiveawaySystem {
//   GiveawayStartEmbed(giveaway) {
//     let embed = new EmbedBuilder().setTitle(`Giveway Started`);
//     return embed;
//   }
//   GiveawayEndNoWinnerEmbed(giveaway) {
//     let embed = new EmbedBuilder().setTitle(`Giveway Ended No Winner`);
//     return embed;
//   }
//   GiveawayEndWinnerEmbed(giveaway) {
//     let embed = new EmbedBuilder().setTitle(`Giveway Ended Winners`);
//     return embed;
//   }
// }

// const manager = new CustomManager(client, {
//   embedColor: "Random",
//   pingEveryone: true,
// });

const manager = new GiveawaySystem(client, {
  embedColor: "Random",
  pingEveryone: true,
});
// We now have a giveawaysManager property to access the manager everywhere!
client.giveawaysManager = manager;

client.on('ready', () => {
    console.log('Bot is ready!');
});

client.login(process.env.DISCORD_BOT_TOKEN);
```

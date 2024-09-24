## Guidance

Answer the following questions considering the learning outcomes for

- [Week 02](https://learn.foundersandcoders.com/course/syllabus/developer/week02-project02-chatbot/learning-outcomes/)

Make sure to record evidence of your processes. You can use code snippets, screenshots or any other material to support your answers.

Do not fill in the feedback section. The Founders and Coders team will update this with feedback on your progress.

## Assessment

### 1. Show evidence of some of the learning outcomes you have achieved this week.

- **Learned how a bot written in my code can talk to a Discord server that only exists (as far as I am concerned) in Discord UI**

```js
const client = new Discord.Client({
  intents: [
    Discord.GatewayIntentBits.Guilds,
    Discord.GatewayIntentBits.MessageContent,
    Discord.GatewayIntentBits.GuildMessages,
  ],
});
```

- **Got more comfortable using methods and properties that are built into an API rather than being visibly defined in code that I have access to**

```js
export default {
  name: Events.MessageCreate,

  async execute(message) {
    handleMessage(message);
  },
};
```

- **Used dotenv for the first time!**

```js
import dotenv from "dotenv"; // Import dotenv using ES6 syntax
dotenv.config(); // Configure dotenv to load .env file
const discordToken = process.env.DISCORD_TOKEN;
```

### 2. Show an example of some of the learning outcomes you have struggled with and/or would like to re-visit.

- **I hate this code and want to be more mindful about pure functions and the single responsibility principle**

```js
// Function to handle messages
async function handleMessage(message) {
  if (message.author.bot) return;
  // If the user has started their message with !
  if (message.content.startsWith("!")) {
    // Clean the message content
    const cleanedMessage = await cleanMessage(message);
    // Get the OpenAI reponse to the message
    const AiResponse = await getOpenAIResponse(cleanedMessage);
    // Send that response to the channel of the original message
    replyDiscord(AiResponse, message);
    // If user has started their message with -
  } else if (message.content.startsWith("-")) {
    // Change the OpenAI personality to the message that the user has entered
    handlePersonalityChange(message.content);
  }
}
```

- **Reading documentation is difficult, and something I hope to get much better at**

- **It would be helpful to draw a diagram of how our app is working beforehand, as I didn't fully understand the task at first. This led me to install and set up Express for no reason at the start of the project.**

```js
const app = express(); // Initialize express

client.on("ready", () => {
  console.log(`Logged in as ${client.user.tag}!`);
});

//this line must be at the very end
client.login(discordToken); //signs the bot in with token

const PORT = 3000;
app.listen(PORT, () => {
  console.log(`Listening on http://localhost:${PORT}`);
});
```

## Feedback (For CF's)

> [**Course Facilitator name**]

Alexander

> [*What went well*]

Excellent. I like the short snippets that get straight to the point. You covered most of the important topics that were introduced this week.

> [*Even better if*]

Would be good to add some testing-related content as well as a bit of the project planning.

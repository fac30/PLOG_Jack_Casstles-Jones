## Guidance

Answer the following questions considering the learning outcomes for

- [Week 03](https://learn.foundersandcoders.com/course/syllabus/developer/week03-project03-server/learning-outcomes/)

Make sure to record evidence of your processes. You can use code snippets, screenshots or any other material to support your answers.

Do not fill in the feedback section. The Founders and Coders team will update this with feedback on your progress.

## Assessment

### 1. Show evidence of some of the learning outcomes you have achieved this week.

- **Used Express endpoints to serve data and to perform operations in app**

```js
// POST endpoint to allow changing the continent database
app.post("/continents", (req: any, res: any) => {
  // Extract the new continent from the request body
  const newContinent = req.body.newContinent;

  console.log(newContinent);

  // Switch the country database to the new continent & respond with that continent as confirmation
  database = changeDatabase(newContinent);
  res.json({ newContinent });
});
```

- **Set up a Typescript config file**

```js
{
  "compilerOptions": {
    "target": "ESNext",
    "module": "CommonJS",
    "rootDir": "./src",
    "outDir": "./dist",
    "esModuleInterop": true,
    "forceConsistentCasingInFileNames": true,
    "strict": true,
    "skipLibCheck": true,
    // "moduleResolution": "Node",

    "allowSyntheticDefaultImports": true
  }
}
```

- **Used Supabase to store the data for our API**

```js
const getCountry = async (
  randomNumber: number,
  database: string
): Promise<{ country: string, code: string }> => {
  const { data } = await supabase
    .from(database)
    .select("country, code")
    .eq("id", randomNumber);

  return data[0];
};
```

- **Drew a diagram of the flow of our app before starting to plan effectively**

- **Used Insomnia to simulate HTTP requests to our API!!**

### 2. Show an example of some of the learning outcomes you have struggled with and/or would like to re-visit.

- **I still feel like this function/endpoint does too much**

```js
app.get("/question", async (req: any, res: any) => {
  // Get a random country object (name, code, etc.) from the specified continent database
  const myRandomCountryObject = await getRandomCountry(database);
  currentCountry = myRandomCountryObject.country; // Store the country globally

  // Fetch the flag URL for the random country
  const flagURL = await getFlagURL(myRandomCountryObject.code);

  // Get a response from OpenAI related to the random country
  const aiResponse = await getOpenAIReponse(myRandomCountryObject.country);

  // Log the flag URL and AI response for debugging purposes
  console.log(`THE FLAG URL IS ${flagURL}, THE AI RESPONSE IS ${aiResponse}`);

  // Respond with a JSON object containing the flag URL, AI response, the current country, and the database (continent)
  res.json({ flagURL, aiResponse, currentCountry, database });
});
```

- **I would've preferred to have our routes handled in a separate route handler file, as Jason is aiming for, instead of having such a large index.ts file**

- **As Jon noted in the [issue](https://github.com/fac30/PRO03_Riley_Josh_Jack/issues/21) he created on our repo, there is currently a bug where two people couldn't 'play' our app simultaneously as the second user would change the currentCountry for all users when they made a request for a new question**

## Feedback (For CF's)

> [**Course Facilitator name**]  
> [*What went well*]  
> [*Even better if*]

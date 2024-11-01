## Guidance

Answer the following questions considering the learning outcomes for

- [Week 08](https://learn.foundersandcoders.com/course/syllabus/developer/week08-project04-test-deploy/learning-outcomes/)

Make sure to record evidence of your processes. You can use code snippets, screenshots or any other material to support your answers.

Do not fill in the feedback section. The Founders and Coders team will update this with feedback on your progress.

## Assessment

### 1. Show evidence of some of the learning outcomes you have achieved this week.

Deployed to Render for the backend, utilising environment variables to mark the difference between development and production envionments

```ts
app.use(
  cors({
    origin: process.env.ORIGIN,
    credentials: true,
    methods: ["GET", "POST"],
  })
);
```

Revisited AWS CDK, assisting others in the cohort for with their deployment

```ts
const cdk = require("aws-cdk-lib");
const FE_1 = require("../lib/FE");
const BE_1 = require("../lib/BE");
const app = new cdk.App();
new FE_1.FE(app, "FE", {});
new BE_1.BE(app, "BE", {});
```

Used Google sheets to host a db for a personal / commercial project

```ts
useEffect(() => {
  const fetchData = async () => {
    try {
      const response = await fetch(
        "https://docs.google.com/spreadsheets/d/e/2PACX-1vQY-sZZXmGZQdBX1httEyxhEFNzznVqnGK_bNDPWbi4HZu0eickSRQDLhy0WdX6pgVYmUIAdAOczZBR/pub?output=csv"
      );
      const csvText = await response.text();

      const parsedData = parseCSV(csvText);

      setData(parsedData);
    } catch (error) {
      console.error("Error fetching data:", error);
    }
  };

  fetchData();
}, []);
```

### 2. Show an example of some of the learning outcomes you have struggled with and/or would like to re-visit.

Issues with Render.com spinning down the server due to inactivity :(

Issues with Supabase pausing the db if there is no activity for 7 days (fixed by using Google sheets)

I definitely need to explore testing more!!!

## Feedback (For CF's)

> [**Course Facilitator name**]  
> [*What went well*]  
> [*Even better if*]

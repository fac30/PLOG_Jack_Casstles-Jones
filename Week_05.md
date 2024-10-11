## Guidance

Answer the following questions considering the learning outcomes for

- [Week 05](https://learn.foundersandcoders.com/course/syllabus/developer/week05-project03-test-deploy/learning-outcomes/)

Make sure to record evidence of your processes. You can use code snippets, screenshots or any other material to support your answers.

Do not fill in the feedback section. The Founders and Coders team will update this with feedback on your progress.

## Assessment

### 1. Show evidence of some of the learning outcomes you have achieved this week.

- **Made an AWS account and used several of the AWS services:**

  - S3 Buckets
  - EC2 Instances
  - IAM
  - AWS CLI
  - CDK
  - Secrets Manager

- **In particular, used CDK via the AWS CLI to create a deployment pipeline that streamlined the AWS experience**

```ts
import "source-map-support/register";
import * as cdk from "aws-cdk-lib";
import { FE } from "../lib/FE";
import { BE } from "../lib/BE";

const app = new cdk.App();
new FE(app, "FE", {});
new BE(app, "BE", {});
```

- **Wrote an npm script that defined a `USE_AWS_SECRETS` environment variable**

```ts
 "server-aws": "USE_AWS_SECRETS=true nodemon",
    "server-dotenv": "USE_AWS_SECRETS=false nodemon"
```

**This was then used in the code to determine whether to pull the API keys in our .env file, our retrieve them from AWS Secrets Manager**

```ts
async function loadSecrets() {
  let supabaseURL: string;
  let supabaseKey: string;
  let openAIKey: string;
  if (process.env.USE_AWS_SECRETS === "true") {
    let response;
    try {
      response = await client.send(
        new GetSecretValueCommand({
          SecretId: secret_name,
          VersionStage: "AWSCURRENT",
        })
      );
      const secret = JSON.parse(response.SecretString);
      supabaseURL = secret.SUPABASE_URL;
      supabaseKey = secret.SUPABASE_KEY;
      openAIKey = secret.OPENAI_API_KEY;
    }
  } else {
    supabaseURL = process.env.SUPABASE_URL;
    supabaseKey = process.env.SUPABASE_KEY;
    openAIKey = process.env.OPENAI_API_KEY;
  }
  return { supabaseURL, supabaseKey, openAIKey };
}
```

### 2. Show an example of some of the learning outcomes you have struggled with and/or would like to re-visit.

- **I would've liked to have had more hands-on experience with testing using Cypress**

- **I also would've liked to have set up a proper CI/CD pipeline using GitHub Actions - I hope to do this on our upcoming projects from the beginning**

- **I think it's important that I spend more time with CDK to understand it properly. Some of the questions from other teams at the end of our presentation were difficult to answer!!**

## Feedback (For CF's)

> [**Course Facilitator name**]  
> [*What went well*]  
> [*Even better if*]

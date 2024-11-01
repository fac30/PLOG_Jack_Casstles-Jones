## Guidance

Answer the following questions considering the learning outcomes for

- [Week 07](https://learn.foundersandcoders.com/course/syllabus/developer/week07-project04-authentication/learning-outcomes/)

Make sure to record evidence of your processes. You can use code snippets, screenshots or any other material to support your answers.

Do not fill in the feedback section. The Founders and Coders team will update this with feedback on your progress.

## Assessment

### 1. Show evidence of some of the learning outcomes you have achieved this week.

- Implemented navigation between different pages using React router

```js
<BrowserRouter>
  <Routes>
    <Route path="/" element={<Home />} />
    <Route path="/about" element={<About />} />
    <Route path="/tutorprofile" element={<TutorProfile />} />
    <Route path="/tutors" element={<Tutors />} />
    <Route path="/subjects" element={<Subjects />} />
    <Route path="/auth" element={<Authentication />} />
    <Route path="/faq" element={<FAQ />} />
    <Route path="/careers" element={<Careers />} />
    <Route path="/termsconditions" element={<TermsConditions />} />
    <Route path="/contactus" element={<ContactUs />} />
    <Route path="/privacypolicy" element={<PrivacyPolicy />} />
    <Route path="/partners" element={<Partners />} />
  </Routes>
</BrowserRouter>
```

Used PassportJS for authentication

```ts
app.use(passport.initialize());
```

### 2. Show an example of some of the learning outcomes you have struggled with and/or would like to re-visit.

I would definitely like to revisit authentication as I wasn't fully involved

```ts
passport.use(
  new LocalStrategy(
    {
      usernameField: "email",
    },
    async (
      email: string,
      password: string,
      done: (error: any, user?: Express.User | false) => void
    )
```

## Feedback (For CF's)

> [**Course Facilitator name**] > [*What went well*] > [*Even better if*]

```

```

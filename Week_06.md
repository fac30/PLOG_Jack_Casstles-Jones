## Guidance

Answer the following questions considering the learning outcomes for

- [Week 06](https://learn.foundersandcoders.com/course/syllabus/developer/week06-project04-databases/learning-outcomes/)

Make sure to record evidence of your processes. You can use code snippets, screenshots or any other material to support your answers.

Do not fill in the feedback section. The Founders and Coders team will update this with feedback on your progress.

- Learn how to design and structure a database schema for the application (K10, S8)
- Implement CRUD (Create, Read, Update, Delete) operations for products and orders (S1, S3, S16)
- Acquire skills in using SQLite to manage and query relational data efficiently (K10, S3)
- Be comfortable with SQL syntax and how to use SELECT and INSERT queries (K10. S3)
- React
- Gain proficiency in using React to create dynamic and responsive user interfaces (K7, S2)
- Understand the use of state management in React to handle the shopping cart functionality (K11, S10)

## Assessment

### 1. Show evidence of some of the learning outcomes you have achieved this week.

- ## **Created a db schema and visualised it using [dbdiagram.io](dbdiagram.io)**

  ![Alt text](../PLOG_Jack_Casstles-Jones/assets/Screenshot%202024-10-14%20at%2016.29.39.png "a title")

- ## **Used SQL to insert data into our db**

```sql
INSERT INTO tutors (full_name, email, address, postal_code, phone_number, description, availability, fk_subject_id, fk_tutortype_id, img_source)
 VALUES
 ('Emily Smith', 'jane.smith@example.com', '456 Tutor St', '54321', '07700900002', 'Hi! I’m Sarah and I’m so excited to start teaching Computer Science. I have a Master’s from MIT and like to sneak everywhere.',
    '{"Monday": ["10:00-12:00", "14:00-16:00"], "Wednesday": ["10:00-12:00"], "Friday": ["14:00-16:00"]}', NULL, NULL,
    'https://images.unsplash.com/photo-1461039088886-b5c863279a0e?q=80&w=2970&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'),
    ('John Doe', 'john.doe@example.com', '123 Tutor Lane', '12345', '07700900001', 'I’m Boris, a mathematician with a degree from the University of Oxford. I like riding horses and travelling around Norfolk.',
    '{"Monday": ["10:00-12:00", "14:00-16:00"], "Wednesday": ["10:00-11:00"], "Friday": ["15:00-17:00"]}', NULL, NULL,
    'https://images.unsplash.com/photo-1556157382-97eda2d62296?q=80&w=2970&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D');

 INSERT INTO subjects (subject_name)
 VALUES
 ('Mathematics'),
 ('Physics'),
 ('Chemistry'),
 ('Biology'),
 ('English');
```

- ## **Created a db model to query our db**

```ts
const tutors = zubiDB.prepare("SELECT * FROM tutors");

const allRows = tutors.all();

const getTutorById = (index: number) => {
  return allRows[index - 1];
};

const getAllTutors = () => {
  return allRows;
};
```

- ## Created dynamic and responsive user interfaces using React, React Router and Tailwind, such as this Card component

```ts
import Button from "../../Button/Button";
import { useNavigate } from "react-router-dom";

const Card = ({ tutor }: CardProps) => {
  const navigate = useNavigate();

  const handleLearnWithMeClick = () => {
    navigate("/tutorprofile", { state: { tutor } });
  };

  return (
    <div className="mb-16 p-8 rounded-md font-helonik tutor-card bg-zubiGreen w-10/12 m-auto text-white flex flex-col items-center gap-7">
      <h3 className="text-2xl">{tutor.full_name}</h3>
      <img src={tutor.img_source} className="h-44 w-64 bg-white rounded-md" />
      <p className="font-sans leading-5">{tutor.description}</p>
      <Button
        onClick={handleLearnWithMeClick}
        label="learn with me"
        buttonType="cardButton"
      />
    </div>
  );
};
```

### 2. Show an example of some of the learning outcomes you have struggled with and/or would like to re-visit.

- I didn't spend as much time on testing as I would have liked to
- Some details of the db are still iffy to me, but not seriously so
- We don't currently have CRUD functionality in our app, looking forward to doing this next week!!

## Feedback (For CF's)

> [**Course Facilitator name**]
 
Alexander

> [*What went well*]  

You PLog explains quite well your journey with SQL, and so far looks great. I also like how you solidified your learnings on React. Well done

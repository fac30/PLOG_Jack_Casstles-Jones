## Guidance

Answer the following questions considering the learning outcomes for

- [Week 04](https://learn.foundersandcoders.com/course/syllabus/developer/week04-project03-frontend/learning-outcomes/)

Make sure to record evidence of your processes. You can use code snippets, screenshots or any other material to support your answers.

Do not fill in the feedback section. The Founders and Coders team will update this with feedback on your progress.

## Assessment

### 1. Show evidence of some of the learning outcomes you have achieved this week.

- **Used Context in React for the first time!**

```tsx
// Create a provider component
export const GameProvider = ({ children }) => {
  const [filledCountries, setFilledCountries] = useState<string[]>([]);
  const [userAnswer, setUserAnswer] = useState("");
  const [redFilledCountries, setRedFilledCountries] = useState<string[]>([]);

  return (
    <GameContext.Provider
      value={{
        setFilledCountries,
        filledCountries,
        setUserAnswer,
        userAnswer,
        redFilledCountries,
        setRedFilledCountries,
      }}
    >
      {children}
    </GameContext.Provider>
  );
};
```

- **Used conditional rendering and .map to render 467 🤯 interactable path elements**

```tsx
  return (
    <g
      onClick={() => {
        setUserAnswer(countryName);
      }}
      key={`${countryName}`}
      className={
        filledCountries.includes(countryName)
          ? `fill-yellow-400`
          : redFilledCountries.includes(countryName)
          ? `fill-red-500`
          : `fill-green-700 hover:fill-pink-300 cursor-pointer`
      }
      id={`${countryName}`} // Set the ID for each country
    >
      {pathsArray.map((path: string, pathIndex: number) => {
        return (
          <path
            id={`${countryName} ${pathIndex}`} // Unique ID for each path based on country and path index
            key={`${countryName} ${pathIndex}`} // Unique key for React's reconciliation process
            d={path} // Set the "d" attribute of the path (defining the shape of the country)
          ></path>
        );
      })}
    </g>
  );
};
```

- **Implemented game logic which also affects conditional rendering of the map**

```tsx
const checkAnswer = () => {
  console.log(`user answer is ${userAnswer}`);
  if (userAnswer === currentCountry) {
    addToFilledCountries(userAnswer);
    resetRemainingGuesses();
    increaseScore(true);
    getRandomCountry();
  } else if (remainingGuesses > 1) {
    decreaseRemainingGuesses();
  } else {
    resetRemainingGuesses();
    addToRedFilledCountries(currentCountry);
    getRandomCountry();
  }
};
```

- **Used the `fetch` API to make `GET` requests to our express server which then retrieved the data from our database 💖**

```tsx
  const fetchCountries = async () => {
    try {
      const response = await fetch(`http://localhost:3000/countries`); // Fetch data
      const data = await response.json();
      const dataArray = data.allCountries;

      setCountriesData(dataArray);
    } catch (error) {
      console.error("Error fetching new country:", error);
    }
  };
```


### 2. Show an example of some of the learning outcomes you have struggled with and/or would like to re-visit.

- **I originally struggled with putting all of the game logic into our context but managed to resolve this**

- **Struggled with getting our map inside a wrapper div to make it seem like the user was navigating around the box. Asked another team for help and Max and Jason were able to help 😍**


```tsx
  return (
    <div className="rounded-lg cursor-grab active:cursor-grabbing w-9/12 bg-white overflow-hidden shadow-lg mt-6 mb-8 m-auto">
      {/* SVG canvas with panzoom functionality */}
      <svg
        ref={canvasRef} // Reference to the SVG element for panzoom
        baseProfile="tiny"
        fill="green"
        stroke="white"
        version="1.2"
        viewBox="0 0 2000 857"
        width="100%"
        height="100%"
        xmlns="http://www.w3.org/2000/svg"
      >
        <g>
          {/* Render each country using the CountryGroup component */}
          {countriesData.map((country, countryIndex) => {
            return (
              <CountryGroup
                key={countryIndex} // Unique key for each country
                index={countryIndex}
                countryName={country.countryName} // Country name prop
                pathsArray={country.paths} // Array of paths for each country
              />
            );
          })}
        </g>
      </svg>
    </div>
  );
};
```

- **Some more best practices could have been followed, like putting our game logic in a seperate `.ts` file**

- **Our team definitely could have practiced more rigorous project management standards**

## Feedback (For CF's)

> [**Course Facilitator name**]  
> [*What went well*]  
> [*Even better if*]

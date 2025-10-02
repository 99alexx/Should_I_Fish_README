# Should_I_Fish_README

# Idea:
An application providing an index of how good the fishing is for the current day.

# What does it solve:
Collecting and analyzing data from different sources, providing the user with the necessary information all at the same place, aswell as creating a index (Initial scale of index 1-10, 1 = dont bother, 10 = Go fish NOW!).

# Primary data for index:
- SMHI | Air pressure
- SMHI | Water temp (if available)
- SMHI | Wind
- SMHI | Weather
- Time | Time of the day
- Huggtabell | Moon phases

# Starting goal:
- The initial goal is for the user to choose a location and get index and other relevant data for that specific location.
- Maybe implement being able to choose between different types of fish and get an unique index for each fish on the specific day.

# Further implementation
- Adding user for favorite fishing spots
- Users being able to logg successful days
- History analysis - fish caught at index A and not on index B or something like that

# Restrictions
- Only available in Sweden as for now.

# Tech stack
Begin with a web app - later possibly create mobile app

- Frontend: React, Vite, Tailwind, Figma
- Backend: Python Flask and for calculating index

# My thoghts during the project
2025-10-01
I decided to use Figma to create prototypes which will speed up the process of programming the UI. To start I've decided to create two pages (start and main page) 

After reading up on SMHI API and how it works I've decided, for now, to only use a dropdown meny to choose a location from. This is because SMHI has some demands: Keep the API calls to a reasonable amount and cache the data. So I've decided to use a number of predefined geolocations which will be fetched in intervalls of three hours, because that is the API:s update frequency.

The option I'm leaning towards is to fetch all the "kommuner" (290) 

2025-10-02
UPDATE - After some research I've decided to move from Python Flask and instead go with Next.js. This decision was made because when I started creating the prototypes in Figma, I created a starting page and started thinking of how I am going to push data between the two different pages. React does have routes but Next does provide this automatically for you, and in the end I can push the whole project (backend and frontend) together. I'm thinking of using Netlify for this. It just overall seems like a more suitible option for this type of project with increased SEO which is always nice but mostly because of faster and easier deployement + server-side rendering (which is really nice for this type of project). I will still use Python for the calculating algorithm.


# Workflow
- Create a basic UI
- Get backend up and running
- Fetch data from API and cache it
- Present the data
- Create index algoritm


- Fetch data
(THIS DIAGRAM IS NOT A TRUE REPRESENTATION OF THE PROJECT)
It was used early just for me to get my thoughts out on how it could/should/might look like
![diagram](images/fetchDiagram.png)

# notes TODO
- Dokumentera licensvillkor
- Make the app in english

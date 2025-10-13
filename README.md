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

- Frontend: Next.js, Vite, Tailwind, Figma
- Backend: ~~Python Flask~~ Python for calculating index, Redis for caching

# Updates and ideas during development
2025-10-01
I decided to use Figma to create prototypes which will speed up the process of programming the UI. To start I've decided to create two pages (start and main page) 

After reading up on SMHI API and how it works I've decided, for now, to only use a dropdown meny to choose a location from. This is because SMHI has some demands: Keep the API calls to a reasonable amount and cache the data. So I've decided to use a number of predefined geolocations which will be fetched in intervalls of three hours, because that is the API:s update frequency.

The option I'm leaning towards is to fetch all the "kommuner" (290) 

2025-10-02
UPDATE - After some research I've decided to move from Python Flask and instead go with Next.js. This decision was made because when I started creating the prototypes in Figma, I created a starting page and started thinking of how I am going to push data between the two different pages. React does have routes but Next does provide this automatically for you, and in the end I can push the whole project (backend + frontend) as one package. I'm thinking of using Netlify for this. It just overall seems like a more suitible option for this type of project with increased SEO which is always nice but mostly because of faster and easier deployement + server-side rendering (which is really nice for this type of project). I will still use Python for the calculating algoritm.

2025-10-03
Done with the start page, now on to the API / Backend part, before building the UI for the main page. I'm currently thinking of going with a Cache-Aside approach and use Redis as database. 

2025-10-(3-9)
I've created my own API which is used to fetch data from the open source SMHI API. In the API I "clean" the fetched data and saves it into a new object and returns it to the frontend. The API also checks if the date already exists in the redis DB, and if so does return this data instead of a new API fetch. 

The UI design is a iterative process, and as mentioned before I'm using Figma for prototyping which has increased the development speed. I've made the main page into three main sections, Header, Navbar and Main Content (Cards).
The Header shows index of the current hour, together with date-time and location.
The main content section is a carousel of three Cards (Data, Fish and Info). The data card shows all the data for the current day (by the hour), aswell as 10 days forward. Fish Card will contain necessary information about different kinds of fish and, and Info Card will contain information about how the index is calculated. 

I also decided not to use a 1-10 scale for the index and instead use 1-5, since 1-10 is a unnecessarily wide range.  


# Workflow
- Create a basic UI
- Get backend up and running
- Fetch data from API and cache it
- Present the data
- Create index algoritm
- Make calculations
- Present the calculated data + regular data

# Deployement
Vercel (Be sure to check so the python script works, if external libraries are installed, include requirements.txt in root)


# Calculating index
My approach is to ask five GenAI (ChatGPT, Gemini, Claude, Perplexity, Grok) to collect reliable data (with sources) about how the different values I'm using (temp, air pressure etc..) affect the fish. I will compare and analyze the answers, and create algoritms accordingly. If 5 of 5 GenAI answers are the same and constructed with relevant sources, they are probably correct and I won't have to compromise. If all the answers differentiate, I will have to look at specific shared and not shared values, and research why they differ. From this I can conclude the data and create the algoritm for the specific value (e.g. temp).


(THIS DIAGRAM IS NOT A TRUE REPRESENTATION OF THE PROJECT)
It was used early just for me to get my thoughts out on how it could/should/might look like
![diagram](images/fetchDiagram.png)

# notes TODO
- Fix Redis DB amount (it can currently store ~200 kommuner) [Maybe by cutting out unnecessary API data] 
- Dokumentera licensvillkor
- Make the app in english

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

# Workflow
- Create a basic UI

Starting with creating a basic layout for the UI using Figma.
From these Figma prototypes the workflow of creating/coding the UI will be substantially faster

- Fetch data
![diagram](images/fetchDiagram.png)

# notes TODO
- Dokumentera licensvillkor
- Make the app in english

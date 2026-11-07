
# Project Information 
The porject is a clone of the 2048 game done in react, the reason i chose this project is because I wanted to edit a game as I have a deep interest in them. And also 2048 was a very simple game tha I could start with, 

# Installation 

Just start dev server on [localhost](http://localhost:3000):

- clone
- `npm install`
- `npm run dev`

# Project Structure

pages/index.tsx = main page where the game is show, with the title score board and other text

educers/game-reducer.ts = The game logic, moving and merging tiles, updating the score

constants.ts = Settings, board size (4×4), animation timing, winning tile combination (orignally at 2048)

# React Component

components/board.tsx: draws the 4×4 grid and the tiles, and turns keyboard arrows and swipes into moves
components/tile.tsx or components/score.tsx: one tile, or the score box

# Code Analysis

```tsx
const handleKeyDown = useCallback(
  (e: KeyboardEvent) => {
    // disables page scrolling with keyboard arrows
    e.preventDefault();

    switch (e.code) {
      case "ArrowUp":
        moveTiles("move_up");
        break;
      case "ArrowDown":
        moveTiles("move_down");
        break;
      case "ArrowLeft":
        moveTiles("move_left");
        break;
      case "ArrowRight":
        moveTiles("move_right");
        break;
    }
  },
  [moveTiles],
);
```

prevent default stops the normal action of arrow keys being used for scrolling. e is a keyboard event so all keyboard default events are not working now (like spacebar scrolling)

then a swtich statement that matches each key to a matching action which is defined in GameContext,

# Customizing

Text

File: pages/index.tsx
Before: the title was "2048", the tab title was "Play 2048" and below the board there was a "Create your own game" section linking to the author's Udemy course.
After: the title is "2048 but done differently", the tab title is "Play 1024!", and that section now says "Edited by 22300778" with the text "2048!".

Style

File: styles/globals.css
Before: the page background was light beige (#faf8ef) and the board was brown (#b59d87).
After: the page background is yellow (#f4dc73) and the board is red (#d91710).

File: tile.module.css
Before: was the normal color for 2048 
After: changed the blocks into a bunch of random colors

UI/Data

File: constants.ts
Before: gameWinTileValue = 2048, so you won by making a 2048 tile.
After: gameWinTileValue = 1024, so the win screen appears when you make a 1024 tile. Moving, merging, scoring and game over still work the same as before.

# Vercel Deployment 
2026ossassign10-cyan.vercel.app

# Weekly Review:
새롭게 배운 내용 3가지: 
What e.preventDefault() does. It stops the browser's default action, I have used it before in forms, but didn't fully understand it till now. 

Open sourcing and what MIT license is: which  lets you modify and redeploy someone else's code, as long as you keep the copyright notice and license file.


I learned that keeping values like the winning tile in constants.ts and colors in CSS variables makes customizing much easier, because one change updates the whole game.


어려웠던 점과 해결 방법: 
Finding the right project was probably the part that took the longest. before this project there was another 2048 game i cloned, however there were some conflicts with the npm version as the project was pretty old, and i did not want to downgrade my version jsut to run it so i found this project instead. It was a bigger project with more files so it was hard to navigate through what each file does 


AI 활용 내용 및 느낀 점
There were initial problems with git commit and pushing so i used cluade to fix my branches and get rid of my old commit. I also used it to understand the general outline of the project, like where each code is located, then i read through the code accordingly. I really like this assignment because we got to actually tackle real projects with proper outcomes, 

I also used AI to find project ideas, which is how i got the idea of 2048 in the first place, however this specific repo was found by myself

I also used claude cli for the first few commits because there were problems with my git push, which was a nifty tool. 



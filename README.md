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

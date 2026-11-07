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

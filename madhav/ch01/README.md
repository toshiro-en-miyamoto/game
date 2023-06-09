# Game Programming Overview

## Updating the Game

### Delta time

*Delta time* is the amount of elapsed game time since the last frame. SDL provides an `SDL_GetTicks` member function that returns the number of milliseconds elapsed since the `SDL_Init` function call.

```c++
class Game
{
public:
  void UpdateGame();
private:
  Unit32 mTicksCount = 0;
  ...
}

void Game::UpdateGame()
{
  // a delta time in seconds
  float deltaTime = (SDL_GetTicks - mTicksCount) / 1000.0f;

  // a ticks count for next frame
  mTicksCount = SDL_GetTicks();

  // Update x position by 150 pixels/second
  enemy.mPosition.x += 150 * deltaTime;
}
```

Consider what happens when you call `UpdateGame`.

- On the very first time
  - Because `mTicksCount` starts at zero, you end up with some positive value of `SDL_GetTicks` and divide it by `1000.0f` to get a delta time in seconds.
- On the next frame,
  - the `deltaTime` line calculates a new delta time based on the old value of `mTicksCount` and the new value.

Thus, on every frame, you compute a delta time based on the ticks elapsed since the previous frame.

### Frame limiting

*Frame limiting* forces the game loop to wait until a target delta time has elapsed. For example, suppose that the target frame rate is 60 FPS. If a frame completes after only 15ms, frame limiting says to wait an additional ~1.6ms to meet the 16.6ms target time.

```c++
while (!SDL_TICKS_PASSED(SDL_GetTicks(), mTicksCount + 16));
```

However, if you pause at a breakpoint in the debugger for five seconds, you’ll end up with a huge delta time, and everything will jump far forward in the simulation.

To fix this problem, you can clamp the delta time to a maximum value (such as `0.05f`).

```c++
void Game::UpdateGame()
{
  // Wait until 16ms has elapsed since last frame
  while (!SDL_TICKS_PASSED(SDL_GetTicks(), mTicksCount + 16));

  // Delta time is the difference in ticks from last frame
  float deltaTime = (SDL_GetTicks() - mTicksCount) / 1000.0f;

  // a ticks count for next frame
  mTicksCount = SDL_GetTicks();

  // Clamp maximum delta time value
  if (deltaTime > 0.05f) {
    deltaTime = 0.05f;
  }

  // Update x position by 150 pixels/second
  enemy.mPosition.x += 150 * deltaTime;
}
```

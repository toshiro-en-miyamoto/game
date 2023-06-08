# Game Programming Overview

## Updating the Game

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
  float deltaTime = (SDL_GetTicks - mTicksCount) / 1000.0f;
  mTicksCount = SDL_GetTicks();

  // TODO: Update objects as function of delta time

  // Update x position by 150 pixels/second
  enemy.mPosition.x += 150 * deltaTime;
}
```

Consider what happens when you call `UpdateGame`.

- On the very first time
  - Because `mTicksCount` starts at zero, you end up with some positive value of `SDL_GetTicks` (the milliseconds since initialization) and divide it by `1000.0f` to get a delta time in seconds.
  - Next, you save the current value of `SDL_GetTicks` in `mTicksCount`.
- On the next frame,
  - the `deltaTime` line calculates a new delta time based on the old value of `mTicksCount` and the new value.

Thus, on every frame, you compute a delta time based on the ticks elapsed since the previous frame.


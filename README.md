# StackSim

StackSim is a single-file browser quiz for practicing pickleball stack positioning serve by serve.

The app simulates full doubles games with side-out scoring and asks two questions each serve:

1. Which side should I be on (left or right)?
2. Am I the server/receiver, or is my partner?

It is designed around a fixed player perspective where **you are starting #2** on your team.

## Project Layout

- `stacksim.html`: Complete app (HTML, CSS, and JavaScript in one file).

## Run Locally

No install or build is required.

1. Open `/Users/robschoen/Dropbox/CC/StackSim/stacksim.html` in a browser.
2. Start answering serves and click **Check Answer**.
3. Click **Play Rally** to advance the simulated game state.

## Controls

- **Check Answer**: Grades the current two answers and shows explanation.
- **Play Rally**: Simulates the next rally and updates score/service.
- **Start New Game**: Resets to a new random starting server.
- Hold `h`: Shows the in-app step-by-step hint overlay for the current serve.

## Rules Modeled

- Side-out scoring to 11, win by 2.
- Opening-game single-server exception (`0-0-2` rotation behavior).
- Service number tracking (`...-1` / `...-2`) per rotation.
- Server selection from starting numbers and team score parity.
- Left/right answers are always from your perspective.

## Logic Overview

Core logic lives in JavaScript inside `stacksim.html`:

- Game + quiz state: `state`
- Serve-state computation: `buildServeState()`
- Rally progression and side-out handling: `playRally()`
- Answer grading: `checkAnswer()`
- Rotation helpers: `startingSideForScore()`, `currentServerStartingNumber()`, `setRotationStart()`

## Notes

- Rally winners are randomized (`Math.random()`), so game flow is stochastic.
- Stats (`Asked`, `Correct`, `Streak`) persist while the page is open.

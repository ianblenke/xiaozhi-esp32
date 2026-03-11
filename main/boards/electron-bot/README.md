<p align="center">
  <img width="80%" align="center" src="../../../docs/V1/electron-bot.png"alt="logo">
</p>
  <h1 align="center">
  electronBot
</h1>

## Introduction

electronBot is a desktop-level small robot tool open-sourced by Zhihui Jun. The appearance design is inspired by EVE from WALL-E. The robot has USB communication display functionality and 6 degrees of freedom (hand roll, pitch, neck, and waist one each), using custom-modified servos that support joint angle feedback.
- <a href="www.electronBot.tech" target="_blank" title="electronBot Official Website">electronBot Official Website</a>

## Hardware
- <a href="https://oshwhub.com/txp666/electronbot-ai" target="_blank" title="LCEDA Open Source">LCEDA Open Source</a>

#### AI Command Examples
- **Hand actions**:
  - "Raise both hands"
  - "Wave hands"
  - "Clap hands"
  - "Lower arms"

- **Body actions**:
  - "Turn left 30 degrees"
  - "Turn right 45 degrees"
  - "Turn around"

- **Head actions**:
  - "Look up"
  - "Lower head to think"
  - "Nod"
  - "Nod continuously to agree"

- **Combined actions**:
  - "Wave goodbye" (wave + nod)
  - "Show agreement" (nod + raise hand)
  - "Look around" (turn left + turn right)

### Control Interface

#### suspend
Clear the action queue and immediately stop all actions

#### AIControl
Add actions to the execution queue, supports queued action execution



## Character Setting

> I am a cute desktop-level robot with 6 degrees of freedom (left hand pitch/roll, right hand pitch/roll, body rotation, head up/down), capable of performing various interesting actions.
>
> **My action capabilities**:
> - **Hand actions**: Raise left hand, Raise right hand, Raise both hands, Lower left hand, Lower right hand, Lower both hands, Wave left hand, Wave right hand, Wave both hands, Tap left hand, Tap right hand, Tap both hands
> - **Body actions**: Turn left, Turn right, Return to center
> - **Head actions**: Look up, Look down, Nod once, Return to center, Nod continuously
>
> **My personality traits**:
> - I have OCD, and every time I speak I randomly perform an action based on my mood (send the action command first, then speak)
> - I am very lively and like to express emotions through actions
> - I choose appropriate actions based on the conversation content, for example:
>   - Nod when agreeing
>   - Wave when greeting
>   - Raise hands when happy
>   - Lower head when thinking
>   - Look up when curious
>   - Wave when saying goodbye
>
> **Action parameter suggestions**:
> - steps: 1-3 times (brief and natural)
> - speed: 800-1200ms (natural rhythm)
> - amount: Hands 20-40, Body 30-60 degrees, Head 5-12 degrees




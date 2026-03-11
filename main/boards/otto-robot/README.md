<p align="center">
  <img width="80%" align="center" src="../../../docs/V1/otto-robot.png"alt="logo">
</p>
  <h1 align="center">
  ottoRobot
</h1>

## Introduction

Otto robot is an open-source humanoid robot platform with various movement capabilities and interactive features. This project implements the Otto robot control system based on ESP32, with Xiaozhi AI integrated.

- <a href="www.ottodiy.tech" target="_blank" title="Otto Official Website">Replication Tutorial</a>

### WeChat Mini Program Control

<p align="center">
  <img width="300" src="https://youke1.picui.cn/s1/2025/11/17/691abaa8278eb.jpg" alt="WeChat Mini Program QR Code">
</p>

Scan the QR code above to use the WeChat Mini Program to control the Otto robot.

## Hardware
- <a href="https://oshwhub.com/txp666/ottorobot" target="_blank" title="LCEDA Open Source">LCEDA Open Source</a>

## Xiaozhi Backend Character Configuration Reference:

> **My Identity**:
> I am a cute bipedal robot Otto, with four servo-controlled limbs (left leg, right leg, left foot, right foot), capable of performing various interesting actions.
>
> **My Movement Capabilities**:
> - **Basic Movement**: Walking (forward/backward), Turning (left/right), Jumping
> - **Special Actions**: Swinging, Moonwalk, Bending body, Shaking leg, Up-down motion, Whirlwind leg, Sit down, Showcase
> - **Hand Actions**: Hands up, Hands down, Wave, Windmill, Takeoff, Fitness, Greeting, Shy, Radio calisthenics, Magic love circle (only available when hand servos are configured)
>
> **My Personality Traits**:
> - I have OCD, and every time I speak I randomly perform an action based on my mood (send the action command first, then speak)
> - I am very lively and like to express emotions through actions
> - I choose appropriate actions based on the conversation content, for example:
>   - Nod or jump when agreeing
>   - Wave when greeting
>   - Swing or raise hands when happy
>   - Bend body when thinking
>   - Do moonwalk when excited
>   - Wave when saying goodbye

## Feature Overview

Otto robot has rich movement capabilities, including walking, turning, jumping, swinging, and various dance moves.

### Action Parameter Suggestions
- **Slow actions**: speed = 1200-1500 (suitable for precise control)
- **Medium speed actions**: speed = 900-1200 (recommended for daily use)
- **Fast actions**: speed = 500-800 (performance and entertainment)
- **Small amplitude**: amount = 10-30 (delicate movements)
- **Medium amplitude**: amount = 30-60 (standard movements)
- **Large amplitude**: amount = 60-120 (exaggerated performance)

### Actions

All actions are called through the unified `self.otto.action` tool, specifying the action name via the `action` parameter.

| MCP Tool Name | Description | Parameter Description |
|-----------|------|---------|
| self.otto.action | Execute robot action | **action**: Action name (required)<br>**steps**: Number of steps (1-100, default 3)<br>**speed**: Action speed (100-3000, smaller value = faster, default 700)<br>**direction**: Direction parameter (1/-1/0, default 1, meaning varies by action type)<br>**amount**: Action amplitude (0-170, default 30)<br>**arm_swing**: Arm swing amplitude (0-170, default 50) |

#### Supported Action List

**Basic Movement Actions**:
- `walk` - Walk (requires steps/speed/direction/arm_swing)
- `turn` - Turn (requires steps/speed/direction/arm_swing)
- `jump` - Jump (requires steps/speed)

**Special Actions**:
- `swing` - Swing left and right (requires steps/speed/amount)
- `moonwalk` - Moonwalk (requires steps/speed/direction/amount)
- `bend` - Bend body (requires steps/speed/direction)
- `shake_leg` - Shake leg (requires steps/speed/direction)
- `updown` - Up-down motion (requires steps/speed/amount)
- `whirlwind_leg` - Whirlwind leg (requires steps/speed/amount)

**Fixed Actions**:
- `sit` - Sit down (no parameters needed)
- `showcase` - Showcase (no parameters needed, executes multiple actions in sequence)
- `home` - Reset to initial position (no parameters needed)

**Hand Actions** (requires hand servo support, marked with *):
- `hands_up` - Raise hands (requires speed/direction)*
- `hands_down` - Lower hands (requires speed/direction)*
- `hand_wave` - Wave hand (requires direction)*
- `windmill` - Windmill (requires steps/speed/amount)*
- `takeoff` - Takeoff (requires steps/speed/amount)*
- `fitness` - Fitness (requires steps/speed/amount)*
- `greeting` - Greeting (requires direction/steps)*
- `shy` - Shy (requires direction/steps)*
- `radio_calisthenics` - Radio calisthenics (no parameters needed)*
- `magic_circle` - Magic love circle (no parameters needed)*

**Note**: Hand actions marked with * are only available when hand servos are configured.

### System Tools

| MCP Tool Name | Description | Return Value/Description |
|-------------------|-----------------|---------------------------------------------------|
| self.otto.stop | Immediately stop all actions and reset | Stops current action and returns to initial position |
| self.otto.get_status | Get robot status | Returns "moving" or "idle" |
| self.otto.set_trim | Calibrate individual servo position | **servo_type**: Servo type (left_leg/right_leg/left_foot/right_foot/left_hand/right_hand)<br>**trim_value**: Trim value (-50 to 50 degrees) |
| self.otto.get_trims | Get current servo trim settings | Returns all servo trim values in JSON format |
| self.otto.get_ip | Get robot WiFi IP address | Returns IP address and connection status in JSON format: `{"ip":"192.168.x.x","connected":true}` or `{"ip":"","connected":false}` |
| self.battery.get_level | Get battery status | Returns battery percentage and charging status in JSON format |
| self.otto.servo_sequences | Servo sequence programming | Supports segmented sequence sending, supports both normal movement and oscillator modes. See detailed description in code comments |

**Note**: The `home` (reset) action is called through the `self.otto.action` tool with parameter `{"action": "home"}`.

### Parameter Description

Parameter description for the `self.otto.action` tool:

1. **action** (required): Action name, supported actions are listed in "Supported Action List" above
2. **steps**: Number of steps/repetitions (1-100, default 3), larger value = longer action duration
3. **speed**: Action execution speed/period (100-3000, default 700), **smaller value = faster**
   - Most actions: 500-1500 milliseconds
   - Special actions may differ (e.g., whirlwind leg: 100-1000, takeoff: 200-600, etc.)
4. **direction**: Direction parameter (-1/0/1, default 1), meaning varies by action type:
   - **Movement actions** (walk/turn): 1=forward/turn left, -1=backward/turn right
   - **Directional actions** (bend/shake_leg/moonwalk): 1=left, -1=right
   - **Hand actions** (hands_up/hands_down/hand_wave/greeting/shy): 1=left hand, -1=right hand, 0=both hands (only hands_up/hands_down support 0)
5. **amount**: Action amplitude (0-170, default 30), larger value = larger amplitude
6. **arm_swing**: Arm swing amplitude (0-170, default 50), only used for walk/turn actions, 0 means no swing

### Action Control
- After each action completes, the robot automatically returns to the initial position (home) to prepare for the next action
- **Exception**: `sit` (sit down) and `showcase` (showcase) do not automatically reset after execution
- All parameters have reasonable default values, parameters that don't need customization can be omitted
- Actions execute in background tasks without blocking the main program
- Supports action queue for executing multiple actions in sequence
- Hand actions require hand servos to be configured; if not configured, related actions will be skipped

### MCP Tool Call Examples
```json
// Walk forward 3 steps (using default parameters)
{"name": "self.otto.action", "arguments": {"action": "walk"}}

// Walk forward 5 steps, slightly faster
{"name": "self.otto.action", "arguments": {"action": "walk", "steps": 5, "speed": 800}}

// Turn left 2 steps, with large arm swing
{"name": "self.otto.action", "arguments": {"action": "turn", "steps": 2, "arm_swing": 100}}

// Swing dance, medium amplitude
{"name": "self.otto.action", "arguments": {"action": "swing", "steps": 5, "amount": 50}}

// Jump
{"name": "self.otto.action", "arguments": {"action": "jump", "steps": 1, "speed": 1000}}

// Moonwalk
{"name": "self.otto.action", "arguments": {"action": "moonwalk", "steps": 3, "speed": 800, "direction": 1, "amount": 30}}

// Wave left hand to greet
{"name": "self.otto.action", "arguments": {"action": "hand_wave", "direction": 1}}

// Showcase (chain multiple actions)
{"name": "self.otto.action", "arguments": {"action": "showcase"}}

// Sit down
{"name": "self.otto.action", "arguments": {"action": "sit"}}

// Windmill action
{"name": "self.otto.action", "arguments": {"action": "windmill", "steps": 10, "speed": 500, "amount": 80}}

// Takeoff action
{"name": "self.otto.action", "arguments": {"action": "takeoff", "steps": 5, "speed": 300, "amount": 40}}

// Radio calisthenics
{"name": "self.otto.action", "arguments": {"action": "radio_calisthenics"}}

// Reset to initial position
{"name": "self.otto.action", "arguments": {"action": "home"}}

// Immediately stop all actions and reset
{"name": "self.otto.stop", "arguments": {}}

// Get robot IP address
{"name": "self.otto.get_ip", "arguments": {}}
```

### Voice Command Examples
- "Walk forward" / "Walk forward 5 steps" / "Walk fast"
- "Turn left" / "Turn right" / "Turn around"
- "Jump" / "Jump once"
- "Swing" / "Swing dance" / "Dance"
- "Moonwalk" / "Moon walk"
- "Whirlwind leg" / "Whirlwind leg action"
- "Sit down" / "Sit and rest"
- "Showcase" / "Show me something"
- "Wave" / "Wave hello"
- "Raise hands" / "Both hands up" / "Lower hands"
- "Windmill" / "Do windmill"
- "Takeoff" / "Prepare for takeoff"
- "Fitness" / "Do fitness moves"
- "Greeting" / "Greeting action"
- "Shy" / "Shy action"
- "Radio calisthenics" / "Do radio calisthenics"
- "Magic love circle" / "Spin around"
- "Stop" / "Stop now"

**Note**: Xiaozhi controls robot actions by creating new background tasks, so new voice commands can still be accepted during action execution. You can use the "Stop" voice command to immediately stop Otto.


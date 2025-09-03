# PLC Programming Knowledge Base

## Structured Text (ST) Syntax

### Basic Data Types
- BOOL: Boolean values (TRUE/FALSE)
- INT: 16-bit signed integer
- REAL: 32-bit floating point
- TIME: Time duration
- STRING: Text string

### Variable Declaration
```st
VAR
    led_output: BOOL := FALSE;
    timer_value: TIME := T#5s;
    counter: INT := 0;
END_VAR
```

### Timer Functions
- TON: Timer On-delay
- TOF: Timer Off-delay  
- TP: Timer Pulse

Example:
```st
VAR
    timer1: TON;
    timer_done: BOOL;
END_VAR

timer1(IN := start_input, PT := T#5s);
timer_done := timer1.Q;
```

### Control Structures
```st
IF condition THEN
    // code
ELSIF other_condition THEN  
    // code
ELSE
    // code
END_IF;

FOR i := 1 TO 10 BY 1 DO
    // loop code
END_FOR;

WHILE condition DO
    // code
END_WHILE;
```

## Common PLC Patterns

### LED Control with Timer
```st
PROGRAM LED_Timer_Control
VAR
    led_timer: TON;
    led_output: BOOL := FALSE;
    start_button: BOOL := FALSE;
END_VAR

led_timer(IN := start_button, PT := T#3s);
led_output := led_timer.Q;
```

### Motor Start/Stop Control
```st
PROGRAM Motor_Control
VAR
    start_button: BOOL;
    stop_button: BOOL;
    motor_running: BOOL := FALSE;
    emergency_stop: BOOL := FALSE;
END_VAR

IF start_button AND NOT emergency_stop THEN
    motor_running := TRUE;
END_IF;

IF stop_button OR emergency_stop THEN
    motor_running := FALSE;
END_IF;
```
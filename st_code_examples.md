# ST Code Examples Database

## Traffic Light Control
```st
PROGRAM Traffic_Light
VAR
    red_light: BOOL := TRUE;
    yellow_light: BOOL := FALSE;
    green_light: BOOL := FALSE;
    
    red_timer: TON;
    yellow_timer: TON;
    green_timer: TON;
    
    state: INT := 1; // 1=Red, 2=Green, 3=Yellow
END_VAR

CASE state OF
    1: // Red state
        red_light := TRUE;
        yellow_light := FALSE;
        green_light := FALSE;
        
        red_timer(IN := TRUE, PT := T#30s);
        IF red_timer.Q THEN
            state := 2;
            red_timer(IN := FALSE);
        END_IF;
        
    2: // Green state
        red_light := FALSE;
        yellow_light := FALSE;
        green_light := TRUE;
        
        green_timer(IN := TRUE, PT := T#25s);
        IF green_timer.Q THEN
            state := 3;
            green_timer(IN := FALSE);
        END_IF;
        
    3: // Yellow state
        red_light := FALSE;
        yellow_light := TRUE;
        green_light := FALSE;
        
        yellow_timer(IN := TRUE, PT := T#5s);
        IF yellow_timer.Q THEN
            state := 1;
            yellow_timer(IN := FALSE);
        END_IF;
END_CASE;
```

## Conveyor Belt Control
```st
PROGRAM Conveyor_Control
VAR
    start_button: BOOL;
    stop_button: BOOL;
    emergency_stop: BOOL;
    sensor_object: BOOL;
    
    conveyor_motor: BOOL := FALSE;
    object_counter: INT := 0;
    
    sensor_trigger: R_TRIG;
END_VAR

// Edge detection for object counting
sensor_trigger(CLK := sensor_object);
IF sensor_trigger.Q THEN
    object_counter := object_counter + 1;
END_IF;

// Motor control logic
IF start_button AND NOT emergency_stop THEN
    conveyor_motor := TRUE;
END_IF;

IF stop_button OR emergency_stop THEN
    conveyor_motor := FALSE;
END_IF;
```

## Tank Level Control
```st
PROGRAM Tank_Level_Control
VAR
    level_sensor: REAL; // 0-100%
    pump_output: BOOL := FALSE;
    valve_output: BOOL := FALSE;
    
    high_level: REAL := 90.0;
    low_level: REAL := 10.0;
    target_level: REAL := 50.0;
    
    fill_mode: BOOL := TRUE;
END_VAR

IF level_sensor < low_level THEN
    pump_output := TRUE;  // Start filling
    valve_output := FALSE;
    fill_mode := TRUE;
ELSIF level_sensor > high_level THEN
    pump_output := FALSE;
    valve_output := TRUE; // Start emptying
    fill_mode := FALSE;
ELSIF fill_mode AND level_sensor >= target_level THEN
    pump_output := FALSE;
ELSIF NOT fill_mode AND level_sensor <= target_level THEN
    valve_output := FALSE;
END_IF;
```
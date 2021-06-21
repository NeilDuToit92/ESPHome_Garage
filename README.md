# ESPHome_Garage

This implements a garage door or gate with one button, which works based on the following logic
 - Door open > Press button > Door closes
 - Door closed > Press button > Door opens
 - Door stopped halfway when it was busy moving towards the open posistion > Press button > Door closes
 - Door stopped halfway when it was busy moving towards the closed posistion > Press button > Door open

This configuration does the following
 - Door open > Press close > Door closes
 - Door closed > Press open > Door opens
 - Door stopped halfway when opening > Press close > Door closes
 - Door stopped halfway when closing > Press close > Door open > Open endstop makes it trigger again > Door closes

Assumptions
  - No manual input (Other than throgh the ESP) will be done when the door is busy moving based on a command received from HA. (See TODO section)

TODO
 - Add a safety mechanism (beam) to block comand from executing
 - Implement a timeout - If the door is MANUALLY stopped mid-movement, it will assume the OPEN state.
 - Allow manually reversing a command (By original remote/switch):
   **IMPORTANT: Most doors also reverses as a safety feature if something is blocking it from moving to the desired position**
   1. Door is at endstop (Closed in this example)
   2. HA says move (Open door in this example)
   3. Door starts moving (Opening in this example)
   4. ESP detects door is no longer at endstop and sends status to HA (Open in this example)
   5. Manual/Safety intervention stops the door
   6. Manual/Safety intervention moves the door (Closing in this example)
   7. ESP stops all commands assuming manual/safety intervention occurred
   8. Send status to HA (Closed in this example)
 

The user [muxa](https://github.com/muxa) has created a different version [here](https://gist.github.com/muxa/9d0b1be8ea7c3daed5a0d4f0db058e4f).

He has also opened a [feature request](https://github.com/esphome/feature-requests/issues/1268) so that we can make a component for this, instead of having to do it in yaml manually.

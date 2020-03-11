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

TODO
 - Add a safety mechanism (beam) to block door from moving
 
Assumptions
  - No alternate input (Mechanical button/remote - other than throigh the ESP) will be done when the door is moving towards it's desired position other
  - When implemented, the stop button can only stop the door when movement was triggered by the ESP, not when triggered by the original mechanical button/remote

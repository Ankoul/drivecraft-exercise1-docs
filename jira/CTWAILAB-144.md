# CTWAILAB-144 — Add vehicle-specific wheel selection to car configurator

| Field    | Value                                                       |
|----------|-------------------------------------------------------------|
| Type     | Story                                                       |
| Status   | New (To Do)                                                 |
| Priority | Low                                                         |
| Project  | CTW AI Enablement Lab (CTWAILAB)                            |
| Reporter | Jose Cruz (CTW)                                             |
| Source   | https://atc.bmwgroup.net/jira/browse/CTWAILAB-144 (mirror)  |

## User Story

As a car configurator user
I want to select a wheel type for my chosen vehicle — including a standard option available to all models and exclusive options only for specific models
So that I can personalise my configuration and see an accurate real-time price that reflects my wheel choice

## Context

DriveCraft is a web-based car configurator where users select a vehicle, colour, and wheel type, with the total price updating in real time.

The wheel selection feature includes one base option (Standard Alloy, $0) available to all 5 vehicles, plus three exclusive options tied to specific models:

- Off-Road Rugged Tyres ($1,200) for Summit SUV
- Sport Low-Profile ($800) for Bolt Coupe
- Aero Efficiency Wheels ($600) for Volt EV

Exclusive wheel options must only appear in the UI when the matching vehicle is selected, and switching vehicle resets the wheel to Standard Alloy if the previously selected wheel is incompatible.

## Reference Documentation

See [`../confluence/drivecraft-car-configurator.md`](../confluence/drivecraft-car-configurator.md)
(original: https://atc.bmwgroup.net/confluence/spaces/CTWAILAB/pages/8486730838/)

## Acceptance Criteria

- [ ] Standard Alloy wheel is shown for all 5 vehicle models at $0 surcharge
- [ ] Off-Road Rugged Tyres (+$1,200) appear only when Summit SUV is selected
- [ ] Sport Low-Profile (+$800) appears only when Bolt Coupe is selected
- [ ] Aero Efficiency Wheels (+$600) appear only when Volt EV is selected
- [ ] Exclusive wheels are hidden in the UI when an incompatible vehicle is selected
- [ ] Switching vehicle resets wheel to Standard Alloy if the active wheel is incompatible with the new model
- [ ] Total price updates in real time when a wheel option is selected
- [ ] Each wheel option displays its corresponding icon in the configuration panel

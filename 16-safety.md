# Stage 16: Robot and Lab Safety

A hobby robot can still break a finger, start a battery fire or throw a limb across a room. This stage gives you habits first and standards awareness second. I am not a safety engineer, and a robot that will work near other people or be sold needs a proper risk assessment by someone qualified. Items marked "search-confirmed" were found on 25 Nov 2026.

## Habits for every bench

Always put a physical emergency stop within reach that cuts motor power, not just the software. Test new code with the robot lifted off the ground or with the joint unloaded and current limits set low. Add software limits on joint range, speed and current, plus a watchdog that stops the motors if the control loop stalls or the bus goes quiet. Never reach into a robot's workspace while it is powered. Keep a fire-safe place and a battery bag for lithium packs, and never charge them unattended. Connect high-current wiring with proper connectors and fuses, and discharge capacitors before touching a drive. File 02 covers the battery protection circuits that back these habits up.

## Why stop functions matter

Industrial machines classify stops into categories. Stop category 0 removes power immediately, and categories 1 and 2 bring the machine to a controlled stop first, as defined in IEC 60204-1 (search-confirmed from a patent that cites it). Knowing the difference helps you choose whether a robot arm should drop or brake when you hit the button, which is a real design decision for an arm holding a load.

## Standards to know exist

ISO 10218 sets safety requirements for industrial robots. The 2025 edition replaced the 2011 one, added clearer functional safety requirements and now absorbs the former ISO/TS 15066 on human-robot collaboration (search-confirmed). ISO 13849 covers safety-related parts of control systems, ANSI/RIA R15.06 aligns with ISO 10218 in the United States, and ISO 13482 covers personal care and service robots (search-confirmed). The ISO 10218 contents include sections on emergency stop, protective stop and normal stop. You can read a free preview from the ANSI web store, but the full text is paid.

## Functional safety in one paragraph

Functional safety means a safety function, such as stopping a motor fast enough to prevent injury, works when needed. An Analog Devices article says it rests on systematic capability, hardware reliability and fault-tolerant architectures, and names IEC 61508, ISO 13849-1 and IEC 62061 as the governing standards (search-confirmed). For a learner the lesson is design: use independent hardware paths for stopping, avoid single points of failure, and never rely on one software thread to keep people safe.

## Risk assessment, practically

A risk assessment lists the hazards of each task, rates how likely and how severe harm would be, and picks mitigations in order: remove the hazard, guard it, then warn people. A SwRI introductory article walks through how to approach this for robot cells and mentions illuminated emergency-stop buttons and light stacks (search-confirmed). The German accident insurer DGUV publishes a detailed robot safety guide that covers protective stops, emergency stops, teach pendants and performance level calculations for a robot cell (search-confirmed).

## Practice

Write a one-page risk assessment for your own test bench, listing every hazard and its mitigation. Add a hardware emergency stop to your motor power and time how long the arm takes to stop. Test your watchdog by unplugging the communication cable mid-motion and confirm the motors cut out safely.

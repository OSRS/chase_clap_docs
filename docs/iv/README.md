# Interactive Visualization
A primary component of cyber analytics and threat hunting is the analyst.

While the CLAP DAG model has no human / user interaction, the CLAP model has been designed with the notion of humans participating in several key ways and areas.

## Human Model
We define the human portion of cyber with 2 key terms: HITL and HOTL

- HITL: Human in the loop [Wikipedia](https://en.wikipedia.org/wiki/Human-in-the-loop)
  - HITL is the traditional model in which a human play a key role in a specific step of a process. Generally the process will progres through steps with any human-centric step "blocking" until a human performs the actions defined by the step.

- HOTL: Human on the loop [IEEE](https://ieeexplore.ieee.org/document/7815473)
  - HOTL is a non-traditional model in which a human observes the process at one or more key points and acts as a supervisor, guide, killswitch or other role. In this model the process flow is not blocked by human interaction as the process is simply observed by the human.
  - HOTL often takes the shape of alerting in which a human receive notices from a process such as via a "dashboard". The human then decides if any action is warranted, potentially via different applications.
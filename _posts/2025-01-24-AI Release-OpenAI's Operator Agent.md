
# AI Release-OpenAI's Operator Agent

On 23 Jan, 2025 Open AI released it's research preview of ***Operator***, an agent that can do web-based tasks for you.

## What is Operator?

Operator is a research preview from OpenAI, employing a *Computer-Using Agent (CUA)* model. This model combines GPT-4o's visual capabilities with advanced reasoning honed through reinforcement learning. The CUA interacts with graphical user interfaces (GUIs) like a human, navigating buttons, menus, text fields, and search bars. It also utilizes a virtual machine environment.


## How it works?
It works by identifying what is on the screen and what task it must accomplish. Then reasons using *chain-of-thought* framework and determines what actions to take. And checks whether the tasks is accomplished and continues doing so till it completes the tasks.
![openai-operator](data/openai-operator.png)

### Perception
Inputs are - Screenshots from the screen and Goal Task by user.
Screenshots from the device screen are added to the model context and Goal task is defined by the user and given as input in text format. It just takes raw pixels rather than using web-specific APIs, which makes it useful across many websites. 

### Reasoning
Given the task and the context , CUA reasons through chain-of-thought reasoning for next steps and decides what action should be performed next. 

### Action
The action is then carried out by virtual mouse and keyboard. It occasionally stops to get user confirmations or further user interactions to continue for critical task steps.


## Performance

Operator set the SOTA benchmark for AI Agents in computer use and browser use. 
- Computer use is evaluated through [OSWorld](https://os-world.github.io/) . It indicates the ability to control OS like Linux, Windows and macOS.
- Browser use is evaluated through [WebArena](https://webarena.dev/) and [Web Voyager](https://langchain-ai.github.io/langgraph/tutorials/web-navigation/web_voyager/). It indicates the ability to perform tasks in live websites like e-commerce websites, booking websites, etc.,.


## Safety
Safety is implemented to mitigate risk in three major classes
### 1. Misuse:
Misusing model is controlled by
- *Refusing* to do harmful things.
- *Blocking* a list of pre-defined websites.
- *Moderating* interactions real-time by making sure it adheres to usage policies.
- *Implementing* Offline detection policies.

### 2. Model Mistakes
Model mistakes may happen when the model hallucinates or takes wrong turn which can cause harm to users or others.
To minimise it, we use
- *User confirmations* before finalising tasks with external side effects such as order confirmation, sending emails. etc.,
- *Limiting* higher-risk tasks like banking transactions, sensitive decisions, etc.
- *Watch mode* for particular actions or websites like emailing, to check the address.

#### Adversarial attacks
Models may make mistakes or prompted to make mistakes during adversarial attacks.
- CUA model is designed to identify and ignore prompt injection on websites.
- Monitoring and pausing the model execution if any suspicious content is detected on the screen
- Implemented automated detection pipelines to identify suspicious content and patterns

### 3. Frontier risk
Frontier risk by agentic models refers to the potential for harm or unintended consequences arising from highly capable AI systems that can autonomously plan and execute complex tasks with minimal human oversight. The risk posed by tools such as Operator, are outlined and assessed by OpenAI by their  [Preparedness Framework](https://cdn.openai.com/openai-preparedness-framework-beta.pdf).



## Conclusion
- **Anthropic's computer use** is also an AI agent, which is used to automate tasks in desktops.
- **Google's Project Mariner** is also an AI agent which is used to navigate in browsers and websites. Currently it is in experiment phase used by small group of testers.
- In that way, **Operator** is OpenAI's first AI agent to be used for web-based tasks. 



# Further Reference
OpenAI Live Demo: [Introduction to Operator & Agents](https://www.youtube.com/watch?v=CSE77wAdDLg)

OpenAI Blog: [Computer-Using Agent](https://openai.com/index/computer-using-agent/)

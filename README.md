<img src="https://capsule-render.vercel.app/api?type=waving&color=0:1F3A5F,100:2A7F8E&height=170&section=header&text=Emma%20Maikuri&fontSize=44&fontColor=ffffff&fontAlignY=40&desc=Game%20Developer%20%7C%20Software%20Engineer&descSize=18&descAlignY=62" width="100%" alt="Emma Maikuri banner"/>

<h3 align="center">Game Developer • Software Engineer • Full-Stack Developer</h3>

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=18&pause=1200&color=2A7F8E&center=true&vCenter=true&width=640&lines=I+build+game+engines+from+scratch+in+C%2B%2B;Engine+architecture+%7C+gameplay+systems;Full-stack+products+and+AI+automation" alt="Typing animation"/>
</p>

<p align="center">
  <a href="https://portfolioemma.vercel.app/"><img src="https://img.shields.io/badge/Portfolio-1F3A5F?style=for-the-badge&logo=vercel&logoColor=white"/></a>
  <a href="https://www.linkedin.com/in/emma-maikuri-997ba631"><img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"/></a>
  <a href="mailto:maikuriemma@gmail.com"><img src="https://img.shields.io/badge/Email-2A7F8E?style=for-the-badge&logo=gmail&logoColor=white"/></a>
</p>

---

## 👩‍💻 About

I build the systems behind interactive products: **C++ game engine foundations**, **full-stack web applications** and **AI-assisted automation**.

- 🎮 Building a game engine from scratch in **C++20**, with a focus on clean architecture
- 🌐 Three years of professional software development, plus freelance work since 2016
- 🏭 Previously Software Developer & IT Lead at **Plumbee Wholefoods**: built websites and data systems, automated recruitment, onboarding and reporting, and set up the company's IT function
- 🚀 I design, build and sell my own products, from idea to payments to support
- ⚽ Amateur footballer who loves teamwork on and off the field

📬 **Open to part-time opportunities in game development and software engineering.**

---

## 🎮 Featured Project: C++ Game Engine

<p>
  <img src="https://img.shields.io/badge/C%2B%2B-20-00599C?style=flat-square&logo=cplusplus&logoColor=white"/>
  <img src="https://img.shields.io/badge/CMake-064F8C?style=flat-square&logo=cmake&logoColor=white"/>
  <img src="https://img.shields.io/badge/OpenGL-4.1_core-5586A4?style=flat-square&logo=opengl&logoColor=white"/>
  <img src="https://img.shields.io/badge/GLFW-window_%2B_input-2A7F8E?style=flat-square"/>
  <img src="https://img.shields.io/badge/Apple_Silicon-ARM64-000000?style=flat-square&logo=apple&logoColor=white"/>
  <img src="https://img.shields.io/badge/status-in_progress-orange?style=flat-square"/>
</p>

A game engine written from scratch, with no off-the-shelf engine underneath, to learn how games actually work: timing, input, simulation and the architecture that keeps them maintainable. The goal is a clean separation between **the engine** (reusable) and **the game** (built on top of it).

<!-- Add a short GIF of the Sandbox running here for maximum impact:
<p align="center"><img src="docs/demo.gif" width="70%" alt="Engine demo"/></p> -->

### Architecture

```mermaid
flowchart LR
    subgraph ENGINE["Engine (reusable)"]
        APP["Application"] --> LOOP["Fixed-timestep loop"]
        APP --> WIN["Window: GLFW + OpenGL 4.1"]
        APP --> INP["Input system"]
        APP --> LOG["Logger"]
        APP --> WORLD["World: entities + components"]
        GI["Game interface"]
    end
    subgraph GAME["Game (Sandbox)"]
        SG["SandboxGame"] --> SYS["MovementSystem"]
        SG --> COMP["Transform, Velocity, InputState"]
    end
    LOOP -- "update + render" --> GI
    SG -. "implements" .-> GI
    SYS --> WORLD
    INP --> COMP
```

### What's built

- ⏱️ **Fixed-timestep game loop** with an accumulator and interpolation, so the simulation is deterministic and rendering stays smooth at any frame rate
- 🧩 **Entity-component `World`**: a registry that stores components per entity, with game code looking them up through the world instead of owning them directly
- 🎹 **Input layer** that separates physical keys from game *intent*, with proper held vs pressed handling, on real GLFW keyboard input
- 🪟 **Native window** on an OpenGL 4.1 core context, running on Apple Silicon
- 🧱 **Strict dependency rule:** the engine never depends on the game, only the other way round

### Design decisions

| Decision | Why |
|---|---|
| Fixed timestep with interpolation | Physics and gameplay behave identically on slow and fast machines |
| Components in a `World` registry, not inside entities | Keeps data and behaviour separate, and prepares the ground for multi-entity ECS |
| Input as intent (`moveLeft`) instead of raw keys (`A`) | Lets controls be rebound and keeps game code free of GLFW |
| Engine and game as separate targets | The engine can be reused by any game without changes |

### The loop at the heart of it

```cpp
const double dt = 1.0 / 60.0;          // fixed simulation step
double accumulator = 0.0;

while (running) {
    accumulator += frameTime();

    while (accumulator >= dt) {         // catch up in fixed steps
        game.update(dt);
        accumulator -= dt;
    }

    game.render(accumulator / dt);      // interpolate between states
}
```

### Roadmap

- [x] Engine skeleton, logger and application structure
- [x] Fixed-timestep loop with interpolation
- [x] Real keyboard input and engine/game boundary
- [x] World registry with components and systems
- [ ] Multi-entity ECS
- [ ] Rendering pipeline
- [ ] Physics integration
- [ ] Modern graphics API backend (Metal / MoltenVK)

---

## 🧱 Products & Projects

| Project | What it is | Built with |
|---|---|---|
| 🎮 **C++ Game Engine** | Engine from scratch (in progress) | C++20, CMake, GLFW, OpenGL |
| 📚 **PromptGuide** | Prompt library web app, sold on Gumroad | React, Vite |
| 📄 **ResumePro** | AI-powered CV analyser | React, Supabase, Paystack |
| 🚀 **LaunchKit** | SaaS starter for launching web products | Next.js |
| 🔁 **n8n Workflows** | Business automation workflows, published on Gumroad | n8n |

More projects: **[portfolioemma.vercel.app](https://portfolioemma.vercel.app/)**

---

## 🛠️ Tech Stack

**🎮 Game Development & Engineering**

<img src="https://skillicons.dev/icons?i=cpp,cmake,opengl,unreal" alt="Game development stack"/>

C++20 • CMake • OpenGL • GLFW • Unreal Engine 5 • Game loops • Entity-component systems • Algorithms and data structures

**💻 Languages**

<img src="https://skillicons.dev/icons?i=cpp,java,py,php,js,ts" alt="Languages"/>

**🌐 Web & Backend**

<img src="https://skillicons.dev/icons?i=react,nextjs,nodejs,express,django,fastapi,spring,laravel,html,css" alt="Web and backend"/>

**🗄️ Data & Cloud**

<img src="https://skillicons.dev/icons?i=mysql,postgres,supabase,aws,gcp,azure" alt="Data and cloud"/>

**🧰 Tools & Automation**

<img src="https://skillicons.dev/icons?i=git,github,vscode,vercel" alt="Tools"/>

n8n • Airtable • REST APIs • Agile • Machine learning

---

## 📈 GitHub Stats

<p align="center">
  <img height="170" src="https://github-readme-stats.vercel.app/api?username=Emmabsy&show_icons=true&theme=tokyonight&hide_border=true" alt="GitHub stats"/>
  <img height="170" src="https://github-readme-stats.vercel.app/api/top-langs/?username=Emmabsy&layout=compact&theme=tokyonight&hide_border=true" alt="Top languages"/>
</p>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:1F3A5F,100:2A7F8E&height=100&section=footer" width="100%" alt="footer"/>

# 【ICX】- IC Bookmark Hackathon

> **[Online Mainnet Demo](https://jeksq-wyaaa-aaaal-qaw3a-cai.ic0.app/)**
> [Demo Video](https://player.vimeo.com/video/708486719?h=a3639199e9)

```bash
          _____                    _____                                  
         /\    \                  /\    \                 ______          
        /::\    \                /::\    \               |::|   |         
        \:::\    \              /::::\    \              |::|   |         
         \:::\    \            /::::::\    \             |::|   |         
          \:::\    \          /:::/\:::\    \            |::|   |         
           \:::\    \        /:::/  \:::\    \           |::|   |         
           /::::\    \      /:::/    \:::\    \          |::|   |         
  ____    /::::::\    \    /:::/    / \:::\    \         |::|   |         
 /\   \  /:::/\:::\    \  /:::/    /   \:::\    \  ______|::|___|___ ____ 
/::\   \/:::/  \:::\____\/:::/____/     \:::\____\|:::::::::::::::::|    |
\:::\  /:::/    \::/    /\:::\    \      \::/    /|:::::::::::::::::|____|
 \:::\/:::/    / \/____/  \:::\    \      \/____/  ~~~~~~|::|~~~|~~~      
  \::::::/    /            \:::\    \                    |::|   |         
   \::::/____/              \:::\    \                   |::|   |         
    \:::\    \               \:::\    \                  |::|   |         
     \:::\    \               \:::\    \                 |::|   |         
      \:::\    \               \:::\    \                |::|   |         
       \:::\____\               \:::\____\               |::|   |         
        \::/    /                \::/    /               |::|___|         
         \/____/                  \/____/                 ~~              
                                                                          
                                                                              
```

## Inspiration

Even though I have hundreds of bookmarks, no more than 20 of them are really useful at the same time.
And I was tired of manage bookmarks from browser to browser. I think my way managing links may not effective enough.
Thus I tried to develop a distributed and erasable bookmarking tool for multi-person collaboration.

## What it does

The ICX is regard as a tool or station, where users can manage bookmarks via Internet Computer.

```bash
# The data structure used Node, and contains 3 Node types.
App Node
    - Collection Node 
        - Bookmark Node
```

There are two types of data:

### Square Data `100% Open to All`

Data is stored in the ICX-Canister. Edit access to data is open to all inludes modify & delete.

Data will be cleared regularly(Monthly), to avoid that, users need a successfull vote for each node data.

### User Data `Only for User` -- Coming Soon

Data is encrypted and stored permanently in the user's Canister. Only userself has access to modify them.

The cost of creating the Canister is borne by the user.

## Features

- Page Home: Open Square. 100% Open to manage bookmarks
- Page Rank: Show User Point. Update after user modify.
- Page Activity: Show loggers.
- Page Feedback: Send report.
- Page About: Intro of app.
- Page Tool: Principal to account.
- IC-Naming
- Identity: Internet Identity & Plug.
- Dark/Light mode switch.(bottom left)
- Readonly/Write mode switch.(bottom left)

## What's next for ICX

- Vote
- Personal User Canister Management.
- Fork datas from suqare to user's own canister.
- Profile Picture

## How we built it

Start with a figma draft of this product, develop backend in motoko and then develop frontend in vue.

## Challenges we ran into

The identity is hard to get started, luckily I reference to many open source projects and examples.

## Accomplishments that we're proud of

### Product

- Feedback is integrated in the service.
- Thanks to IC, support with the Fast & Easy network interaction.

### Not Bad UI : )

- Support Dark/Light mode.
- The Msg-Bot at right bottom for UI Embellishments.
- The Human Check Verify Popup.

## What we learned

- How to deploy & upgrade dapps on IC.
- Separate front and back-end development on IC.

## Design Rule

### Theme Color

| Color            | Hex                                                              |
| ---------------- | ---------------------------------------------------------------- |
| Background       | ![#e81a91](https://via.placeholder.com/10/e81a91?text=+)![#c865b3](https://via.placeholder.com/10/c865b3?text=+)![#978cd8](https://via.placeholder.com/10/978cd8?text=+)![#03acfd](https://via.placeholder.com/10/03acfd?text=+)|
| Primay SKY       | ![#0ea5e9](https://via.placeholder.com/10/0ea5e9?text=+) #0ea5e9 |
| Primay ROSE      | ![#f43f5e](https://via.placeholder.com/10/f43f5e?text=+) #f43f5e |
| Highlight AMBER  | ![#f59e0b](https://via.placeholder.com/10/f59e0b?text=+) #f59e0b |
| Info BLUE  | ![#60a5fa](https://via.placeholder.com/10/60a5fa?text=+) #60a5fa |
| Success GREEN  | ![#4ade80](https://via.placeholder.com/10/4ade80?text=+) #4ade80 |
| Warn AMBER  | ![#fbbf24](https://via.placeholder.com/10/fbbf24?text=+) #fbbf24 |
| Error ROSE  | ![#fb7185](https://via.placeholder.com/10/fb7185?text=+) #fb7185 |

### Brand Logo

> Just for fun, not Commercial

- Dfinity-LOGO

![dfinity](/docs/dfinity.svg)

- ICX-LOGO

![icx](/docs/logo.svg)

- LOADING

![loading](/docs/human.gif)

### Figma Sketch

![figma_1](/docs/figma_1.png)

![figma_2](/docs/figma_2.png)

![figma_3](/docs/figma_3.png)

## Tech Rule

### Skill Stack

- Network: Internet Computer
- Backend: Motoko
- Frontend: Vue+Vite+Ts+Tailwind

### Commands

To run this project, you will need to add the following environment variables to your `.env` file

```yaml
VITE_APP_DFX_NETWORK=""
```

Local dev

```bash
#1.enter icx
cd icx
#2.Remove ICXInterface in dfx.json
#3.start local net
dfx start
#4.deploy backend
dfx deploy
#5.initial Data with your wallet
dfx canister call ICX initialNodes
#6.enter icx/interface
cd /interface
#7.bootstrap & can skip if already installed
npm i
#8 run frontend
npm run dev
```

### Services/Canister

#### 1.ICX

Core: `jki7y-niaaa-aaaal-qaw2a-cai`

- User
- Node
  - AppInfo(Root:L1)
  - Collection(L2)
  - Bookmark(L3)

#### 2.Factory

Factory: `jnjzm-aqaaa-aaaal-qaw2q-cai`

- Feedback
- EventLogger

#### 3.ICXInterface

Frontend: `jeksq-wyaaa-aaaal-qaw3a-cai`

### Data & Type

```motoko
UserInfo {
  id: Text;
  account: AID.Address;
  no: Nat;
  point: Nat;
  alias: Text;
}

Node {
  base: {
    id: Nat;
    pid: Nat;
    pids: [Nat];
    level: Nat;
    isRoot: Bool;
  };
  main: {
    title: Text;
    desc: Text;
    cover: Text;
    content: Text;
  };
  authors: [Text];
  lastUpdate: Time.Time;  
}

FeedbackBody {
  group: Text;
  message: Text;
  timestamp: Time.Time;
  opreator: Text;
}

WorkEvent {
  level: Nat;
  work: Text;
  content: Text;
  ref: Text;
  timestamp: Time.Time;
  opreator: Text;
}
```

### Directory Structure

Front and back-end separation

```bash
icx
├ interface   # Frontend
│ ├ dist    # build files
│ ├ public    # static assets
│ │ ├ assets   # img,fonts,mp3...
│ │ ├ components   # global widget
│ │ ├ directives   # global directive
│ │ ├ hooks   # Module Func
│ │ ├ layout   # layout widget
│ │ ├ model   # data types
│ │ ├ plugin   # plugins register
│ │ ├ router   # vue-router
│ │ ├ store   # vuex:pinia
│ │ ├ styles   # css
│ │ ├ utils   # tools
│ │ ├ views   # pages
│ │ ├ App.vue   # Main Template
│ │ └ main.ts   # Main Entry
│ ├ src   # source code
│ ├ index.html    # page entry
│ ├ ...
│ ├ tailwind.config.js    #tailwin config
│ └ vite.config.ts    # vite-config like webpack
├ motoko    # Backend
│ ├ modules   # Tools 
│ │ ├ AID   # AccountId Tools
│ │ ├ DateTime.mo   # DateTime Tools
│ │ └ XNODe.mo    # XNode Tools
│ ├ types   # Types
│ ├ Factory.mo    # Factory-Entry
│ └ Main.mo   # Main-Entry
│ ...
```

## Authors

- [@Mulander-J](https://github.com/Mulander-J)

## Feedback

If you have any feedback, please reach out to me at [Email](mulander_j@outlook.com).

## Contributing

Contributions are always welcome!

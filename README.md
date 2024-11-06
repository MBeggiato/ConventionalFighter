# ConventionalFighter

ConventionalFighter (CF) aims to create an easy way to generate conventional commit messages by providing a [simple web GUI](https://mbeggiato.github.io/ConventionalFighter/).

CF follows the Conventional Commits specification 1.0.0 found [here](https://www.conventionalcommits.org/en/v1.0.0/).

## Why Use Conventional Commits
- Automatically generating CHANGELOGs.
- Automatically determining a semantic version bump (based on the types of commits landed).
- Communicating the nature of changes to teammates, the public, and other stakeholders.
- Triggering build and publish processes.
- Making it easier for people to contribute to your projects by allowing them to explore a more structured commit history.

## Getting Started

### Prerequisites
- Node.js (version 14 or later)
- npm (version 6 or later)

### Installation
1. Clone the repository:
    ```sh
    git clone https://github.com/mbeggiato/ConventionalFighter.git
    cd ConventionalFighter
    ```

2. Install dependencies:
    ```sh
    npm install
    ```

### Running the Application
To start the development server, run:
```sh
npm run dev
```
This will start the application at `http://localhost:5173/`.

### Building
To build this project run
```sh
npm run build
```

> [!TIP]  
> Checkout this projects GitHub actions to learn more about building and deploying.


## License
This project is licensed under the MIT License. 
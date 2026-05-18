# Cypress E2E Testing Project
### CSE482 — Software Testing | Spring 2026

---

## 📌 About This Project

This project uses [Cypress](https://www.cypress.io/) to perform **End-to-End (E2E) testing** on [SauceDemo](https://www.saucedemo.com) — a public demo e-commerce application built specifically for testing practice.

The project is divided into two tasks as per the semester project requirements:

- **Task 1** — UI Test Suite (Login, Navigation, and Form tests)
- **Task 2** — Assertions, Aliases, Custom Commands, and beforeEach hooks

---

## 🛠️ Prerequisites

Make sure you have the following installed before running anything:

| Tool | Version | Download |
|------|---------|----------|
| Node.js | v18 or higher | https://nodejs.org |
| npm | comes with Node.js | — |
| Git | any recent version | https://git-scm.com |

Check your versions:
```bash
node -v
npm -v
```

---

## 📁 Project Structure

```
cypress-project/
│
├── cypress/
│   ├── e2e/
│   │   ├── task1/
│   │   │   ├── login.cy.js          ← Login Test 1, 2, 3
│   │   │   ├── navigation.cy.js     ← Navigation Test 1, 2
│   │   │   └── form.cy.js           ← Form Test 1
│   │   │
│   │   └── task2/
│   │       ├── assertions.cy.js     ← 3 assertion types + negative + alias
│   │       └── custom_commands.cy.js ← Tests using cy.login() custom command
│   │
│   ├── support/
│   │   ├── commands.js              ← Custom commands: login(), logout(), addToCart()
│   │   └── e2e.js                   ← Auto-imports commands before every spec
│   │
│   ├── screenshots/                 ← Auto-saved screenshots from cy.screenshot()
│   └── fixtures/                    ← (empty — not needed for this project)
│
├── cypress.config.js                ← Cypress settings (baseUrl, viewport, etc.)
├── package.json                     ← Project dependencies and npm scripts
└── README.md                        ← You are here
```

---

## 🚀 How to Install & Run

### 1. Clone the repository
```bash
git clone https://github.com/YOUR_USERNAME/cypress-project.git
cd cypress-project
```

### 2. Install dependencies
```bash
npm install
```
This downloads Cypress and everything it needs (~500MB first time, cached after that).

### 3. Run tests in interactive mode (recommended for first run)
```bash
npm run cy:open
```
This opens the Cypress Test Runner in your browser. You can:
- Click any spec file to run it individually
- Watch tests execute live in the browser
- See passing (green) and failing (red) tests in real time

### 4. Run all tests headlessly (terminal only)
```bash
npm run cy:run
```

### 5. Run only Task 1 tests
```bash
npm run cy:run:task1
```

### 6. Run only Task 2 tests
```bash
npm run cy:run:task2
```

---

## ✅ Task 1 — UI Test Suite

**Website tested:** https://www.saucedemo.com

| File | Test Name | What it checks |
|------|-----------|----------------|
| `login.cy.js` | Login Test 1 | Valid login lands on Products page |
| `login.cy.js` | Login Test 2 | Wrong password shows error message |
| `login.cy.js` | Login Test 3 | Empty fields shows validation error |
| `navigation.cy.js` | Navigation Test 1 | Burger menu opens and links work |
| `navigation.cy.js` | Navigation Test 2 | Two pages navigate correctly in sequence |
| `form.cy.js` | Form Test 1 | Checkout form fills and shows order summary |

**Cypress commands used:** `cy.visit()`, `cy.get()`, `cy.should()`, `cy.type()`, `cy.click()`, `cy.url()`

---

## ✅ Task 2 — Assertions, Aliases & Custom Commands

| File | Exercise | What it demonstrates |
|------|----------|----------------------|
| `assertions.cy.js` | Assertion 1 | `should('be.visible')` |
| `assertions.cy.js` | Assertion 2 | `should('have.text', '...')` |
| `assertions.cy.js` | Assertion 3 | `should('have.attr', '...')` |
| `assertions.cy.js` | Negative Assertion | `should('not.exist')` |
| `assertions.cy.js` | Alias Practice | `.as('name')` and `cy.get('@name')` |
| `custom_commands.cy.js` | Custom Command | `cy.login()` defined in commands.js |
| `custom_commands.cy.js` | beforeEach | `cy.login()` called before every test |
| `custom_commands.cy.js` | Screenshot | `cy.screenshot()` saves to screenshots/ |

### Custom Commands defined in `cypress/support/commands.js`:

```js
cy.login(username, password)  // visits site, fills credentials, clicks login
cy.logout()                   // opens menu, clicks logout, asserts login page
cy.addToCart(index)           // clicks the nth Add to Cart button
```

---

## 📸 Screenshots

Screenshots are automatically saved to `cypress/screenshots/` when:
- `cy.screenshot()` is called inside a test
- A test **fails** in headless mode (Cypress saves one automatically)

The screenshot `inventory-page-logged-in.png` is captured in the custom command test to demonstrate a passing state.

---

## 📝 Task 2 Reflection

During this project, the most challenging part was understanding **how aliases work** in Cypress. At first I kept trying to store the result of `cy.get()` in a regular JavaScript variable, which doesn't work because Cypress commands are asynchronous and return chainable objects, not actual DOM elements. The fix was to use `.as('aliasName')` and then retrieve it later with `cy.get('@aliasName')`. Reading the Cypress docs on its command queue made this click — Cypress queues all commands and runs them in order, so you have to use its own aliasing system instead of regular JS variables.

---

## 👤 Author

- **Student Name:** shahzaib ahmad
- **Registration No:** fa22-bse-081
- **Course:** CSE482 — Software Testing
- **Instructor:** Ms. Yella Mehroze
- **Semester:** Spring 2026

---

*Individual Semester Project — Do Not Share*

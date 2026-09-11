# 🚌 Bus Ticket PWA

<br>

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6%2B-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![Platform](https://img.shields.io/badge/Platform-Web-4285F4?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-In%20Development-orange?style=for-the-badge)
![License](https://img.shields.io/badge/License-Personal-lightgrey?style=for-the-badge)

**Bus Ticket PWA** is a small personal, mobile-first web application designed to simplify the daily process of creating and managing a bus ticket.

It provides a single place to store the information needed for the transport company's website, quickly copy the required codes, access frequently used pages, keep track of the subscription, and save the current day's ticket for later access.

The application is completely client-side: there is no backend, no account system, and no database. Personal data is stored locally in the browser.

---

### 🌐 Live

The application is currently deployed and accessible at:

[flaviolanzafame.github.io/bus-ticket-pwa](https://flaviolanzafame.github.io/bus-ticket-pwa/?utm_source=chatgpt.com)

---

## 💡 Why

The project was created to simplify a repetitive daily task.

The transport service I use to travel to school requires two pieces of information to be entered manually every time a ticket is created:

* the **user card number**
* the **subscription code**

Both are long codes, and the website does not reliably retain them through browser autofill. As a result, the same information has to be retrieved and entered again every day.

The ticket itself also presents another inconvenience: after some time, the ticket page logs the user out. If the ticket needs to be checked again later in the day, the login process has to be repeated.

This application was created as a small personal utility to make that workflow more convenient.

Rather than replacing or automating the transport company's website, it acts as a **personal dashboard around it**:

```text
Store personal information once
            ↓
    Copy codes quickly
            ↓
   Open the required page
            ↓
     Create the ticket
            ↓
 Save the ticket screenshot
            ↓
Access it again during the day
```

The goal is simply to reduce the amount of repetitive work required for something that is done every day.

---

## 📋 Features

### 🎫 Today's Ticket

* Save a screenshot of the generated ticket
* Keep the ticket available throughout the day
* Automatically remove the saved ticket when the next day begins
* Display the time at which the ticket was saved
* Delete the saved ticket manually when needed

### 💳 Digital Card

* Store the user's name and transport company
* Store the route and card validity dates
* Upload a personal card photo
* Display the card as a flip-able 3D interface
* Show the user card number on the front
* Display route and validity information on the back

### 📋 Quick Copy

* Store the **10-digit user card number**
* Store the **subscription/title code**
* Copy either code with a single tap
* Keep the required information immediately accessible

### 🔗 Quick Links

* Access the ticket creation page directly
* Access the ride-time change page
* Add additional frequently used pages
* Edit and save up to three custom links

### 🎟️ Subscription Tracking

* Track the number of remaining tickets
* Configure the total number of tickets in the current period
* Support **weekly** and **monthly** subscriptions
* Manually mark a ticket as used
* Reset the ticket counter when necessary
* Set the next renewal date

### ⏳ Expiration Tracking

* Track the user card expiration date
* Track the subscription expiration date
* Display the number of days remaining
* Highlight approaching or expired dates

---

## ⚙️ How It Works

The application is built as a **single static HTML file** containing the interface, styling, and JavaScript logic.

No application server or build system is required.

### Local Data

All user information is stored using the browser's `localStorage` API.

The application separates its stored data into several local records:

| Data                        | Stored locally as |
| --------------------------- | ----------------- |
| User and subscription codes | `profile-data`    |
| Card information and photo  | `card-data`       |
| Subscription counter        | `counter-data`    |
| Expiration dates            | `expiry-data`     |
| Custom links                | `links-data`      |
| Today's ticket screenshot   | `ticket-image`    |

All records use the `bus-app:` prefix to keep the application's local storage entries separated from unrelated browser data.

### Today's Ticket

When a ticket screenshot is uploaded, the application:

1. Reads the image locally
2. Resizes it if necessary
3. Converts it to a compressed JPEG
4. Stores the resulting image as a data URL
5. Records the current date and time
6. Displays it in the **Today's Ticket** section

When the application starts, it compares the stored ticket date with the current date. If they are different, the previous ticket is removed automatically.

---

## 🚌 Daily Workflow

The intended workflow is:

```text
Open the app
     │
     ▼
Copy user card number
     │
     ▼
Copy subscription code
     │
     ▼
Open "Create ticket"
     │
     ▼
Create the ticket on the transport website
     │
     ▼
Take a screenshot
     │
     ▼
Save it in the app
     │
     ▼
Access the ticket again when needed
```

The app does **not** automatically log into or interact with the transport company's website.

The actual ticket creation remains on the official website. The application simply keeps the information and shortcuts needed for that process immediately accessible.

---

## 🚀 Getting Started

### Requirements

* A modern web browser
* JavaScript enabled
* An `https://` origin for reliable browser storage
* A mobile or desktop device

### Run Locally

There is no build system or dependency installation required.

The entire application is contained in:

```text
index.html
```

You can serve it using any static HTTP server.

For example:

```bash
python3 -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

> Opening the file directly with `file://` is not recommended, particularly on mobile browsers, as browser storage behaviour can be inconsistent.

---

## 📱 Mobile Use

The interface is designed primarily for mobile devices and can be used directly from a browser.

### 🍎 iPhone / iPad

Using **Safari**:

1. Open the deployed application
2. Tap **Share**
3. Select **Add to Home Screen**
4. Confirm the installation
5. Launch the app from the Home Screen

This provides an app-like experience without requiring a native iOS application.

### 🤖 Android

Using **Google Chrome**:

1. Open the deployed application
2. Open the browser menu (`⋮`)
3. Select **Add to Home screen** or **Install app**, depending on the browser and device
4. Confirm
5. Launch the application from the Home Screen

Other Chromium-based Android browsers may provide a similar option.

### 💻 Desktop

The application can also be used from a desktop browser. No installation is required.

Simply open the deployed page and use it normally.

---

## 🔒 Privacy

The application is designed to keep personal information on the user's device.

The following information can be stored locally:

* user card number
* subscription code
* name
* transport company
* route
* card photo
* validity dates
* subscription information
* ticket screenshots
* custom links

This information is stored using the browser's `localStorage` API and is not stored in the repository.

There is:

* **No backend**
* **No database**
* **No user account**
* **No analytics or tracking implemented by the application**
* **No server-side storage of personal data**

The public repository and deployed page contain only the application itself. Personal information is entered at runtime by the user.

> **Important:** local storage belongs to the specific browser and origin on the device. Clearing browser data, changing browsers, or using another device will not transfer the stored information.

---

## 🧰 Tech Stack

* **HTML5** — application structure
* **CSS3** — responsive interface, styling and 3D card animation
* **JavaScript** — application logic and state management
* **Web Storage API** — local data persistence
* **FileReader API** — local image processing
* **Canvas API** — image resizing and compression
* **Clipboard API** — one-tap code copying
* **Google Fonts** — Fraunces, IBM Plex Mono and Inter

No frameworks.
No build step.
No package manager.
No backend.

---

## 📁 Project Structure

```text
bus-ticket-pwa/
├── index.html
├── LICENSE
└── README.md
```

The application is intentionally kept as a single HTML file to make it simple to run, deploy, and maintain.

---

## 📄 License

Released under the [Apache License 2.0](LICENSE).

---

Built with HTML, CSS & JavaScript

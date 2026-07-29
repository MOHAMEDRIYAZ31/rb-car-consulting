# 🚗 RB Car Consulting

A lightweight two-site platform for a used-car consulting business — a public **customer site** to browse cars, and a private **owner dashboard** to add/edit listings in real time. No backend server, no code editing needed to add a new car.

🔗 **Live demo:** _add your deployed links here_
- Customer site: `https://rb-cars-customer.web.app/`
- Owner dashboard: `https://your-owner-site.web.app`

---

## ✨ Features

**Customer Site**
- 🔍 Search cars by model or location
- 🎛️ Filter by ownership count
- 🖼️ Photo gallery with lightbox viewer (swipe/arrow-key navigation)
- 📞 One-tap "Call Seller" button
- 📱 Fully responsive, mobile-first layout
- ⚡ Live updates — new listings appear instantly, no refresh needed

**Owner Dashboard**
- 🔐 Secure email/password login (Firebase Auth)
- ➕ Add, ✏️ edit, and 🗑️ delete car listings
- 📸 Multi-photo upload with live preview
- 🧾 Simple form — model, year, fuel, ownership, km, price, and more
- 🔄 Changes sync to the customer site in real time

---

## 🛠️ Tech Stack

| Layer | Tech |
|---|---|
| Frontend | HTML, CSS, Vanilla JS |
| Auth | Firebase Authentication |
| Database | Cloud Firestore |
| Storage | Firebase Storage (car photos) |
| Hosting | Firebase Hosting |

No frameworks, no build step — just plain HTML/CSS/JS talking directly to Firebase.

---

## 📁 Project Structure

```
rb-car-consulting/
├── customer-site/
│   └── index.html        # Public-facing car listings
├── owner-site/
│   └── index.html        # Owner login + dashboard
├── firebase.json         # Multi-site Hosting config
└── .firebaserc            # Firebase project alias
```

---

## 🚀 Getting Started

1. **Clone the repo**
   ```bash
   git clone https://github.com/MOHAMEDRIYAZ31/rb-car-consulting.git
   cd rb-car-consulting
   ```

2. **Create a Firebase project** at [console.firebase.google.com](https://console.firebase.google.com), then enable:
   - Authentication → Email/Password
   - Firestore Database
   - Storage

3. **Add your Firebase config** into the `firebaseConfig` object inside both `customer-site/index.html` and `owner-site/index.html`.

4. **Set security rules** so only the logged-in owner can write data (see below).

5. **Deploy**
   ```bash
   npm install -g firebase-tools
   firebase login
   firebase deploy --only hosting
   ```

---

## 🔒 Security Rules

**Firestore**
```js
match /cars/{carId} {
  allow read: if true;
  allow write: if request.auth != null;
}
```

**Storage**
```js
match /{allPaths=**} {
  allow read: if true;
  allow write: if request.auth != null;
}
```

Anyone can *view* listings and photos — only the authenticated owner can *add or change* them.

---

## 📸 Preview

     (owner.png)
     (customer.png)
---

## 📬 Contact

**RB Car Consulting**
📞 +91 73393 52147

---

<p align="center">Built with ❤️ using Firebase</p>

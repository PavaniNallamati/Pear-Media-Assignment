# Pear Media AI Prototype 🚀

## 📌 Overview

This project is a web-based AI application that processes both **text and image inputs** to generate enhanced prompts and AI-generated images.

It demonstrates the integration of multiple AI APIs for **Natural Language Processing (NLP)** and **Computer Vision workflows**.

---

## ⚙️ Tech Stack

* React.js
* Tailwind CSS
* OpenAI API (Text Enhancement & Image Generation)
* Google Gemini API (Image Analysis)

---

## ✨ Features

### 🟣 Text Workflow

* User enters a simple prompt
* AI enhances the prompt using NLP
* User can edit and approve the enhanced prompt
* AI generates an image based on the final prompt

---

### 🔵 Image Workflow

* User uploads an image
* AI analyzes:

  * Objects
  * Style
  * Colors
* AI generates variations based on analysis

---

## 🛠️ How to Run Locally

### 1. Clone Repository

```bash
git clone https://github.com/your-username/pearmedia-ai-prototype
cd pearmedia-ai-prototype
```

### 2. Install Dependencies

```bash
npm install
```

### 3. Setup Environment Variables

Create a `.env` file in the root directory:

```env
REACT_APP_OPENAI_KEY=your_openai_api_key
REACT_APP_GEMINI_KEY=your_gemini_api_key
```

### 4. Start the App

```bash
npm start
```

---

## 🌐 Deployment

The application is deployed using Vercel.

---

## 🎥 Demo Video

(Add your screen recording link here)

---

## 📸 Screenshots

(Add screenshots of your UI and results here)

---

## 📂 Project Structure

```
src/
├── components/
│   ├── WorkflowText.js
│   ├── WorkflowImage.js
│   └── ImageCard.js
├── utils/
│   └── apiHelpers.js
├── App.js
```

---

## ⚠️ Notes

* API keys are stored securely using `.env`
* `.env` file is excluded using `.gitignore`
* Error handling is implemented using try/catch

---

## ✅ Conclusion

This project successfully demonstrates:

* API integration
* Prompt engineering
* Image processing workflows
* Clean UI/UX design

---

## 🙌 Acknowledgements

* OpenAI
* Google Gemini

---

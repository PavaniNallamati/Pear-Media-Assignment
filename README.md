## 1. Objective The primary goal is to build a responsive web application that bridges the gap between simple user inputs and advanced AI outputs through two specific logic flows: - **Workflow A (Text):** Uses NLP to "engineer" a better prompt, requires human-in-the-loop approval, and generates an image. - **Workflow B (Image):** Uses Computer Vision to reverse-engineer an image's metadata and style to create stylistic variations. ## 2. Technical Requirements ### Required Environment - **Node.js (v18+):** The runtime for React. - **npm or yarn:** Package managers to handle libraries like axios or lucide-react. - **VS Code Extensions:** Prettier (for formatting) and ES7+ React/Redux/React-Native snippets. ### The "Pear Media" API Stack Choose at least one from each category for the full 6-hour sprint: 1. **Text Analysis & Generation:** * *Option 1:* OpenAI (GPT-4o-mini) - Best for intent analysis. - *Option 2:* Gemini 1.5 Flash - Best because it has a high free tier and handles both text and vision. 2. **Image Generation:** * *Option 1:* Stability AI (SDXL) - High-quality artistic control. - *Option 2:* DALL-E 3 - Easiest integration via OpenAI SDK. 3. **Vision/Analysis:** - *Option 1:* Gemini 1.5 Flash (Multimodal). - *Option 2:* Hugging Face (Salesforce/BLIP models) for free image captioning. ## 3. Detailed Step-by-Step Instructions ### Phase 1: Setup & Security (30 Minutes) 1. **Create the Gmail:** Register namepearmedia@gmail.com. Use this for all API signups to keep keys centralized. 2. **Project Start:** Run npx create-react-app pear-media-lab. 3. **Environment Variables:** Create a .env file in the root. - *Tip:* Always prefix variables with REACT_APP_ (e.g., REACT_APP_GEMINI_KEY=...) so React can access them. - *Warning:* Add .env to your .gitignore file immediately to avoid leaking keys to GitHub. ### Phase 2: UI Foundation (60 Minutes) 1. **Layout Design:** Use a "Two-Pane" or "Tabbed" layout. - **Tab 1:** Creative Studio (Text Workflow). - **Tab 2:** Style Lab (Image Workflow). 2. **Global Loading State:** Create a single isLoading state. Use a progress bar or a spinner to give the user feedback during long API calls. 3. **Tailwind/CSS:** Focus on a "Clean Tech" aesthetic: rounded corners (rounded-xl), lots of white space, and indigo/violet primary colors. ### Phase 3: The Text Workflow (90 Minutes) 1. **Step 1 (The Hook):** Capture user input in a state variable (userPrompt). 2. **Step 2 (The Enhancement):** Send userPrompt to an NLP API. - *System Prompt:* "You are an expert prompt engineer. Transform the following simple request into a 50-word descriptive masterpiece including lighting, camera angle, and artistic style." 3. **Step 3 (The Approval):** Render the enhanced text in an editable <textarea>. - *Logic:* Only show the "Generate Image" button after this text is returned. 4. **Step 4 (Final Image):** Send the *edited/approved* text to the image API (e.g., DALL-E 3). ### Phase 4: The Image Workflow (90 Minutes) 1. **Image Handling:** Use FileReader API to convert the user's file into a Base64 string. 2. **Visual Analysis:** Send the Base64 string to a vision model. Ask for: - Main Objects - Color Palette - Artistic Style (e.g., Cyberpunk, Oil Painting) 3. **Variation Generation:** Construct a new prompt using those identified details and trigger the Image Generation API. ### Phase 5: Deployment & Documentation (60 Minutes) 1. **GitHub:** Create a repository named pearmedia-ai-prototype. 2. **README:** Use the "Project Structure" below as a template. Include "How to Run" instructions. 3. **Vercel:** Import the repo. Add your .env keys in the Vercel Dashboard "Environment Variables" section. 4. **Demo Video:** Use Loom or OBS to record a 5-minute walkthrough. ## 4. Project Structure
pearmedia-ai-prototype/
├── .env                    # Secret API Keys
├── .gitignore              # Files to ignore (node_modules, .env)
├── README.md               # Detailed project documentation
├── package.json            # Project dependencies
└── src/
    ├── App.js              # State management & Main Layout
    ├── App.css             # Custom styles and animations
    ├── components/
    │   ├── Navbar.js       # Navigation and Logo
    │   ├── WorkflowText.js # Input, Enhance, Approve, Generate logic
    │   ├── WorkflowImage.js# Upload, Analyze, Variation logic
    │   └── ImageCard.js    # Reusable component to display results
    └── utils/
        ├── apiHelpers.js   # All fetch() logic organized by API
        └── constants.js    # Default prompts and configuration
## 5. Example Codes & Logic ### Advanced API Integration Logic (utils/apiHelpers.js) This structure allows you to swap APIs easily without breaking the UI.
// Function to handle the "Enhance" step
export const getEnhancedPrompt = async (input) => {
  try {
    const response = await fetch('https://api.openai.com/v1/chat/completions', {
      method: 'POST',
      headers: {
        'Authorization': `Bearer ${process.env.REACT_APP_OPENAI_KEY}`,
        'Content-Type': 'application/json'
      },
      body: JSON.stringify({
        model: "gpt-4o-mini",
        messages: [{
          role: "system",
          content: "Enhance this image prompt for a professional photographer."
        }, {
          role: "user",
          content: input
        }]
      })
    });
    const data = await response.json();
    return data.choices[0].message.content;
  } catch (error) {
    console.error("Enhancement failed:", error);
    return input; // Fallback to original
  }
};
### Multimodal Analysis Helper (Gemini Example) How to send an image for analysis.
const analyzeImage = async (base64Image) => {
  // Logic to send to Gemini-Vision
  // The prompt should ask for JSON or a structured list
  const prompt = "Analyze this image and list: 1. Main Subject 2. Lighting 3. Style.";

  // Return the analysis to be used in the next generation step
};
### Error Handling Strategy Don't let the app crash. Use try/catch blocks for every network request and update a statusMessage state to tell the user what went wrong (e.g., "Invalid API Key" or "Image too large"). ## 6. **Submission Guidelines:** - Hosted Link (Vercel/Render/Netlify + Backend on Render) - GitHub Repository (well-structured codebase) - README file with: - Tech stack - Features - How to run locally - Screenshots Submit Your Screen Record link ### **Submission Details** 1. **GitHub Repository Link:** 👉 https://github.com/your-username/your-repo-name 2. **Deployed / Published Application Link:** 👉 https://your-frontend.vercel.app 3. **Screen Recording (Drive Link):** 👉 https://drive.google.com/file/d/your-screen-recording-link/view

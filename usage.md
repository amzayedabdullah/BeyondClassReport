# How to Use

## User Side Guide (Getting Started)
1.  **Sign Up**: Create an account on the BeyondClass platform.
2.  **Browse Courses**: Navigate to the dashboard to see available modules.
3.  **Start Learning**: Click on a module (e.g., "Git Mastery") to begin lessons.
4.  **Submit Assignments**: At the end of a module, complete the task and submit your code for AI feedback.

## Programmer Side Guide (Getting Started)
1.  **Clone the Repository**:
    ```bash
    git clone https://github.com/amzayedabdullah/BeyondClass.git
    cd BeyondClass
    ```
2.  **Install Dependencies**:
    ```bash
    npm install
    ```
3.  **Set Up Environment**:
    -   Create a `.env.local` file.
    -   Add Supabase credentials (`NEXT_PUBLIC_SUPABASE_URL`, `NEXT_PUBLIC_SUPABASE_ANON_KEY`) and AI API keys.
4.  **Run Development Server**:
    ```bash
    npm run dev
    ```
    Open [http://localhost:3000](http://localhost:3000) with your browser.

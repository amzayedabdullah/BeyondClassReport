# AI-Assisted Assignments & Auto-Grading

## Non-Technical Description
Each module ends with an industry-style practical task.
**Workflow:**
1.  Students submit code for an assignment.
2.  The system tests it.
3.  AI provides instant, friendly feedback, allowing students to improve immediately.

## Technical Implementation
**AI Integration:**
-   **Library**: `ai` (Vercel AI SDK) and `@ai-sdk/google`.
-   **Model**: Google Generative AI (e.g., Gemini) is configured for text generation.

**Backend Workflow (`/api/assignment/submit`):**
1.  **Input Processing**: Receives `assignmentId`, `answers`, and `userId`.
2.  **Context Retrieval**: Fetches the specific assignment questions and rubric from the `assignments` table in Supabase.
3.  **AI Grading**:
    -   Constructs a prompt containing the question, student's answer, and correct answer criteria.
    -   Calls `generateText` to evaluate the submission.
    -   Returns a JSON object with `score`, `feedback` per question, and `general_feedback`.
4.  **Progression Logic**:
    -   If `score >= 70`, the system updates `lesson_progress` table.
    -   Automatically finds the next lesson (based on `sort_order`) and unlocks it by ensuring an entry exists in `lesson_progress` with `is_unlocked: true`.

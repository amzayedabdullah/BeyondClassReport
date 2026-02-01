# Module-Based Learning System

## Non-Technical Description
The platform is organized into practical, skill-focused modules such as Git, Linux, Bash, MERN, Laravel, and more.
**Workflow:**
1.  Students pick a module.
2.  Lessons appear in short, structured sections with curated videos.
3.  Progress is tracked automatically as they learn at their own pace.

## Technical Implementation
**Database Schema (Supabase):**
The curriculum is structured using a relational model in PostgreSQL/Supabase:
-   **`modules` Table**: Groups lessons together.
    -   Columns: `id`, `course_id`, `title`, `sort_order`.
-   **`lessons` Table**: Contains the actual content.
    -   Columns: `id`, `module_id`, `title`, `video_url`, `content` (Markdown), `duration`, `is_preview`.
    -   Foreign Key: `module_id` references `modules(id)`.

**API Architecture:**
-   **Endpoint**: `GET /api/course/[id]/curriculum`
-   **Logic**:
    1.  Fetches all modules for the course, ordered by `sort_order`.
    2.  Extracts all `module_id`s.
    3.  Performs a single optimized query to fetch all lessons where `module_id` is in the list (using `.in('module_id', moduleIds)`).
    4.  Maps lessons to their respective modules in memory to construct a nested JSON response.
    -   *Benefit*: Reduces database round-trips compared to querying lessons for each module individually (N+1 problem).

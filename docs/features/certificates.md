# Skill Certificates & Portfolio Builder

## Non-Technical Description
Students earn certificates to showcase their skills and build a professional identity.
**Workflow:**
1.  Every completed module generates a skill certificate.
2.  Completing all modules unlocks the full course certificate.
3.  Tasks and projects automatically appear in a shareable portfolio.

## Technical Implementation
**Client-Side PDF Generation:**
-   **Library**: `jspdf`.
-   **Component**: `CertificationCard.jsx`.
-   **Logic**:
    -   The certificate is generated entirely in the browser (no server load).
    -   Initializes a `jsPDF` instance with landscape orientation (`600x400` px).
    -   **Styling**:
        -   Draws a border using `doc.rect(20, 20, 560, 360)` with a 10px line width.
        -   Uses custom fonts ("helvetica", "times") for typography hierarchy.
        -   Specifically centers text using `{ align: "center" }` coordinates (e.g., Student Name at `x: 300`).
    -   **Dynamic Data**: Injects `userName` and `course.title` directly into the canvas.
    -   **Output**: Triggers a download via `doc.save('${course.title}_Certificate.pdf')`.

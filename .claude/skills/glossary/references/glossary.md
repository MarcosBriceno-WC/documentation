# Glossary Reference

Full alphabetical glossary for technical writing projects.  
Maintained as a reference file — consumed by `SKILL.md`.

---

### Abbreviation [noun]
**Definition:** A shortened form of a word or phrase, typically consisting of the first letter(s) or a truncated version of the original (e.g., *dept.* for *department*). Distinct from an acronym or initialism.  
**Usage Context:** Use in body text when a term is long and recurs frequently. Always spell out the full term on first use, followed by the abbreviation in parentheses.  
**Example:** "The configuration management database (CMDB) tracks all infrastructure assets. Query the CMDB before making changes."  
**Related Terms:** Acronym, Initialism  
**Usage Note:** Do not introduce an abbreviation unless the term appears at least three more times after its first use.

---

### Acronym [noun]
**Definition:** An abbreviation formed from the initial letters of a phrase that is pronounced as a single word (e.g., *NASA*, *SCUBA*).  
**Usage Context:** Spell out on first use. Apply title case or all caps per your project style guide.  
**Example:** "The product meets all requirements of the Self-Contained Underwater Breathing Apparatus (SCUBA) certification standard."  
**Related Terms:** Abbreviation, Initialism  
**Usage Note:** Do not confuse with *initialism*. An acronym is spoken as a word; an initialism is spelled out letter by letter. *FBI* is an initialism; *NATO* is an acronym.

---

### Active Voice [noun phrase]
**Definition:** A sentence construction in which the grammatical subject performs the action expressed by the verb (e.g., "The administrator configures the server").  
**Usage Context:** Preferred in technical writing for clarity, directness, and reduced word count. Particularly important in procedural steps.  
**Example:** "Click **Save** to apply your changes." (active) vs. "The changes are applied when **Save** is clicked." (passive)  
**Related Terms:** Passive Voice  
**Usage Note:** Passive voice is appropriate when the actor is unknown, irrelevant, or when you want to de-emphasize responsibility.

---

### Admonition [noun]
**Definition:** A visually distinct notice embedded in a document to alert the reader to important information, potential risks, or required actions. Common types: Note, Tip, Caution, Warning, Danger.  
**Usage Context:** Use sparingly so admonitions retain their signal value. Place immediately before or after the content they relate to.  
**Example:** "> **Warning:** Deleting this partition permanently removes all data. This action cannot be undone."  
**Related Terms:** Callout, Note, Warning  
⚠️ **Variation Note:** Hierarchy and labels vary by standard. DITA defines *note*, *tip*, *fastpath*, *restriction*, *important*, *attention*, *caution*, and *danger*. Microsoft Style Guide uses *Note*, *Tip*, *Important*, *Caution*, and *Warning*. Establish the set your project will use at the outset.

---

### Audience Analysis [noun phrase]
**Definition:** The process of identifying and documenting the characteristics, needs, technical background, goals, and constraints of the people who will read a document.  
**Usage Context:** Performed at the start of any documentation project. May be formal (structured persona development) or informal (stakeholder interviews, support ticket review).  
**Example:** "Our audience analysis revealed that most users are facilities managers with no programming background, so all API references were moved to an appendix."  
**Related Terms:** Persona, User Research, Stakeholder

---

### Callout [noun]
**Definition:** A visually separated block of text—often boxed, shaded, or icon-tagged—that draws attention to supplementary or critical information without interrupting the main narrative flow.  
**Usage Context:** Used to highlight tips, warnings, cross-references, or asides. Overuse dilutes impact.  
**Related Terms:** Admonition, Sidebar, Pull Quote  
**Usage Note:** In structured authoring environments (particularly DITA), *admonition* carries specific semantic meaning. Prefer *admonition* in DITA contexts.

---

### Chunking [noun]
**Definition:** The practice of dividing content into small, discrete, self-contained units that each address a single idea or task.  
**Usage Context:** Applied during content planning and information architecture. Foundational to topic-based writing and DITA.  
**Example:** "Instead of one long 'Getting Started' page, we chunked the content into three topics: system requirements, installation, and initial configuration."  
**Related Terms:** Topic, Modular Writing, Information Architecture

---

### Conditional Text [noun phrase]
**Definition:** Content tagged so it appears only in specific output versions—based on audience, product variant, platform, or delivery format.  
**Usage Context:** Used in single-sourcing environments where one source file produces multiple outputs.  
**Example:** "We used conditional text to exclude the Linux installation steps from the Windows-only PDF output."  
**Related Terms:** Profiling, Filtering, Single Sourcing, Variant

---

### Content Reuse [noun phrase]
**Definition:** The practice of writing content once and incorporating it into multiple documents without duplicating the source text. Changes to the source automatically propagate to all locations.  
**Usage Context:** Core practice in structured authoring, DITA, and component content management systems (CCMS).  
**Example:** "The standard disclaimer is stored as a single reusable component and pulled into all twelve user guides automatically."  
**Related Terms:** Conref (DITA), Snippet, Modular Writing, Single Sourcing

---

### DITA [noun, initialism]
**Definition:** Darwin Information Typing Architecture. An XML-based open standard for authoring, producing, and delivering technical content. Structures content into typed topics (task, concept, reference) and supports robust content reuse and conditional publishing.  
**Usage Context:** Used in large-scale documentation environments, particularly in software, hardware, and regulated industries.  
**Example:** "All product documentation is authored in DITA and published to both PDF and HTML5 using a custom DITA-OT transform."  
**Related Terms:** Topic, Content Reuse, XML, DITA-OT, Structured Authoring  
⚠️ **Variation Note:** DITA has its own terminology that sometimes conflicts with general technical writing vocabulary (e.g., *map*, *conref*, *profiling*). Avoid importing DITA-specific terms into non-DITA environments without explanation.

---

### Draft [noun / verb]
**Definition:** (noun) A preliminary version of a document, not yet approved for publication. (verb) The act of writing that preliminary version.  
**Usage Context:** Documents typically move through defined draft stages (First Draft → Review Draft → Final Draft → Approved).  
**Example:** "Please review the attached review draft and return comments by Friday."  
**Related Terms:** Review Cycle, Revision, Version

---

### End User [noun phrase]
**Definition:** The person who ultimately uses a product, system, or document in the course of their regular work or daily life. Distinct from the buyer, implementer, or administrator.  
**Usage Context:** Used in audience analysis and persona development.  
**Related Terms:** Audience, Persona, Stakeholder  
**Usage Note:** Avoid the redundant construction *end user user*. Write *end user* or simply *user* once the audience has been established.

---

### Front Matter [noun phrase]
**Definition:** The introductory pages of a document preceding the main body. Typically includes the title page, copyright notice, table of contents, list of figures or tables, and a preface or introduction.  
**Usage Context:** Standard in formal technical documents such as user manuals, specifications, and reports.  
**Related Terms:** Back Matter, Body, Table of Contents

---

### Heading [noun]
**Definition:** A title or label that introduces a section, organized hierarchically (H1, H2, H3, etc.).  
**Usage Context:** Every major section requires a heading. Headings should be descriptive, parallel in structure, and consistent in capitalization style.  
**Example:** "**Installing the Software**" (H2) followed by "**System Requirements**" (H3).  
**Related Terms:** Title, Section, Hierarchy, Table of Contents  
**Usage Note:** Do not skip heading levels. Screen readers and automated TOC generators depend on a logical heading hierarchy.

---

### Index [noun]
**Definition:** An alphabetical list of terms, topics, and names found in a document, with corresponding page or section references.  
**Usage Context:** Required in long-form print documents such as reference manuals. Less common in web-based documentation, where full-text search serves the same function.  
**Related Terms:** Table of Contents, Metadata, Findability

---

### Information Architecture [noun phrase]
**Definition:** The structural design of a document or documentation set—how content is organized, labeled, and navigated.  
**Usage Context:** Established during the planning phase. Documented in a content plan, site map, or TOC outline.  
**Example:** "Before writing began, the team developed an information architecture that grouped content into three main areas: Setup, Configuration, and Troubleshooting."  
**Related Terms:** Chunking, Navigation, Table of Contents, Content Strategy

---

### Initialism [noun]
**Definition:** An abbreviation formed from the initial letters of a phrase, where each letter is pronounced individually (e.g., *FBI*, *HTML*, *API*).  
**Usage Context:** Spell out on first use. Whether to use *the* before an initialism depends on pronunciation (e.g., "the HTML file").  
**Related Terms:** Acronym, Abbreviation  
**Usage Note:** See *Acronym* for the distinction between acronyms and initialisms.

---

### Inline Definition [noun phrase]
**Definition:** A brief explanation of a term provided directly in body text—typically in parentheses or set off by an em dash—rather than referring the reader to a separate glossary entry.  
**Usage Context:** Use when a term appears infrequently, the audience is unlikely to consult a glossary, or the definition is short enough not to disrupt reading flow.  
**Example:** "The system uses a daemon (a background process that runs without direct user interaction) to manage scheduled tasks."  
**Related Terms:** Glossary, Parenthetical, Appositive  
**Usage Note:** If a term requires more than one sentence to define, direct the reader to the glossary rather than defining inline.

---

### Localization [noun]
**Definition:** The process of adapting a document for a specific locale, including translation of text and adjustment of cultural references, date formats, units of measure, images, and other locale-specific elements.  
**Usage Context:** Relevant for documentation distributed in more than one country or language. Distinct from *translation*, which refers only to converting text from one language to another.  
**Example:** "The user guide required localization for the Japanese market, including translation, conversion of units to metric, and replacement of US-centric example scenarios."  
**Related Terms:** Translation, Internationalization (i18n), Globalization  
⚠️ **Variation Note:** *Localization* and *translation* are frequently conflated in casual usage. In professional contexts, they are distinct activities with different scope and cost implications.

---

### Metadata [noun]
**Definition:** Data that describes a document or content component—such as title, author, creation date, version, subject, audience, and language.  
**Usage Context:** Assigned to documents in a CMS, CCMS, or repository. Also embedded in file properties or DITA map attributes.  
**Example:** "Without accurate metadata, the search tool cannot surface the correct version of the installation guide for each product release."  
**Related Terms:** Taxonomy, Tagging, Findability, DITA

---

### Minimalism [noun]
**Definition:** A technical writing philosophy that advocates for providing only the information a user needs to complete a task—eliminating background theory, redundant explanation, and unsolicited detail. Based on John Carroll's research.  
**Usage Context:** Applied during content planning and editing. Minimalism means *purposeful*, not *sparse*.  
**Example:** "Following minimalist principles, the team removed the five-page product history section from the quick-start guide and replaced it with a single paragraph linking to the product overview."  
**Related Terms:** Task Orientation, User-Centered Design, Chunking

---

### Modular Writing [noun phrase]
**Definition:** A writing approach in which content is created as independent, self-contained units (modules or topics) that can be combined, reordered, or reused across multiple documents and outputs.  
**Usage Context:** Foundational to structured authoring and single-sourcing strategies.  
**Related Terms:** Topic, Chunking, Content Reuse, DITA

---

### Passive Voice [noun phrase]
**Definition:** A sentence construction in which the grammatical subject receives the action rather than performing it (e.g., "The report was submitted by the analyst").  
**Usage Context:** Generally avoided in technical writing. Acceptable when the actor is unknown or unimportant, or when focus belongs on the object rather than the subject.  
**Example:** "The server must be restarted after each configuration change." (acceptable passive—actor implied by context)  
**Related Terms:** Active Voice

---

### Persona [noun]
**Definition:** A fictional but research-based profile of a representative user, created to guide documentation decisions. Captures goals, background, technical skill level, frustrations, and typical use scenarios.  
**Usage Context:** Developed during audience analysis. Referenced throughout the project to answer questions like "Would our user know this term?"  
**Example:** "Persona: 'Dana, the Field Technician' — 10 years of hands-on hardware experience, no programming background, works under time pressure, prefers visual job aids over long text."  
**Related Terms:** Audience Analysis, User Research, End User

---

### Procedure [noun]
**Definition:** A set of numbered steps a user follows to complete a specific task. Each step describes a single, discrete action written in the imperative mood.  
**Usage Context:** The core content unit in task-based documentation. A well-formed procedure includes a goal statement, prerequisites, numbered steps, and an expected result.  
**Example:** Step 1: "Click **File**, then select **Export**." Step 2: "Choose a file format from the dropdown menu."  
**Related Terms:** Task, Step, Tutorial, Work Instruction  
**Usage Note:** Do not combine two actions in one step unless the actions are inseparable.

---

### Readability [noun]
**Definition:** The ease with which a reader can understand written text. Influenced by sentence length, word choice, structure, white space, and formatting. Often measured using readability scores (e.g., Flesch-Kincaid Grade Level).  
**Usage Context:** A primary quality metric for technical documents. Targets should be set based on audience analysis.  
**Related Terms:** Plain Language, Scannability, Audience Analysis  
**Usage Note:** High readability scores do not guarantee comprehension—accurate content, logical structure, and appropriate terminology are equally important.

---

### Release Notes [noun phrase]
**Definition:** A document accompanying a product release that describes new features, bug fixes, known issues, deprecated features, and upgrade considerations.  
**Usage Context:** Published with every product version. Should be structured consistently across releases to support scanning and comparison.  
**Related Terms:** Changelog, Version History, What's New

---

### Revision [noun]
**Definition:** A change made to a document after its initial creation, whether in response to review feedback, updated source information, or quality improvements.  
**Usage Context:** Distinguish between *minor revisions* (corrections, formatting) and *major revisions* (structural changes, new content).  
**Related Terms:** Draft, Version, Review Cycle, Change Log

---

### Scannability [noun]
**Definition:** The quality of a document that allows readers to quickly locate relevant information without reading every word. Achieved through headings, bullet points, tables, numbered lists, bold text, and white space.  
**Usage Context:** Critical for online and reference documentation, where users typically search for specific answers rather than reading linearly.  
**Related Terms:** Readability, Information Architecture, Heading, Chunking

---

### Single Sourcing [noun phrase]
**Definition:** A documentation strategy in which content is authored once and published to multiple formats, audiences, or outputs from that single source—without maintaining separate copies.  
**Usage Context:** Reduces maintenance burden and version drift. Requires a supporting infrastructure (CCMS, DITA, or structured templates).  
**Example:** "Using single sourcing, the team publishes the same core content as a PDF user guide, a web help system, and an in-app tooltip library."  
**Related Terms:** Content Reuse, Conditional Text, DITA, Modular Writing

---

### SME [noun, initialism]
**Definition:** Subject Matter Expert. A person with deep knowledge of a specific technical domain who provides accurate information for documentation.  
**Usage Context:** Technical writers interview SMEs, have SMEs review drafts for technical accuracy, and attribute review sign-off to SMEs in formal processes.  
**Example:** "The security chapter was reviewed by the SME lead for the identity management team before publication."  
**Related Terms:** Stakeholder, Review Cycle, Technical Accuracy

---

### Step [noun]
**Definition:** A single, discrete action within a procedure. Written in the imperative mood, numbered sequentially, describing exactly one action.  
**Usage Context:** The atomic unit of a procedure. Should be completable in one user interaction.  
**Example:** "3. Enter your username in the **Username** field."  
**Related Terms:** Procedure, Task, Substep

---

### Structured Authoring [noun phrase]
**Definition:** A documentation approach in which content is written according to a predefined information model or schema (such as DITA or DocBook), with explicit rules about content types, element hierarchy, and metadata.  
**Usage Context:** Used in organizations that produce high volumes of technical content, require regulatory compliance, or need robust reuse and multi-channel publishing.  
**Related Terms:** DITA, XML, Content Reuse, Single Sourcing

---

### Style Guide [noun phrase]
**Definition:** A document that establishes rules and conventions for writing, formatting, and presenting content within a specific organization or project.  
**Usage Context:** Referenced at every stage of the writing process. Internal style guides take precedence over external reference guides.  
**Example:** "Per our style guide, all UI element names are bolded and match the exact capitalization shown in the interface."  
**Related Terms:** Terminology, Brand Voice, Glossary  
⚠️ **Variation Note:** Common reference style guides include the *Microsoft Writing Style Guide*, *Google Developer Documentation Style Guide*, *Apple Style Guide*, and *The Chicago Manual of Style*. Each differs on specific rules (e.g., Oxford comma, capitalization of UI elements, singular *they*).

---

### Table of Contents (TOC) [noun phrase]
**Definition:** A navigational list, typically placed at the beginning of a document, that lists major sections and their page numbers or hyperlinks.  
**Usage Context:** Required in documents longer than approximately 10 pages or with more than three main sections. In online documentation, often a persistent side panel.  
**Related Terms:** Index, Navigation, Heading, Information Architecture

---

### Task [noun]
**Definition:** A goal-oriented unit of work that a user performs to accomplish a specific objective. In DITA, a *task topic* is a structured content type for supporting one user task.  
**Usage Context:** The foundation of task-based and minimalist documentation. Tasks map to user goals, not system features.  
**Example:** "The task 'Back Up Your Configuration' corresponds to the user goal of protecting their settings, not to the system's export function."  
**Related Terms:** Procedure, Topic, Step, DITA

---

### Technical Accuracy [noun phrase]
**Definition:** The correctness of technical information in a document—ensuring that instructions, specifications, descriptions, and data reflect the actual behavior of the product or system.  
**Usage Context:** Verified through SME review, hands-on testing, and comparison against engineering specifications.  
**Related Terms:** SME, Review Cycle, Verification

---

### Topic [noun]
**Definition:** A discrete, self-contained unit of content that addresses a single subject or supports a single user goal. In structured authoring, classified by type (concept, task, reference).  
**Usage Context:** The foundational building block in DITA and topic-based authoring. Topics should be meaningful when read in isolation.  
**Related Terms:** Chunking, Modular Writing, DITA, Task, Concept, Reference  
⚠️ **Variation Note:** Outside structured authoring, *topic* is sometimes used loosely to mean any section or subject area. In DITA, it has a precise technical meaning with defined element structures.

---

### User-Centered Design (UCD) [noun phrase]
**Definition:** A design philosophy that places the needs, goals, and limitations of the end user at the center of every decision in a product or document's development.  
**Usage Context:** Informs documentation strategy, information architecture, and content decisions. Applied through audience analysis, usability testing, and iterative revision.  
**Related Terms:** Audience Analysis, Persona, Minimalism, Usability Testing

---

### Version Control [noun phrase]
**Definition:** A system that tracks changes to files over time, allowing authors to review revision history, revert to previous versions, and manage concurrent editing. Common tools: Git, Subversion, CCMS versioning.  
**Usage Context:** Essential for documentation maintained by more than one person or synchronized with software releases.  
**Example:** "All documentation source files are stored in a Git repository, with branches for each product release."  
**Related Terms:** Revision, Draft, Change Log, Single Sourcing

---

### White Space [noun phrase]
**Definition:** The empty areas of a page or screen not occupied by text or images—including margins, line spacing, paragraph spacing, and padding.  
**Usage Context:** Used deliberately to improve readability, reduce visual clutter, and guide the reader's eye.  
**Related Terms:** Layout, Scannability, Readability

# Project Description:

Inspecto is an AI-assisted inspection reporting tool that compresses a 2-to-3-hour end-of-
day documentation workflow into minutes. It ingests photos, short voice notes, checklists,
and on-site annotations, then auto-drafts a structured, branded report with clear issues,
severities, location tags, and recommended follow-ups. Inspecto standardizes
terminology, reduces manual copy and paste, and prevents missed items by guiding
inspectors during the walkthrough and pre-filling sections from evidence. Reports export to
PDF and client portals and integrate with existing templates. The result is faster
turnaround, higher report quality and consistency, and improved client trust. Inspectors
spend more time on site and less time on paperwork.

---

# Primary Features:

These are the primary features to be developed first. They are the core of what makes our
product unique and need to be testable in the MVP and prototypes to do determine their
need and value to the app. In their MVP form they will be lightweight features and will not
be connected to Auth or database. The primary feature finished versions will need to have
the dependencies completed first.

## 1. Template Creation

### <a id="p1"></a>P1. Template Setup

User story: As an Efficiency Seeker I want to set up an inspection template quickly so that
future reports are consistent and faster to produce.

Acceptance criteria:

- A Template section exists with options to ‘Upload existing’ or ‘Use guided generator’.
- Saved templates appear in my Template list with name, version, and last updated
  time.
- I can select a saved template when starting a new report.

Estimate: 1 day  
Dependencies: [A1](#a1), [D4](#d4)  
Status: In progress  
Target milestone: M2  
Actual delivery: October 10th

### <a id="p1a"></a>P1 a. Upload Existing Template or Report

User story: As an Efficiency Seeker I want to upload a prior report or template so that the
app can build a reusable template from it.

Acceptance criteria:

- I can upload PDF or DOCX up to the documented size limit.
- After upload, I see an analyzing state.
- Invalid type or unreadable file shows a clear error with retry.
- Uploaded file is stored securely for processing and linked to the derived template.

Estimate: 2 to 3 days  
Dependencies: [A1](#a1), [D4](#d4)  
Status: Nearly completed  
Target milestone: M2  
Actual delivery: October 10th

### <a id="p1b"></a>P1 b. AI Extraction to Derive Template

User story: As an Efficiency Seeker I want the app to analyze my uploaded file and extract
sections, styles, and components so that I get a template that matches my past work.

Acceptance criteria:

- The system identifies sections, headings, common components, and any severity
  fields.
- Styles such as heading hierarchy and caption patterns are captured where possible.
- The derived template is structured into editable sections and fields.
- A summary shows what was detected and anything that needs manual review.

Estimate: 7 days  
Dependencies: [P1A](#p1a), [D7](#d7)  
Status: In progress  
Target milestone: M3  
Actual delivery: October 31st

### <a id="p1c"></a>P1 c. Guided Generator for Generic Template

User story: As an Efficiency Seeker I want a guided flow to create a generic template so that
I can start without an existing report.

Acceptance criteria:

- I can step through a checklist of components such as Cover, Summary, Rooms or
  Areas, Issues, Severity, Photos, Recommendations.
- My selections produce a draft template with sensible defaults.
- I can edit names and order of sections before saving.
- I can cancel and resume the generator without losing progress.

Estimate: 2 to 3 days  
Dependencies: [A1](#a1), [D4](#d4)  
Status: Not started  
Target milestone: M3  
Actual delivery: October 31st

### <a id="p1d"></a>P1 d. Template Preview and Save

User story: As an Efficiency Seeker I want to preview and edit a draft template before saving
so that it fits my needs.

Acceptance criteria:

- I see a preview of the draft template with editable section names and fields.
- I can reorder sections and toggle optional components.
- Saving creates a reusable template with name and version.
- The template appears in my Template list and can be selected when starting a
  report.

Estimate: 2 to 3 days  
Dependencies: [P1B](#p1b) or [P1C](#p1c), [D4](#d4)  
Status: Not started  
Target milestone: M3  
Actual delivery: October 31st

### <a id="p1e"></a>P1 e. Error Handling and Validation

User story: As an Efficiency Seeker I want clear feedback when something fails so that I can
correct issues and continue.

Acceptance criteria:

- Invalid file type, file too large, or parse failure shows a clear message and retry.
- Generator failures show a message and allow me to resume or start over.

Estimate: 1 day  
Dependencies: [P1A](#p1a), [P1B](#p1b), [P1C](#p1c)  
Status: Not started  
Target milestone: M3  
Actual delivery: October 31st

---

## 2. Report Initialization

### <a id="p2"></a>P2. Report Initialization from Template

User story: As an Efficiency Seeker I need to start a new report so that most client and
property data is already loaded into the template before my inspection.

Acceptance criteria:

- I can click or tap Start New Report.
- I can select an existing template from my Template list.
- A draft report is created and opened for editing.
- MVP shows a mock save confirmation without auth or database.

Estimate: 1 day  
Dependencies: [P1](#p1)  
Status: In progress  
Target milestone: M3  
Actual delivery: October 31st

### <a id="p2a"></a>P2 a. Template selection or upload at report start

User story: As an Efficiency Seeker I want to choose a template or upload one at report
start so that the report matches my format.

Acceptance criteria:

- I can press Select a template to pick from my saved templates.
- I can choose Upload a template if I do not have one saved.
- The chosen or uploaded template populates the draft report structure.
- Errors for missing or invalid template show a clear message and retry.

Estimate: 1 to 2 days  
Dependencies: [P1A](#p1a), [P1D](#p1d)  
Status: In progress  
Target milestone: M3  
Actual delivery: October 31st

### <a id="p2b"></a>P2 b. MLS lookup and prefill

User story: As an Efficiency Seeker I want to prefill client and property details from MLS so
that I do less manual typing.

Acceptance criteria:

- I can insert an MLS link to the listing or search for the property.
- If MLS prefill succeeds, the app fills client and property fields in the draft.
- If MLS prefill fails, the app explains the issue and falls back to manual entry.
- MVP uses mocked MLS responses. Full version uses APIs and stores results.

Estimate: 2 to 3 days  
Dependencies: [D4](#d4), [D7](#d7)  
Status: Not started  
Target milestone: M3  
Actual delivery: October 31st

### <a id="p2c"></a>P2 c. Manual property entry

User story: As an Efficiency Seeker I want to enter property details manually so that I can
proceed without MLS access.

Acceptance criteria:

- I can manually fill client name, address, unit, city, postal code, and other fields.
- Required fields are validated before save.
- Manually entered data appears in the draft report immediately.
- MVP persists to local storage. Full version persists to the database.

Estimate: 1 to 2 days  
Dependencies: [P2](#p2)  
Status: Not started  
Target milestone: M3  
Actual delivery: October 31st

### <a id="p2d"></a>P2 d. Draft creation, autosave, and temporary storage

User story: As an Efficiency Seeker I want reliable saves so that my work is not lost while I
set up the report.

Acceptance criteria:

- On submit, the app creates a draft report and shows last saved time.
- Autosave runs after key edits or data entries.
- MVP uses in memory or local storage as a temporary store.
- Full version writes drafts to PostgreSQL with a unique draft id.

Estimate: 1 to 2 days  
Dependencies: [D2](#d2)  
Status: Not started  
Target milestone: M3 or M4  
Actual delivery: November 28th

### <a id="p2e"></a>P2 e. Suggested checklist attach

User story: As an Efficiency Seeker I want a suggested checklist based on the template and
property so that I do not miss key items.

Acceptance criteria:

- The app shows a suggested checklist that I can edit before inspection.
- I can create a new checklist or load a previously created one.
- The chosen checklist is attached to the draft report.
- MVP uses a static ruleset. Full version uses rules derived from template
  components.

Estimate: 2 days  
Dependencies: [P1D](#p1d)  
Status: Not started  
Target milestone: M3 or M4  
Actual delivery: November 28th

### <a id="p2f"></a>P2 f. Ready for Inspection state

User story: As an Efficiency Seeker I want to mark the draft as Ready for Inspection so that
the report is prepared for on-site work.

Acceptance criteria:

- I can click or press Ready for Inspection.
- The report status changes to Ready and is visible in my report list.
- Any missing required fields are flagged before allowing Ready state.
- MVP updates status in memory. Full version updates status in the database.

Estimate: 1 day  
Dependencies: [P2D](#p2d)  
Status: Not started  
Target milestone: M3  
Actual delivery: October 31st

### <a id="p2g"></a>P2 g. Error handling

User story: As an Efficiency Seeker I want clear messages when something fails so that I
can fix issues and continue.

Acceptance criteria:

- Missing template, failed MLS lookup, or invalid manual fields show actionable
  messages.

Estimate: 2 to 3 days  
Dependencies: [P2A](#p2a), [P2B](#p2b), [P2C](#p2c)  
Status: Not started  
Target milestone: Future  
Actual delivery: —

---

## 3. On-site Capture

### <a id="p3"></a>P3. On-site Capture entry

User story: As an Efficiency Seeker I want to load an initialized report at the job site or start
a new one so that I can begin my inspection immediately.

Acceptance criteria:

- From the home screen I can choose Load Report or Start New Report.
- I can search and select the correct draft.
- I see a confirmation that the report is ready to start.
- MVP shows mock save without auth or database.

Estimate: 1 day  
Dependencies: [P2](#p2)  
Status: Not started  
Target milestone: M3  
Actual delivery: October 31st

### <a id="p3a"></a>P3 a. Checklist view and quick create

User story: As an Efficiency Seeker I want to see or quickly make a checklist so that I can
follow a structured workflow.

Acceptance criteria:

- I can view the checklist attached to the draft report.
- I can add, rename, reorder, or delete checklist items.
- Changes are reflected immediately in the current session.

Estimate: 1 to 2 days  
Dependencies: [P2E](#p2e)  
Status: Not started  
Target milestone: M3  
Actual delivery: October 31st

### <a id="p3b"></a>P3 b. Photo capture per checklist item

User story: As an Efficiency Seeker I want to take many photos per checklist location so
that I can document evidence thoroughly.

Acceptance criteria:

- From a checklist item I can capture a set number of photos.
- I can select a photo to annotate and save the annotation.
- MVP stores photos locally; full version links to media storage.

Estimate: 2 to 3 days  
Dependencies: [P3A](#p3a), [D7](#d7)  
Status: Not started  
Target milestone: M3  
Actual delivery: October 31st

### <a id="p3c"></a>P3 c. Photo annotation and risk tagging

User story: As an Efficiency Seeker I want to draw on photos and set a risk level so that
issues are clear.

Acceptance criteria:

- I can draw simple shapes such as circles on a selected photo.
- I can choose a Risk Level from a dropdown that is editable in Settings.
- Annotations and risk level are saved with the photo record.
- I can undo or clear annotations before saving.

Estimate: 3 to 4 days  
Dependencies: [P3B](#p3b), [A4](#a4)  
Status: Not started  
Target milestone: M4 or M5  
Actual delivery: December 5th

### <a id="p3d"></a>P3 d. Text notes and voice transcription

User story: As an Efficiency Seeker I want to attach notes and short voice recordings so
that I capture details hands free.

Acceptance criteria:

- I can type a note attached to the current header item.
- I can press Voice Record to capture a short note and see a transcription.
- The note or transcription is linked to the same checklist item.

Estimate: 2 to 3 days  
Dependencies: [P3A](#p3a)  
Status: In Progress  
Target milestone: M2 or M3  
Actual delivery: October 31st

### <a id="p3e"></a>P3 e. Video capture

User story: As an Efficiency Seeker I want to record short videos when needed so that I can
show motion or sound issues.

Acceptance criteria:

- I can press Video Record to capture a clip attached to the current checklist item.
- Thumbnails appear in the item’s evidence list.

Estimate: 2 days  
Dependencies: [P3A](#p3a), [D7](#d7)  
Status: Not started  
Target milestone: Future  
Actual delivery: —

### <a id="p3f"></a>P3 f. Offline-first save and resume

User story: As an Efficiency Seeker I want progress saved even without cell service so that I
never lose work.

Acceptance criteria:

- All captures and edits are saved locally first.
- If connection is lost, I can continue working without errors.
- When connection returns, data syncs without duplication.
- Resume returns me to the last checklist item and state.

Estimate: 7 days  
Dependencies: [D2](#d2), [D7](#d7)  
Status: Not started  
Target milestone: Future  
Actual delivery: —

### <a id="p3g"></a>P3 g. Auto-stitch evidence to sections

User story: As an Efficiency Seeker I want the app to organize evidence under the right
sections so that the report is consistent.

Acceptance criteria:

- New evidence is linked to the active checklist item and its section.
- The report draft shows counts of photos, notes, and videos per section.
- A background process creates associations using timestamps and item context.

Estimate: 2 to 3 days  
Dependencies: [P3A](#p3a), [D7](#d7)  
Status: Not started  
Target milestone: M4  
Actual delivery: November 28th

### <a id="p3h"></a>P3 h. Submit data for processing

User story: As an Efficiency Seeker I want to submit all collected data so that drafting can
begin.

Acceptance criteria:

- I can press Save or Submit Data for Processing.
- The system validates that required items are complete and shows any gaps.
- A submission receipt with a reference id is shown.
- MVP simulates processing; full version triggers draft generation.

Estimate: 3 to 4 days  
Dependencies: [P3G](#p3g)  
Status: Not started  
Target milestone: M4  
Actual delivery: November 5th

### <a id="p3i"></a>P3 i. Cloud backup on submit

User story: As an Efficiency Seeker I want a full back up to my cloud drive so that evidence
is archived independent of report results.

Acceptance criteria:

- On submit, a bundled backup is sent to the selected provider and folder.
- Upload progress and completion are visible.
- MVP mocked; full version uses linked provider.

Estimate: 2 to 3 days  
Dependencies: [C1](#c1), [C2](#c2), [C3](#c3), [D6](#d6)  
Status: Not started  
Target milestone: M5  
Actual delivery: November 5th

### <a id="p3j"></a>P3 j. Reopen job and resubmit

User story: As an Efficiency Seeker I want to reopen an inspection to add more data and
resubmit so that I can address missed items.

Acceptance criteria:

- I can reopen a submitted job and continue capturing evidence.
- New evidence merges cleanly with existing data without duplicates.
- A new submission version is created and tracked.

Estimate: 2 days  
Dependencies: [P3H](#p3h), [D7](#d7)  
Status: Not started  
Target milestone: M4  
Actual delivery: November 5th

### <a id="p3k"></a>P3 k. Error handling

User story: As an Efficiency Seeker I want clear messages when anything fails so that I can
fix issues and continue.

Acceptance criteria:

- Missing report, failed capture, storage errors, or sync conflicts show actionable
  messages.

Estimate: 1 day  
Dependencies: [P3A](#p3a) to [P3J](#p3j)  
Status: Not started  
Target milestone: Future  
Actual delivery: —

---

## 4. Report Finalization and Delivery

### <a id="p4"></a>P4. Report Editor and Finalization

User story: As an Efficiency Seeker I want to edit, save, and submit the report so that the
client receives the final version and I get paid.

Acceptance criteria:

- I can open Finalize Report and see the automated draft in edit mode.
- I can edit text, media, and simple style variables like color.
- I can confirm company logo, brand imaging, and marketing details.
- I can save progress and return later.

Estimate: 1 day  
Dependencies: [P3H](#p3h), [P3J](#p3j)  
Status: Not started  
Target milestone: M4  
Actual delivery: —

### <a id="p4a"></a>P4 a. Core editor for text and media

User story: As an Efficiency Seeker I want to select and edit text and media so that the
report is accurate and client ready.

Acceptance criteria:

- I can click into any section to edit text and captions.
- I can replace, move, or remove photos and videos within a section.
- I can change color, logo, and basic typography choices from a simple palette.
- Inline evidence references stay linked to the correct items after edits.
- Save confirms and persists changes.

Estimate: 4 to 5 days  
Dependencies: [D7](#d7), [A4](#a4), [P3G](#p3g)  
Status: Not started  
Target milestone: Future  
Actual delivery: —

### <a id="p4b"></a>P4 b. Section create, read, update, delete and mass insert

User story: As an Efficiency Seeker I want to add, remove, reorder, or restore whole
sections so that the structure matches the job.

Acceptance criteria:

- I can create, rename, delete, and reorder sections.
- I can quickly insert a predefined section such as Basement that auto populates with
  sensible defaults.
- Deleting a section moves its evidence to an Unassigned area until I relink or
  permanently remove it.

Estimate: 2 to 3 days  
Dependencies: [P1D](#p1d), [D7](#d7)  
Status: Not started  
Target milestone: Future  
Actual delivery: —

### <a id="p4c"></a>P4 c. Undo and redo

User story: As an Efficiency Seeker I want smooth undo and redo with a large stack so that I
can experiment safely.

Acceptance criteria:

- I can undo and redo recent edits to text, media placement, and section structure.
- The stack size supports at least some number of steps in the session.

Estimate: 1 to 2 days  
Dependencies: [P4A](#p4a), [P4B](#p4b)  
Status: Not started  
Target milestone: Future  
Actual delivery: —

---

## 5. Client Delivery and Archiving

### <a id="p5a"></a>P5 a. Payment confirmation gate

User story: As an Efficiency Seeker I want to confirm client payment before sending the
report so that I get paid.

Acceptance criteria:

- Finalize flow requires confirmed payment before Send to client is enabled.
- I can see current payment status and retry failed charges.
- The app records the payment confirmation on the report.

Estimate: 2 days  
Dependencies: [B1](#b1), [B2](#b2), [D5](#d5)  
Status: Not started  
Target milestone: M5  
Actual delivery: December 5th

### <a id="p5b"></a>P5 b. Send report to client

User story: As an Efficiency Seeker I want to deliver the final report to the client so that they
receive the correct version.

Acceptance criteria:

- I can send via secure link or email with a short message.
- The recipient sees the final version only.
- Delivery is logged with recipient, time, and method.

Estimate: 1 to 2 days  
Dependencies: [P5A](#p5a)  
Status: Not started  
Target milestone: M5  
Actual delivery: December 5th

### <a id="p5c"></a>P5 c. Cloud copy on delivery

User story: As an Efficiency Seeker I want a copy of the final report sent to my cloud drive
so that my records are complete.

Acceptance criteria:

- On send, a copy is exported and saved to the selected provider and folder.
- Completion is confirmed or a retry is offered on failure.

Estimate: 1 to 2 days  
Dependencies: [C1](#c1), [C2](#c2), [C3](#c3), [D6](#d6)  
Status: Not started  
Target milestone: Future  
Actual delivery: —

---

Backlog Features:
This is a list of the secondary features. They will be essential to the day-to-day operations
of our product – but are not a primary feature and can be mocked until the MVP has been
prototyped, tested, and iterated.

## 1. Authentication Account Setup

### <a id="a1"></a>A1. Create Account and Company Setup

User story: As an Efficiency Seeker I want to create an account so that I can set up my
company profile and start using the app.

Acceptance criteria:

- From homepage, user can select Create account.
- User can enter username and password that meet strength rules.
- User can enter company or personal info and save it to the profile.
- User can pick a billing plan and enter payment info.
- On successful confirmation, account is created and user lands on the
  authenticated home.

Estimate: 4 to 6 days  
Dependencies: payment provider keys available  
Status: Not started  
Target milestone: M3  
Actual delivery: —

### <a id="a2"></a>A2. Log In

User story: As an Efficiency Seeker I want to log in to my account so that I can start using
the app.

Acceptance criteria:

- From homepage, user can open Sign in.
- User can enter account name and password and submit.
- On success, user reaches authenticated home with their data loaded.
- On failure, user sees a clear error and can retry.
- Session persists until logout or timeout.

Estimate: 1 to 2 days  
Dependencies: [A1](#a1)  
Status: Not started  
Target milestone: M3  
Actual delivery: —

### <a id="a3"></a>A3. Log Out and Session Management

User story: As an Efficiency Seeker I want to log out of my account when I am finished for
the day so that I do not burn my phone battery or accidentally change something.

Acceptance criteria:

- While logged in, user can open account menu and choose Log out.
- If there is unsaved work, the app prompts to save or discard before logging out.
- After logout, user is returned to the sign in screen and session tokens are
  invalidated.
- Background sync stops after logout.

Estimate: 1 to 2 days  
Dependencies: [A2](#a2)  
Status: Not started  
Target milestone: M3  
Actual delivery: —

### <a id="a4"></a>A4. Manage Profile and Settings

User story: As an Efficiency Seeker I want to manage my profile and settings so that I can
update my profile, change my billing, and manage where my backup data gets saved.

Acceptance criteria:

- While logged in, user can navigate to Settings and open Edit Profile, Storage, and
  Billing.
- User can edit name, company, phone, email, logo, and time zone.
- User can edit Billing (See B1, B2, B3.)
- User can edit Data and could storage (See C1, C2, C3.)
- Invalid inputs show clear inline errors and cannot be saved.
- Successful save shows a confirmation and persists after refresh.

Estimate: 7 days  
Dependencies: [A1](#a1), [B1](#b1), [B2](#b2), [B3](#b3), [C1](#c1), [C2](#c2), [C3](#c3), [C4](#c4)  
Status: Not started  
Target milestone: M4  
Actual delivery: —

---

## 2. Billing and Plan Management

### <a id="b1"></a>B1. Update Payment Method

User story: As an Efficiency Seeker I want to update my payment method so that billing
continues without interruption.

Acceptance criteria:

- While logged in, user can navigate to Settings and open Edit Profile, Storage, and
  Billing.
- From Settings, user can open Billing.
- User can add or replace a payment method using the provider hosted form.
- App never displays full card numbers.
- Successful update shows confirmation and stores last4 and expiry for reference.
- Failed update shows a clear error and leaves prior method unchanged.

Estimate: 2 to 3 days  
Dependencies: [A1](#a1), payment provider keys  
Status: Not started  
Target milestone: M4  
Actual delivery: —

### <a id="b2"></a>B2. Change Plan or Tier

User story: As an Efficiency Seeker I want to change plans so that I can upgrade or
downgrade smoothly.

Acceptance criteria:

- Current plan and limits are visible with renewal date.
- User can select a new plan and confirm the change.
- Proration is applied if the provider supports it.
- New limits take effect immediately after confirmation.
- Confirmation email is sent, and plan change is logged.

Estimate: 2 to 3 days  
Dependencies: [B1](#b1)  
Status: Not started  
Target milestone: M4  
Actual delivery: —

### <a id="b3"></a>B3. Invoices and Receipts

User story: As an Efficiency Seeker I want to view and download invoices so that I can keep
records for accounting.

Acceptance criteria:

- Billing page lists invoices with date, amount, and status.
- User can download a PDF of any invoice.
- Email receipt is automatically sent on successful charges.
- Failed payment shows status and retry guidance.

Estimate: 1 to 2 days  
Dependencies: [B1](#b1)  
Status: Not started  
Target milestone: M4  
Actual delivery: —

---

## 3. Storage and Cloud Sync

### <a id="c1"></a>C1. Connect Cloud Provider

User story: As an Efficiency Seeker I want to connect my cloud account so that backups
can be stored in my own drive.

Acceptance criteria:

- From Settings, Manage Data shows Google Drive, Dropbox, and OneDrive options.
- User can link a provider with OAuth and approve required scopes.
- After linking, provider shows as Connected with the linked account email.
- User can disconnect a provider and the status changes to Disconnected.

Estimate: 7 days  
Dependencies: [A1](#a1), provider credentials  
Status: Not started  
Target milestone: M4  
Actual delivery: —

### <a id="c2"></a>C2. Choose Backup Destination Folder

User story: As an Efficiency Seeker I want to choose a destination folder so that my
backups are organized.

Acceptance criteria:

- After connecting a provider, user can open a folder picker.
- Selected folder path is saved and displayed.
- The app remembers the folder for future backups until changed.
- If the folder is deleted or access is revoked, the app shows a clear error and prompts
  to reselect.

Estimate: 2 to 3 days  
Dependencies: [C1](#c1)  
Status: Not started  
Target milestone: M4  
Actual delivery: —

### <a id="c3"></a>C3. Automatic Backup on Report Submission

User story: As an Efficiency Seeker I want reports to back up automatically on submission
so that my work is archived without manual steps.

Acceptance criteria:

- Toggle to enable automatic backup on submission.
- On finalizing a report, an archive is created in the selected folder with a clear
  naming convention.
- Upload progress indicator shows status and completes even if the app window is
  minimized.
- If upload fails, the app retries and surfaces a retry action to the user.

Estimate: 3 to 4 days  
Dependencies: [C2](#c2)  
Status: Not started  
Target milestone: M4  
Actual delivery: —

### <a id="c4"></a>C4. Manual Backup Now

User story: As an Efficiency Seeker I want to run a manual backup so that I can archive on
demand.

Acceptance criteria:

- From Manage Data, user can trigger Backup now.
- Backup packages reports and media and uploads to the selected folder.
- On success, user sees a confirmation with a link to the folder.
- On failure, user sees a clear error and can retry.

Estimate: 1 to 2 days  
Dependencies: [C2](#c2)  
Status: Not started  
Target milestone: M3  
Actual delivery: —

---

## 4. Database and Data Persistence (PostgreSQL)

### <a id="d1"></a>D1. Create PostgreSQL for Dev and Prod

User story: As an Efficiency Seeker I want a reliable database so that all accounts, settings,
and reports are stored safely.

Acceptance criteria:

- A managed PostgreSQL instance exists for dev and prod with unique database
  names.
- App roles are created with least privilege for read and write.
- SSL connections are required.

Estimate: 1 to 2 days  
Dependencies: —  
Status: Not started  
Target milestone: M3  
Actual delivery: —

### <a id="d2"></a>D2. Application Connection and Configuration

User story: As an Efficiency Seeker I want the app to connect to PostgreSQL using secure
settings so that data persists without errors.

Acceptance criteria:

- Backend connects to PostgreSQL using environment variables for host, port, db,
  user, and password.
- Local developer setup documented with sample .env values.

Estimate: 1 to 2 days  
Dependencies: [D1](#d1)  
Status: Not started  
Target milestone: M3  
Actual delivery: —

### <a id="d3"></a>D3. Core Auth Schema

User story: As an Efficiency Seeker I want secure storage for users and sessions so that
login and logout work reliably.

Acceptance criteria:

- Tables exist for users, credentials, sessions, and password reset tokens.
- Passwords are stored using a strong one-way hash.
- Unique indexes exist on username and email.

Estimate: 2 to 3 days  
Dependencies: [A1](#a1), [A2](#a2), [D2](#d2)  
Status: Not started  
Target milestone: M4  
Actual delivery: —

### <a id="d4"></a>D4. Profile and Company Schema

User story: As an Efficiency Seeker I want my profile and company data stored so that
settings persist across sessions.

Acceptance criteria:

- Tables exist for company and user profile with fields for name, logo, phone, email,
  and time zone.
- Foreign keys link users to company.
- Updates are audited with who and when.
- Validation rules enforced at the database level where appropriate.

Estimate: 2 days  
Dependencies: [D2](#d2), [D3](#d3)  
Status: Not started  
Target milestone: M4  
Actual delivery: —

### <a id="d5"></a>D5. Billing Data Model and Webhooks

User story: As an Efficiency Seeker I want my plan and invoices synced so that billing
reflects my billing status.

Acceptance criteria:

- Tables store provider customer id, plan id, and invoice metadata.
- No full card numbers are stored; only last4, brand, and expiry metadata.
- Failed payment states are recorded and visible to the app.

Estimate: 4 to 5 days  
Dependencies: [B1](#b1), [B2](#b2), [B3](#b3), [D2](#d2)  
Status: Not started  
Target milestone: M5  
Actual delivery: —

### <a id="d6"></a>D6. Cloud Provider Links and Backup Destinations

User story: As an Efficiency Seeker I want my connected Drive or Dropbox saved so that
backups go to my chosen folder.

Acceptance criteria:

- Tables store provider type, account email, OAuth tokens, and selected folder path.
- Tokens are encrypted at rest and rotated on refresh.
- Disconnection removes tokens and marks provider as Disconnected.
- Folder selection persists and is validated before use.

Estimate: 4 to 5 days  
Dependencies: [C1](#c1), [C2](#c2), [D2](#d2)  
Status: Not started  
Target milestone: M5  
Actual delivery: —

### <a id="d7"></a>D7. Reports, Evidence, and Media Index

User story: As an Efficiency Seeker I want my reports and attached media indexed so that
drafts and exports are consistent.

Acceptance criteria:

- Tables exist for reports, sections, checklist items, findings, and evidence records.
- Evidence rows reference media objects by storage key and original filename.
- Cascade rules prevent orphaned records.

Estimate: 4 to 5 days  
Dependencies: [D2](#d2), [D4](#d4)  
Status: Not started  
Target milestone: M5  
Actual delivery: —

### <a id="d8"></a>D8. Data Protection and Retention

User story: As an Efficiency Seeker I want clear data protection so that personal data is
secured and removed when no longer needed.

Acceptance criteria:

- Columns with sensitive tokens are encrypted at rest.
- A retention policy exists for stale reports and logs.
- A data export and delete flow exists for account closure.

Estimate: 2 to 3 days  
Dependencies: [D3](#d3), [D4](#d4), [D7](#d7)  
Status: Not started  
Target milestone: Future  
Actual delivery: —

---

- 1. Template Creation
- 1. Authentication Account Setup
- A1. Create Account and Company Setup
- A2. Log In
- A3. Log Out and Session Management

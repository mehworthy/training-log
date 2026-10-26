# Training log

A phone-friendly gym log that saves straight into your Google Sheet
("3 day hypertrophy - ALWIN") and graphs every exercise over time.

## How it works

- `index.html` is the app. GitHub Pages hosts it for free.
- `Code.gs` lives inside your Google Sheet (Apps Script). It receives each
  session and writes it to a new tab called **Training Log**, one row per set,
  with your comments, RIR, volume and estimated 1RM. Your existing Block 1 tab
  is never touched.
- Your web app URL and PIN are stored on your phone only, never in the repo,
  so the repo can be public.

## 1. Connect the sheet (about 5 minutes)

1. Open your spreadsheet, then **Extensions > Apps Script**.
2. Delete what's there, paste in everything from `Code.gs`.
3. Change `const PIN = '1234';` to your own PIN. Click the save icon.
4. In the function dropdown at the top pick **setup**, click **Run**, and
   approve the permissions (choose your account, then Advanced > Go to project).
   A "Training Log" tab appears in your sheet.
5. Click **Deploy > New deployment**. Click the gear next to "Select type",
   choose **Web app**, then set:
   - Execute as: **Me**
   - Who has access: **Anyone**
6. Click **Deploy** and copy the **Web app URL** (it ends in `/exec`).

If you ever edit `Code.gs` later, go to **Deploy > Manage deployments >
edit (pencil) > Version: New version > Deploy** so the change goes live. The
URL stays the same.

## 2. Put the app on GitHub Pages

1. Create a new repository on github.com (e.g. `training-log`).
2. **Add file > Upload files**, upload `index.html` (and this README if you like), commit.
3. Go to **Settings > Pages**, under "Build and deployment" choose
   **Deploy from a branch**, branch **main**, folder **/ (root)**, Save.
4. After a minute your app is at `https://<your-username>.github.io/training-log/`.

## 3. First use

1. Open the app on your phone, tap the gear, paste the web app URL and your PIN.
2. Tap **Test connection**, then **Save settings**.
3. Add it to your home screen (Safari: Share > Add to Home Screen;
   Chrome: menu > Add to Home screen) so it opens like an app.

## Using it

- Tap a plate to pick the day, set the week and date, fill in kg and reps.
  Last session's numbers show faintly in each box so you know what to beat.
- Each exercise has a comments box and a last-set RIR picker.
- Tap **Progress** on any exercise for a graph: top weight, estimated 1RM,
  volume or total reps (or hold time for planks). Tap a point to see that
  day's sets and comment.
- Entries are kept on your phone as you type, so losing signal mid-session is
  fine. Tap **Save session to sheet** when you have connection. Saving the
  same day and date again updates that session rather than duplicating it.
- Swapping a machine? Use **Swap in or add an exercise** at the bottom.

## Changing the program

When your coach writes a new block, edit the `PROGRAM` list near the top of
the `<script>` in `index.html` (exercise names, sets, the scheme text), then
upload the new file to GitHub. Keep exercise names the same between blocks
when it's the same lift so the graphs carry on.

# 🌼 Sprout Homework Hub

A colorful, responsive homework planner with assignments, priorities, completion tracking, student filters, subjects/teachers, weekly class schedule, and real-time collaboration via Firebase Firestore.

## Try it

Open `index.html` in a browser. Without Firebase configuration, the app works in **demo mode**: changes are saved to that browser only, not shared with others.

## Enable live collaboration (about 10–20 minutes)

1. Create a Firebase project at https://console.firebase.google.com/.
2. Add a **Web app** under Project settings → Your apps, and copy its Firebase config.
3. In **Authentication → Sign-in method**, enable **Anonymous** authentication.
4. In **Firestore Database**, create a database. Open **Rules**, paste the contents of `firestore.rules`, and publish the rules.
5. Edit `index.html`: replace the empty `firebaseConfig` values (`apiKey`, `authDomain`, `projectId`, `appId`) with your Web app config. These are public client identifiers, not private server credentials.
6. Deploy the folder to a static website host such as Netlify (drag-and-drop the folder at https://app.netlify.com/drop) or GitHub Pages. The live site must be served over HTTPS. Opening a local HTML file is for demo/testing, not collaboration.
7. Open the hosted URL. The app generates a long, random `#room=` link. Click **Share planner** and send the full link to collaborators. Everyone with that link can edit the same planner; edits appear live.

## Important privacy and limitations

- **Anyone with the complete room link can view, edit, or delete planner data.** There are no roles or per-user permissions. Do not store sensitive student information or private grades.
- The Firestore rules use an unguessable room ID as the access capability, plus anonymous authentication. They do **not** protect against a link recipient forwarding the link. This is suitable for a small trusted study group, not a school-wide private student database.
- If someone loses the link, they may lose access to that room. Keep it bookmarked.
- Firebase has usage quotas and may charge if you exceed free allowances; check Firebase pricing.
- The app saves the entire planner document for each edit. Simultaneous edits to different fields can overwrite each other (last write wins). For heavy collaboration, use per-task Firestore documents and transactions.
- For production use with students, consider authenticated accounts, member-based Firestore rules, backups, and admin controls.
- Google Drive can store and share the files, but does not host an interactive HTML app; use a web host for live collaboration.

## Customize

Edit colors in the CSS `:root` and the `.hero`, `.stat`, and `.class` rules. Add subjects, teachers, students, tasks, and class periods from the Settings and New task buttons. No build step or package manager is required.

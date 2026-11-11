# 3. Features

The app has six must-have features, each mapped to a course topic.

| # | Feature | Course topic | What the user does |
| --- | --- | --- | --- |
| 1 | Moving between screens: venue list, venue detail, report sheet, sign in / sign up, profile | Navigation | Taps a venue in the list to open its detail page, opens the report sheet from there, switches to the profile from the bottom bar |
| 2 | Sign-in with a university email and live occupancy | Firebase (Auth + Firestore) | Signs up with a `@std.yildiz.edu.tr` address and verifies it; a report made on one phone appears on every other phone instantly |
| 3 | Last known status without internet | Local DB (Hive) | Sees each venue's last status with an "updated 12 min ago" label when offline |
| 4 | Weather warning | API / JSON (Open-Meteo) | Sees a note above the list that venues with outdoor seating are not recommended while it rains |
| 5 | Animated occupancy indicator | Animation | When a venue's status changes, the indicator's color and fill bar change smoothly |
| 6 | Each screen's logic lives in its own ViewModel | MVVM + Riverpod | (Invisible) Screens only draw; calculations and data access happen in ViewModels |

## Rules

- **Viewing is open:** No sign-in is needed to see how crowded venues are.
- **Reporting needs a verified university email:** Only verified `@std.yildiz.edu.tr` accounts can report. The rule is enforced both in the app and in Firestore security rules.
- **You must be at the venue:** The report button works only within 100–150 m of the venue (GPS). For the presentation, a demo mode in settings turns this check off.
- **Rate limit:** One person can report on the same venue at most once every 15 minutes.
- **Three levels:** Empty, Moderate, Full.
- **Opening hours:** Outside opening hours a venue shows "Closed", moves to the bottom of the list and cannot receive reports. The dining hall is open 11:30–14:30 and 17:00–19:15.
- **Interface language:** The app's interface is in Turkish because its users are YTU students. All documentation and code are in English.

## Venues

Seven venues on Davutpaşa Campus: Hokka Cafe, Kayıntı Cafe, Büyük Ev Cafe, Yıldız Cafe, Yirmibirco, YTU Dining Hall and YTU Gym. The list is fixed; users cannot add venues. The dining hall's lower and upper floors are calculated separately, so the database holds 8 records; the list shows both floors on a single card with two rows.

## Later versions

An hourly busyness chart ("usually full at 12:30") is not part of the MVP: it needs weeks of collected data to be meaningful.

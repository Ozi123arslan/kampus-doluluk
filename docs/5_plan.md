# 5. Plan and Risks

Each member owns a layer: Oğuzhan builds the data and logic (repositories, ViewModels, Firebase), Sıla and Rabia build the screens (views) from the Figma mockup. At the end of each week a working version is merged into `main`. The final presentation date is not yet announced; the plan assumes six working weeks and a preparation week.

## Weekly tasks

| Week | Oğuzhan Arslan | Sıla | Rabia |
| --- | --- | --- | --- |
| 1 (Nov 16–22) | Flutter project, MVVM folder structure, Firebase project and Auth | Flutter basics; app theme, colors and fonts | Flutter basics; `VenueCard` widget |
| 2 (Nov 23–29) | Firestore `venues` / `reports`, VenueRepository, ReportRepository | Venue list screen | Venue detail screen |
| 3 (Nov 30–Dec 6) | `OccupancyCalculator` with unit tests, VenueListViewModel | Sign in, sign up and email verification screens | Report sheet and status animations |
| 4 (Dec 7–13) | Location check, 15-minute rule, opening hours, Firestore security rules | Profile and settings (demo mode) | Weather strip (Open-Meteo) |
| 5 (Dec 14–20) | Hive offline cache, WeatherService | Offline and closed states | "Too far" and "report sent" states |
| 6 (Dec 21–27) | Integration, bug fixes, APK build | Testing on real phones; collecting real reports on campus | 2-minute demo video |
| 7 | Presentation rehearsal (all members) | | |

## Risks

| Risk | Impact | Mitigation |
| --- | --- | --- |
| Few reports at the start ("cold start") | Venues show "no data" and the app looks empty | One-tap reporting; "low confidence" label; team members report on campus during testing week |
| False reports | Wrong status shown | Verified university email, GPS check, 15-minute limit and weighted majority (see Section 4) |
| GPS is inaccurate indoors (20–50 m) | Users inside a venue cannot report | 100–150 m radius per venue; demo mode for the presentation |
| University mail server delays or blocks verification emails | Users cannot finish sign-up | Test with team accounts in week 1; "resend email" button and spam-folder hint |
| Two members are new to Flutter | Screen work falls behind | Week 1 is for basics; screens are built from the existing Figma components; weekly pair-programming session |
| Firebase free-tier limits | Writes or reads are blocked | Only recent reports are queried (30–90 min windows); no images stored in Firebase |
| Exam weeks overlap with the plan | Weekly versions slip | Sunday 30-minute progress meeting; tasks are reassigned when someone falls behind |

CALPADS Basics (Session 700)
====

2,000 acronyms in CALPADS (In the documentation as well)


Aeries Client
----
- Web is only for SSID as of right now
- Eventually, when everything is moved to web (.NET) then CALPADS reporting will function the same
- Check on things in the School Options (`LOC`)
  - Session Type needs to be Regular for reporting
  - School Code must be 7 0's for the District (School Code 0)
- For Fall 2, you must have a Calendar
- If you want to keep all Staff data, you can associate them with School Code 0 so they are "at the District", even if not employed anymore
- Can store Classified staff in Aeries because of CBEDS Aura(?)
- Until Fall 1 is certified, recommended to "Extract All Data This Year" for SENR
  - Afterwards, choose "Extract Only Data Changes"
- Documentation on CALPADS stuff
  - `Aeries.com -> Training and Support -> CALPADS`
- Aeries table `LGD` (Log Details)
  - Contains something something something... record changes
  - Students who get extracted and don't look like they should, will have a record here
- SPRG 70 errors are about duplicate Programs
  - CALPADS wasn't checking for duplicates at some Point


Aeries Web
----
- `Programs -> Special Programs` contains things that are still reported to CALPADS
- If tables are given for things like Free and Reduced, use those and not the Special Programs table
- Top right of GUI, `Gear -> Highlight State Reporting Fields`


Misc
----
- `LAC`: Language Accuisition
- __ODS Import__ brings in students and their `LAC` status from CALPADS
- `STU.LF` = `LangFlu` = Language Fluency
- Wait until after __End of Year__ reporting before rolling over the database
- Closing out the Year
  - You must go through the process of closing out the Year
  - Upload `SENR` of all students so they get a `E155` exit code
  - Query in the information for students who move from one school to another because they hit the grade limit of a school, etc.

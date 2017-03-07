New Year Cycle (Session 990)
====
- PDF in Documentation covers the Rollover and Update from Aeries Web Version
- Need BETA Feature enabled in order to do this through the web
  - `School Info -> Functions -> New Year Rollover (BETA)`
- Preschool and TK students don't roll over correctly in Streets table


Overview
----
1. Security
  - Need `ROL` permission, aka `New Year Rollover`
  - Give everyone Read-only __ONLY__ during this process
2. New Year Rollover Requirements
  - Must be run under SSL before continuing
3. Data Verification
  - Next school (`STU.NS`) must be populated for __ABSOLUTELY EVERYBODY__
  - SQL Scripts will be put on FreshDesk
  - Make sure all graduating seniors have 12 as their next grade. If they have 13, they will rollover
  - Make sure CALPADS End of Year is complete first


Settings Tab
----
1. District Wide and Inactive School Options
  - Have a different Inactive Code for the Inactive tag. That way you know a student was marked as Inactive later, but during the New Year Rollover instead of just being Inactive for other reasons
2. School Based Options
  - Leave "Change New Students School Mobility to new grade" unchecked if you pre-enroll students. Otherwise they get rolled to the next grade (ex: 1st -> 2nd)
  - Only copy Student (STU) records under 25 years of age
    - Keep students for easier search later because they look at the IDN table


Processes Tab
----
1. Pre-Rollover Reports
  - Table record counts
    - `STU` should always match the count of `SSD`
  - Force an update to make sure everything is working, such as Indexes, tables etc.
  - Force Cascading DEL Tags will make sure there are no orphaned records
  - Database Cleanup will delete all DEL tagged records. Not required anymore
  - Fix ENR Records cleans up student enrollments and can be done durng the year to try and fix any possible errors
  - Create new year Database
    - Create New Database
      - DST17000xxxx
    - Options
      - Parametrization: Forced
    - Open `eagle\SQLMODEL.SQL` and run the script
  - Back in Aeries CS, change to the new year you just created
2. Rollover
  - Must be over HTTPS in order to perform
3. Post-Rollover Reports


3rd Party Integration Considerations
----

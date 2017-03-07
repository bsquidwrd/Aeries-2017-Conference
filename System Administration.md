Reporting Service/Server (Session 910)
=====
`C:\AppSettings` contains settings (can be found in IIS -> Under the site (probably "Default Site") -> Properties of the `AppSettings` folder)
If you make a change to `C:\AeriesReporting\AeriesReportingConfig.config` then copy it to `C:\AppSettings` to make sure they are up to date.
  - `C:\AeriesReporting\Service` contains InstallService.bat and UninstallService.bat
    - Need to reinstall service when changes are made to AeriesReportingConfg.config
    - After reinstall, start the service
    - Check under "Applications and Services/Aeries Reporting" in Event Viewer and if you get 4 "I" icons for Information, then it started correctly
      - You can not just "restart" the service, due to "programming" not allowing the re-read of the config file after changes. Requires installer re-run

### Viewing reports that have been run
- Files stored in `C:\AeriesReporting\FileStore\<username>`
- It is recommended to clear these out every year

Actual Web server
=====
AppPool needs to have v4.0 and "Process Model/Identity" needs to be set to a Domain account (only if on the same server as Reporting) or NetworkService account

### Create Sandbox site
- Create new "Virtual Directory"
  - Point to the Physical folder of the Aeries install
  - Change the folder to an Application
  - Change the AppPool to the Aeries AppPool
  - Create an `AppSettings` folder that is different from the live
    - Copy AeriesNetConnectoin.config, AeriesReportingConfi.config, AppSettings.config files to the new folder for the Sandbox site

## AppSettings.config
- Maintains what type of Portal setup is being used
  - Either Admin, Parent, Teacher for "SystemType"


Security
====
### Users
- Creating Users
  - Can be setup however you want, regarding the name. Any pattern, it's up to you
    - ID: PK, AI
    - Type: User level of access
    - Identity Provider: Leave to Aeries unless using Google Integration
    - Username: duh..
    - Expiration Date: Can be set a head of time
    - Status: Active, Locked, Disabled, Pending
      - Active is the only one that allows logins
      - Locked and Pending are used typically for temporary purposes
      - Disabled is for people who are no longer there
    - Passwords: wtf you think this is, first grade?
    - Staff ID is used for things such as CALPADS and linking users to a Staff record
    - First and Last name are optional (Populate if you link a Staff ID)
    - Email Address is required

- Assigning/Editing Permissions
  - Only viewable on accounts that are not Admin type
  - You can assign permission expirations for specific nodes
  - When assigning a School, if you check "Read-Only" it will override any permissions they may be assigned with "write"
  - Certain tables allow field-to-field permissions and can be set a the Group/User level

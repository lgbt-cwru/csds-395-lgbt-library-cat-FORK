# LIBRARY MANAGEMENT AND CATALOG PROJECT
## ARCHIVAL NOTES

##### Project authors: Fei Triolo, Nat Qiu, Borris Brondz, Dan Burwell, Deb Park, Hannah Hejazi | FALL 2025
##### Past library managers: Fei Triolo (2024-2026), Esther-David Moyer (2023-2024), Anya Hsung (2021-2023)
##### Archival author: Fei Triolo | 5/15/2026

### Table of contents:
1. [Purpose Statment](#purpose-statement) -- What this repo is, why it is
2. [Repository Structure](#repository-structure) -- Overall structure of the repository, what's included and why, and how to use it
4. [Disclaimer](#disclaimer) -- Hedging my bets, don't get your hopes up if you want to finish what I started
4. [Codebase Structure](#codebase-structure) -- Overview of the codebase archived here
    - [Frontend](#frontend)
    - [Backend API](#backend-api)
    - [Backend Database](#backend-database)
    - [CAS Integration](#cas-integration)
4. [Existing LGBT Center Library Infrastructure](#existing-lgbt-center-library-infrastructure) -- Overview of the previous/current infrastructure and what/why is archived here
5. [Project Continuation](#project-continuation) -- Unstructured thoughts and advice on how to continue something like this


### Purpose Statement 
This repository is an archive of the existing work done for a library catalog and management system for the LGBT Center's library. This project was originally a CSDS Senior Project conducted in the Fall of 2025. While it was technically complete for the purposes of the project, we were never able to complete it to a quality that would be useablefor the center. This archive serves as a reference and boilerplate for if/when future LGBT Center staff (or myself, as a 3rd party voluteer) would like to resume this project or take their own stab at revamping the existing LGBT Center Library management and user system. 

This README details the structure of this archive repo, as well as an overview of the project state at timeof archival. I hope that it serves as a jumping off point to navigate the existing codebase, decode the software architecture, understand problems and contextualize experiments preserved in this archive.

### Repository Structure
This archival repository is set up on a github under the LGBT Center official email. Since this is the first repository hosted by the center, it's my hope that this github will become home to other future student-coordinator-led projects aimed at improving the Center's tech infrastructure. 

If you are resuming this project, and are planning on utilizing, remixing, or experimenting with the existing codebase, please *branch* or *fork* your own version from this main archival head to preserve archival integrity. If you plan on developing your own software while using this archive as a design *reference* (i.e. ideas, inspiration, what to do and what *not* to do), feel free to use this github to host your own repo and add the personal accounts of you and your teammembers as collaborators (Speak to Greyson, Avery, or whoever is the current director if you have issues accessing the lgbt-cwru github account). Additional reflections and advice for continueing this project is the [Project Continuation](#project-continuation) section.

This archival repository is divided into 3 sections:
1. [Codebase](#codebase-structure) -- The preserved software that was developed for this project. The structure of this section is cloned from the original project repository that we used in development to preserver our in-situ documentation. Additionally, since this repo is a *fork* of that very original repository, how the codebase developed over time is also accessible via git commit history logs. For clarity, all archival superstructures and documents will be appended to the main branch, leaving the other development branches untouched.

2. Project Development Documents -- Archived uploads of the original project development documents we drafted during the design process. Most of these are *required deliverables for the CSDS Senior Project* and are formatted as such. They provide additional documentation and insight into the software architecture of the original project, though the final archived codebase may or may not completley reflect the information outlined. They may provide partial documentation as well as insight into our design philosophy and inspiration for future iterations of this project.

3. [Existing and previous Library Infrastructure](#existing-lgbt-center-library-infrastructure) -- The existing infrastructure for managing the lgbt center library collection, taking out loans and tracking due dates. This is an archive of all the infrastructure as it exists both at time of archival and at time of project start. It is archived here to preserve the original problem that the project was inteded to solve. If the system has changed organically over time, it may prove useful to compare how we attempted to improve the lgbt center library system vs. what it's currently like in order consider what design features may or may not be relevent from our project.

There might be some overlap between what's featured in each of these sections (i.e. existing infrastructure details within the project development documents to support the project's problem statement, documentation in the development docs that was included in the codebase because it was used during active development but was also important to submit as a part of a deliverable, dummy data that was used during development and was extracted from the existing infrastructure, etc.). this archive is constructed to include as much relevent information as possible while maintaining the in-situ integrity of each section for future reference. These sections are organized for ease of repo navigation and compartmentalizing the respective documents with what was relevent for each of them. 

### Disclaimer
This archive makes no promises to the functionality, integrity, and robustness of the codebase and documentation within. It may take considerable effort for anyone to attempt to relaunch the fullstack application, frontend, API, or database as is. The project relied on several key pieces of infrastructure may now be inaccessible, deprecated, or compromised at time of reading. This is limited to but not including RHEL9 Server hosting through uTech, specific versions of GoLang, React, Typescript, and MySQL, AXIOS API and HTTP(S) protocols and CAS authorization for CWRU Single Sign-On, Environmental variables, specific system/service configurations, etc. in various levels of documentation or non-documentation throughout the archive. Each of these was its own integration hurdle during development and ***Will pose a challenge*** to outside future developers. Additionally, using any boilerplate infrastructure, existing code, or design architecture should be done with full caution and complete knowledge and understanding of what you are doing, as this archive cannot garuntee stability of security with any future system integration. While we did *try* to write secure code and calued the operational safety and privacy of the LGBT Center and its constituents, there is obviosuly a lot of shoddy code here so **proceed at your own risk**. Additionally, I heavily encourage *this archive, and any other clones of the original repository to remain **private*** especially LGBT Center tech infrastructure project.

### Codebase Structure
The codebase is divided into 2, 3, or 4 sections depending on how you count them. The repo generally reflects this architecture, but it's not always clear. here is an overview of the software architecture and what you will find in each section of the archived codebase
> #### Frontend
> The frontend of the library catalog and management webapp. This is written in React + TypeScript for some reason. The basic idea is to have a page for full catalog search, collection management (including adding books, removing books, editing metadata), and managing patrons, loans, and staff access. In typical webapp server/client architecture, the frontend is served to the client via network access. The frontend makes calls to request and post data, and displays that data in an accessible format for the user.

> #### Backend API
> The Backend API was written in Golang, recieves Axios calls from the frontend, processes those calls, queries the database for necessary data, processes that data as needed, and either serves the relevent data to the frontend or makes edits to the database. Archived here is the backend API code and working documentation for setting up the AXIOS calls to the frontend.

> #### Backend Database
> The database is a MySQL database hosted as a service on the server and is accessed though a private port by the backend. It is set up to structure relevent data and metadata about books, loans, and users including both patron and staff access levels. Archived here is the DDL queries that define the database schema used in the project.

> #### CAS Integration
> This compenent of the Backend speaks with the CAS authentication API for users to sign in with CWRU Single Sign-On, the existing university tech authentication service that allows us to sign in to university-approved software with our caseIDs. This was never fully implemented in the project since we had continued issues with authorizing our app to use the CAS API during development.

### Server Management
Server Management documentation is unfortunately very sparse in this archive. Here is a breakdown of what was needed for server management during development.
1. Secure server hosting though uTech, gain ssh access. We were able to use our Senior Project Advisor's unused RHEL9 server space, and the LGBT Center was also willing to pay for continued space upon project completion. Speak to Greyson/Avery/Current LGBT Center Admin if you want to continue to host through uTech for project continuation.
2. Install relevent packages: React, Golang, AXIOS, MySQL. At time of development, RHEL9's package installer didn't support the version of Go that our backend was written in so we had to do some extra stuff to install it.
3. Clone codebase to server. NOTE: make sure file permissions have root access so they can compile and run as processes.
4. Rebuild database from codebase. Create a system user for MySQL for automating queries on the MySQL system service
5. Run database as system service using system user, enable MySQL service to run on system start
6. Initialize environmental variables for integration. For us this included AXIOS keys and MySQL access string for the backend to speak to the database. More robust backend architecture might not need this!!
7. Compile backend API and enable as service. For us, it didn't want to compile so we hacked together a bash script that would wait for MySQL service, run backend API through Go interpretar rather than compiled binary.
8. Set up frontend to be served to the client via open port 

I would love to include more archived documentation about server management but since I no longer have access to the server that wouldn't be possible.

### Existing LGBT Center Library Infrastructure
The existing LGBT Center Library Infrastructure at both time of development and archival, consists of a google form for patrons to check out loans, and a google sheet for patrons to browse the collection and staff to keep updated. Staff were required to manually keep track of the various loans out and hold patrons accountable to their returns. The
overhead this presented to both staff and patrons was the primary motivator for the original project. Archived here are copies of those existing documents and infrastructure. The loans sheet has been anonymized as to preserve the privacy of historic Library patrons, which has always been a priority of this project. This archive includes the (anonymized) portable .xml export of the google sheets, a viewable .pdf export of the google form, pdfs of the patron instructional graphics that have been posted next to the library, and any relevant archived staff documents (such as transition documents of previous staff library managers).

### Project Continuation
Reflecting months later on the scope of this project, challenges, constraints, and issues faced, here are some unstructured thoughts and advice on how to go about continuing the effort to renovate the LGBT Center's library system via developing tech infrastructure, either for myself if I ever return to this project as a 3rd party volunteer, or future staff who may be interested in pursuing their own version of this project.
1. USE EXISTING RESOURCES such as open source library management APIs. You don't have to make everything from scratch yourself (i.e. FOLIO, Koha, Evergreen)
2. KEEP TEAM SMALL and make sure everyone on your team knows how everything else works.
3. If you don't know how to integrate a technology, research how it works before you start
4. Keep portability in mind. You're going to need to integrate mocks while developing and might not always have the final environment. Build something that's easy to deploy
Desired future features: Notifications, CAS login

# 📄 Software Requirements Specification (SRS) for Movie Recommender

Software Requirements

Specification

For Movie Recommender Project - Group 5

Prepared by Camilla L., Khushali S., Naga N., Hamilton D.,

Sai Girish Reddy V., Jackson S.

University of Colorado at Colorado Springs

Dr. Kristen Walcott CS 4310/5310

Table of Contents


# Revision History

Introduction


## Purpose

The purpose of this document is to define the software requirements for the Movie Recommender Project. This system is designed to help users efficiently discover movies based on various filtering criteria such as genre, themes, length, release date, popularity, mood, and personal preferences. The aim is to reduce the time users spend searching for content by providing intelligent recommendations based on user-defined filters and past interactions.

The Movie Recommender is intended for diverse user groups including, but not limited to:

Students

Movie Enthusiasts

Casual Movie Watchers

Parents, Guardians, and/or Babysitters

Book Lovers & Adaptation Enthusiasts

Each stakeholder of whom may have distinct preferences in the movies they watch and in what circumstance they are watching from. Our will provide users with personalized movie recommendations, filtering options, a watchlist, ratings and review features, and notifications for expiring content so that they can watch the Movie content they wish and when they wish to based on their distinct user data.

This document will serve as a reference for all stakeholders, including developers, testers, designers, and customers, to ensure alignment on the functional and non-functional requirements of the system.


## Scope

The Movie Recommender Project is a web-based application designed to help users find movies tailored to their preferences using advanced filters and recommendation algorithms. The system shall allow users to search for movies based on genre, release date, popularity, mood, themes, and other personal preferences. It shall support features such as user ratings, reviews, watchlists, and notifications for expiring content.

This application will not stream or host movies like Netflix or other streaming services. Instead, it focuses solely on enhancing the movie discovery experience by guiding users to content they can access through their preferred platforms.


### Application and Benefits:

The Movie Recommender Project aims to improve the movie discovery process by offering smart, efficient, and user-friendly recommendations. The primary benefits include:

Time Efficiency: Reducing the time spent searching for suitable movies.

Personalization: Offering tailored suggestions based on user behavior and preferences.

User Engagement: Encouraging interaction through ratings, reviews, and curated watchlists.

Convenience: Helping users track expiring content and explore new releases seamlessly.


### Objectives & Goals

Seems like it has been covered above to a sufficient degree.

The project at its core is meant to be a time reducer so users do not have to search by hand or on one specific site.


## Definitions, acronyms, and abbreviations

This section details any definitions, acronyms, or abbreviations utilized in this document for better readability.

Lo-fi - "lo-fi" or “low-fi” (short for "low fidelity") generally refers to a production or reproduction style characterized by unpolished, rough, or imperfect quality.

UI - “User Interface” which pertains to how a system may look to the user.

Functional Requirements - pertains to applicable features of the system.

API - “Application Programming Interface” which pertains to any software with a distinct function. In reference to this document, API refers to a serviceable database that returns information to the application for its inevitable use.

TMDB - “The Movie Database”, An official acronym for a DE-2.

SQL - “Structured Query Language” pertains to a language utilized to interact with a SQLite Database file to store data within tables, which can then be queried for or to put in data.

Hash - Hash Functions usually take a string or integer and produce a fixed-length, encrypted based on its contents, hard to replicate string of letters and numbers. Commonly used in password security.

Salted Hash - The addition of a string into an string to-be-hashed that decreases the likelihood of decryption.

Peppered Hash - Like Salted Hash, however ‘pepper’ is where a string is stored elsewhere and separate from any encryption, making it harder to find and further decreasing likelihood of decryption.

MoSCoW - A method of prioritization utilized in this document. For more information, see Section 1.4, number 6.

HTTP(S) - Hyper-Text Transfer Protocol (Secure), pertains to the information transfer protocol between client and server on the internet, specifically through an internet browser.

Role-Based Access Control - Pertains to user accounts that have access to information based on their role. Administrators, for example, will have different access than a regular user because administrators are responsible for data flow and security. Users, in contrast, are not.


## References

This section lists the references cited throughout the Software Requirements Specification (SRS) document, including references to other systems’ features for comparison, documents from research, and other useful documents.

Netflix, Netflix API Documentation. [Online]. Available: . [Accessed: Mar. 5, 2025].

Rotten Tomatoes, Movie Reviews and Ratings. [Online]. Available: . [Accessed: Mar. 5, 2025].

The Movie Database API, Database API Documentation. [Online]. Available:  [Accessed: April 4, 2025]

Django Project, Web Development Framework Documentation. [Online]. Available: . [Accessed: Mar. 31, 2025]

US & Canada Film Genres By Popularity, Genres. [Online]. Available:

. [Accessed: Mar. 31, 2025]

ProductPlan, "MoSCoW Prioritization," ProductPlan Glossary, [Online]. Available: . [Accessed: Apr. 11, 2025].

U.S. Department of Justice, "Web Accessibility Guidance," ADA.gov, [Online]. Available: . [Accessed: Apr. 17 2025].

W3C Web Accessibility Initiative, "Web Content Accessibility Guidelines (WCAG)," W3C, [Online]. Available:

. [Accessed: Apr. 17,2025 ].


## Overview

The rest of this SRS document portrays our project in its domain, how it interacts with other platforms, and how features are implemented in accordance to our stakeholders. From this point, our document concerns itself with building our project in terms of its functions, constraints, assumptions, then applies those to our specific requirements needed of our app to satisfy our customer’s requirements

Section 2 within this document concerns itself with explaining key features of this system’s problem statement including, but not limited to Product Functions, Product Constraints, and any assumptions that had to be made for production.

Section 3 portrays requirements such as UI, hardware specifications, software specifications, functional requirements, and design constraints to name a few. This section lays out the foundation for the system in detail and is the most important section to reference.

The Appendix of this document is split into 2 sections: Appendix A: Analysis Models and Appendix B: To Be Determined List. Appendix A is where any diagrams, models, and relevant pictures will be displayed for ease of access. Appendix B portrays any sections of this document that have yet to be filled out to completion and/or sections that need more expansions as our iterations go on.


# Overall description


## Product perspective

The Movie Recommender System is designed as a multi-layered web application with a modular and extensible architecture that enables personalized recommendations through streamlined user interaction, intelligent data processing, and robust API integration. At its core, the system aims to simplify the movie discovery experience by offering customized content recommendations, filtering options, and child-safe controls.

The topmost layer of the architecture comprises the User Interface (UI), which is developed using Django templates and styled with Bootstrap to ensure a responsive and consistent user experience across desktops, tablets, and mobile devices. This interface presents core features such as a search bar with dynamic filters, personalized homepages, watchlists, and profile settings.

Beneath the UI lies the Application Layer, powered by Django's backend logic. This layer handles all critical tasks including user authentication, session management, filter processing, child mode enforcement, and interaction logging. It serves as the intermediary between user actions and deeper system components.

At the center of the system lies the Recommendation Engine, which is responsible for generating personalized movie suggestions. This engine uses data derived from user profiles, watch history, filter selections, and interactions. The system is designed to eventually incorporate rule-based logic or machine learning models for deeper personalization.

The Data Layer leverages SQLite as its relational database management system. It stores user profiles, login credentials (secured with salted and peppered hash algorithms), watch history, cached metadata, and administrative activity logs. This layer ensures data persistence, rapid access, and secure separation of admin and user data.

Lastly, the system relies heavily on External APIs—particularly The Movie Database (TMDB) API—to retrieve real-time movie information such as genres, actors, ratings, and availability. To handle API limitations and ensure reliability, a local caching mechanism is implemented.

Frequently accessed data is stored temporarily to reduce downtime, improve response times, and maintain functionality during API unavailability. This structured architecture empowers the Movie Recommender System to deliver a seamless and tailored user experience while maintaining performance, scalability, and security. Please refer to the architecture diagram 2.1.1 below for a visual representation of this system

System Architecture Diagram


## Product functions

This subsection provides a summary of the major functions that the software performs. Each of the major functions blankets several functional requirements that contribute to the major functionality of the program as a movie recommender.


#### Search Bar Filters

The product will provide search bar functionality, providing the user with a list of options to filter the movie results of a search. The user will be able to choose any number of filtering options from none to all as chosen from the following list:

Popularity

Genre

Actors

Commendations

Release Date

Themes

Director

Producer

​

See Appendix A.2.8 for a sequence diagram detailing the process taken to collect filter selections from the user and display the results.


#### Home Page Filters

The product will provide homepage filtering functionality, providing the user with customization control over the products filters when displaying recommendations on the homepage for the user to browse.

The product will display recommended content for a logged in user based on user data. Filters that are applied from user data will appear as headers, sorting content into:

Popular Movies

Genres the user has shown interest in

New releases

Book-to-Movie adaptations

The purpose of these features is to allow users to browse without manually searching using commonly used filters across the platform, as well as easily browse the specific user’s preferences for efficient selection.


#### Homepage Features

The product will provide a homepage visible to all users, while also restricting any additional interaction beyond viewing movie titles to users that are logged in. Any blocked interaction will redirect users to a log-in page, prompting a log-in or account creation.

Once a user has logged into their account, the homepage will display their profile photo as a button in the top right that once pressed lets a user access their saved movies, homepage settings, account settings, and Child-Mode toggle.

The homepage will contain several separations for movie recommendations by various categories such as Genre, Award-Winning, Popularity, Recent, etc. These will be displayed as horizontal lists that contain the movie name and poster for each recommendation.

Centralized at the top of the homepage will be the navigation bar, providing a search function for movie titles and additional filtering options.


#### Movie Description Pages

The product will provide a page containing information about any given movie selected by the user. The movie profile/description page will consist of the following relevant information for explaining and recommending a movie:

Title

Description

Movie Poster

Movie Clips/Trailers

Reviews and Ratings

Availability on Streaming Services and pricing

The description page will be easily accessible from the homepage or from filtered results when browsing movies by selecting the desired movie, and will be easily closed to return the user to their previous location on their homepage. See diagram 3.2.5.5.2 for a mock-up of the movie profile/description page.


#### Child-Friendly Content Recommendations

The product will provide toggleable settings titled “Child-Mode” to limit homepage and filter results to the appropriate child-friendly ratings. This mode will restrict available movies to ratings fetched from TMDB and will prevent access to content rated for older audiences.

The separation of content between Child-Mode being toggled on and off will also create separate recommendations based on the data acquired from preferences in each state to create safer browsing for children and accurate recommendations for adults/parents. The child recommendation data will be stored alongside the main users data, but will not modify the recommendation data acquired for the main user profile.

If an attempt is made to access inappropriate content, the system will block access with a display message notifying the user that the content is unavailable in Child-Mode.


## User characteristics

The primary users of the system include:

End Users: Individuals with basic to intermediate technical knowledge who will interact with the system for daily operations. A few specific, provided stakeholders include:

Students

Movie Enthusiasts

Casual Movie Watchers

Parents, Guardians, and/or Babysitters

Book Lovers & Adaptation Enthusiasts

Administrators: Users with advanced technical expertise responsible for system maintenance, configuration, and troubleshooting.

Users are expected to have familiarity with standard operating procedures and basic computing skills. Training materials and user guides will be provided to ensure smooth adoption of the system.


## Constraints

This section details software constraints for this application.

Supported Platforms & Browsers

The web application must be compatible with Google Chrome, Mozilla Firefox, Safari, and Microsoft Edge (latest versions preferred).

Mobile responsiveness must be ensured for iOS and Android devices.

Programming Languages & Frameworks

The frontend must be developed using Django Views, HTML Templates, and Bootstrap for styling.

The backend must use Models and Templates using Django and SQLite. Specifically, Django requires Python as a language.

Database constraints: SQL for relational data storage.

Performance Limitations

The application must support up to 100,000 concurrent users without degradation.

Load time must not exceed 10 seconds for any user request.

Security Constraints

User data will be included in their own SQL database

Hashed passwords

Third-Party Integrations

API calls must not exceed 500 requests per minute to external services.

Regulatory & Compliance Requirements

Must adhere to GDPR and CCPA privacy laws.

Accessibility must comply with WCAG 2.1 AA standards.


## Assumptions and dependencies

This subsection details a list of each factor that affects or may affect the requirements, usability, and more of this application. Note that these are not design constraints, but changes to said constraints that can affect the requirements of the SRS.


#### Assumptions

In the context of this document, assumptions pertain to ideas or factors that affect the functionality or usability of the app. The authors of this document assume the following:

AS-1 Basic Application User Expertise

That a user of this application must have basic knowledge of how to navigate a website and understands that they can learn the intricacies of this application

AS-2 Basic, Stable Network Connectivity

That a user of this application must have a network connection that can support a connection to this application through HTTP

AS-3 Lofi Documents & Their Mobile Counter Parts

That all lofi mockups and representations of stylized html and css can be interpreted to a similar degree into a mobile application if not specified.


#### Dependencies

In the context of this document, dependencies relate to specific factors that the application relies on in order to run up to customer standards. This application’s dependencies are:

DE-1 Django

The authors of this document plan to utilize Django[4], a python-based web application framework, to store user data, create html templates, allow for API calls, and the entirety of our application’s functionality.

DE-2 The Movie Database (TMDB)

This system relies on The Movie Database and its API[3] for its popularity filters to function.

DE-3 SQL

The system utilizes SQL databases and its respective languages to store user data and logins, store administrator logins, and to make movie caching possible.

DE-4 macIOS & Android SDK

In order to be ported into a mobile application, some amount of development will need to be made on MacIOS and ADK


# Specific Requirements


## External interface requirements

This section identifies all the points at which the Movie Recommender System interfaces with external entities, including users, hardware, software services, and communication protocols. These interfaces define how data is exchanged between the system and its environment and ensure seamless integration of the application within its technical ecosystem. Detailing these interfaces is essential for designing a robust, interoperable, and user-friendly system that performs consistently under varying conditions.


#### User interfaces

The User Interface (UI) of the Movie Recommender System is the primary point of interaction for end-users and is designed with an emphasis on usability, accessibility, and responsiveness. The UI will be accessible via modern browsers and will support desktops, tablets, and mobile devices using responsive design practices.

To ensure a seamless and user-friendly experience, the system incorporates consistent layouts, meaning the placement of navigation elements (such as the menu, filter options, and user profile icon) remains uniform across pages to reduce cognitive load and learning effort for users. For instance, the top navigation bar, search bar, and category-based carousels will appear in the same structure whether users are on the homepage, search results, or movie detail pages.

Clear icons refer to graphical symbols that are intuitive and universally recognizable—for example, a magnifying glass for search, a gear icon for settings, or a user avatar for profiles. These icons help users identify actions quickly without needing textual guidance, improving efficiency and minimizing confusion.

The system also ensures accessible color contrasts by selecting color palettes that meet WCAG


# 2.1 AA standards. This includes maintaining a contrast ratio of at least 4.5:1 for normal text and 3:1 for large text, ensuring that all users—including those with visual impairments or color blindness—can read and interact with content comfortably.

The UI also includes personalized home pages, movie detail views, rating/review features, and account settings. Interaction elements such as buttons, dropdowns, and form inputs will be designed to support keyboard navigation and screen reader compatibility. Additionally, a child mode toggle, profile-based content personalization, and redirection for unauthenticated users will be seamlessly integrated.


#### Hardware interfaces

Since the system is cloud-hosted and accessed via a browser, hardware interface requirements for end-users are minimal. It is compatible with standard consumer devices, including desktops, laptops, smartphones, and tablets. The recommended hardware configuration includes a modern processor with at least 2 GB of RAM, and an active internet connection for streaming metadata and images. Devices must support HTML5 and modern browser standards to render dynamic components like trailers, posters, and filter panels effectively. Future enhancements may require notification permissions or offline caching support depending on feature expansion.


#### Software interfaces

The backend of the Movie Recommender System is built using the Django web framework, which is responsible for managing HTTP requests, handling user sessions, executing filtering logic, and integrating with third-party movie databases. The application communicates with a local SQLite database, which stores persistent data such as user credentials, preference tags, filter interactions, session logs, and cached movie metadata.

A critical software dependency is the TMDB API, which supplies dynamic movie content including titles, genres, cast details, ratings, and streaming availability. The system may also interface with additional APIs like Rotten Tomatoes to enrich data where applicable. These software services are accessed through RESTful APIs, with JSON used as the primary format for data exchange.

To enhance reliability and performance, the system implements a robust caching mechanism. Frequently accessed data such as popular movies, genre lists, and previously recommended items are cached locally in the database. These caches are updated periodically—either on a fixed schedule or when new data is detected—ensuring data freshness while reducing API dependency.

In the event of external API downtime or rate-limiting, the system gracefully degrades by serving cached responses instead of returning error messages. Additionally, retry logic and backoff strategies are implemented to handle transient failures without overwhelming the external services. This fallback strategy ensures that users can still browse previously accessed data and receive meaningful recommendations even when external connections are temporarily unavailable.

Authentication tokens and input validation are enforced at every endpoint to ensure secure and reliable interactions with all software components. These combined strategies allow the system to maintain functionality, reduce latency, and improve the overall user experience, even in unpredictable network or API conditions.


#### Communications interfaces

Data exchange across system layers is conducted over secure HTTPS protocols, ensuring that sensitive information—such as passwords, reviews, and user preferences—is encrypted in transit. The frontend and backend communicate using RESTful API calls following HTTP standards (e.g., GET for data retrieval, POST for data creation).

To maintain performance at scale, the system employs rate-limiting for external APIs, asynchronous request handling, and retry logic for failed transactions. Additionally, the system logs communication events and tracks API error responses for debugging and service recovery.

As usage grows, future versions may implement WebSockets or similar technologies for real-time updates and enhanced responsiveness across client sessions.


## Functional requirements

This section portrays features of the system that will be incorporated into deployment at some point in development based on their priority. Refer to the figure 3.2.A for an overall view of all the user stories represented through a universal use case diagram.

This document utilizes MoSCoW for feature prioritization. This method utilizes the following letters to portray the need for their features within a system:

M - Must-have feature. the system will not function properly and to document standards without this feature.

S - Should-have feature. Important, but non vital features that add significant functionality.

C - Could-have feature. Features that have a small impact on functionality.

W - Will-have feature. Features that are not achievable within deployment, however will be implemented eventually.

3.2.A Universal Use Case Diagram


#### System Interactions & Backend


##### User Database

Priority Rating - M (Must-Have)


###### Preconditions

System must maintain a functional user database in SQL.

Users must be able to store movie preferences.


###### Functional Requirements

REQ-1 The system must store user data including, but not limited to

Username

Password

Boolean tag whether account is utilized by a child

Email

Phone number

Filter Preference

REQ-2 The system should record and store user interactions, such as:

Movie preferences

Filter selections

REQ-3 Stored data should be used to improve personalized recommendations.


###### Postconditions

Users are allowed to make, edit, and delete their account based on their personal need.

User data is accurately saved and updated as interactions occur.

The system can present refined recommendations.


###### Risks

Database failure: Loss of stored data could prevent preference-based suggestions.

User privacy: Proper security measures must be implemented to protect user information.

Salt & Peppered Hash

User Database stored separate from movie caching


###### Diagrams

The following diagrams relate to these functional requirements. These can be found in Section 3.2.1.5 for reference.

Diagram 2 - User & Admin Login/Sign-Up Use Case Diagram

Diagram 4 - User Class Diagram

Admin User Database Priority Rating - M (Must-Have) Preconditions

The system must provide administrators with secure access to manage user accounts.

Admin users must have elevated permissions to view, modify, and deactivate accounts.

Functional Requirements

REQ-1 The system must allow administrators to perform CRUD (Create, Read, Update, Delete) operations on user accounts.

REQ-2 The system should store administrator accounts with the following information in an SQL data table.

Username

Password

Email

Phone Number

REQ-3 Administrators must be able to audit user activity, including:

Login history and failed login attempts

Preference updates and viewing activity

Security settings modifications

REQ-4 The system must provide role-based access control, ensuring that only authorized admins can modify user accounts.

REQ-5 The system should log all administrative actions and changes for compliance tracking and display them in an activity log for review.

REQ-6 Admin users must have access to bulk operations, such as mass deactivation of account data retrieval for analysis.

Postconditions

User accounts can be securely managed without compromising stored data integrity.

Admins can efficiently maintain and troubleshoot user accounts.

System logs ensure transparency in administrative actions.

Risks

Unauthorized access: Admin privilege misuse could lead to unintended data modifications.

Data integrity issues: Errors in bulk operations could affect large portions of the user database.

Security breaches: Failure to properly hash and encrypt sensitive admin activities could compromise user privacy.

Salt & Peppered Hash

Separate admin user database management logs from standard user preference storage.


###### Diagrams

The following diagrams relate to these functional requirements. These can be found in Section 3.2.1.5 for reference.

Diagram 2 - User & Admin Login/Sign-Up Use Case Diagram

Diagram 3 - Administrator Class Diagram


##### Sign-up

Priority Rating: M (Must-Have)


###### Preconditions:

User must access the sign-up page.

System must be connected to the database for user account creation.


###### Functional Requirements:

REQ-1 The system must allow new users to create an account.

REQ-2 The system must verify email format and check for duplicate usernames.

REQ-3 The system must hash passwords securely using Salted and Peppered Hash.


###### Postconditions:

A new user account is created and stored in the database.

Users are redirected to the login page or homepage after successful registration.


###### Risks:

Weak password policies can lead to security risks.

Database errors can result in incomplete registrations.


###### Diagrams

The following diagrams relate to these functional requirements. These can be found in Section 3.2.1.5 for reference.

Diagram 1 - User & Admin Login/Sign-Up Activity Diagram

Diagram 2 - User & Admin Login/Sign-Up Use Case Diagram


##### Login

Priority Rating: M (Must-Have)


###### Preconditions:

User has a valid account.

System must be able to verify login credentials with the database.


###### Functional Requirements:

REQ-1 The system must allow users to log in using either username or email and password.

REQ-2 The system must verify user credentials with encrypted records in the database.

REQ-3 The system must provide an error message on invalid credentials.

REQ-4 The system should redirect users to the personalized homepage on successful login.

REQ-5 Implement brute-force protection and session timeout.


###### Postconditions:

Authenticated users gain access to their dashboard and saved preferences.


###### Risks:

Unauthorized access attempts.

Session hijacking if proper token security is not enforced.


###### Diagrams

The following diagrams relate to these functional requirements. These can be found in Section 3.2.1.5 for reference.

Diagram 1 - User & Admin Login/Sign-Up Activity Diagram

Diagram 2 - User & Admin Login/Sign-Up Use Case Diagram


##### Diagrams

This section includes any relevant diagrams for the features in Section 3.2.1 above.

User & Admin Login/Sign-Up Activity Diagram

User & Admin Login/Sign-Up Use Case Diagram

Administrator Class Diagram

User Class Diagram

Sign Up / Login Page UI Diagram


#### Search Bar Filters


##### Popularity

Priority Rating - S (Should-Have)


###### Preconditions:

User has access to the search bar.

The system has a connection to the Rotten Tomatoes Private API.


###### Functional Requirements

REQ-1 The system must provide a popularity filter for the search bar.

REQ-2 When selected, the system should return up to the top 100 most popular movies (or fewer, based on API limitations).

REQ-3 Data is retrieved via TMDB.


###### Postconditions

The user is presented with a list of popular movies based on TMDB rankings.

The user can refine their search further if needed.


###### Risks

API availability: If the Rotten Tomatoes API becomes unavailable, the feature will be inoperable.

Relevance of popularity: Rankings may not align with user expectations; a fallback mechanism may be required.


##### Genre

Priority Rating - S (Should-Have)


###### Preconditions

User has access to the search bar.

The system has an active connection to TMDB API.


###### Functional Requirements

REQ-1 The system must provide a genre filter in the search bar.

REQ-2 Users should be able to filter by at least 7 popular genres, including:

REQ-3 Adventure, Action, Comedy, Drama, Thriller, Horror, Romantic Comedy, Musical, Black Comedy, Documentary.

REQ-4 The system must return the highest-rated movies within the selected genre (ratings provided by TMDB API).


###### Postconditions

The user receives a list of movies sorted by the selected genre.

The user can explore recommendations more easily.


###### Risks

API availability: If TMDB API shuts down, this filter will not work.

Genre relevance: These genres are expected to remain relevant for at least 20 years, but adjustments may be necessary over time.


##### Actor & Award-Winning Films Filter

Priority Rating - S (Should-Have)


###### Preconditions

User has access to the search bar.

The system can pull movie data from TMDB API.


###### Functional Requirements

REQ-1 Users can search for movies featuring specific actors.

REQ-2 When an actor’s name is entered, the system displays all movies they have appeared in.

REQ-3 Users can filter by award-winning films, including winners of:

REQ-4 Oscars, Golden Globes, BAFTAs.


###### Postconditions

Users receive filtered results based on actor or award-winning status.

They can discover films more efficiently.


###### Risks

API availability: If TMDB API shuts down, actor searches and award-winning film filters will be affected.

Award relevance: New award categories may emerge; regular updates may be needed.


##### New Releases

Priority Rating - S (Should-Have)


###### Preconditions

User has access to the search bar.

The system has up-to-date release date information for movies via API.


###### Functional Requirements

The system must provide a new releases filter for the search bar.

Users should be able to filter movies based on release date, ensuring access to the latest adaptations.

Movies included may be:

Recently published books turned into films.

Remastered classic novels adapted into movies.

General Movie Releases


###### Postconditions

The user receives a list of newly released movies.

Users can explore newly released movies more easily.


###### Risks

Database accuracy: If the system does not maintain correct release dates, users may receive outdated results.

Adaptation availability: Not all books may have corresponding movie adaptations.


##### Themes

Priority Rating - C (Could-Have)


###### Preconditions

User has access to the search bar.

The system categorizes thematic elements for movies.


###### Functional Requirements

REQ-1 The system must allow filtering by themes such as:

Class Struggles

Self-discovery

Man vs. Nature

Death

REQ-2 Users should be able to combine themes with genres to refine searches.


###### Postconditions

Users receive movie recommendations based on their selected themes.

They can more easily discover adaptations of novels with relevant thematic elements.


###### Risks

Theme classification accuracy: Some films may not be correctly categorized under themes.

User expectation mismatch: Themes may vary between books and their movie adaptations.


##### Director

Priority Rating - S (Should-Have)


###### Preconditions

User has access to the search bar.

The system must have access to movie metadata including director information from TMDB API.


###### Functional Requirements

REQ-1 The system shall allow users to search for movies by entering a director’s name.

REQ-2 The system must display all movies directed by the specified individual.


###### Postconditions

The user receives a list of movies filtered by the entered director.

The user can explore the director's full filmography efficiently.


###### Risks

API availability: If TMDB API becomes unavailable, this feature will not function.

Metadata completeness: Some movies may not have accurate or complete director data.


##### Producer

Priority Rating - S (Should-Have)


###### Preconditions

User has access to the search bar.

The system must have access to movie metadata including producer information from TMDB API.


###### Functional Requirements

REQ-1 The system shall allow users to search for movies by entering a producer’s name.

REQ-2 The system must display all movies produced by the specified individual.


###### Postconditions

The user receives a list of movies filtered by the entered producer.

The user can track movies based on producer styles or choices.


###### Risks

API availability: If TMDB API becomes unavailable, this feature will not function.

Metadata completeness: Some movies may not list producers or may list incorrect data.

Search Results Display & Sorting Options Priority Rating - M (Must-Have) Preconditions

User must have applied a search bar filter.

The system must have retrieved a list of results.


###### Functional Requirements

REQ-1 The system shall display results in a structured, user-friendly format.

REQ-2 The system must provide sorting options, including:

Release Date (Newest to Oldest, Oldest to Newest)

Popularity (Highest Rated, Most Reviewed)

Alphabetical Order (A-Z, Z-A)


###### Postconditions

The user can view and sort filtered movie results based on their preferences.


###### Risks

Sorting accuracy: Sorting may fail if metadata is missing.

Performance: Sorting large datasets may cause UI lag.


##### Combined Search Filters – Director & Producer

Priority Rating - C (Could-Have)


###### Preconditions

User has access to the search bar.

The system must be connected to TMDB API and able to cross-reference director and producer metadata.


###### Functional Requirements

REQ-1 The system must support advanced filtering by both director and producer.

REQ-2 When both names are entered, the system shall display only movies where both individuals collaborated.


###### Postconditions

The user receives a refined list of movies where the entered director and producer worked together.


###### Risks

API dependency: If data retrieval fails, the search will return incomplete or no results.

Data accuracy: Collaboration metadata may be inconsistent across movies.


##### Diagrams

This section includes any relevant diagrams for the features in Section 3.2.2 above.

Search Bar Filters UseCase Diagram

Search Bar filters Class diagram

Search Filter State Diagram

Search Filter UI Diagram


#### Homepage Filters


##### Popularity & Genre

Priority Rating - S (Should-Have)


###### Preconditions

Users must be logged in.

Systems can retrieve user preference data from their quantifier tags stored in their profile information.


###### Functional Requirements

REQ-1 The system’s homepage must provide recommended content based on user data.

REQ-2 Filters should appear as headers, sorting content into:

Popular movies.

Movies in genres the user has shown interest in.

REQ-3 The system should store user preferences in a database under each user profile (potential for class diagram in future iterations).


###### Postconditions

The user receives recommendations without needing to search manually.


###### Risks

API dependency: If TMDB API shuts down, recommendations will be disrupted.

Popularity relevance: Filtering mechanisms should stay updated with user trends.


##### New Releases

Priority Rating - S (Should-Have)


###### Preconditions

Users must be logged in.

The system can retrieve recently released movies.


###### Functional Requirements

REQ-1 The homepage must display newly released…

Book-To-Movie adaptations

Movies in General

REQ-2 These recommendations should be automatically presented as headers. See 3.2.4.5.1 for a mock-up.

REQ-3 Users can browse without manually searching for new adaptations.


###### Postconditions

Users can discover new adaptations as soon as they visit the homepage.

The browsing experience is seamless and intuitive.


###### Risks

API dependency: If release dates are pulled from an API, any downtime could affect the feature.

Adaptation frequency: Some users may expect frequent book-to-movie adaptations, but availability depends on industry trends.


##### Diagrams

Use Case Diagram with Database (Popularity & Genre, New Releases)

Activity Diagram with Database (Popularity & Genre, New Releases)


#### Homepage Features

Homepage Login & Redirects Priority Rating - S (Should-Have) Preconditions

User must be accessing the homepage.


###### Functional Requirements

REQ-1 The system must allow users to redirect to the login page if they are not signed in. See diagram 3.2.1.5.5.

REQ-2 The homepage should include a register redirect for new users.

REQ-3 The homepage should offer movie recommendations based on stored user preferences.


###### Postconditions

Users are either redirected or presented with personalized recommendations.

They can seamlessly transition to login or registration.


###### Risks

Navigation errors: Broken redirects could prevent access to login/register pages.

Recommendation accuracy: If user preference storage fails, personalized results may be incorrect.


##### Navigation Bar

Priority Rating: S (Should-Have)


###### Preconditions:

The user must be on the homepage or a page that includes the navigation bar.

The navigation bar must be successfully rendered and interactive.


###### Functional Requirements:

REQ-1: The system must allow users to search movies by title or general keyword using the navigation bar.

REQ-2: The navigation bar must interface with the filtering system to show relevant results.

REQ-3: The navigation bar must remain accessible on all pages for consistent navigation.


###### Postconditions:

Users can quickly access and locate content from anywhere in the app.

The navigation experience remains consistent and intuitive.


###### Risks:

Search Failure: If keyword matching fails, the system must inform the user that no results were found.

UI Inconsistency: Navigation bar inconsistency across pages may confuse users.

Movie Categorical Display Priority Rating: S (Should-Have) Preconditions:

The user must be on the homepage.

The system must have access to categorized movie data via the TMDB API or cached results.


###### Functional Requirements:

REQ-1: The homepage must organize movies into horizontally scrollable categories such as:

Genre

Award-Winning

Popularity

Recently Released

REQ-2: Each category section must display a row of movie posters or thumbnails. See diagram 3.2.4.5.1.

REQ-3: Rows must dynamically update based on user preferences where applicable.


###### Postconditions:

The user is presented with a clean, segmented view of movie categories.

Browsing is efficient and tailored to viewing intent.


###### Risks:

API Downtime: Without TMDB access, fallback categories or cached results must be displayed.

Performance Lag: Too many visible rows may cause load delays on lower-end devices.


##### User Profile Button

Priority Rating: S (Should-Have)


###### Preconditions:

The user is authenticated and viewing the homepage.


###### Functional Requirements:

REQ-1: A user profile icon must be visible in the top-right corner of the homepage.

REQ-2: Upon clicking, the icon must display a dropdown or redirect the user to their profile page.

REQ-3: From the profile menu, users must be able to:

Access saved movies.

Change homepage display settings.

Toggle Child Mode (see Section 3.2.6.1).

Manage account settings.


###### Postconditions:

Users can easily access profile and personalization features.


###### Risks:

Session Expiry: If session data expires, clicking the profile may result in redirection to login.

Child Mode Toggle Abuse: Profile button toggles must be protected by security settings if used by children.


##### Diagrams

Movie Categorical Display UI Diagram

Homepage Display Sequence Diagram

Use Case Diagram with Homepage


#### Movie Profiles/Description Page

Movie Description Page Priority Rating - M (Must-Have) Preconditions

User must be on the movie selection interface.

The system must have access to TMDB API and review data sources.


###### Functional Requirements

REQ-1 The system shall allow users to select a movie and view its details within the same interface.

REQ-2 The system must display the movie’s title, clear description, rating, reviews, and poster in a single view.

REQ-3 All content should be presented clearly and must not require navigation to a different page.


###### Postconditions

The user is presented with a centralized movie description interface that provides all essential details.


###### Risks

Metadata availability: Some movie details may not be available.

Internet or API latency: Slow loading may occur.

The system shall display placeholder text or hide unavailable fields gracefully.


##### Title and Description

Priority Rating - M (Must-Have)


###### Preconditions

User must be on the movie selection interface.

The system must have access to the movie’s metadata and/or user interest tags.


###### Functional Requirements

REQ-1 The system shall display the movie’s title and duration at the top of the description section.

REQ-2 A short summary (maximum 100 characters) must be shown beneath the title.

REQ-3 If the movie was recommended, the description should reflect user interests.

REQ-4 If no recommendation logic applies, the description shall be derived from metadata, including genre, setting, cast, and awards.


###### Postconditions

The user sees a concise, relevant movie summary.


###### Risks

If the description exceeds the character limit, the system may have memory overflow issues.

The system shall truncate it down to said limit.

If metadata is missing, description may not display correctly


##### Reviews and Rating

Priority Rating - M (Must-Have)


###### Preconditions

The system must have access to review data via API or internal database.

Users must be authenticated to submit ratings or reviews.


###### Functional Requirements

REQ-1 The system shall allow authenticated users to rate movies using a standardized rating scale (e.g., 1 to 5 stars).

REQ-2 Authenticated users shall be permitted to submit one written review per movie and can edit or delete it later.

REQ-3 The system must display up to three user reviews with associated ratings, with an option to expand for more.

REQ-4 The system shall calculate and display the average rating for each movie and allow sorting of reviews by date, rating, or helpfulness.

REQ-5 The system shall enforce rating accountability, preventing duplicate submissions and providing moderation tools to admin users.

REQ-6	The system shall support the ability to submit ratings to The Movie Database (TMDB) using their official API ().

Users must be authenticated

A valid TMDB session token is required to post ratings externally

Ratings submitted via the platform may enrich global TMDB review data for consistency and expanded visibility.


###### Postconditions

Users can rate and review movies locally within the application.

Reviews and ratings are visible and sortable by other users.

Ratings submitted to TMDB may reflect on external platforms, given proper authentication and session tokens.

Admins can manage reviews for quality control and accountability.


###### Risks

If reviews are unavailable, the system may be nonfunctional.

The system shall show: "No reviews available at this time.”

If the API server is down or times out, reviews and ratings cannot be fetched.

Unauthenticated users may attempt to rate or review movies, which must be blocked.

Duplicate or spammy content may affect reliability if not moderated.

TMDB integration may fail due to:

Invalid or expired session tokens

API rate limiting or connection errors


##### Movie Poster / Teaser Clip

Priority Rating - S (Should-Have)


###### Preconditions

The system must have access to TMDB API.

The user must be on the movie description page.


###### Functional Requirements

REQ-1 The system must retrieve and display the movie’s poster.

REQ-2 On hover or click, the system shall fade out the poster and automatically play a teaser clip (if available).

On mouse exit or second click, the poster must return to its original state.


###### Postconditions

The user is shown a poster and optionally a teaser in the same interfaces

If teaser content is unavailable...

The system shall show only the poster and a tooltip stating: "Teaser unavailable."


###### Risks

If the TMDB API is down or unreachable, the poster and teaser clip cannot be retrieved

Poor network conditions can cause long load times or failed playback for teaser clips.


##### Diagrams

This section includes any relevant diagrams for the features in Section 3.2.5 above.

Movie Description Display Sequence Diagram

Movie Profile/Description Page Mock-up


#### Child-Friendly Content Recommendations

Age-Based Content Filtering Priority Rating - M (Must-Have) Preconditions

The user has created a profile with an age or child mode selected.

The system must have access to content rating metadata (e.g., G, PG, PG-13).


###### Functional Requirements

REQ-1 The system shall allow users to create a child-safe profile.

REQ-2 The system shall only recommend movies and shows marked appropriate for the child’s age.

REQ-3 If unsafe content is attempted, the system shall hide or restrict access and display a message: “This content is unavailable in child mode.”

REQ-4 The system shall support playlist creation for child-friendly content.

REQ-5 The system shall include a “Child Mode On/Off” toggle button in the user profile for quick switching between regular and child-safe browsing.

REQ-6 When "Child Mode" is ON, all filtered content shall match child-appropriate ratings only.


###### Postconditions

Kids only see age-appropriate content.

Parents feel reassured that inappropriate content is filtered.

Users can activate or deactivate child filtering using the toggle.


###### Risks

Content ratings may be missing or inconsistent across APIs.

Kids may switch profiles or toggle off child mode if not locked (future enhancement: parental PIN required to turn off).


##### Parental Controls and Separate Recommendations

Priority Rating - S (Should-Have)


###### Preconditions

The user is logged in and has a child profile linked to their account.


###### Functional Requirements

REQ-1 The system must maintain separate recommendation histories for parents and their children.

REQ-2 The parent can view or manage what their child has watched or is recommended.

REQ-3 The system should allow parents to see what other parents (friends) are recommending for their kids.

REQ-4 The system must provide a repeat-playlist option for shows/movies frequently rewatched by children.

REQ-5 The toggle state for “Child Mode On/Off” must be persistent and user-specific until manually changed.


###### Postconditions

Parents can easily manage and separate viewing experiences.

Kids have a consistent, curated experience with the toggle helping control viewing mode.


###### Risks

Privacy: Sharing what friends’ kids watch may need opt-in consent.

Recommendation confusion: Mixing child and adult preferences could affect accuracy.

Improper toggling: If the child toggles off child mode, risk of exposure to inappropriate content exists. Future updates may require a PIN lock on toggle.

Note: Refer to Appendix A.1.4 – Lofi Mockup for the child-friendly content recommendations interface.


##### Child-Friendly Content Recommendations Sequence Diagram

Child-Mode Toggle in User Settings UI Diagram


## Performance requirements


#### API Dependency & Response Time

The Movie Recommender’s performance is heavily reliant on external APIs and their polling mechanisms. Due to the unpredictable nature of APIs, every fetch carries an inherent risk of delays or failures.

API requests should ideally complete within 0.1 to 5 seconds, depending on the volume of data being retrieved. The system shall display a progress bar or some indication that the application is working on a request.

If an API request exceeds 10 seconds, the system must trigger a timeout and notify the user with an appropriate error message.


#### Caching & Data Persistence

All fetched movie data should be cached to improve response time and reduce repetitive API calls.

Cached movie entries should remain in the database for up to one month unless accessed recently. If a movie entry is not requested within this timeframe, it should be automatically removed to optimize storage and performance.


#### Scalability

The system must auto-scale to support double peak traffic during high-demand periods.

Cloud infrastructure should support horizontal scaling when CPU usage exceeds 75%.


#### Availability & Reliability

The web application must maintain 99.99% uptime annually.

Scheduled downtime should not exceed 30 minutes per month for maintenance.


#### Load Testing & Stress Testing

Load testing should simulate 200,000 concurrent users without crashing.

Stress testing should identify breakpoints under 5x normal traffic loads.


#### Database Performance

Query execution time must be under 250 milliseconds for common requests.

Cache system must reduce direct database hits by at least 50%.


## Design Constraints


#### Framework and Language Constraint

The system must be developed using Django (Python) for backend processing.

The frontend must be created using Django HTML templates and Bootstrap for responsiveness.


#### Database Constraint

The application must use SQLite for all data storage, including user profiles, preferences, reviews, and admin logs.


#### Security Standards

Passwords must be stored using salted and peppered hash encryption.

Role-Based Access Control (RBAC) must be used to differentiate between normal users and admin users.


#### Browser Compatibility

The system must work smoothly on the latest versions of Chrome, Firefox, Safari, and Microsoft Edge.

The layout must be responsive across desktop, tablet, and mobile devices.


#### External API Use

The layout must be responsive across desktop, tablet, and mobile devices.

The system relies on The Movie Database (TMDB) API. API call limits and availability must be considered during development.

A local cache mechanism must be used to prevent system failure if the API is down.


#### Compliance and Accessibility

The design must meet GDPR and CCPA privacy laws.

Accessibility must follow WCAG 2.1 AA standards (color contrast, keyboard navigation, etc.)


#### Performance

The system should load any page or search result in under 10 seconds, even with 100,000 concurrent users.

Backend queries must not exceed 250 milliseconds for common operations.


## Software System Attributes

This section describes the non-functional attributes of the system that impact its usability, reliability, performance, and security.


#### Usability

The Movie Recommender System will be easy to use and understand. It will work smoothly on computers, tablets, and mobile phones. The layout will be clean and simple, with clear buttons, icons, and menus that are always in the same place. This helps users find what they need without confusion. A help guide and small tips will be available to help new users learn how to use the system.


#### Reliability

The system is designed to maintain 99.99% uptime annually. It will continue functioning even if external APIs (e.g., TMDB) are temporarily unavailable, using a local caching mechanism to provide fallback data. Session recovery features will allow users to resume activity after temporary disconnections or timeouts.


#### Availability

The application will be hosted on scalable cloud infrastructure, capable of supporting high availability. Maintenance windows will be scheduled during low-traffic periods and will not exceed 30 minutes per month. A status page may be provided to alert users of downtime or disruptions.


#### Security

Security is ensured through the following:

Passwords stored with salted and peppered hash encryption.

Role-Based Access Control (RBAC) to separate user and admin privileges.

Enforced HTTPS for all communication between the client and server.

Rate-limiting and brute-force protection for authentication endpoints.


#### Maintainability

The system is developed using the Django framework with modular architecture to promote maintainability. Components such as filters, user authentication, and movie recommendations are decoupled for easier debugging and updates. Well-documented code, logging mechanisms, and version control will support future maintenance and development.


#### Portability

Since the system runs in a web browser, it can be used on any device or operating system (Windows, Mac, iOS, Android). It will also be ready for mobile app development in the future, and the design will support that.


## Other Requirements

This section describes additional important requirements that do not directly fit into functional or interface categories but are still necessary for the system’s success.


#### Regulatory and Compliance Requirements

The system must comply with GDPR to protect user data privacy.

The system should follow WCAG 2.1 guidelines to ensure accessibility for users with disabilities.

Documentation and system specifications should align with IEEE Standard 830-1998 for software requirements.


#### Software Quality Attributes

Usability: The system must be easy to use, with a clean and consistent layout, responsive design, and minimal learning curve for new users.

Scalability: The system must support high traffic and scale automatically to handle double peak user loads.

Performance: Search results and movie listings should be displayed within 2–5 seconds during normal conditions.

Security: All sensitive data (such as user accounts and preferences) must be stored securely using salted and peppered hashing, and all communications must be encrypted via HTTPS.


#### Business Rules

Only logged-in users are allowed to save, rate, or write reviews for movies.

User preferences, such as filters and settings, should be preserved even after logout.

Admin users have elevated access rights and can manage movie content, user data, and moderate reviews.

All users must agree to the terms of service and data policy during account registration.


#### API Usage and Fallback Mechanism

The system depends on The Movie Database (TMDB) API for most real-time content.

To avoid service disruption, a local caching system must be used to store frequently accessed data and ensure the app remains functional if the API is temporarily unavailable.

API requests should respect rate limits and include timeout and retry mechanisms for robustness.


# Appendix


## Appendix A: Analysis Models

Optionally, include any pertinent analysis models, such as data flow diagrams, class diagrams, state-transition diagrams, or entity-relationship diagrams.

Appendix A.1.0 - Lo-fi Mockup for Home Page including search, personalized recommendations, filtering, and trending movies.

Appendix A.1.1 - Lo Fi Mockup for a Watch Page List that displays saved movies, sorting options, and a remove button.

Appendix A.1.2 - Lo-Fi Mockup for a Movie Details Page that shows title, description, poster, streaming links, and reviews.

Appendix A.1.3 - Lofi Mockup for a User Ratings & Reviews Page that lists user reviews, a text box for writing new reviews, and a sorting feature.

Appendix A.1.4 - Lofi Mockup for a Movie Playlist Page

Appendix A.1.4 - Lofi Mockup for Child-Friendly Content Recommendations

Appendix A.2.1 - Sequence Diagram for Genre Search Bar Filters

Appendix A.2.2 - Sequence Diagram for Genre Search Bar Filters

Appendix A.2.4 - Use case Diagram for Director & Producer Search Bar Filters

Appendix A.2.5 - Use case Diagram for Actor & Award Winning Film

Appendix A.2.6 - Use case Diagram for Movie Description Page

Appendix A.2.7 - Sequence Diagram for Sorting Movies by New Releases

Appendix A.2.8 - Sequence Diagram for Applying and Returning Filters

Appendix A.2.9 - Entity-Relationship Diagram showing the core entities and relationships within the Movie Recommender System

Appendix A.2.10 - Use case diagram for rating and review


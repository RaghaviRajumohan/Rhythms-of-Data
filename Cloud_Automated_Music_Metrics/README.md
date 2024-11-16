## Automated Music Metrics Tracker

### Overview

In the modern music industry, where data drives success, tracking and analyzing performance metrics is essential. This repository contains two automated solutions designed to streamline workflows for music professionals:

1. **YouTube Comments Tracker**: Automates the tracking and storage of YouTube video comments and video metrics.
2. **Daily Artist Metrics Tracker**: Tracks and centralizes daily artist metrics from YouTube and Spotify.

### Objective
This project leverages the **Google Cloud Console** to automate the extraction, processing, and storage of music industry performance metrics, providing real-time, actionable insights. The system uses cloud functions to interact with the **YouTube Data API** and **Spotify API**, retrieving data such as video metrics, comments, follower counts, and popularity scores. These functions process the raw data into structured, analysis-ready formats and update a centralized Google Sheet to ensure data accuracy and accessibility. Using Google Cloud Scheduler, these functions are triggered on a scheduled basis (e.g., daily), ensuring that metrics are updated automatically without manual intervention. By automating this pipeline, the project eliminates manual workflows, enabling music industry professionals to monitor artist growth, audience engagement, and market trends efficiently and effectively.

--- 
### Tools and Technologies

#### Cloud Infrastructure: ![Google Cloud Console](https://img.shields.io/badge/Google%20Cloud%20Console-4285F4?style=flat-square&logo=google-cloud&logoColor=white)  ![Google Cloud Scheduler](https://img.shields.io/badge/Google%20Cloud%20Scheduler-F4B400?style=flat-square&logo=google-cloud&logoColor=white) ![google-auth](https://img.shields.io/badge/google--auth-34A853?style=flat-square&logo=google&logoColor=white)   

#### Storage and Integration: ![Google Sheets](https://img.shields.io/badge/Google%20Sheets-34A853?style=flat-square&logo=google-sheets&logoColor=white)  ![gspread](https://img.shields.io/badge/gspread-34A853?style=flat-square&logo=python&logoColor=white)

#### Programming and Libraries: ![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)   ![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)   ![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white)   ![HTTPS Requests](https://img.shields.io/badge/HTTPS%20Requests-20232A?style=flat-square&logo=python&logoColor=white)  ![logging](https://img.shields.io/badge/logging-F4B400?style=flat-square&logo=python&logoColor=white)

#### API Interactions: ![YouTube API](https://img.shields.io/badge/YouTube%20API-FF0000?style=flat-square&logo=youtube&logoColor=white)  ![Spotify API](https://img.shields.io/badge/Spotify%20API-1DB954?style=flat-square&logo=spotify&logoColor=white)

---

### Demo Videos

#### Comments Tracker Demo (Click)
<a href="https://youtu.be/vbNEWR7OnXg" target="_blank">
  <img src="https://img.youtube.com/vi/vbNEWR7OnXg/0.jpg" alt="Comments Tracker" width="400">
</a>

#### Daily Metrics Demo (Click)
<a href="https://youtu.be/KiGJzic31Zo" target="_blank">
  <img src="https://img.youtube.com/vi/KiGJzic31Zo/0.jpg" alt="Daily Metrics" width="400">
</a>


#### Comments Tracker Demo (Click)
<a href="https://youtu.be/vbNEWR7OnXg" target="_blank" rel="noopener noreferrer">
  <img src="https://img.youtube.com/vi/vbNEWR7OnXg/0.jpg" alt="Comments Tracker" width="400">
</a>

#### Daily Metrics Demo (Click)
<a href="https://youtu.be/KiGJzic31Zo" target="_blank" rel="noopener noreferrer">
  <img src="https://img.youtube.com/vi/KiGJzic31Zo/0.jpg" alt="Daily Metrics" width="400">
</a>


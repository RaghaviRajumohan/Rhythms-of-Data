## Automated Music Metrics Tracker

### Overview

In the modern music industry, where data drives success, tracking and analyzing performance metrics is essential. This repository contains two automated solutions designed to streamline workflows for music professionals:

1. **YouTube Comments Tracker**: Automates the tracking and storage of YouTube video comments and video metrics.
2. **Daily Artist Metrics Tracker**: Tracks and centralizes daily artist metrics from YouTube and Spotify.

### Objective

This project leverages the **Google Cloud Console** to automate the extraction, processing, and storage of music industry performance metrics, providing real-time, actionable insights. The system uses cloud functions to interact with the **YouTube Data API** and **Spotify API**, retrieving data such as video metrics, comments, follower counts, and popularity scores. These functions process the raw data into structured, analysis-ready formats and update a centralized Google Sheet to ensure data accuracy and accessibility. Using Google Cloud Scheduler, these functions are triggered on a scheduled basis (e.g., daily), ensuring that metrics are updated automatically without manual intervention. By automating this pipeline, the project eliminates manual workflows, enabling music industry professionals to monitor artist growth, audience engagement, and market trends efficiently and effectively.


### Tools and Technologies

#### Cloud Infrastructure: ![Google Cloud Functions](https://img.shields.io/badge/Google%20Cloud-Functions-blue) ![Google Cloud Scheduler](https://img.shields.io/badge/Google%20Cloud-Scheduler-orange)


#### API Interactions: ![YouTube Data API](https://img.shields.io/badge/YouTube-Data%20API-red)  ![Spotify Web API](https://img.shields.io/badge/Spotify-Web%20API-green)

#### Storage and Integration: ![Google Sheets](https://img.shields.io/badge/Google%20Sheets-Integration-brightgreen)  ![gspread](https://img.shields.io/badge/gspread-Google%20Sheets%20Access-lightblue)

### Programming and Libraries: ![Python](https://img.shields.io/badge/Python-Programming%20Language-yellow)  ![Requests](https://img.shields.io/badge/Requests-HTTP%20Library-blue)  ![google-auth](https://img.shields.io/badge/google--auth-API%20Authentication-brightgreen)  ![logging](https://img.shields.io/badge/logging-Debugging%20Logs-yellowgreen)![Pandas](https://img.shields.io/badge/Pandas-Data%20Manipulation-blue)  ![NumPy](https://img.shields.io/badge/NumPy-Scientific%20Computing-lightblue)

---

### Cloud Infrastructure
![Google Cloud Console](https://img.shields.io/badge/Google%20Cloud-Console-4285F4?style=flat-square&logo=google-cloud&logoColor=white)  
![Google Cloud Scheduler](https://img.shields.io/badge/Google%20Cloud-Scheduler-F4B400?style=flat-square&logo=google-cloud&logoColor=white)

### API Interactions
![YouTube API](https://img.shields.io/badge/YouTube%20API-FF0000?style=flat-square&logo=youtube&logoColor=white)  
![Spotify Web API](https://img.shields.io/badge/Spotify%20Web%20API-1DB954?style=flat-square&logo=spotify&logoColor=white)  

### Storage and Integration
![Google Sheets](https://img.shields.io/badge/Google%20Sheets-Integration-34A853?style=flat-square&logo=google-sheets&logoColor=white)  
![gspread](https://img.shields.io/badge/gspread-Google%20Sheets%20Access-34A853?style=flat-square&logo=python&logoColor=white)

### Programming and Libraries
![Python](https://img.shields.io/badge/Python-Programming%20Language-3776AB?style=flat-square&logo=python&logoColor=white)  
![Pandas](https://img.shields.io/badge/Pandas-Data%20Manipulation-150458?style=flat-square&logo=pandas&logoColor=white)  
![NumPy](https://img.shields.io/badge/NumPy-Scientific%20Computing-013243?style=flat-square&logo=numpy&logoColor=white)  
![Requests](https://img.shields.io/badge/Requests-HTTP%20Library-20232A?style=flat-square&logo=python&logoColor=white)  
![google-auth](https://img.shields.io/badge/google--auth-API%20Authentication-34A853?style=flat-square&logo=google&logoColor=white)  
![logging](https://img.shields.io/badge/logging-Debugging%20Logs-F4B400?style=flat-square&logo=python&logoColor=white)


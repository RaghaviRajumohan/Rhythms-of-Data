### Automated Music Metrics Tracker

#### Overview

In the modern music industry, where data drives success, tracking and analyzing performance metrics is essential. This repository contains two automated solutions designed to streamline workflows for music professionals:

1. **YouTube Comments Tracker**: Automates the tracking and storage of YouTube video comments and video metrics.
2. **Daily Artist Metrics Tracker**: Tracks and centralizes daily artist metrics from YouTube and Spotify.

#### Objective

This project leverages the **Google Cloud Console** to automate the extraction, processing, and storage of music industry performance metrics, providing real-time, actionable insights. The system uses cloud functions to interact with the **YouTube Data API** and **Spotify API**, retrieving data such as video metrics, comments, follower counts, and popularity scores. These functions process the raw data into structured, analysis-ready formats and update a centralized Google Sheet to ensure data accuracy and accessibility. Using Google Cloud Scheduler, these functions are triggered on a scheduled basis (e.g., daily), ensuring that metrics are updated automatically without manual intervention. By automating this pipeline, the project eliminates manual workflows, enabling music industry professionals to monitor artist growth, audience engagement, and market trends efficiently and effectively.

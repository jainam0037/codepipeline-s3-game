# Meme Matching Card Game

## Overview
This project is a simple meme matching card game where players flip cards to find matching pairs of memes. The objective is to clear all the cards by matching them correctly.

## Key Features
- **Card Matching Logic**: Players click on cards to reveal images. If two cards match, they are cleared from the board.
- **Shuffle & Match**: The game logic includes shuffling the cards at the start and checking for pairs on each move.
- **Simple Styling**: Basic CSS for styling the game interface.

## Code Structure
- `index.html`: Contains the static structure of the game, including buttons and text.
- `game.js`: JavaScript file responsible for the core logic like shuffling, flipping, and matching cards.
- `style.css`: Styles the layout and appearance of the game.
- **Images**: Five meme images are used, stored in an array for shuffling during gameplay.

## Hosting and Deployment

### 1. Upload Code to GitHub
Before deploying the game to AWS, upload the project files to a GitHub repository.

- **Repository**: Fork the project repository containing the HTML, JavaScript, CSS, and meme images.
- **GitHub Connection**: This repository will be linked to AWS CodePipeline for continuous integration and deployment.

### 2. Configure S3 for Website Hosting
Amazon S3 is used to host the game as a static website.

#### Steps:
1. **Create an S3 Bucket**:
   - Go to the AWS Management Console, navigate to S3, and create a bucket (ensure the name is globally unique).

2. **Public Access**:
   - Disable "Block all public access" to make the website accessible publicly.

3. **Enable Static Website Hosting**:
   - In the bucket properties, enable static website hosting and set `index.html` as the index document.

4. **Permissions**:
   - Add a bucket policy that allows public read access to the objects stored in the bucket.

### 3. Set Up AWS CodePipeline for Automated Deployment
AWS CodePipeline automates the deployment process, pushing changes from GitHub to S3.

#### Steps:
1. **Source Stage**:
   - Choose GitHub as the source for the code. Connect your GitHub repository to CodePipeline.

2. **Build Stage**:
   - Skip the build stage for this project since no build or compilation is required.

3. **Deploy Stage**:
   - Set S3 as the deployment destination. This will automatically push code changes to the S3 bucket.

### 4. Testing the Pipeline
Once CodePipeline is set up:

- It automatically fetches code from GitHub and deploys it to S3.
- The game will be accessible via the S3 bucket's static website URL.

### 5. Continuous Deployment and Code Updates
- **Automatic Updates**: Whenever you make updates to the code (e.g., changing the welcome message in `index.html`), CodePipeline detects the changes and redeploys the updated code to S3.
- **Live Updates**: The changes will be reflected immediately on the live site.

## Clean-Up
After completing the project, clean up the AWS resources to avoid incurring unnecessary costs.

1. **Delete the Pipeline**:
   - Go to the AWS CodePipeline dashboard and delete the pipeline.

2. **Delete the S3 Bucket**:
   - Before deleting, ensure you empty the bucket. Then, delete the bucket to prevent storage charges.

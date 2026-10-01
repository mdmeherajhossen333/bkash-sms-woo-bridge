# bKash SMS → WooCommerce Bridge v2.1

## What is included
- Android SMS receiver that detects merchant payment SMS, extracts amount + TrxID, and sends them over HTTPS.
- WooCommerce plugin with an admin page under WooCommerce → bKash SMS Bridge.
- Optional checkout field for the payer's bKash number to improve matching.
- GitHub Actions workflow that builds a debug APK and uploads it as an artifact.

## Important
This is notification-based automation, not official bKash API verification. It never automates bKash PIN/OTP or private bKash app endpoints.

## Setup
1. Install the WordPress plugin and activate it.
2. Open WooCommerce → bKash SMS Bridge.
3. Generate a long random secret token and save it.
4. Put the REST endpoint and same token into the Android app.
5. Keep the merchant phone online and allow SMS permission.
6. Commit/push this project to your GitHub repository.
7. GitHub → Actions → Build Android APK → Run workflow.
8. Download the `bkash-woo-bridge-apk` artifact.

## Matching
The bridge only completes an order when exactly one recent pending/on-hold order has the same amount, with an optional payer-number match. If multiple orders match, it rejects the payment rather than guessing.

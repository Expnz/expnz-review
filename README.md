# Expnz - App Review Sample Data Repository

Purpose: This repository contains curated sample receipt images for App Store and Google Play reviewers testing the Expnz expense tracking application.

## Overview
Expnz is a privacy-centric expense management tool designed for independent professionals. The application utilizes the Gemini AI API to perform OCR and structured data extraction from receipt images, allowing users to digitize financial records for tax compliance without manual entry.

## Privacy & Data Handling

Expnz is architected with privacy-first principles, ensuring users maintain complete control over their financial data.

### Local-First Architecture
All transaction data and receipt metadata are stored **exclusively on the user's device**. There is no centralized database containing user financial information.

### Decentralized Cloud Sync
Cloud synchronization is entirely **optional** and uses the user's personal iCloud (iOS) or Google Drive (Android) containers via standard system APIs. The developer has **zero access** to synchronized data.

### Privacy-Focused Authentication

**Production Environment:**  
The app uses Apple Sign-In and Google Sign-In exclusively, ensuring seamless integration with users' personal cloud storage without requiring separate account credentials.

**Review Environment:**  
For this review only, traditional email/password authentication has been temporarily enabled via Firebase Remote Config to allow testing without requiring reviewers' personal OAuth credentials. This authentication method will be disabled immediately following App Store approval to maintain our privacy-first standards.

### Zero-Knowledge Infrastructure
The developer **cannot access** user financial details or transaction content at any time. All sensitive data remains under exclusive user control, stored either locally or in their personal cloud accounts.

### Telemetry & Analytics
To optimize regional features (currency support, localization) and monitor API performance, the app collects minimal anonymized data with **explicit user consent**:

- **Coarse Location:** City-level only (e.g., "Chennai, India") - never precise GPS coordinates
- **Usage Metrics:** Aggregate monthly bill upload counts - no transaction amounts or merchant details

Users can opt out of all analytics collection at any time via Settings.

### AI Processing & Data Retention
Receipt image processing is performed via secure, encrypted API calls to Google's Gemini AI service. Images are processed in real-time for text extraction purposes only and are **never stored, cached, or retained** by either our infrastructure or the AI provider beyond the duration of the processing request.

### Compliance
**Full Privacy Policy:** [https://expnz.github.io/expnz-app/privacy.html](https://expnz.github.io/expnz-app/privacy.html)  
**Terms of Service:** [https://expnz.github.io/expnz-app/terms.html](https://expnz.github.io/expnz-app/terms.html)

## For App Review Teams

### Reviewer Credentials
Email:    reviewer@getexpnz.com
Password: [Provided in App Review Information section]

### Admin Credentials
Email:    test-admin@getexpnz.com
Password: [Provided in App Review Information section]

### Reviewer Account Management

**Administrative Access Required:**  
Reviewer account configuration and management is restricted to users with administrative privileges. This includes:

- Access to reviewer-specific features and settings
- Monitoring and analytics for review accounts

**Security Implementation:**  
The reviewer management system is implemented via Firebase Cloud Functions with role-based access control (RBAC). Only authenticated administrators can modify reviewer account settings, ensuring the integrity of the review process.

**Post-Review Configuration:**  
After App Store approval, the email/password authentication method will be disabled remotely via Firebase Remote Config. The reviewer account will remain accessible for future app updates and reviews.

## Sample Bills for Testing

### Accessing Sample Receipts

All sample receipt images are available in the **[Sample Bills](Sample%20Bills/)** folder of this repository. These receipts have been specifically curated to demonstrate Expnz's AI extraction capabilities across various business expense categories.

### How to Use Sample Bills

1. **Clone or download this repository** as ZIP
2. **Extract the ZIP file**
3. **Navigate to Sample Bills folder**
4. **All receipts ready for testing**

### Testing Workflow

Once you have downloaded sample receipts:

1. **Open Expnz App**
   - Login with: `reviewer@getexpnz.com`
   - Use password provided in App Review Information

2. **Scan Your First Receipt**
   - Select **"Take Photo / Select from Gallery"** or **"Upload Files"**
   - Choose a downloaded sample bill from your device
   - Wait for AI processing

3. **Verify AI Extraction**
   - Confirm merchant name extracted correctly
   - Check date parsing accuracy
   - Verify total amount matches receipt
   - Review itemized breakdown

4. **Test Editing Capabilities**
   - Tap the pencil icon in bill details page to edit any field
   - Modify merchant name, amount, or date
   - Assign expense category

5. **Repeat for Multiple Bills**
   - Upload additional sample bills
   - Test filtering
   - Verify data organization


## Subscription Model

### Free Tier
- **Lifetime Limit:** 50 bills total
- **Note:** Users can delete old bills to upload new ones within the 50-bill limit.

### Pro Tier ($4.99/month)
- **Bill Limit:** 1000 bills total
- **Note:** Users can delete old bills to upload new ones within the 1,000-bill limit.


## Features to Test

### Core Functionality

**Receipt Scanning & AI Extraction**
- Upload sample bills from the [Sample Bills](Sample%20Bills/) folder
- Verify merchant name, date, and amount extraction
- Check itemized breakdown accuracy
- Test with multiple receipt types (grocery, restaurant, office supplies, etc.)

**Bill Management**
- View all bills in organized list
- Tap on any bill to see full details
- Edit bills using the pencil icon
- Delete individual bills
- Filter by date range or category

**Categorization**
- Change categories for existing bills (Groceries, Meals & Entertainment, Travel, Office Supplies, etc.)
- Filter bills by category

**Bill Limit Testing**
- Upload more than 50 bills (Free tier limit) without restriction
- Verify Pro subscription removes the Free tier limitation

**Export Functionality**
- Navigate to Settings → Export
- Export all bills to Zip format
- Export all bills to CSV format
- Verify exported data completeness

**Cloud Backup**
- Settings → Backup & Sync
- Enable iCloud backup (iOS) or Google Drive backup (Android)
- Verify backup initiation
- Test restore functionality (optional)

**Data Privacy Controls**
- Settings → Privacy
- Review data collection consent options
- Test opt-out for analytics
- Verify local-first storage claims


## Troubleshooting

### Common Scenarios

**Issue:** Account starts empty with no bills  
**Resolution:** This is expected behavior. Expnz uses local-first architecture with no backend database. All users, including reviewers, start with a clean state. Use sample bills from the [Sample Bills](Sample%20Bills/) folder for testing.

**Issue:** "Internet connection required" error during scanning  
**Resolution:** Receipt OCR requires network connectivity to access Gemini AI API. This is normal behavior and disclosed during onboarding. Ensure device has active internet connection.

**Issue:** AI extraction appears incomplete or inaccurate  
**Resolution:** Sample bills are optimized for high accuracy (95%+). Real-world receipts may vary in quality. Users can manually edit any extracted field via the pencil icon in bill details.

**Issue:** Cloud backup fails or doesn't appear  
**Resolution:** Cloud backup requires signing into your personal iCloud (iOS) or Google Drive (Android) account. The app uses standard system APIs - ensure you're signed into cloud services in device settings.

**Issue:** Sample bill image URLs not loading  
**Resolution:** Verify repository is set to PUBLIC visibility. URLs must use `raw.githubusercontent.com` format, not standard `github.com` links.


## Frequently Asked Questions

**Q: Why does the reviewer account start with no data?**  
A: Expnz uses local-first storage with no backend database. Every user, including reviewers, starts with an empty state. Sample bills in the [Sample Bills](Sample%20Bills/) folder are provided specifically for testing purposes.

**Q: Can I test cloud backup without my personal account?**  
A: Cloud backup requires the reviewer's personal iCloud (iOS) or Google Drive (Android) credentials. This demonstrates our privacy-first model where data syncs to the user's own cloud storage, not our servers. Backup testing is optional but recommended to verify the feature works correctly.

**Q: What happens to email/password authentication after approval?**  
A: Email/password login will be disabled remotely via Firebase Remote Config immediately after App Store approval. Production users will only see Apple Sign-In and Google Sign-In options. No app update is required - the change is server-side only.

**Q: Is AI processing done on-device?**  
A: No. Receipt OCR is processed via Google's Gemini AI API over secure HTTPS. Images are transmitted for processing and are not stored by either Expnz or Google. An internet connection is required for scanning.

**Q: What happens if I delete the app?**  
A: All locally stored data is permanently deleted (standard iOS/Android behavior). If cloud backup was enabled, data remains in the user's personal iCloud/Google Drive and can be restored upon app reinstallation.

**Q: Can users export their data?**  
A: Yes. Users can export all bills to ZIP, JSON or CSV format. This ensures data portability.

**Q: What data does Expnz collect?**  
A: With explicit user consent only:
- Coarse location (city-level, e.g., "Chennai, India") for regional feature optimization
- Monthly aggregate bill upload counts for API scaling
- NO financial details, merchant data, or transaction amounts are collected


## Support & Contact

**Primary Contact:**  
📧 Email: support@getexpnz.com  
⏰ Response Time: Within 2 hours during business hours (9 AM - 6 PM IST, Monday-Friday)  
🌍 Timezone: India Standard Time (UTC+5:30)

**Escalation Contact:**  
📧 Email: sathish@nyl.technology
📞 Phone: +91 93454 62312

**Repository Issues:**  
If sample bills are inaccessible or URLs are broken, please file an issue in this GitHub repository or contact us directly at the email above.

### Response Commitment

We are committed to responding promptly to all reviewer inquiries:
- **Critical Issues** (app crashes, login failures): Within 1 hour
- **Feature Questions** (how to test, expected behavior): Within 2 hours
- **General Inquiries**: Within 4 hours

**After-Hours Support:**  
For urgent issues outside business hours, please email with "URGENT - APP REVIEW" in the subject line. We monitor critical communications 24/7 during active review periods.

### What to Include in Support Requests

To help us assist you quickly, please provide:
- Device model and OS version (e.g., iPhone 14 Pro, iOS 17.2)
- Detailed description of the issue
- Screenshots or screen recordings if applicable
- Steps to reproduce the issue

## Documentation Links

### Official Documentation

**Privacy Policy:**  
🔗 [https://expnz.github.io/expnz-app/privacy.html](https://expnz.github.io/expnz-app/privacy.html)  
Comprehensive privacy policy covering data collection, storage, and user rights.

**Terms of Service:**  
🔗 [https://expnz.github.io/expnz-app/terms.html](https://expnz.github.io/expnz-app/terms.html)  
Legal terms governing app usage, subscriptions, and user obligations.


## Developer Information

### Company Details

**Legal Entity:** NYL10 Softwares Private Limited  
**Headquarters:** Chennai, Tamil Nadu, India  
**Registration No:** 33AAGCN2029R1Z6
**Tax ID:** CHEN10786G




# Email Automation Using Python

A complete automated Python pipeline that **reads names and email addresses from an Excel spreadsheet** and **dispatches personalized emails** with dynamic subjects and custom body content.

---

## 📌 Topics Covered
1. **Reading Data from Excel with Pandas:**
   * Using `pandas.read_excel()` to load tabular contact information.
   * Cleaning missing data with `.dropna(subset=['Name', 'Email'])`.
2. **Dynamic Email Personalization:**
   * Programmatically generating personalized emails (`f"Hello {name},"`) tailored to each individual recipient.
   * Formatting custom subjects incorporating the recipient's name and registered event.
   * Supporting both clean **Plain Text** and modern **HTML Rich Text** for maximum email client compatibility.
3. **Sending Emails via SMTP (`smtplib` & `email.message`):**
   * Connecting securely via SSL on port `465` (`smtplib.SMTP_SSL`) or STARTTLS on port `587`.
   * Authenticating using modern App Passwords.
4. **Secure Credential Management:**
   * Protecting sender credentials with environment variables (`python-dotenv` & `.env`).
   * `.gitignore` prevents sensitive credentials from ever being committed to GitHub.
   * Includes a safe **Dry-Run / Simulation Mode** for testing without needing real credentials.

---

## 📂 Project Structure

```text
Email_Automation/
├── send_emails.py                 # Main Python email automation script
├── recipients.xlsx                # Sample Excel sheet containing recipient details
├── .env.example                   # Template for email credentials
├── .gitignore                     # Prevents .env and credentials from being pushed
├── received_email_screenshot.png  # Screenshot of a successfully received personalized email
└── README.md                      # Complete documentation and setup guide
```

---

## 🚀 How to Run

### Option 1: Safe Test / Simulation Mode (Default)
Run the script directly to verify the Excel data reading and personalized message formatting:
```bash
python send_emails.py
```
*(If `.env` is not configured, it automatically runs in simulation mode, displaying each prepared email in the console).*

### Option 2: Live Dispatch via SMTP (Gmail / Outlook)
1. Copy `.env.example` to `.env`:
   ```bash
   cp .env.example .env
   ```
2. Open `.env` and fill in your sender email and **16-character Google App Password**:
   ```ini
   SENDER_EMAIL=your_email@gmail.com
   SENDER_PASSWORD=your_16_character_app_password
   ```
   > **Note on Gmail:** Generate an App Password at: [Google Account Security → App Passwords](https://myaccount.google.com/apppasswords).
3. Run the script:
   ```bash
   python send_emails.py
   ```

---

## 📊 Sample Excel Structure (`recipients.xlsx`)

| Name | Email | Event | Registration_ID |
| :--- | :--- | :--- | :--- |
| Alex Smith | alex.smith@example.com | Python Workshop | REG-101 |
| Emily Davis | emily.davis@example.com | Web Development Bootcamp | REG-102 |
| Michael Brown | michael.brown@example.com | Data Science Seminar | REG-103 |
| Sarah Connor | sarah.connor@example.com | Python Workshop | REG-104 |
| David Johnson | david.j@example.com | AI & Machine Learning Meetup | REG-105 |

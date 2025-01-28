![image](https://firebasestorage.googleapis.com/v0/b/checkoutmerchant-8cc2f.appspot.com/o/agreed%2FagreedLogoColored.png?alt=media&token=4c3d1dc6-2e75-4cfb-a40e-c77f9afe276f)
# Agreed

Agreed is a one-stop solution for creating, managing, analyzing, and monitoring agreements. It streamlines the agreement lifecycle, enabling users to draft valid agreements, track changes, check conflicts, and gain actionable insights from their agreements using AI. Designed with efficiency and clarity in mind, Agreed helps individuals and businesses escape the "Agreement Trap" and unlock the full potential of their agreement data.

---

## Features

### 1. Create Agreements on the Fly

- Quickly draft legally valid agreements with ease.

### 2. Import Existing Agreements

- Centralize all your agreements by importing existing ones into the platform.

### 3. Track Expirations and Notifications

- Get automatic reminders about agreement expiration dates or required renewals.

### 4. Conflict Checker

- Analyze new agreements against existing ones to detect potential conflicts.
- Ensure no prior commitments are violated.

### 5. Query Agreements

- Use AI to ask questions about lengthy agreements and get simple, concise answers.

### 6. Summarize Agreements

- Generate bullet-point summaries to highlight key terms and nuances in agreements.

### 7. Monitor Changes

- Track changes made to agreements by other parties.
- Receive notifications and approve or disapprove changes in real-time.

### 8. Agreement Management Dashboard

- Access a centralized hub for managing, signing, and analyzing agreements efficiently.

---

## How It Works

### Technology Stack

- **Frontend**: Flutter for a seamless, cross-platform user experience.
- **Backend**: Flask API for robust processing and integration.
- **Database**: Snowflake for secure storage and efficient querying of agreement data.
- **AI Integration**: Snowflake Cortex for:
  - Summarizing agreements.
  - Detecting conflicts using LLMs.
  - Context-based querying for quick insights.

### Core Workflows

1. **Drafting and Importing Agreements**:

   - Create agreements or import Word/PDF files.
   - Chunk agreements by paragraphs and pages for efficient processing.
2. **Conflict Detection**:

   - Use AI to compare new agreements with existing ones.
   - Flag conflicting clauses and provide detailed insights.
3. **Query and Summarization**:

   - Leverage AI to answer questions about agreements.
   - Generate easy-to-read summaries.
4. **Monitoring**:

   - Track changes in agreements across all parties.
   - Approve or reject updates as needed.

---

## Installation and Setup

### Prerequisites

- Python 3.8+
- Snowflake Account
- Flutter SDK

### Backend Setup

1. Clone this repository:

   ```bash
   git clone https://github.com/yourusername/agreed.git
   cd agreed/backend
   ```
2. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```
3. Set up environment variables for Snowflake configuration:

   ```bash
   export SNOWFLAKE_USER="your_username"
   export SNOWFLAKE_PASSWORD="your_password"
   export SNOWFLAKE_ACCOUNT="your_account"
   export SNOWFLAKE_DATABASE="your_database"
   export SNOWFLAKE_SCHEMA="your_schema"
   ```
4. Run the Flask server:

   ```bash
   python app.py
   ```

### Frontend Setup

1. Navigate to the Flutter project:

   ```bash
   cd ../frontend
   ```
2. Install dependencies:

   ```bash
   flutter pub get
   ```
3. Run the Flutter app:

   ```bash
   flutter run
   ```

---

## Usage

### Backend Endpoints

- **`/api/save-document`**: Save and process agreements (Word/PDF).
- **`/api/context-retrieval`**: Query agreements for context and insights.
- **`/api/conflict-checker`**: Analyze new agreements for conflicts with existing ones.

### Frontend Features

- Intuitive dashboard to manage agreements.
- Real-time notifications for changes and expirations.
- AI-powered insights and queries.

---

## Demo Video

[Watch the 5-minute demo here](https://youtu.be/2SMHwo_i9LI)

---

## Contribution

We welcome contributions to improve Agreed! Feel free to fork this repository and submit a pull request.

---

## License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT).

---

## Team

- **Victor**: AI Integration
- **Stephen**: Backend Developer
- **Kausar**: Flutter Developer

---

## Acknowledgements

- **Docusign API**: For enabling seamless agreement management.
- **Snowflake**: For powering the backend with efficient AI and data processing capabilities.
- **Flutter**: For creating a beautiful, cross-platform user interface.

---

## Contact

For questions or support, reach out to us.

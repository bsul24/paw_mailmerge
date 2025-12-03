# PAW MailMerge

PAW MailMerge is a privacy-sensitive, email-provider-agnostic, web-based mail merge solution.  
It allows users to upload a CSV file, create reusable email templates with placeholder fields, preview outputs, and generate fully merged emails as TXT files, PDFs, or new browser tabs.

Live Demo: **https://pawmailmerge.netlify.app/**

## 🚀 Features

### **CSV Upload & Parsing**

- Uploads CSV files using the native file input and an accessible custom label control
- Parses CSV content using **PapaParse**
- Automatically extracts headers and recipient entries
- Requires an `email` column for generating merged messages

### **Email Template System**

- Create and manage multiple templates
- Editable template names
- Templates stored in `localStorage` for persistence
- Supports placeholders using curly brackets, e.g., `{name}`, `{deadline}`, `{project}`

### **Dynamic Email Preview**

- Real-time preview updates as you edit templates
- Automatically replaces placeholders with the selected recipient's data

### **Recipient Selection**

- Displays all recipients extracted from the CSV
- Keyboard- and screen-reader-friendly
- Updating the selected recipient instantly updates the preview

### **Email Generation Options**

Users can generate final emails in three formats:

- **View in new browser tabs**
- **Download as TXT**
- **Download as PDF**
  - Uses **jsPDF** under the hood

## 🧠 How PAW MailMerge Works

### 1. Upload CSV

A CSV is parsed using PapaParse, converting each row into a recipient object with key/value pairs matching column headers.

### 2. Template Editing

Templates contain user-defined placeholders in curly brackets (e.g., `{name}`).  
PAW MailMerge displays all available CSV headers to guide the user.

### 3. Placeholder Replacement

When generating or previewing emails, each `{header}` placeholder is replaced with the corresponding value from the selected recipient.

### 4. Output

Users choose to:

- Open emails in new tabs
- Download a combined TXT file
- Download a PDF with one page per recipient

## 📁 Project Structure

```
frontend/
│
├── src/
│   ├── components/
│   │   ├── FileUpload.jsx
│   │   ├── TemplatesList.jsx
│   │   ├── TemplateEditor.jsx
│   │   ├── EmailPreview.jsx
│   │   ├── RecipientsList.jsx
│   │   ├── GenerationButtons.jsx
│   │   ├── InstructionsPage.jsx
│   │   ├── Header.jsx
│   │   └── Footer.jsx
│   │
│   ├── App.jsx
│   ├── index.jsx
│   └── App.css
│
├── package.json
└── public/
```

## 🛠️ Tech Stack

**Frontend**

- React (CRA)
- React Router
- PapaParse (CSV parsing)
- jsPDF (PDF generation)
- LocalStorage for templates

**Deployment**

- Built and deployed via **Netlify**

## 🧪 Testing the App

Use this sample CSV:

```csv
email,name,project,role,deadline,custom_note
alex@example.com,Alex Johnson,Airport Navigation Assistant,Product Manager,2025-01-15,"Excited but concerned about accessibility during tight layovers."
jamie@example.com,Jamie Rivera,Airport Navigation Assistant,UX Researcher,2025-01-20,"Interested in helping test with screen readers and voice control."
morgan@example.com,Morgan Lee,Airport Navigation Assistant,Software Engineer,2025-01-25,"Has experience with real-time guidance systems and mapping APIs."
```

## 🧩 Usage Guide

1. **Upload CSV** — Must include a column named `email`.
2. **Select or Add a Template** — Create multiple templates with customizable names.
3. **Edit Template** — Use curly-brace placeholders matching CSV header names.
4. **Preview Email** — Updates automatically based on selected recipient.
5. **Generate Output** — View in tabs, download TXT, or download PDF.

## 🏗️ Running Locally

### Install dependencies

```bash
cd frontend
npm install
```

### Run development server

```bash
npm start
```

App runs at: **http://localhost:3000**

## 🌐 Deployment (Netlify)

Deployed at: **https://pawmailmerge.netlify.app/**

Netlify:

- **Base directory**: `frontend`
- **Build command**: `npm run build`
- **Publish directory**: `build`

## ⚠️ Known Limitations

- Requires CSVs with consistent headers
- Does not send emails—only generates content
- jsPDF output is plain text
- Templates must match CSV headers exactly

## 📌 License

Licensed under the **Apache-2.0 License**.

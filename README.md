![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=for-the-badge&logo=fastapi)
![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB)
![TypeScript](https://img.shields.io/badge/typescript-%23007ACC.svg?style=for-the-badge&logo=typescript&logoColor=white)
![Vite](https://img.shields.io/badge/vite-%23646CFF.svg?style=for-the-badge&logo=vite&logoColor=white)
![Jest](https://img.shields.io/badge/Jest-323330?style=for-the-badge&logo=Jest&logoColor=white)
![HTML5](https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/css3-%231572B6.svg?style=for-the-badge&logo=css3&logoColor=white)

# Loan Simulator

An educational Proof-of-Concept (PoC) / Minimum Viable Product (MVP) that demonstrates how loan payments are calculated and distributed between principal and interest over the loan term using simple interest calculations.

## Project Overview

The Loan Simulator is a web application designed to help users understand loan payment structures through visual representation of how monthly payments break down over time. The application features a clean three-level responsive design (Desktop/Tablet/Mobile) with an API-first architecture and test-driven development approach.

### Key Features

- Simple interest loan calculation engine
- Monthly payment calculation and amortization schedule generation
- REST API for loan calculations
- Web-based user interface with input form and results display
- Three-level responsive design with side-panel layout (Desktop/Tablet)
- Basic validation and error handling
- Comprehensive unit testing for both backend and frontend

### Responsive Design

- **Desktop** (≥1024px): Side-panel layout with LoanForm on the left, results on the right
- **Tablet** (≥768px): Compact side-panel layout
- **Mobile** (<768px): Single-column stacked layout

## Prerequisites

- [Python](https://www.python.org/downloads/) (version 3.8 or higher)
- [Node.js](https://nodejs.org/en/download/) (version 16 or higher)
- [npm](https://www.npmjs.com/get-npm) (usually installed with Node.js)

## Project Structure

```
├── backend/                    # FastAPI backend
│   ├── main.py                 # Application entry point
│   ├── routes/
│   │   └── loan_routes.py      # API endpoints
│   ├── services/
│   │   └── loan_calculator.py  # Core calculation logic
│   ├── models/
│   │   └── loan_models.py      # Request/response models
│   ├── tests/
│   │   ├── test_loan_calculator.py
│   │   └── test_loan_routes.py
│   └── requirements.txt        # Python dependencies
├── frontend/                   # React + Vite frontend
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   │   ├── LoanForm.tsx        # Input form component
│   │   │   ├── PaymentDisplay.tsx   # Monthly payment display
│   │   │   └── InstallmentTable.tsx # Amortization table component
│   │   ├── services/
│   │   │   └── api.ts              # API communication layer
│   │   ├── tests/
│   │   │   ├── LoanForm.test.tsx
│   │   │   ├── PaymentDisplay.test.tsx
│   │   │   └── InstallmentTable.test.tsx
│   │   ├── App.tsx              # Main application component
│   │   └── main.tsx             # Application entry point
│   ├── package.json            # Node dependencies and scripts
│   └── vite.config.ts          # Vite configuration
├── .specify/                   # Project specification and constitution
├── preparation/
│   ├── constitution.md         # Project constitution
│   └── technical.md            # Technical specifications
└── README.md                   # This file
```

## Backend Setup

1. Navigate to the backend directory:
```bash
cd backend
```

2. Create a virtual environment (recommended):
```bash
python -m venv venv
```

3. Activate the virtual environment:
- Windows: `venv\Scripts\activate`
- macOS/Linux: `source venv/bin/activate`

4. Install dependencies:
```bash
pip install -r requirements.txt
```

5. Run the backend server:
```bash
python main.py
```

The API will be available at `http://localhost:8000`

## Frontend Setup

1. Navigate to the frontend directory:
```bash
cd frontend
```

2. Install dependencies:
```bash
npm install
```

3. Run the development server:
```bash
npm run dev
```

The application will be available at `http://localhost:5173`

## Running Tests

### Backend Tests

In the backend directory, run:
```bash
pytest
```

### Frontend Tests

In the frontend directory, run:
```bash
npm test
```

## API Usage

### Calculate Loan

**Endpoint**: `POST /api/calculate-loan`  
**Content-Type**: `application/json`

#### Request
```json
{
  "amount": 10000,
  "term": 12,
  "rate": 5
}
```

#### Response
```json
{
  "monthlyPayment": 875.00,
  "totalPayment": 10500.00,
  "totalInterest": 500.00,
  "installments": [
    {
      "paymentNumber": 1,
      "paymentAmount": 875.00,
      "principal": 833.33,
      "interest": 41.67,
      "remainingBalance": 9166.67
    },
    // ... more installments
  ]
}
```

#### Error Response
```json
{
  "detail": "Validation error message"
}
```

## Development Workflow

This project follows a Spec-Driven Development (SDD) approach with Test-Driven Development (TDD). The development flow is:

1. **API-First Development**: Define API contract first, then implement
2. **TDD Cycle**: Write failing test → Make it pass → Refactor
3. **Git Conventions**: Use conventional commit messages (feat:, fix:, test:, docs:, refactor:)

## Simple Interest Formula

The application uses simple interest calculations:

```
Total Interest = Principal × Rate × Time
where:
  Principal = Loan amount
  Rate = Annual interest rate (as decimal)
  Time = Loan term in years

Total Amount = Principal + Total Interest
Monthly Payment = Total Amount / Number of Months
```

## Project Constitution

This project follows a constitution that defines all development standards, architectural decisions, and quality requirements. The constitution can be found in `.specify/memory/constitution.md`.

## Limitations

- Simple interest only (no compound interest)
- Monthly payments only with fixed frequency
- No database or data persistence
- Development mode only (not production-ready)
- No authentication or user accounts
- No history saving or comparison features

## License

This project is for educational purposes only.

## Contributing

This is a learning project designed to demonstrate loan calculations and modern web development practices with Spec-Driven Development with Speckit
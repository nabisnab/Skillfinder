# Skillfinder - AI-Powered Resume Analyzer

An intelligent resume analysis platform that leverages artificial intelligence and natural language processing to evaluate, score, and provide actionable feedback on resumes. Skillfinder helps job seekers optimize their resumes and assists recruiters in identifying top candidates more efficiently.

![Skillfinder](https://img.shields.io/badge/status-active-brightgreen) ![License](https://img.shields.io/badge/license-MIT-blue) ![Python](https://img.shields.io/badge/python-3.8%2B-blue) ![Node.js](https://img.shields.io/badge/node.js-14%2B-green)

## Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Installation](#installation)
  - [Backend Setup](#backend-setup)
  - [Frontend Setup](#frontend-setup)
- [API Endpoints](#api-endpoints)
- [NLP Features](#nlp-features)
- [Scoring Methodology](#scoring-methodology)
- [Configuration](#configuration)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

## Features

### Core Capabilities
- **Resume Parsing**: Automatically extracts and structures information from resumes (PDF, DOCX, TXT)
- **AI-Powered Analysis**: Utilizes advanced NLP models to understand resume content and context
- **Intelligent Scoring**: Multi-dimensional resume scoring based on skill relevance, experience, and format quality
- **Real-time Feedback**: Provides instant, actionable recommendations for resume improvement
- **Skill Extraction**: Identifies and categorizes technical and soft skills with proficiency levels
- **Job Matching**: Matches resume content against job descriptions for compatibility analysis
- **Duplicate Detection**: Identifies similar or duplicate resumes in bulk uploads

### Advanced Features
- **Customizable Scoring Weights**: Adjust scoring parameters based on industry or job role
- **Batch Processing**: Analyze multiple resumes in a single request
- **Export Reports**: Generate detailed analysis reports in PDF or JSON format
- **Resume Comparison**: Compare multiple resumes side-by-side
- **API Rate Limiting**: Built-in rate limiting for API protection
- **Authentication & Authorization**: Secure endpoints with JWT-based authentication

## Tech Stack

### Backend
- **Runtime**: Python 3.8+
- **Framework**: Flask/FastAPI
- **NLP Libraries**:
  - spaCy (Named Entity Recognition, POS tagging)
  - NLTK (Natural Language Toolkit)
  - Transformers (Hugging Face BERT models)
  - scikit-learn (Machine learning algorithms)
- **Database**: PostgreSQL / MongoDB
- **File Processing**: PyPDF2, python-docx, pptx
- **API**: RESTful API with OpenAPI/Swagger documentation
- **Authentication**: PyJWT
- **Deployment**: Docker, Docker Compose

### Frontend
- **Framework**: React 18+ / Vue 3 / Angular
- **State Management**: Redux / Vuex / NgRx
- **UI Framework**: Material-UI / Tailwind CSS / Bootstrap
- **File Upload**: React Dropzone / similar
- **HTTP Client**: Axios / Fetch API
- **Build Tool**: Webpack / Vite
- **Testing**: Jest, React Testing Library

### DevOps & Tools
- **Containerization**: Docker, Docker Compose
- **Version Control**: Git
- **CI/CD**: GitHub Actions / GitLab CI
- **Monitoring**: Prometheus, Grafana (optional)
- **Logging**: ELK Stack / CloudWatch

## Project Structure

```
Skillfinder/
├── backend/
│   ├── app/
│   │   ├── __init__.py
│   │   ├── main.py                 # Application entry point
│   │   ├── config.py               # Configuration management
│   │   ├── requirements.txt        # Python dependencies
│   │   ├── routes/
│   │   │   ├── __init__.py
│   │   │   ├── resume.py           # Resume upload & retrieval endpoints
│   │   │   ├── analysis.py         # Analysis endpoints
│   │   │   ├── jobs.py             # Job matching endpoints
│   │   │   └── auth.py             # Authentication endpoints
│   │   ├── models/
│   │   │   ├── __init__.py
│   │   │   ├── resume.py           # Resume data model
│   │   │   ├── analysis.py         # Analysis results model
│   │   │   └── user.py             # User model
│   │   ├── services/
│   │   │   ├── __init__.py
│   │   │   ├── resume_parser.py    # Resume parsing logic
│   │   │   ├── nlp_analyzer.py     # NLP analysis engine
│   │   │   ├── scorer.py           # Scoring engine
│   │   │   └── job_matcher.py      # Job matching logic
│   │   ├── utils/
│   │   │   ├── __init__.py
│   │   │   ├── file_handler.py     # File upload/download handling
│   │   │   ├── validators.py       # Input validation
│   │   │   └── helpers.py          # Utility functions
│   │   ├── middleware/
│   │   │   ├── __init__.py
│   │   │   ├── auth.py             # Authentication middleware
│   │   │   └── error_handler.py    # Error handling middleware
│   │   └── database/
│   │       ├── __init__.py
│   │       ├── db.py               # Database connection
│   │       └── migrations/         # Database migrations
│   ├── tests/
│   │   ├── __init__.py
│   │   ├── test_resume_parser.py
│   │   ├── test_nlp_analyzer.py
│   │   ├── test_scorer.py
│   │   └── test_routes.py
│   ├── Dockerfile
│   └── .env.example
│
├── frontend/
│   ├── public/
│   │   ├── index.html
│   │   └── favicon.ico
│   ├── src/
│   │   ├── components/
│   │   │   ├── ResumeUpload.jsx
│   │   │   ├── AnalysisResult.jsx
│   │   │   ├── JobMatcher.jsx
│   │   │   ├── Dashboard.jsx
│   │   │   └── Navigation.jsx
│   │   ├── pages/
│   │   │   ├── Home.jsx
│   │   │   ├── Analyze.jsx
│   │   │   ├── Results.jsx
│   │   │   └── About.jsx
│   │   ├── services/
│   │   │   ├── api.js             # API client
│   │   │   └── authService.js     # Authentication service
│   │   ├── store/
│   │   │   ├── actions.js
│   │   │   ├── mutations.js
│   │   │   └── state.js
│   │   ├── styles/
│   │   │   ├── main.css
│   │   │   └── variables.css
│   │   ├── App.jsx
│   │   └── index.js
│   ├── public/
│   ├── package.json
│   ├── package-lock.json
│   ├── .env.example
│   ├── Dockerfile
│   └── nginx.conf
│
├── docker-compose.yml
├── .gitignore
├── LICENSE
└── README.md
```

## Installation

### Prerequisites

- Python 3.8+ (Backend)
- Node.js 14+ and npm 6+ (Frontend)
- Docker & Docker Compose (Optional, for containerized setup)
- PostgreSQL 12+ or MongoDB 4.0+ (Database)

### Backend Setup

#### 1. Clone the Repository

```bash
git clone https://github.com/nabisnab/Skillfinder.git
cd Skillfinder/backend
```

#### 2. Create Virtual Environment

```bash
python -m venv venv

# On Windows
venv\Scripts\activate

# On macOS/Linux
source venv/bin/activate
```

#### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

#### 4. Download NLP Models

```bash
python -m spacy download en_core_web_sm
python -m nltk.downloader punkt averaged_perceptron_tagger wordnet
```

#### 5. Configure Environment Variables

```bash
cp .env.example .env
# Edit .env with your configuration
```

**Example .env file:**
```
FLASK_ENV=development
FLASK_DEBUG=True
DATABASE_URL=postgresql://user:password@localhost:5432/skillfinder
SECRET_KEY=your-secret-key-here
JWT_SECRET=your-jwt-secret
ALLOWED_ORIGINS=http://localhost:3000,http://localhost:8080
MAX_FILE_SIZE=5242880  # 5MB in bytes
UPLOAD_FOLDER=uploads/
```

#### 6. Initialize Database

```bash
flask db upgrade  # Or your migration command
```

#### 7. Run Backend Server

```bash
python app/main.py
# or
flask run
```

Backend will be available at `http://localhost:5000`

### Frontend Setup

#### 1. Navigate to Frontend Directory

```bash
cd Skillfinder/frontend
```

#### 2. Install Dependencies

```bash
npm install
```

#### 3. Configure Environment Variables

```bash
cp .env.example .env
# Edit .env with your API endpoint
```

**Example .env file:**
```
REACT_APP_API_URL=http://localhost:5000/api
REACT_APP_ENV=development
```

#### 4. Start Development Server

```bash
npm start
```

Frontend will be available at `http://localhost:3000`

#### 5. Build for Production

```bash
npm run build
```

### Docker Deployment

#### Using Docker Compose

```bash
# From root directory
docker-compose up -d

# View logs
docker-compose logs -f

# Stop services
docker-compose down
```

**docker-compose.yml** includes:
- PostgreSQL database
- Backend service
- Frontend service
- Redis cache (optional)

## API Endpoints

### Authentication

```
POST /api/auth/register
- Register a new user
- Body: { email, password, name }
- Response: { token, user_id }

POST /api/auth/login
- Login user
- Body: { email, password }
- Response: { token, user_id, expires_in }

POST /api/auth/refresh
- Refresh authentication token
- Headers: { Authorization: Bearer token }
- Response: { token }

POST /api/auth/logout
- Logout user
- Headers: { Authorization: Bearer token }
```

### Resume Management

```
POST /api/resumes/upload
- Upload and parse a resume
- Headers: { Authorization: Bearer token }
- Body: FormData with file
- Response: { resume_id, extracted_data, upload_time }

GET /api/resumes/{resume_id}
- Retrieve resume details
- Headers: { Authorization: Bearer token }
- Response: { resume_id, name, email, phone, education, experience, skills }

GET /api/resumes
- List all user resumes
- Headers: { Authorization: Bearer token }
- Query: ?page=1&limit=10&sort=created_at
- Response: { resumes: [], total, page, limit }

DELETE /api/resumes/{resume_id}
- Delete a resume
- Headers: { Authorization: Bearer token }
- Response: { message: "Resume deleted successfully" }

PUT /api/resumes/{resume_id}
- Update resume metadata
- Headers: { Authorization: Bearer token }
- Body: { name, tags }
- Response: { resume_id, updated_resume }
```

### Analysis

```
POST /api/analysis/analyze
- Analyze a resume
- Headers: { Authorization: Bearer token }
- Body: { resume_id, job_description (optional) }
- Response: { 
    analysis_id, 
    overall_score, 
    dimensions: { 
      skills_match, 
      experience_relevance, 
      format_quality 
    },
    recommendations: [],
    skills_extracted: [],
    analysis_timestamp
  }

GET /api/analysis/{analysis_id}
- Retrieve analysis results
- Headers: { Authorization: Bearer token }
- Response: { analysis details }

GET /api/analysis
- List all analyses for user
- Headers: { Authorization: Bearer token }
- Query: ?resume_id=xxx&limit=10
- Response: { analyses: [] }
```

### Job Matching

```
POST /api/jobs/match
- Match resume against job description
- Headers: { Authorization: Bearer token }
- Body: { resume_id, job_description }
- Response: {
    match_score,
    skill_gaps: [],
    matched_skills: [],
    recommendations: [],
    experience_alignment: {}
  }

POST /api/jobs/batch-match
- Match resume against multiple job descriptions
- Headers: { Authorization: Bearer token }
- Body: { resume_id, job_descriptions: [] }
- Response: { matches: [ { job_id, score, skills_gaps } ] }
```

### Reports

```
GET /api/reports/{analysis_id}/pdf
- Download analysis report as PDF
- Headers: { Authorization: Bearer token }
- Response: PDF file

GET /api/reports/{analysis_id}/json
- Get analysis report as JSON
- Headers: { Authorization: Bearer token }
- Response: { full analysis report }
```

### Health & System

```
GET /api/health
- Health check endpoint
- Response: { status: "healthy", timestamp }

GET /api/version
- Get API version
- Response: { version: "1.0.0" }
```

## NLP Features

### 1. **Named Entity Recognition (NER)**
Identifies and extracts:
- Person names
- Organizations/Companies
- Locations
- Educational institutions
- Dates and duration periods

```python
# Example: extracting entities from resume text
from services.nlp_analyzer import extract_entities
entities = extract_entities(resume_text)
# Output: { PERSON: [], ORG: [], GPE: [], INSTITUTION: [], DATE: [] }
```

### 2. **Skill Extraction**
- Recognizes technical skills (programming languages, frameworks, tools)
- Identifies soft skills (leadership, communication, teamwork)
- Extracts skill proficiency levels
- Matches against comprehensive skill taxonomy

### 3. **Experience Analysis**
- Extracts job titles and descriptions
- Identifies keywords indicating seniority level
- Analyzes years of experience
- Detects industry experience patterns

### 4. **Education Processing**
- Extracts degree types and fields of study
- Identifies educational institutions
- Recognizes certifications and courses
- Evaluates education relevance

### 5. **Text Similarity & Matching**
- Calculates semantic similarity between resume and job description
- Uses TF-IDF and cosine similarity
- Applies word embeddings (Word2Vec, GloVe)
- Identifies skill gaps

### 6. **Language Quality Analysis**
- Grammar and spelling checks
- Readability scoring (Flesch-Kincaid)
- Keyword density analysis
- Format and structure evaluation

## Scoring Methodology

The AI-powered scoring system evaluates resumes across multiple dimensions:

### Overall Score: 0-100

#### 1. **Skills Match (Weight: 30%)**
- Alignment of resume skills with industry standards
- Technical skills relevance (70%)
- Soft skills relevance (30%)
- Skill proficiency levels
- Rarity/demand of skills

```
Skills Score = (Matched Skills / Total Required Skills) × 100
```

#### 2. **Experience Relevance (Weight: 35%)**
- Years of relevant experience
- Industry experience alignment
- Job title progression/seniority
- Employment gaps assessment
- Consistency with skill set

```
Experience Score = (Relevant Years / Expected Years) × Experience Weight
```

#### 3. **Format & Structure Quality (Weight: 20%)**
- Document parsing success rate
- Proper formatting and organization
- Readability metrics
- Completeness of sections
- Grammar and spelling

```
Quality Score = (Perfect Metrics / Total Metrics) × 100
```

#### 4. **Education Credentials (Weight: 15%)**
- Degree level and field relevance
- Educational institution tier
- Relevant certifications
- Continuous learning indicators

```
Education Score = (Relevant Credentials / Total Credentials) × 100
```

### Job Match Scoring (0-100)

```
Job Match Score = (Matched Skills / Required Skills) × 0.5 +
                  (Experience Alignment / Max Years) × 0.3 +
                  (Education Relevance) × 0.2
```

### Recommendation Generation

The system generates recommendations based on:
- **Critical Gaps**: Skills or experience missing for target role
- **Enhancement Opportunities**: Skills to add for better matching
- **Format Improvements**: Structure and presentation suggestions
- **Certifications**: Industry-relevant certifications to pursue

## Configuration

### Backend Configuration (config.py)

```python
class Config:
    """Base configuration"""
    DEBUG = False
    TESTING = False
    MAX_CONTENT_LENGTH = 5 * 1024 * 1024  # 5MB
    UPLOAD_FOLDER = 'uploads'
    ALLOWED_EXTENSIONS = {'pdf', 'docx', 'txt'}
    
class DevelopmentConfig(Config):
    """Development configuration"""
    DEBUG = True
    SQLALCHEMY_ECHO = True

class ProductionConfig(Config):
    """Production configuration"""
    DEBUG = False
    SQLALCHEMY_TRACK_MODIFICATIONS = False
```

### Frontend Configuration (.env)

```
REACT_APP_API_URL=http://localhost:5000/api
REACT_APP_ENV=development
REACT_APP_MAX_FILE_SIZE=5242880
REACT_APP_TIMEOUT=30000
```

## Usage

### 1. Upload a Resume

**Frontend:**
```javascript
const uploadResume = async (file) => {
  const formData = new FormData();
  formData.append('file', file);
  
  const response = await api.post('/resumes/upload', formData, {
    headers: { 'Content-Type': 'multipart/form-data' }
  });
  return response.data;
};
```

**Backend Response:**
```json
{
  "resume_id": "res_123456",
  "extracted_data": {
    "name": "John Doe",
    "email": "john@example.com",
    "phone": "+1-555-0123",
    "education": [...],
    "experience": [...],
    "skills": [...]
  },
  "upload_time": "2025-12-17T10:31:23Z"
}
```

### 2. Analyze Resume

**Request:**
```javascript
const analyzeResume = async (resumeId, jobDescription = null) => {
  const response = await api.post('/analysis/analyze', {
    resume_id: resumeId,
    job_description: jobDescription
  });
  return response.data;
};
```

**Response:**
```json
{
  "analysis_id": "ana_789012",
  "overall_score": 78,
  "dimensions": {
    "skills_match": 85,
    "experience_relevance": 72,
    "format_quality": 75,
    "education_credentials": 80
  },
  "recommendations": [
    {
      "category": "critical",
      "title": "Add AWS Certification",
      "description": "AWS is required for the target role"
    }
  ],
  "skills_extracted": [
    {
      "skill": "Python",
      "category": "technical",
      "proficiency": "advanced"
    }
  ]
}
```

### 3. Match Against Job Description

**Request:**
```javascript
const matchJob = async (resumeId, jobDescription) => {
  const response = await api.post('/jobs/match', {
    resume_id: resumeId,
    job_description: jobDescription
  });
  return response.data;
};
```

### 4. Generate Report

```javascript
const downloadReport = async (analysisId) => {
  const response = await api.get(`/reports/${analysisId}/pdf`, {
    responseType: 'blob'
  });
  // Download PDF
  const url = window.URL.createObjectURL(new Blob([response.data]));
  const link = document.createElement('a');
  link.href = url;
  link.setAttribute('download', `report-${analysisId}.pdf`);
  document.body.appendChild(link);
  link.click();
};
```

## Testing

### Backend Tests

```bash
# Run all tests
pytest

# Run with coverage
pytest --cov=app tests/

# Run specific test file
pytest tests/test_nlp_analyzer.py -v

# Run with specific markers
pytest -m "unit" -v
```

### Frontend Tests

```bash
# Run all tests
npm test

# Run with coverage
npm test -- --coverage

# Run in watch mode
npm test -- --watch

# Run specific test file
npm test -- ResumeUpload.test.jsx
```

## Contributing

We welcome contributions! Please follow these guidelines:

### 1. Fork the Repository

```bash
git clone https://github.com/nabisnab/Skillfinder.git
cd Skillfinder
```

### 2. Create a Feature Branch

```bash
git checkout -b feature/your-feature-name
# or for bug fixes
git checkout -b bugfix/issue-description
```

### 3. Make Your Changes

- Follow the existing code style and conventions
- Write clear, descriptive commit messages
- Add tests for new functionality
- Update documentation as needed

### 4. Commit Your Changes

```bash
git add .
git commit -m "feat: add new feature" 
# or
git commit -m "fix: resolve issue with X"
```

**Commit Message Format:**
- `feat:` A new feature
- `fix:` A bug fix
- `docs:` Documentation only changes
- `style:` Changes that don't affect code meaning
- `refactor:` Code change that neither fixes a bug nor adds a feature
- `perf:` Code change that improves performance
- `test:` Adding or updating tests

### 5. Push to Your Branch

```bash
git push origin feature/your-feature-name
```

### 6. Create a Pull Request

- Provide a clear description of your changes
- Reference any related issues using #issue_number
- Ensure all tests pass
- Request review from maintainers

### Code Style Guidelines

- **Python**: Follow PEP 8 (use `black` and `flake8`)
- **JavaScript/React**: Follow Airbnb JavaScript Style Guide
- **Naming**: Use descriptive, meaningful names
- **Comments**: Add comments for complex logic
- **Functions**: Keep functions small and focused

### Running Linters

```bash
# Backend
black app/
flake8 app/
pylint app/

# Frontend
npm run lint
npm run format
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Support & Contact

- **Issues**: Report bugs or feature requests on [GitHub Issues](https://github.com/nabisnab/Skillfinder/issues)
- **Email**: contact@skillfinder.dev
- **Documentation**: [Full Documentation](https://docs.skillfinder.dev)

## Acknowledgments

- spaCy for NLP capabilities
- Hugging Face for transformer models
- The open-source community for invaluable tools and libraries

---

**Last Updated**: 2025-12-17

**Version**: 1.0.0

**Status**: Active Development

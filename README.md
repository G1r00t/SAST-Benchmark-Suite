# SAST Benchmark Suite 🔍

A comprehensive vulnerable codebase designed to test and benchmark Static Application Security Testing (SAST) tools. This repository contains intentionally vulnerable code in Python and JavaScript to evaluate how well security scanners detect real-world vulnerabilities, handle dead code analysis, and minimize false positives.

## 📊 Repository Statistics

- **Total Files**: 81 files
- **Languages**: Python & JavaScript
- **Total Vulnerabilities**: 755+ findings
- **Dead Code Vulnerabilities**: 310 (41%)
- **Live Code Vulnerabilities**: 445 (59%)
- **Lines of Code**: ~10,000+ LOC

## 🎯 Purpose

This repository serves as a standardized benchmark for evaluating SAST tools across multiple dimensions:

- **Vulnerability Detection Accuracy**: Test detection of common security flaws
- **Dead Code Analysis**: Evaluate ability to distinguish between reachable and unreachable vulnerabilities
- **False Positive Rates**: Measure precision with clean code examples
- **Multi-language Support**: Test capabilities across Python and JavaScript
- **Severity Classification**: Assess accuracy of risk scoring

## 🏗️ Repository Structure

```
sast-benchmark-suite/
├── backend/                    # Python Backend (Flask/FastAPI)
│   ├── controllers/           # API endpoints with various vulnerabilities
│   ├── models/               # Database models (clean + vulnerable)
│   ├── services/             # Business logic with security flaws
│   ├── utils/                # Utility functions (mixed security)
│   ├── middleware/           # Authentication & security middleware
│   └── tests/                # Test files with embedded secrets
│
├── frontend/                  # JavaScript Frontend (React/Vue)
│   ├── src/components/       # UI components with XSS vulnerabilities
│   ├── src/services/         # API services with client-side flaws
│   ├── src/utils/            # Helper functions with security issues
│   ├── src/pages/            # Page components with various vulns
│   └── tests/                # Frontend tests with hardcoded data
│
├── scripts/                   # Build/deployment scripts
├── config/                    # Configuration files with secrets
├── docs/                      # Documentation (some with vuln examples)
└── shared/                    # Shared utilities and schemas
```

## 🚨 Vulnerability Categories

### Python Vulnerabilities
- **SQL Injection**: Raw query construction, ORM misuse
- **Command Injection**: Unsafe subprocess calls
- **Path Traversal**: Unvalidated file operations
- **Insecure Deserialization**: pickle, yaml.load vulnerabilities
- **Authentication Bypass**: Logic flaws in auth mechanisms
- **Hardcoded Secrets**: API keys, passwords in source code
- **XXE**: XML parsing vulnerabilities
- **SSRF**: Server-side request forgery
- **Weak Cryptography**: MD5 usage, weak random generation

### JavaScript Vulnerabilities
- **Cross-Site Scripting (XSS)**: DOM-based, reflected, stored
- **Prototype Pollution**: Object merge vulnerabilities
- **Client-side Authentication Bypass**: Frontend-only security
- **Insecure Data Storage**: Sensitive data in localStorage
- **CSRF**: Missing token validation
- **Hardcoded API Keys**: Secrets in frontend code
- **Unsafe Regular Expressions**: ReDoS vulnerabilities
- **DOM Manipulation**: Unsafe innerHTML usage

## 💀 Dead Code Strategy

This repository implements a sophisticated dead code strategy to test SAST tools' ability to distinguish between exploitable and non-exploitable vulnerabilities:

### Dead Code Distribution
- **41% of vulnerabilities** are in dead/unreachable code
- **59% of vulnerabilities** are in live/reachable code paths

### Dead Code Scenarios
1. **Unreachable Functions**: Functions that are never called
2. **Impossible Conditions**: Code behind `if (false)` or similar
3. **Commented Code**: Vulnerable code left in comments
4. **Unused Imports**: Vulnerable libraries that aren't utilized
5. **Legacy Code**: Old functions/modules no longer in use
6. **Development Artifacts**: Debug code accidentally left in production

## 🧪 Testing Your SAST Tool

### Expected Results
A well-configured SAST tool should detect:
- **Total Findings**: 700-800 potential vulnerabilities
- **True Positives**: 400-500 exploitable vulnerabilities
- **Dead Code**: 300-350 vulnerabilities in unreachable code
- **Clean Files**: Zero findings in 15-20 intentionally clean files

### Severity Distribution
- **Critical**: 15-20% (Remote code execution, auth bypass)
- **High**: 25-30% (SQL injection, privilege escalation)
- **Medium**: 35-40% (XSS, path traversal, weak crypto)
- **Low**: 15-20% (Information disclosure, weak validation)

### Key Evaluation Metrics
1. **Detection Rate**: Percentage of actual vulnerabilities found
2. **Precision**: Ratio of true positives to total findings
3. **Dead Code Handling**: Ability to flag unreachable vulnerabilities
4. **False Positive Rate**: Incorrect findings in clean code
5. **Severity Accuracy**: Correct risk classification

## 🚀 Getting Started

### Prerequisites
- Python 3.8+
- Node.js 14+
- Docker (optional)

### Quick Setup
```bash
# Clone the repository
git clone https://github.com/yourusername/sast-benchmark-suite.git
cd sast-benchmark-suite

# Install Python dependencies
pip install -r requirements.txt

# Install JavaScript dependencies
npm install

# Run with Docker (optional)
docker-compose up -d
```

### Running SAST Analysis
```bash
# Example with popular SAST tools
semgrep --config=auto .
bandit -r backend/
eslint frontend/src/
sonarqube-scanner
```

## 📈 Benchmarking Results

Track your SAST tool's performance:

| Metric | Target Range | Your Tool |
|--------|-------------|-----------|
| Total Findings | 700-800 | ___ |
| True Positives | 400-500 | ___ |
| Dead Code Detected | 300-350 | ___ |
| False Positives | < 50 | ___ |
| Critical Severity | 100-150 | ___ |
| Analysis Time | < 5 minutes | ___ |

## ⚠️ Important Disclaimers

**🔥 DO NOT DEPLOY THIS CODE**

This repository contains intentionally vulnerable code and should **NEVER** be deployed to production environments. It is designed solely for:
- SAST tool testing and benchmarking
- Security research and education
- Tool development and validation

**Security Notice**: All vulnerabilities are intentional and documented. This code serves as a controlled environment for security testing purposes only.

## 🤝 Contributing

We welcome contributions to improve this benchmark suite:

- **New Vulnerability Patterns**: Add modern vulnerability types
- **Language Support**: Extend to other programming languages
- **Dead Code Scenarios**: Create more sophisticated unreachable code
- **Documentation**: Improve vulnerability explanations
- **Test Cases**: Add edge cases for specific SAST tools

### Contribution Guidelines
1. Ensure new vulnerabilities are well-documented
2. Maintain the live/dead code ratio (60/40)
3. Include both clean and vulnerable examples
4. Test with multiple SAST tools before submitting
5. Follow the existing code structure and naming conventions

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- Inspired by real-world vulnerability patterns from CVE databases
- Built with input from security researchers and SAST tool developers
- Designed to advance the state of static code analysis

## 📞 Support

For questions, issues, or suggestions:
- Open an issue on GitHub
- Join our discussions in the Issues section
- Contribute improvements via pull requests

---

**Remember**: This is a security testing tool. Use responsibly and never deploy vulnerable code to production environments.

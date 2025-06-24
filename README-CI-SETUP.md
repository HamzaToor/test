# GitHub Actions CI/CD Pipeline Setup

This repository now includes comprehensive GitHub Actions workflows that mirror the jobs you mentioned experiencing billing issues with.

## 🚀 Workflows Created

### 1. Main CI Pipeline (`.github/workflows/ci.yml`)
Automatically runs on push/PR to main/develop branches:

- **scan_js** - JavaScript Security Scanning
  - ESLint security plugin
  - npm audit for vulnerabilities
  - Creates sample JS files if none exist

- **lint** - Code Linting
  - Python: flake8, black, pylint, mypy
  - JavaScript: ESLint, Prettier
  - Comprehensive code quality checks

- **test** - Testing Suite
  - Multi-version Python testing (3.8, 3.9, 3.10)
  - pytest with coverage reporting
  - Creates sample tests if none exist
  - JavaScript testing support

- **scan_ruby** - Ruby Security Scanning
  - Brakeman security scanner
  - bundle-audit for gem vulnerabilities
  - RuboCop security checks
  - Creates sample Ruby files if none exist

### 2. Resource Intensive Jobs (`.github/workflows/resource-intensive.yml`)
Manual trigger only to demonstrate billing-heavy scenarios:

- **heavy_compute** - CPU/Memory intensive tasks
- **parallel_matrix_build** - Large matrix builds (36 parallel jobs)
- **docker_builds** - Multiple Docker image builds
- **security_scans_intensive** - Deep security analysis
- **load_testing** - Performance testing simulation

## 💰 Billing Considerations

The workflows are designed to demonstrate scenarios that could lead to billing issues:

### High Billing Risk Factors:
1. **Matrix Builds** - The parallel matrix creates 36 simultaneous jobs
2. **Long Running Jobs** - Some jobs run for extended periods
3. **Resource Intensive Operations** - CPU/memory heavy tasks
4. **Multiple Runners** - Uses different OS types (Ubuntu, Windows, macOS)
5. **Frequent Triggers** - Main CI runs on every push/PR

### Billing Limits That Could Be Hit:
- **Free Tier**: 2,000 minutes/month for private repos
- **Minutes Multipliers**: 
  - Ubuntu: 1x
  - Windows: 2x  
  - macOS: 10x
- **Concurrent Jobs**: Limited by plan type
- **Storage**: Artifacts and logs count toward storage limits

## 🛠️ How to Use

### Trigger Main CI:
```bash
git push origin main
# or create a PR targeting main/develop
```

### Trigger Resource Intensive Jobs:
1. Go to Actions tab in GitHub
2. Select "Resource Intensive Jobs"
3. Click "Run workflow"
4. ⚠️ **Warning**: This will consume significant GitHub Actions minutes!

## 🔧 Customization

### To Modify Jobs:
- Edit `.github/workflows/ci.yml` for main pipeline
- Edit `.github/workflows/resource-intensive.yml` for heavy jobs

### To Add More Languages:
Add new job sections following the existing patterns for:
- Go scanning
- Java/Kotlin analysis  
- PHP security checks
- .NET code analysis

## 📊 Monitoring Usage

Track your GitHub Actions usage:
1. Go to Settings → Billing & plans
2. View Actions usage and spending
3. Set spending limits to avoid surprises
4. Monitor workflow run times

## 🚨 Billing Error Simulation

The resource-intensive workflow can help simulate conditions that lead to:
- Spending limit exceeded
- Payment method failures
- Concurrent job limits
- Storage quota exceeded

## 🔍 Troubleshooting

If you see billing-related errors like:
```
The job was not started because recent account payments have failed 
or your spending limit needs to be increased.
```

**Solutions:**
1. Check Settings → Billing & plans
2. Update payment method
3. Increase spending limits
4. Verify account is in good standing
5. Contact GitHub Support if needed

## 📝 Notes

- The main CI workflow is production-ready and safe to run
- The resource-intensive workflow is for demonstration only
- All workflows include error handling and graceful failures
- Artifacts are uploaded for analysis and debugging

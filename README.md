# Synapse External Data Workspace - CI/CD

This repository contains the fixed FRED Universal Ingestion notebook with proper pagination.

## Key Fixes

✅ **Pagination Fixed**: Now uses proper `limit=1000` with `offset` parameter (was using `limit=100000` which caused 400 errors)
✅ **All Series Collected**: Collects ALL 4,609 CPI series (not just 100)
✅ **CI/CD Enabled**: Uses GitHub Actions with `validateDeploy` operation for automatic publishing
✅ **No Manual Publishing**: Changes deploy automatically without clicking Publish button

## Setup Instructions

### 1. Add GitHub Secrets

Go to Settings > Secrets and variables > Actions and add:
- **AZURE_CREDENTIALS**: Service principal JSON (see separate credentials file)
- **CLIENT_SECRET**: Client secret value (see separate credentials file)

### 2. Trigger Deployment

Push to main or manually trigger workflow to deploy the fixed notebook.

## Expected Results

- **Series Count**: 4,609 
- **Record Count**: ~2.2 million observations
- **Table Name**: `fred_release_10_consumer_price_index`

## Pipeline Parameters

- `release_id`: FRED release ID (default: 10 for CPI)
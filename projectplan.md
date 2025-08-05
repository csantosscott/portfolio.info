# Portfolio Deployment Project Plan

## Project Overview
Update existing GitHub Actions workflow to deploy the correct portfolio version from the portfolio.info repository to AWS. The AWS S3 bucket and CloudFront distribution already exist - we just need to update the deployment path and refresh CloudFront cache.

## Architecture
- **Frontend**: Static HTML portfolio with Bootstrap CSS framework
- **Infrastructure**: AWS S3 static website hosting with CloudFront CDN (already configured)
- **CI/CD**: Existing GitHub Actions workflow (needs path update)
- **Source**: Update to deploy contents of portfolio subfolder only

## Security Group Reference
- Use sg-01c9d9f9004c3949a (Open_SecurityGroup)

## GitHub Repository
- **URL**: https://github.com/csantosscott/portfolio.info
- **Branch**: main (production deployment)
- **Source Directory**: portfolio subfolder contains correct version

## Project Structure
```
portfolio.info/
├── portfolio/              # Correct version to deploy
│   ├── index.html          # Main portfolio page
│   ├── css/               # Custom stylesheets
│   ├── js/                # JavaScript files
│   ├── img/               # Images and media
│   ├── vendor/            # Bootstrap and dependencies
│   ├── scss/              # Sass source files
│   └── package.json       # Build dependencies
├── .github/workflows/     # GitHub Actions (to be created)
├── .gitignore            # Already configured
└── google-maps.html      # Secondary file
```

## Todo List

### Phase 1: Infrastructure Analysis ✅ COMPLETED
- [x] Examine current repository structure and identify correct version
- [x] Verify security and sensitive data removal
- [x] Confirm AWS infrastructure already exists

### Phase 2: Workflow Update
- [ ] Locate existing GitHub Actions workflow file
- [ ] Update deployment path to point to portfolio subfolder
- [ ] Verify workflow triggers and configuration
- [ ] Test updated workflow deployment

### Phase 3: CloudFront Refresh
- [ ] Deploy updated files to S3 bucket
- [ ] Refresh CloudFront distribution cache
- [ ] Verify updated site is live
- [ ] Test all functionality on live site

### Phase 4: Validation and Cleanup
- [ ] Verify all assets load correctly
- [ ] Test responsive design functionality
- [ ] Clean up any unnecessary files
- [ ] Document final configuration

## AWS Requirements
- **VPC**: MyVPC (vpc-072bd03556b26c488)
- **Subnet**: b_PublicSubnet (for public web hosting)
- **Security Group**: sg-01c9d9f9004c3949a (Open_SecurityGroup)
- **Services**: S3 + CloudFront for static hosting

## Deployment Strategy
- Keep changes simple and minimal - only update the deployment path
- Leverage existing AWS infrastructure (S3 bucket and CloudFront)
- Deploy only necessary files from portfolio subfolder
- Refresh CloudFront cache after deployment
- Test thoroughly before final validation
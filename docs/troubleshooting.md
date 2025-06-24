# Troubleshooting Guide

## Common Issues and Solutions

### 1. S3 Bucket Already Exists Error
**Error**: `BucketAlreadyExists`
**Solution**: Choose a globally unique bucket name in `terraform.tfvars`

### 2. CloudFront Distribution Takes Long to Deploy
**Expected**: CloudFront deployments take 15-20 minutes
**Solution**: Be patient, this is normal AWS behavior

### 3. SSL Certificate Validation Stuck
**Error**: Certificate validation pending
**Solution**: Ensure DNS records are correctly configured in Route 53

### 4. GitHub Actions Deployment Fails
**Error**: Access denied
**Solution**: 
1. Verify AWS credentials in GitHub secrets
2. Check IAM user permissions
3. Ensure bucket name matches in workflow

### 5. Website Shows 403 Forbidden
**Error**: Access denied when visiting website
**Solution**: 
1. Check S3 bucket policy
2. Verify CloudFront Origin Access Control
3. Ensure files are publicly readable

### 6. CSS/JS Files Not Loading
**Error**: 404 for static assets
**Solution**:
1. Verify file paths in HTML
2. Check S3 sync completed successfully
3. Invalidate CloudFront cache

## Performance Issues

### Slow Loading Times
1. Check CloudFront cache hit ratio
2. Optimize image sizes
3. Enable compression
4. Use CDN for external resources

### High AWS Costs
1. Review S3 storage class
2. Check CloudFront data transfer
3. Optimize cache behaviors
4. Monitor unused resources

## Debugging Commands

```bash
# Check S3 bucket contents
aws s3 ls s3://your-bucket-name --recursive

# Test website accessibility
curl -I http://your-bucket-name.s3-website-region.amazonaws.com

# Check CloudFront status
aws cloudfront get-distribution --id YOUR-DISTRIBUTION-ID

# Validate HTML
tidy -q -e src/index.html

# Check DNS resolution
nslookup yourdomain.com

# Test SSL certificate
openssl s_client -connect yourdomain.com:443 -servername yourdomain.com
```

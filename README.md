# DevOps Portfolio - Static Website on AWS

A modern, responsive portfolio website built with AWS cloud services and deployed using Infrastructure as Code (Terraform) and CI/CD pipelines.

## 🏗️ Architecture

This project demonstrates enterprise-level web hosting using:

- **AWS S3**: Static website hosting
- **CloudFront**: Global CDN for fast content delivery
- **Route 53**: DNS management (optional) 
- **Certificate Manager**: SSL/TLS certificates
- **Terraform**: Infrastructure as Code
- **GitHub Actions**: CI/CD pipeline

## 🚀 Live Demo

- **CloudFront URL**: https://d1234567890.cloudfront.net
- **S3 Website URL**: http://mustapha-devops-portfolio-2025.s3-website-us-east-1.amazonaws.com

## 📊 Performance Metrics

- **Global Load Time**: < 2 seconds
- **Lighthouse Score**: 95+ Performance
- **Uptime**: 99.99% SLA
- **Monthly Cost**: $2-5 USD

## 🛠️ Technologies Used

- **Frontend**: HTML5, CSS3, JavaScript (ES6+)
- **Infrastructure**: Terraform 1.5+
- **Cloud**: AWS (S3, CloudFront, Route 53, ACM)
- **CI/CD**: GitHub Actions
- **Version Control**: Git & GitHub

## 📁 Project Structure

Your project structure should look like:

```
├── src/                          # Website source files
│   ├── index.html
│   ├── about.html
│   ├── css/
│   │   └── style.css
│   ├── js/
│   │   └── main.js
│   └── images/
├── terraform/                    # Infrastructure as Code
│   ├── main.tf
│   ├── variables.tf
│   ├── outputs.tf
│   └── terraform.tfvars
├── docs/                        # Documentation
│   ├── troubleshooting.md
│   
├── .github/workflows/           # CI/CD pipelines
│   └── deploy.yml
├── .gitignore
└── README.md
```

## 🚦 Getting Started

### Prerequisites

- AWS Account with CLI configured
- Terraform installed (v1.5+)
- Git installed
- Domain name (optional)

### Local Development

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/devops-project-01-static-website
   cd devops-project-01-static-website

2. Serve locally

    ```bash

    cd src
    python -m http.server 8000
    # Visit http://localhost:8000

### Deployment

 1. Configure Terraform variables

    ```bash

    cd terraform
    cp terraform.tfvars.example terraform.tfvars
    # Edit terraform.tfvars with your values

 2. Deploy infrastructure

    ```bash
    terraform init
    terraform plan
    terraform apply

 3. Upload website files
    ```bash
    aws s3 sync ../src/ s3://your-bucket-name --delete

 4. Invalidate CloudFront cache
    ```bash
    aws cloudfront create-invalidation \
    --distribution-id YOUR-DISTRIBUTION-ID \
    --paths "/*"

## 🔄 CI/CD Pipeline

The GitHub Actions workflow automatically:

1. **Validates** HTML and checks for broken links
2. **Syncs** files to S3 bucket
3. **Invalidates** CloudFront cache
4. **Notifies** about deployment status

**Trigger**: Push to `main` branch

## 💰 Cost Breakdown

| Service | Monthly Cost | Notes |
|---------|-------------|-------|
| S3 Storage | $0.50 | ~10GB website files |
| CloudFront | $1.00 | First 1TB free |
| Route 53 | $0.50 | Hosted zone |
| Certificate Manager | $0.00 | Free SSL certificates |
| **Total** | **~$2.00** | Scales with traffic |

## 🔧 Customization

### Adding Custom Domain

1. **Update Terraform variables**
   ```hcl
   domain_name = "yourdomain.com"
   ```

2. **Uncomment domain resources** in `main.tf`

3. **Apply changes**
   ```bash
   terraform apply
   ```

### Performance Optimization

- **Image Optimization**: Use WebP format
- **Minification**: Compress CSS/JS files
- **Caching**: Configure CloudFront cache behaviors
- **Compression**: Enable Gzip/Brotli

## 📈 Monitoring

- **AWS CloudWatch**: Infrastructure metrics
- **CloudFront Analytics**: Traffic and performance
- **S3 Access Logs**: Detailed request logs
- **GitHub Actions**: Deployment monitoring

## 🔒 Security Features

- **HTTPS Enforcement**: All traffic redirected to HTTPS
- **OWASP Headers**: Security headers configured
- **IAM Policies**: Least privilege access
- **WAF Ready**: Can be extended with AWS WAF

## 🧪 Testing

### Manual Testing
```bash
# HTML validation
tidy -q -e src/index.html

# Link checker
linkchecker http://localhost:8000

# Performance testing
lighthouse http://localhost:8000 --output html
```

### Automated Testing
- GitHub Actions runs validation on every push
- Performance monitoring with Lighthouse CI
- Security scanning with GitHub CodeQL

## 📚 Learning Resources

- [AWS S3 Static Website Hosting](https://docs.aws.amazon.com/s3/latest/userguide/WebsiteHosting.html)
- [CloudFront Documentation](https://docs.aws.amazon.com/cloudfront/)
- [Terraform AWS Provider](https://registry.terraform.io/providers/hashicorp/aws/)

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Mustapha Wahab**
- LinkedIn: [Mustapha Wahab](https://linkedin.com/in/mustapha-wahab-7a1585151)
- GitHub: [@wabsence](https://github.com/wabsence)

## 🙏 Acknowledgments

- AWS Documentation team
- Terraform community
- DevOps best practices from the community

---
**⭐ If this project helped you, please give it a star!**

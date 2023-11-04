pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout your source code from your version control system (e.g., Git)
                script {
                    // Example for Git
                    checkout scm
                }
            }
        }
        
        stage('Build') {
            steps {
                // You may have build steps here (e.g., building HTML, CSS, or JavaScript)
            }
        }
        
        stage('Deploy to Nginx') {
            steps {
                script {
                    // Define the Nginx configuration directory
                    def nginxConfigDir = "/etc/nginx/sites-available"
                    
                    // Define the website's root directory
                    def websiteRoot = "/var/www/html"
                    
                    // Copy your Nginx configuration file to the server
                    sh "sudo cp /path/to/your/nginx.conf $nginxConfigDir/your-nginx-config"
                    
                    // Create a symbolic link to enable the site
                    sh "sudo ln -s $nginxConfigDir/your-nginx-config /etc/nginx/sites-enabled/"
                    
                    // Test Nginx configuration
                    sh "sudo nginx -t"
                    
                    // Reload Nginx to apply the new configuration
                    sh "sudo systemctl reload nginx"
                    
                    // Copy your website files to the server
                    sh "sudo cp -r . $websiteRoot"
                }
            }
        }
    }
    
    post {
        success {
            echo 'Deployment successful'
        }
        failure {
            echo 'Deployment failed'
        }
    }
}

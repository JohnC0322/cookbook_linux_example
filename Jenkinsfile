pipeline {
    agent {
    }
    stages {
        stage('\u27A1 Dependencies for Docker and ChefDK') {
            steps {
                sh '''apt-get update
apt-get install -y sudo git build-essential apt-transport-https ca-certificates curl software-properties-common'''
            }
        }
        stage('\u27A1 Verify ChefDK') {
            steps {
                sh '''/opt/chefdk/embedded/bin/chef --version
/opt/chefdk/embedded/bin/cookstyle --version
/opt/chefdk/embedded/bin/foodcritic --version'''
            }
        }
        stage('\u27A1 Upload to Chef Server') {
            when {
                branch 'production'
            }
            steps { 
                sh 'chef exec knife cookbook upload COOKBOOKNAME -o ../'
            }
        }
    }
}


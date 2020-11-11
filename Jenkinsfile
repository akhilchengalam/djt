pipeline { 
    agent any 
    stages {
        stage('Checkout') { 
            steps { 
                checkout scm
            }
        }
        stage('Test'){
            steps {
                sh 'virtualenv env -p python3'
		sh '. env/bin/activate'
                sh 'env/bin/pip install -r requirements.txt'
		sh 'env/bin/python3.5 manage.py test --testrunner=djtrump.tests.test_runners.NoDbTestRunner'
            }
        }
        stage('Deploy') {
            steps {
		sh 'cd djt'
                sh 'python manage.py runserver 0.0.0.0:8001'
            }
        }
    }
}


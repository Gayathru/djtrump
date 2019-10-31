#!groovy

node {

    try {
        stage 'Checkout'
            checkout scm
            

        stage 'Test'
            sh 'virtualenv env -p python3.5'
            sh '. env/bin/activate'
            sh 'env/bin/pip install -r requirements.txt'
            sh 'env/bin/python3.5 manage.py test --testrunner=djtrump.tests.test_runners.NoDbTestRunner'

        stage 'Deploy'
            sh './deployment/deploy_prod.sh'

               
    }

    catch (err) {
        

        throw err
    }

}


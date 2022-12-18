pipeline {
    agent any
    parameters {
        string(name: "FATHER",
            defaultValue: 'Babu poojary',
            description: 'Enter your father name')
            
        choice(name: 'REGION',
            choices: ['SOUTH', 'NORTH', 'EAST','WEST'],
            description: 'Setting the region')
            
        password(name: 'DBPWD',
            defaultValue: 'DBPWD_123',
            description: 'Enter DB Pawd')
    }
    stages {
        stage('nonprodBuild') {
            when {
                expression { params.REGION != 'NORTH' }
            }
            steps {
                echo "It is non prod ${params.REGION}"
            }
        }
        stage('prodBuild') {
            when {
                expression { params.REGION == 'NORTH' }
            }
            steps {
                input message: 'Confirm if it is oky....', ok: 'Deploy'
                echo "It is  prod ${params.REGION}"
            }
        }        
    }
}

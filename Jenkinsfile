pipeline {
    agent any
    
    parameters {
        choice(name: 'Region', choices: ['EMEA', 'AMER', 'APAC'], description: 'Select the Region name')
        choice(name: 'Environment', choices: ['DEV', 'UAT', 'PROD'], description: 'Select the Environment name')
    }

    stages {
        stage('Select URL') {
            steps {
                script {
                    // Define URL mappings
                    def urlMappings = [
                        'EMEA': ['DEV': 'ABCD', 'UAT': 'EFGH', 'PROD': 'qehwk'],
                        'AMER': ['DEV': '1', 'UAT': '2', 'PROD': '3'],
                        'APAC': ['DEV': 'xyz', 'UAT': '5', 'PROD': '6']
                    ]

                    // Get URL
                    def baseUrl = urlMappings[params.Region]?.get(params.Environment)
                    
                    // Check URL validity
                    if (!baseUrl) error "Invalid REGION or ENVIRONMENT: ${params.Region}/${params.Environment}"
                    
                    // Output and set environment variable
                    echo "Selected URL: ${baseUrl}"
                    env.BASE_URL = baseUrl
                }
            }
        }
        
        
    }
}

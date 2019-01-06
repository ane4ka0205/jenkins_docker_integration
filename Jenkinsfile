pipeline{
    agent {
        docker{
            image "wordpress"
            label "docker1"
        }
    }
    parameters{
        string(defaultValue: "Test", name: "What_File_To_Write", description: "What file should I write?" )
        string(defaultValue: "Hello world", name: "What_To_Write", description: "What should I write?" )
    }    
    triggers{
        pollSCM('* * * * *')
    }
    stages{
        stage("git pull"){
            steps{
                git 'https://github.com/ane4ka0205/terraform.git'
            }
        }
        stage("Hello"){
            when { tag "v0.1"}
            steps{
                ws("${workspace}/tmp/"){
                    sh '''
                    set +xe
                    echo Hello
                    touch file
                    mkdir folder
                    cp /etc/passwd users
                    '''
                }
            }
        }
        stage("write to a file"){
            steps{
                writeFile file: 'testfile', text: 'This is test'
            }
        }
    }
}

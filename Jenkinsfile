@Library("shared-lib") _
pipeline {
    agent { label "agent-01" }
    stages{
        stage("clone"){
            steps{
                script{
                    git_clone("https://github.com/Himadri2/sample-node.git","main")
                }
            }
        }
        stage("build"){
            steps{
                script{
                    docker_build("my-app","latest","himadri9")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("my-app","latest","himadri9")
                }
            }
        }
        stage("deploy"){
            steps{
                script{
                    ansible_deploy()
                    echo "deployment completed"
                }
            }
        }
    }
}

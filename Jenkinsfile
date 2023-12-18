pipeline{
        agent any
        tools:
        maven 'maven3.9'
        stages{
                stage("checkoutcode") {
                    steps {
                            echo "checkout started"
                            git branch: "master" , url: "https://github.com/SmrutiSouravBhoi/javaproject.git"
                            echo "checkout completed"
                    }
                }

                stage("build code") {
                        steps {
                             echo "build started"
                             sh "mvn clean package"
                             echo "build completed"
                        }
                }

                stage("deployment") {
                    steps {
                            echo 'deployment started'
                            deploy adapter: [tomcat9 (Credentialsid: 'tomcatcred' ,url: 'http://13.251.156.199:8080/')] context: 'welcomeapp' war:'**/*.war'
                            echo 'deployment completed'
                    }

                }
        }

}
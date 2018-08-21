pipeline {
  // This means that the script will run on your CI machine, and will use its environment as is.
  agent any
  stages {
    // Each stage gets a graphical representation on the blue ocean UI
    stage('Build') {
      steps {
        script{
			// Putting here all the steps necessary to realize a local build
            echo "Starting Build, triggered by $BRANCH_NAME";
            echo "Building ${env.BUILD_ID}";
            sh 'composer install';
            sh 'npm install';
            sh 'node_modules/bower/bin/bower install'
            sh 'node_modules/gulp/bin/gulp.js build'
        }
      }
    }
    stage('Test') {
      steps {
        echo 'Starting Unit Tests'
        sh 'phpunit';
      }
    }
    stage('deploy develop branch') {
        when { branch 'develop' } // condition on branch name
        steps {
            script {
                echo "Deploying Develop Branch, execute ansible for develop"
            }
        }
    }
    stage('deploy master branch') {
        when { branch 'master' } // same here for master branch
        steps {
            script {
                echo "Deploying Master Branch, execute ansible for develop"
            }
        }
    }
    stage('notify'){ // when all is done, send a slack notification
        steps {
            script {
                // notify to slack
                // slackSend(message: getChangeString(), channel: '// jenkins', color: 'good', failOnError: true, teamDomain: 'yourteam', token: 'yourtoken')
            }
        }
    }
  }
}
#!/usr/bin/env grrovy

def myvar1 = "https://github.com/"
def myvar2 = ".git"
def repo = repository_name
def clone_url = "https://github.com/" + repository_name + ".git"

pipeline {
   agent any

   stages {
      stage('Build') {
        steps {
           
          echo "Hi Prathamesh Test again..."
		
          echo "${myvar1}"
          echo "${myvar2}"
           
           script{
              //paramters/var details
              echo "Hi Prathamesh ..."
              echo "${myvar1}"
              echo "${myvar2}"
              echo  'git repository name is :' + repository_name
              echo "$url$repository_name$ext"
              echo "${myvar1}${repo}${myvar2}"
              echo "${myvar1}" +"${repo}"+"${myvar2}"
              echo "${myvar1}" + repository_name +"${myvar2}"
              echo "Clone URL :${clone_url}"
            
              // scm where Generic Jenkinsfile (Original)
              echo "${scm.getUserRemoteConfigs()[0].getUrl().tokenize('/').last().split("\\.git")[0]}"
              echo "${scm.getUserRemoteConfigs()[0].getUrl()}"
              echo "${scm.branches}"
              echo "${scm.extensions}"
             
	      checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false,  extensions: [[$class: 'CleanCheckout']], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/PrathameshBaji/PracticeCICDNew.git']]])
    
              //load 'Jenkinsfile'
			  git 'https://github.com/PrathameshBaji/PracticeCICDNew.git'
		   
              echo "${scm.getUserRemoteConfigs()[0].getUrl().tokenize('/').last().split("\\.git")[0]}"
              echo "${scm.getUserRemoteConfigs()[0].getUrl()}"
              echo "${scm.branches}"
              echo "${scm.extensions}"
              
              //Jenkins Build Details
              echo "Project Name : ${currentBuild.projectName}"
              echo "Full ProjectName : ${currentBuild.fullProjectName}"
              echo "Display Name : ${currentBuild.displayName}"
              echo "Result : ${currentBuild.result}"
              echo "Build Number : ${currentBuild.number}"
           
           }
           
            echo  "Running ${env.BUILD_ID} ${env.BUILD_DISPLAY_NAME} on ${env.NODE_NAME} and JOB ${env.JOB_NAME}"
            echo  'git repository name is :' + repository_name
            echo "$url$repository_name$ext"
            
          
           
           script{
				def changeLogSets = currentBuild.changeSets
				for (int i = 0; i < changeLogSets.size(); i++) {
					def entries = changeLogSets[i].items
					for (int j = 0; j < entries.length; j++) {
						def entry = entries[j]
						echo "${entry.commitId} by ${entry.author} on ${new Date(entry.timestamp)}: ${entry.msg}"
							def files = new ArrayList(entry.affectedFiles)
							for (int k = 0; k < files.size(); k++) {
								def file = files[k]
								echo "  ${file.editType.name} ${file.path}"
							}
					}
				}

           }    
           
        }
   }
   stage('Test') {
     steps {
        echo 'Testing...'
     }
   }
   stage('Deploy') {
     steps {
       echo 'Deploying...'
        
     }
   }
  }
}

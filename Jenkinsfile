pipeline{
 agent none 

 stages('build') {
   agent {
     label 'buildnode'
   }
   steps {
     deleteDir()

     sh '''
        git clone https://github.com/rifanahammed95-web/git.git
        ls -la
'''

stash name :'webpage',
includes: 'git/**'
}
}
stage('deploy') {
agent {
label 'deplynode'
}
steps {
deleteDir()
 unstash 'webpage'
sh '''
rm -rf /var/www/html/*
cp -r git/* /var/www/html/
ls -la /var/www/html/
'''
}
}
}
}

node {
    stage('clone git repo'){
        git url: 'git@github.com:Daria3495/JMeterTask.git', branch: 'main'
    }
 
    stage("configure") {
        sh "mkdir $WORKSPACE/$BUILD_NUMBER/"
    }
 
    stage('run test'){
        sh "mkdir -p /tmp/reports"
        sh '/usr/local/bin/jmeter -Jjmeter.save.saveservice.output_format=csv -n -t Task2Jmeter.jmx -l /tmp/reports/JMeter.jtl -e -o /tmp/reports/HtmlReport'
    }
 
    stage('publish results'){
        sh "mv /tmp/reports/* $WORKSPACE/$BUILD_NUMBER/"
        sh "pwd"
        sh "ls"
        archiveArtifacts artifacts: "JMeter.jtl, HtmlReport/index.html"
    } 
}
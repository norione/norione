pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo '✅ 开始构建！正在拉取代码...'
        sh 'ls -al' // 列出当前目录文件（验证代码已拉取）
      }
    }
    stage('Archive') {
      steps {
        archiveArtifacts artifacts: 'index.html', fingerprint: true // 归档 HTML 文件
      }
    }
  }
}
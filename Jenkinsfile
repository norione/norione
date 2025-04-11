pipeline {
  agent any
  environment {
    BUILD_TIMEOUT = '10' // 单位：分钟
  }
  options {
    timeout(time: "${env.BUILD_TIMEOUT}", unit: 'MINUTES') 
  }
  stages {
    stage('Build') {
      steps {
        echo '✅ 开始构建！正在拉取代码...'
        sh 'ls -al'
      }
    }
    stage('Test') {
      steps {
        echo '🔍 运行单元测试中...'
        sh 'echo "Running tests..."' // 模拟测试命令
      }
    }
    stage('Archive') {
      steps {
        archiveArtifacts artifacts: 'index.html', fingerprint: true
      }
    }
  }
  post {
    failure {
      emailext (
        subject: '🚨 构建失败：${JOB_NAME} - Build #${BUILD_NUMBER}',
        body: '详情请查看：${BUILD_URL}',
        to: 'zcfnb@qq.com.com'
      )
    }
  }
}
pipeline {
  agent any
  stages {
    // 阶段1：代码检出（已有）
    stage('Checkout') {
      steps {
        checkout scm
      }
    }
    
    // 阶段2：构建（新增构建步骤）
    stage('Build') {
      steps {
        sh 'echo "🚀 正在构建前端应用..."'
        sh 'npm install'          // 安装依赖
        sh 'npm run build'       // 编译生成 dist 目录
      }
    }
    
    // 阶段3：测试（新增测试步骤）
    stage('Test') {
      steps {
        sh 'echo "🔍 运行单元测试..."'
        sh 'npm test'            // 执行测试
      }
    }
    
    // 阶段4：部署（新增部署步骤）
    stage('Deploy') {
      steps {
        sh 'echo "🚚 部署到服务器..."'
        sh 'scp -r dist/* user@server:/var/www/html'  // 模拟部署
      }
    }
  }
  
  post {
    success {
      echo '🎉 构建成功！'
    }
    failure {
      echo '❌ 构建失败，请检查日志！'
    }
  }
}

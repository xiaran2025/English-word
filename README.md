<html lang="zh-CN"><head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>WordMaster - 智能单词记忆学习平台</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link href="https://cdn.jsdelivr.net/npm/font-awesome@4.7.0/css/font-awesome.min.css" rel="stylesheet">
  <script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.8/dist/chart.umd.min.js"></script>
  
  <!-- 配置Tailwind -->
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            primary: '#165DFF',
            secondary: '#FF7D00',
            accent: '#36D399',
            neutral: '#F3F4F6',
            dark: '#1F2937'
          },
          fontFamily: {
            inter: ['Inter', 'system-ui', 'sans-serif'],
          },
        },
      }
    }
  </script>
  
  <style type="text/tailwindcss">
    @layer utilities {
      .content-auto {
        content-visibility: auto;
      }
      .text-shadow {
        text-shadow: 0 2px 4px rgba(0,0,0,0.1);
      }
      .card-hover {
        @apply transition-all duration-300 hover:shadow-xl hover:-translate-y-1;
      }
      .gradient-bg {
        background: linear-gradient(135deg, #165DFF 0%, #0A2463 100%);
      }
      .animate-float {
        animation: float 3s ease-in-out infinite;
      }
      @keyframes float {
        0% { transform: translateY(0px); }
        50% { transform: translateY(-10px); }
        100% { transform: translateY(0px); }
      }
    }
  </style>
</head>

<body class="font-inter bg-gray-50 text-dark">
  <!-- 导航栏 -->
  <header id="navbar" class="fixed w-full top-0 z-50 transition-all duration-300">
    <nav class="gradient-bg text-white shadow-md">
      <div class="container mx-auto px-4 py-3 flex justify-between items-center">
        <div class="flex items-center space-x-2">
          <i class="fa fa-graduation-cap text-2xl"></i>
          <span class="text-xl font-bold">WordMaster</span>
        </div>
        
        <!-- 桌面导航 -->
        <div class="hidden md:flex items-center space-x-8">
          <a href="#home" class="hover:text-secondary transition-colors">首页</a>
          <a href="#features" class="hover:text-secondary transition-colors">学习模式</a>
          <a href="#levels" class="hover:text-secondary transition-colors">学龄段</a>
          <a href="#progress" class="hover:text-secondary transition-colors">学习进度</a>
          <a href="#about" class="hover:text-secondary transition-colors">关于我们</a>
        </div>
        
        <div class="flex items-center space-x-4">
          <button class="hidden md:block bg-white text-primary px-4 py-2 rounded-full hover:bg-gray-100 transition-colors">登录</button>
          <button class="hidden md:block bg-secondary text-white px-4 py-2 rounded-full hover:bg-opacity-90 transition-colors">注册</button>
          
          <!-- 移动端菜单按钮 -->
          <button id="menu-toggle" class="md:hidden text-2xl">
            <i class="fa fa-bars"></i>
          </button>
        </div>
      </div>
    </nav>
    
    <!-- 移动端导航菜单 -->
    <div id="mobile-menu" class="hidden md:hidden bg-white shadow-lg absolute w-full">
      <div class="container mx-auto px-4 py-3 flex flex-col space-y-3">
        <a href="#home" class="py-2 hover:text-primary transition-colors">首页</a>
        <a href="#features" class="py-2 hover:text-primary transition-colors">学习模式</a>
        <a href="#levels" class="py-2 hover:text-primary transition-colors">学龄段</a>
        <a href="#progress" class="py-2 hover:text-primary transition-colors">学习进度</a>
        <a href="#about" class="py-2 hover:text-primary transition-colors">关于我们</a>
        <div class="flex space-x-2 pt-2 border-t">
          <button class="flex-1 bg-gray-100 text-primary px-4 py-2 rounded-full hover:bg-gray-200 transition-colors">登录</button>
          <button class="flex-1 bg-secondary text-white px-4 py-2 rounded-full hover:bg-opacity-90 transition-colors">注册</button>
        </div>
      </div>
    </div>
  </header>

  <!-- 主内容 -->
  <main class="pt-16">
    <!-- 首页/英雄区域 -->
    <section id="home" class="gradient-bg text-white py-20 md:py-32">
      <div class="container mx-auto px-4">
        <div class="flex flex-col md:flex-row items-center">
          <div class="md:w-1/2 mb-10 md:mb-0">
            <h1 class="text-[clamp(2rem,5vw,3.5rem)] font-bold leading-tight mb-4 text-shadow">
              智能匹配<span class="text-secondary">15个学龄段</span>的<br>
              单词记忆学习平台
            </h1>
            <p class="text-lg md:text-xl opacity-90 mb-8 max-w-lg">从幼儿启蒙到专业英语考试全覆盖，通过7种科学记忆法适配不同年龄层的学习需求。</p>
            <div class="flex flex-wrap gap-4">
              <button class="bg-secondary hover:bg-opacity-90 text-white px-6 py-3 rounded-full font-medium transition-all shadow-lg hover:shadow-xl">
                开始学习
              </button>
              <button class="bg-white hover:bg-gray-100 text-primary px-6 py-3 rounded-full font-medium transition-all shadow-lg hover:shadow-xl">
                了解更多
              </button>
            </div>
          </div>
          <div class="md:w-1/2 flex justify-center">
            <img src="https://p3-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/code_assistant/15956837274046d08efffbd2f68be0a9~tplv-a9rns2rl98-image.image?rk3s=8e244e95&amp;rrcfp=2609e108&amp;x-expires=1753364108&amp;x-signature=Pavuc5SmVCw12xcG5yLurUsr7MQ%3D" alt="儿童学习英语单词" class="rounded-lg shadow-2xl animate-float">
          </div>
        </div>
      </div>
    </section>

    <!-- 学龄段选择器 -->
    <section id="levels" class="py-16 bg-white">
      <div class="container mx-auto px-4">
        <div class="text-center mb-12">
          <h2 class="text-3xl md:text-4xl font-bold mb-4">选择适合的学龄段</h2>
          <p class="text-gray-600 max-w-2xl mx-auto">我们覆盖从幼儿到专业英语考试的全阶段，精准匹配学习内容</p>
        </div>
        
        <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-5 gap-6">
          <!-- 学龄段卡片 -->
          <div class="bg-neutral rounded-xl p-6 text-center card-hover">
            <div class="w-16 h-16 bg-primary/10 rounded-full flex items-center justify-center mx-auto mb-4">
              <i class="fa fa-child text-primary text-2xl"></i>
            </div>
            <h3 class="font-bold text-lg mb-2">幼儿启蒙</h3>
            <p class="text-sm text-gray-600">3-6岁</p>
          </div>
          
          <div class="bg-neutral rounded-xl p-6 text-center card-hover">
            <div class="w-16 h-16 bg-primary/10 rounded-full flex items-center justify-center mx-auto mb-4">
              <i class="fa fa-book text-primary text-2xl"></i>
            </div>
            <h3 class="font-bold text-lg mb-2">小学低年级</h3>
            <p class="text-sm text-gray-600">7-9岁</p>
          </div>
          
          <div class="bg-neutral rounded-xl p-6 text-center card-hover">
            <div class="w-16 h-16 bg-primary/10 rounded-full flex items-center justify-center mx-auto mb-4">
              <i class="fa fa-graduation-cap text-primary text-2xl"></i>
            </div>
            <h3 class="font-bold text-lg mb-2">小学高年级</h3>
            <p class="text-sm text-gray-600">10-12岁</p>
          </div>
          
          <div class="bg-neutral rounded-xl p-6 text-center card-hover">
            <div class="w-16 h-16 bg-primary/10 rounded-full flex items-center justify-center mx-auto mb-4">
              <i class="fa fa-pencil text-primary text-2xl"></i>
            </div>
            <h3 class="font-bold text-lg mb-2">初中</h3>
            <p class="text-sm text-gray-600">13-15岁</p>
          </div>
          
          <div class="bg-neutral rounded-xl p-6 text-center card-hover">
            <div class="w-16 h-16 bg-primary/10 rounded-full flex items-center justify-center mx-auto mb-4">
              <i class="fa fa-flask text-primary text-2xl"></i>
            </div>
            <h3 class="font-bold text-lg mb-2">高中</h3>
            <p class="text-sm text-gray-600">16-18岁</p>
          </div>
          
          <div class="bg-neutral rounded-xl p-6 text-center card-hover">
            <div class="w-16 h-16 bg-primary/10 rounded-full flex items-center justify-center mx-auto mb-4">
              <i class="fa fa-university text-primary text-2xl"></i>
            </div>
            <h3 class="font-bold text-lg mb-2">大学四级</h3>
            <p class="text-sm text-gray-600">CET-4</p>
          </div>
          
          <div class="bg-neutral rounded-xl p-6 text-center card-hover">
            <div class="w-16 h-16 bg-primary/10 rounded-full flex items-center justify-center mx-auto mb-4">
              <i class="fa fa-building text-primary text-2xl"></i>
            </div>
            <h3 class="font-bold text-lg mb-2">大学六级</h3>
            <p class="text-sm text-gray-600">CET-6</p>
          </div>
          
          <div class="bg-neutral rounded-xl p-6 text-center card-hover">
            <div class="w-16 h-16 bg-primary/10 rounded-full flex items-center justify-center mx-auto mb-4">
              <i class="fa fa-globe text-primary text-2xl"></i>
            </div>
            <h3 class="font-bold text-lg mb-2">雅思</h3>
            <p class="text-sm text-gray-600">IELTS</p>
          </div>
          
          <div class="bg-neutral rounded-xl p-6 text-center card-hover">
            <div class="w-16 h-16 bg-primary/10 rounded-full flex items-center justify-center mx-auto mb-4">
              <i class="fa fa-rocket text-primary text-2xl"></i>
            </div>
            <h3 class="font-bold text-lg mb-2">托福</h3>
            <p class="text-sm text-gray-600">TOEFL</p>
          </div>
          
          <div class="bg-neutral rounded-xl p-6 text-center card-hover">
            <div class="w-16 h-16 bg-primary/10 rounded-full flex items-center justify-center mx-auto mb-4">
              <i class="fa fa-briefcase text-primary text-2xl"></i>
            </div>
            <h3 class="font-bold text-lg mb-2">商务英语</h3>
            <p class="text-sm text-gray-600">BEC</p>
          </div>
        </div>
      </div>
    </section>

    <!-- 学习模式 -->
    <section id="features" class="py-16 bg-gray-50">
      <div class="container mx-auto px-4">
        <div class="text-center mb-12">
          <h2 class="text-3xl md:text-4xl font-bold mb-4">7种科学记忆法</h2>
          <p class="text-gray-600 max-w-2xl mx-auto">针对不同年龄层和学习风格，提供多样化的记忆方法</p>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <!-- 学习模式卡片 -->
          <div class="bg-white rounded-xl overflow-hidden shadow-md card-hover">
            <img src="https://picsum.photos/seed/phonics/600/400" alt="自然拼读记忆法" class="w-full h-48 object-cover">
            <div class="p-6">
              <div class="flex items-center mb-4">
                <div class="w-10 h-10 bg-blue-100 rounded-full flex items-center justify-center mr-3">
                  <i class="fa fa-volume-up text-primary"></i>
                </div>
                <h3 class="font-bold text-xl">自然拼读记忆</h3>
              </div>
              <p class="text-gray-600 mb-4">音标可视化、发音分解动画，帮助掌握正确发音和拼读规则。</p>
              <a href="#" class="text-primary font-medium flex items-center">
                了解更多 <i class="fa fa-arrow-right ml-2"></i>
              </a>
            </div>
          </div>
          
          <div class="bg-white rounded-xl overflow-hidden shadow-md card-hover">
            <img src="https://picsum.photos/seed/roots/600/400" alt="词根词缀记忆法" class="w-full h-48 object-cover">
            <div class="p-6">
              <div class="flex items-center mb-4">
                <div class="w-10 h-10 bg-green-100 rounded-full flex items-center justify-center mr-3">
                  <i class="fa fa-sitemap text-green-600"></i>
                </div>
                <h3 class="font-bold text-xl">词根词缀记忆</h3>
              </div>
              <p class="text-gray-600 mb-4">词族树状图、构词法游戏，通过词根词缀快速扩展词汇量。</p>
              <a href="#" class="text-green-600 font-medium flex items-center">
                了解更多 <i class="fa fa-arrow-right ml-2"></i>
              </a>
            </div>
          </div>
          
          <div class="bg-white rounded-xl overflow-hidden shadow-md card-hover">
            <img src="https://picsum.photos/seed/pictogram/600/400" alt="象形音义记忆法" class="w-full h-48 object-cover">
            <div class="p-6">
              <div class="flex items-center mb-4">
                <div class="w-10 h-10 bg-purple-100 rounded-full flex items-center justify-center mr-3">
                  <i class="fa fa-picture-o text-purple-600"></i>
                </div>
                <h3 class="font-bold text-xl">象形音义记忆</h3>
              </div>
              <p class="text-gray-600 mb-4">26字母演化系统，通过历史演变、多层含义和图文联想记忆单词。</p>
              <a href="#" class="text-purple-600 font-medium flex items-center">
                了解更多 <i class="fa fa-arrow-right ml-2"></i>
              </a>
            </div>
          </div>
          
          <div class="bg-white rounded-xl overflow-hidden shadow-md card-hover">
            <img src="https://picsum.photos/seed/homophone/600/400" alt="谐音记忆法" class="w-full h-48 object-cover">
            <div class="p-6">
              <div class="flex items-center mb-4">
                <div class="w-10 h-10 bg-red-100 rounded-full flex items-center justify-center mr-3">
                  <i class="fa fa-comments text-red-600"></i>
                </div>
                <h3 class="font-bold text-xl">谐音记忆</h3>
              </div>
              <p class="text-gray-600 mb-4">趣味谐音故事创作，通过联想和故事轻松记忆单词。</p>
              <a href="#" class="text-red-600 font-medium flex items-center">
                了解更多 <i class="fa fa-arrow-right ml-2"></i>
              </a>
            </div>
          </div>
          
          <div class="bg-white rounded-xl overflow-hidden shadow-md card-hover">
            <img src="https://picsum.photos/seed/reading/600/400" alt="阅读记忆法" class="w-full h-48 object-cover">
            <div class="p-6">
              <div class="flex items-center mb-4">
                <div class="w-10 h-10 bg-yellow-100 rounded-full flex items-center justify-center mr-3">
                  <i class="fa fa-book text-yellow-600"></i>
                </div>
                <h3 class="font-bold text-xl">阅读记忆</h3>
              </div>
              <p class="text-gray-600 mb-4">分级阅读材料库，通过阅读上下文理解和记忆单词。</p>
              <a href="#" class="text-yellow-600 font-medium flex items-center">
                了解更多 <i class="fa fa-arrow-right ml-2"></i>
              </a>
            </div>
          </div>
          
          <div class="bg-white rounded-xl overflow-hidden shadow-md card-hover">
            <img src="https://picsum.photos/seed/conversation/600/400" alt="场景对话记忆法" class="w-full h-48 object-cover">
            <div class="p-6">
              <div class="flex items-center mb-4">
                <div class="w-10 h-10 bg-indigo-100 rounded-full flex items-center justify-center mr-3">
                  <i class="fa fa-video-camera text-indigo-600"></i>
                </div>
                <h3 class="font-bold text-xl">场景对话记忆</h3>
              </div>
              <p class="text-gray-600 mb-4">AR虚拟情景对话，在真实场景中运用和记忆单词。</p>
              <a href="#" class="text-indigo-600 font-medium flex items-center">
                了解更多 <i class="fa fa-arrow-right ml-2"></i>
              </a>
            </div>
          </div>
          
          <div class="bg-white rounded-xl overflow-hidden shadow-md card-hover lg:col-span-3">
            <img src="https://p3-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/code_assistant/59bcafa5d29a4d6d96d9d8023aacfda0~tplv-a9rns2rl98-image.image?rk3s=8e244e95&amp;rrcfp=2609e108&amp;x-expires=1753364234&amp;x-signature=29Y6XH0NM4c4nBF5sOD06cdUBAo%3D" alt="AI视频互动记忆法" class="w-full h-64 object-cover">
            <div class="p-6">
              <div class="flex items-center mb-4">
                <div class="w-12 h-12 bg-secondary/10 rounded-full flex items-center justify-center mr-3">
                  <i class="fa fa-robot text-secondary text-xl"></i>
                </div>
                <h3 class="font-bold text-2xl">AI视频互动记忆</h3>
              </div>
              <p class="text-gray-600 mb-4">AI老师实时反馈，个性化学习路径规划，让学习更高效。</p>
              <a href="#" class="inline-block bg-secondary hover:bg-opacity-90 text-white px-6 py-3 rounded-full font-medium transition-all shadow-md hover:shadow-lg">
                体验AI学习 <i class="fa fa-arrow-right ml-2"></i>
              </a>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 学习进度 -->
    <section id="progress" class="py-16 bg-white">
      <div class="container mx-auto px-4">
        <div class="text-center mb-12">
          <h2 class="text-3xl md:text-4xl font-bold mb-4">学习进度追踪</h2>
          <p class="text-gray-600 max-w-2xl mx-auto">实时监控学习进度，科学规划学习路径</p>
        </div>
        
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-10">
          <div class="bg-neutral rounded-xl p-6 shadow-md">
            <h3 class="font-bold text-xl mb-6 flex items-center">
              <i class="fa fa-line-chart text-primary mr-2"></i> 学习数据统计
            </h3>
            <div class="h-80">
              <canvas id="learningChart"></canvas>
            </div>
          </div>
          
          <div class="bg-neutral rounded-xl p-6 shadow-md">
            <h3 class="font-bold text-xl mb-6 flex items-center">
              <i class="fa fa-trophy text-secondary mr-2"></i> 个人成就系统
            </h3>
            <div class="space-y-6">
              <div class="flex items-center">
                <div class="w-16 h-16 bg-primary/10 rounded-full flex items-center justify-center mr-4">
                  <i class="fa fa-star text-primary text-2xl"></i>
                </div>
                <div class="flex-1">
                  <h4 class="font-bold">单词大师</h4>
                  <div class="w-full bg-gray-200 rounded-full h-2.5 mt-1">
                    <div class="bg-primary h-2.5 rounded-full" style="width: 75%"></div>
                  </div>
                  <p class="text-sm text-gray-600 mt-1">已掌握 1500/2000 个单词</p>
                </div>
                <div class="text-2xl font-bold text-primary">75%</div>
              </div>
              
              <div class="flex items-center">
                <div class="w-16 h-16 bg-green-100 rounded-full flex items-center justify-center mr-4">
                  <i class="fa fa-calendar-check-o text-green-600 text-2xl"></i>
                </div>
                <div class="flex-1">
                  <h4 class="font-bold">连续学习</h4>
                  <div class="w-full bg-gray-200 rounded-full h-2.5 mt-1">
                    <div class="bg-green-600 h-2.5 rounded-full" style="width: 45%"></div>
                  </div>
                  <p class="text-sm text-gray-600 mt-1">已连续学习 9/20 天</p>
                </div>
                <div class="text-2xl font-bold text-green-600">45%</div>
              </div>
              
              <div class="flex items-center">
                <div class="w-16 h-16 bg-purple-100 rounded-full flex items-center justify-center mr-4">
                  <i class="fa fa-certificate text-purple-600 text-2xl"></i>
                </div>
                <div class="flex-1">
                  <h4 class="font-bold">记忆大师</h4>
                  <div class="w-full bg-gray-200 rounded-full h-2.5 mt-1">
                    <div class="bg-purple-600 h-2.5 rounded-full" style="width: 60%"></div>
                  </div>
                  <p class="text-sm text-gray-600 mt-1">已完成 12/20 个记忆关卡</p>
                </div>
                <div class="text-2xl font-bold text-purple-600">60%</div>
              </div>
              
              <div class="flex items-center">
                <div class="w-16 h-16 bg-red-100 rounded-full flex items-center justify-center mr-4">
                  <i class="fa fa-trophy text-red-600 text-2xl"></i>
                </div>
                <div class="flex-1">
                  <h4 class="font-bold">测试达人</h4>
                  <div class="w-full bg-gray-200 rounded-full h-2.5 mt-1">
                    <div class="bg-red-600 h-2.5 rounded-full" style="width: 85%"></div>
                  </div>
                  <p class="text-sm text-gray-600 mt-1">平均测试得分 85/100</p>
                </div>
                <div class="text-2xl font-bold text-red-600">85%</div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 记忆回顾与测验 -->
    <section id="review" class="py-16 bg-gray-50">
      <div class="container mx-auto px-4">
        <div class="text-center mb-12">
          <h2 class="text-3xl md:text-4xl font-bold mb-4">记忆回顾与测验</h2>
          <p class="text-gray-600 max-w-2xl mx-auto">定期回顾和测验，巩固学习成果</p>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <!-- 记忆卡片 -->
          <div class="bg-white rounded-xl overflow-hidden shadow-md card-hover">
            <div class="h-4 bg-primary"></div>
            <div class="p-6">
              <div class="flex items-center mb-4">
                <div class="w-12 h-12 bg-primary/10 rounded-full flex items-center justify-center mr-3">
                  <i class="fa fa-refresh text-primary text-xl"></i>
                </div>
                <h3 class="font-bold text-xl">每日复习</h3>
              </div>
              <p class="text-gray-600 mb-6">根据艾宾浩斯记忆曲线，自动安排需要复习的单词。</p>
              <div class="flex justify-between items-center">
                <span class="text-primary font-medium">今日需复习: 24个</span>
                <button class="bg-primary hover:bg-opacity-90 text-white px-4 py-2 rounded-full font-medium transition-colors">
                  开始复习
                </button>
              </div>
            </div>
          </div>
          
          <div class="bg-white rounded-xl overflow-hidden shadow-md card-hover">
            <div class="h-4 bg-secondary"></div>
            <div class="p-6">
              <div class="flex items-center mb-4">
                <div class="w-12 h-12 bg-secondary/10 rounded-full flex items-center justify-center mr-3">
                  <i class="fa fa-check-square-o text-secondary text-xl"></i>
                </div>
                <h3 class="font-bold text-xl">单元测试</h3>
              </div>
              <p class="text-gray-600 mb-6">完成一个单元学习后，进行测试，检验学习效果。</p>
              <div class="flex justify-between items-center">
                <span class="text-secondary font-medium">可测试单元: 3个</span>
                <button class="bg-secondary hover:bg-opacity-90 text-white px-4 py-2 rounded-full font-medium transition-colors">
                  开始测试
                </button>
              </div>
            </div>
          </div>
          
          <div class="bg-white rounded-xl overflow-hidden shadow-md card-hover">
            <div class="h-4 bg-green-600"></div>
            <div class="p-6">
              <div class="flex items-center mb-4">
                <div class="w-12 h-12 bg-green-100 rounded-full flex items-center justify-center mr-3">
                  <i class="fa fa-bar-chart text-green-600 text-xl"></i>
                </div>
                <h3 class="font-bold text-xl">学习报告</h3>
              </div>
              <p class="text-gray-600 mb-6">生成详细的学习报告，分析学习进度和记忆效果。</p>
              <div class="flex justify-between items-center">
                <span class="text-green-600 font-medium">最近更新: 今天</span>
                <button class="bg-green-600 hover:bg-opacity-90 text-white px-4 py-2 rounded-full font-medium transition-colors">
                  查看报告
                </button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 关于我们 -->
    <section id="about" class="py-16 bg-white">
      <div class="container mx-auto px-4">
        <div class="text-center mb-12">
          <h2 class="text-3xl md:text-4xl font-bold mb-4">关于我们</h2>
          <p class="text-gray-600 max-w-2xl mx-auto">我们致力于提供最科学、最有效的英语单词学习方法</p>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-2 gap-10 items-center">
          <div>
            <h3 class="font-bold text-2xl mb-4">我们的使命</h3>
            <p class="text-gray-600 mb-6">
              WordMaster 致力于为不同年龄段的学习者提供科学、高效、有趣的英语单词学习平台。我们相信，通过结合先进的技术和教育心理学原理，可以让每个人都能轻松掌握英语单词。
            </p>
            <h3 class="font-bold text-2xl mb-4">我们的团队</h3>
            <p class="text-gray-600 mb-6">
              我们由教育专家、语言学家和技术团队组成，拥有丰富的教育和技术经验。我们的共同目标是打造一个让学习英语变得简单而有趣的平台。
            </p>
            <div class="flex space-x-4 mt-8">
              <a href="#" class="bg-primary hover:bg-opacity-90 text-white px-6 py-3 rounded-full font-medium transition-colors flex items-center">
                <i class="fa fa-weixin mr-2"></i> 关注我们
              </a>
              <a href="#" class="bg-white border border-primary text-primary hover:bg-primary/5 px-6 py-3 rounded-full font-medium transition-colors flex items-center">
                <i class="fa fa-envelope mr-2"></i> 联系我们
              </a>
            </div>
          </div>
          <div class="rounded-xl overflow-hidden shadow-lg">
            <img src="https://p9-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/code_assistant/e6894b3f21814edb8a3064fb2c3d5b8c~tplv-a9rns2rl98-image.image?rk3s=8e244e95&amp;rrcfp=2609e108&amp;x-expires=1753364149&amp;x-signature=sg61vm2cdH8o7XDjneeD4iR9Pj4%3D" alt="我们的团队" class="w-full h-auto">
          </div>
        </div>
      </div>
    </section>
  </main>

  <!-- 页脚 -->
  <footer class="bg-dark text-white py-12">
    <div class="container mx-auto px-4">
      <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
        <div>
          <div class="flex items-center space-x-2 mb-6">
            <i class="fa fa-graduation-cap text-2xl"></i>
            <span class="text-xl font-bold">WordMaster</span>
          </div>
          <p class="text-gray-400 mb-6">
            智能匹配15个学龄段的单词记忆学习平台，让英语学习更简单。
          </p>
          <div class="flex space-x-4">
            <a href="#" class="text-gray-400 hover:text-white transition-colors">
              <i class="fa fa-weibo text-xl"></i>
            </a>
            <a href="#" class="text-gray-400 hover:text-white transition-colors">
              <i class="fa fa-weixin text-xl"></i>
            </a>
            <a href="#" class="text-gray-400 hover:text-white transition-colors">
              <i class="fa fa-instagram text-xl"></i>
            </a>
            <a href="#" class="text-gray-400 hover:text-white transition-colors">
              <i class="fa fa-youtube-play text-xl"></i>
            </a>
          </div>
        </div>
        
        <div>
          <h4 class="font-bold text-lg mb-4">学习资源</h4>
          <ul class="space-y-2">
            <li><a href="#" class="text-gray-400 hover:text-white transition-colors">英标学习</a></li>
            <li><a href="#" class="text-gray-400 hover:text-white transition-colors">单词记忆</a></li>
            <li><a href="#" class="text-gray-400 hover:text-white transition-colors">听力练习</a></li>
            <li><a href="#" class="text-gray-400 hover:text-white transition-colors">阅读理解</a></li>
            <li><a href="#" class="text-gray-400 hover:text-white transition-colors">写作练习</a></li>
            <li><a href="#" class="text-gray-400 hover:text-white transition-colors">语法提升</a></li>
            <li><a href="#" class="text-gray-400 hover:text-white transition-colors">口语练习</a></li>
          </ul>
        </div>
        
        <div>
          <h4 class="font-bold text-lg mb-4">关于我们</h4>
          <ul class="space-y-2">
            <li><a href="#" class="text-gray-400 hover:text-white transition-colors">公司简介</a></li>
            <li><a href="#" class="text-gray-400 hover:text-white transition-colors">团队介绍</a></li>
            <li><a href="#" class="text-gray-400 hover:text-white transition-colors">加入我们</a></li>
            <li><a href="#" class="text-gray-400 hover:text-white transition-colors">联系方式</a></li>
            <li><a href="#" class="text-gray-400 hover:text-white transition-colors">常见问题</a></li>
          </ul>
        </div>
        
        <div>
          <h4 class="font-bold text-lg mb-4">联系我们</h4>
          <ul class="space-y-2">
            <li class="flex items-center">
              <i class="fa fa-map-marker text-gray-400 mr-2"></i>
              <span class="text-gray-400">上海市宝山区</span>
            </li>
            <li class="flex items-center">
              <i class="fa fa-phone text-gray-400 mr-2"></i>
              <span class="text-gray-400">123-456-7890</span>
            </li>
            <li class="flex items-center">
              <i class="fa fa-envelope text-gray-400 mr-2"></i>
              <span class="text-gray-400">contact@wordmaster.com</span>
            </li>
          </ul>
          <div class="mt-6">
            <h5 class="font-medium mb-2">订阅我们的更新</h5>
            <div class="flex">
              <input type="email" placeholder="您的邮箱地址" class="px-4 py-2 rounded-l-full focus:outline-none text-dark flex-1">
              <button class="bg-secondary hover:bg-opacity-90 text-white px-4 py-2 rounded-r-full transition-colors">
                订阅
              </button>
            </div>
          </div>
        </div>
      </div>
      
      <div class="border-t border-gray-800 mt-12 pt-8 text-center">
        <p class="text-gray-400">© 2025 WordMaster. 保留所有权利。</p>
      </div>
    </div>
  </footer>

  <!-- JavaScript -->
  <script>
    // 导航栏滚动效果
    const navbar = document.getElementById('navbar');
    window.addEventListener('scroll', () => {
      if (window.scrollY > 50) {
        navbar.classList.add('bg-white', 'shadow-md');
        navbar.classList.remove('gradient-bg');
        // 修改导航链接颜色
        const navLinks = navbar.querySelectorAll('nav a');
        navLinks.forEach(link => {
          link.classList.remove('text-white');
          link.classList.add('text-dark');
        });
        // 修改按钮样式
        const loginBtn = navbar.querySelector('nav button:first-of-type');
        const registerBtn = navbar.querySelector('nav button:nth-of-type(2)');
        loginBtn.classList.remove('bg-white', 'text-primary');
        loginBtn.classList.add('bg-primary', 'text-white');
        registerBtn.classList.remove('bg-secondary', 'text-white');
        registerBtn.classList.add('bg-primary', 'text-white');
      } else {
        navbar.classList.remove('bg-white', 'shadow-md');
        navbar.classList.add('gradient-bg');
        // 恢复导航链接颜色
        const navLinks = navbar.querySelectorAll('nav a');
        navLinks.forEach(link => {
          link.classList.add('text-white');
          link.classList.remove('text-dark');
        });
        // 恢复按钮样式
        const loginBtn = navbar.querySelector('nav button:first-of-type');
        const registerBtn = navbar.querySelector('nav button:nth-of-type(2)');
        loginBtn.classList.add('bg-white', 'text-primary');
        loginBtn.classList.remove('bg-primary', 'text-white');
        registerBtn.classList.add('bg-secondary', 'text-white');
        registerBtn.classList.remove('bg-primary', 'text-white');
      }
    });

    // 移动端菜单切换
    const menuToggle = document.getElementById('menu-toggle');
    const mobileMenu = document.getElementById('mobile-menu');
    menuToggle.addEventListener('click', () => {
      mobileMenu.classList.toggle('hidden');
    });

    // 学习数据统计图表
    const ctx = document.getElementById('learningChart').getContext('2d');
    const learningChart = new Chart(ctx, {
      type: 'line',
      data: {
        labels: ['周一', '周二', '周三', '周四', '周五', '周六', '周日'],
        datasets: [
          {
            label: '学习时长(分钟)',
            data: [45, 59, 38, 47, 60, 75, 65],
            borderColor: '#165DFF',
            backgroundColor: 'rgba(22, 93, 255, 0.1)',
            tension: 0.4,
            fill: true
          },
          {
            label: '新学单词',
            data: [25, 30, 18, 22, 28, 35, 32],
            borderColor: '#FF7D00',
            backgroundColor: 'rgba(255, 125, 0, 0.1)',
            tension: 0.4,
            fill: true
          }
        ]
      },
      options: {
        responsive: true,
        maintainAspectRatio: false,
        plugins: {
          legend: {
            position: 'top',
          },
          tooltip: {
            mode: 'index',
            intersect: false
          }
        },
        scales: {
          y: {
            beginAtZero: true
          }
        }
      }
    });

    // 平滑滚动
    document.querySelectorAll('a[href^="#"]').forEach(anchor => {
      anchor.addEventListener('click', function (e) {
        e.preventDefault();
        
        const targetId = this.getAttribute('href');
        const targetElement = document.querySelector(targetId);
        
        if (targetElement) {
          window.scrollTo({
            top: targetElement.offsetTop - 80,
            behavior: 'smooth'
          });
          
          // 关闭移动端菜单
          if (!mobileMenu.classList.contains('hidden')) {
            mobileMenu.classList.add('hidden');
          }
        }
      });
    });
  </script>

</body></html>

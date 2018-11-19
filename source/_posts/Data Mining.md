---
title: Data Mining
date: 2018-11-20 06:19:39
tags:
---

<!doctype html>



  


<html class="theme-next muse use-motion" lang="en">
<head>
  <!-- hexo-inject:begin --><!-- hexo-inject:end --><meta charset="UTF-8"/>
<meta http-equiv="X-UA-Compatible" content="IE=edge" />
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1"/>



<meta http-equiv="Cache-Control" content="no-transform" />
<meta http-equiv="Cache-Control" content="no-siteapp" />












  
  
  <link href="/lib/fancybox/source/jquery.fancybox.css?v=2.1.5" rel="stylesheet" type="text/css" />




  
  
  
  

  
    
    
  

  

  

  

  

  
    
    
    <link href="//fonts.googleapis.com/css?family=Lato:300,300italic,400,400italic,700,700italic&subset=latin,latin-ext" rel="stylesheet" type="text/css">
  






<link href="/lib/font-awesome/css/font-awesome.min.css?v=4.6.2" rel="stylesheet" type="text/css" />

<link href="/css/main.css?v=5.1.0" rel="stylesheet" type="text/css" />


  <meta name="keywords" content="data mining," />








  <link rel="shortcut icon" type="image/x-icon" href="/favicon.ico?v=5.1.0" />






<meta name="description" content="Data Object And Attributeattribute : dimension, feature, variable
nominal attribute : hair_color 、 marital_status
binary attribute : bool
ordinal attribute : ranking
numeric attribute :
Statistical De">
<meta property="og:type" content="article">
<meta property="og:title" content="What is data?">
<meta property="og:url" content="http://yoursite.com/2017/03/06/Data Mining/index.html">
<meta property="og:site_name" content="Nocis' workshop">
<meta property="og:description" content="Data Object And Attributeattribute : dimension, feature, variable
nominal attribute : hair_color 、 marital_status
binary attribute : bool
ordinal attribute : ranking
numeric attribute :
Statistical De">
<meta property="og:updated_time" content="2017-03-06T13:08:01.610Z">
<meta name="twitter:card" content="summary">
<meta name="twitter:title" content="What is data?">
<meta name="twitter:description" content="Data Object And Attributeattribute : dimension, feature, variable
nominal attribute : hair_color 、 marital_status
binary attribute : bool
ordinal attribute : ranking
numeric attribute :
Statistical De">



<script type="text/javascript" id="hexo.configurations">
  var NexT = window.NexT || {};
  var CONFIG = {
    root: '/',
    scheme: 'Muse',
    sidebar: {"position":"left","display":"post"},
    fancybox: true,
    motion: true,
    duoshuo: {
      userId: '0',
      author: 'Author'
    },
    algolia: {
      applicationID: '',
      apiKey: '',
      indexName: '',
      hits: {"per_page":10},
      labels: {"input_placeholder":"Search for Posts","hits_empty":"We didn't find any results for the search: ${query}","hits_stats":"${hits} results found in ${time} ms"}
    }
  };
</script>



  <link rel="canonical" href="http://yoursite.com/2017/03/06/Data Mining/"/>





  <title> What is data? | Nocis' workshop </title><!-- hexo-inject:begin --><!-- hexo-inject:end -->
</head>

<body itemscope itemtype="http://schema.org/WebPage" lang="en">

  










  
  
    
  

  <!-- hexo-inject:begin --><!-- hexo-inject:end --><div class="container one-collumn sidebar-position-left page-post-detail ">
    <div class="headband"></div>

    <header id="header" class="header" itemscope itemtype="http://schema.org/WPHeader">
      <div class="header-inner"><div class="site-meta ">
  

  <div class="custom-logo-site-title">
    <a href="/"  class="brand" rel="start">
      <span class="logo-line-before"><i></i></span>
      <span class="site-title">Nocis' workshop</span>
      <span class="logo-line-after"><i></i></span>
    </a>
  </div>
    
      <p class="site-subtitle"></p>
    
</div>

<div class="site-nav-toggle">
  <button>
    <span class="btn-bar"></span>
    <span class="btn-bar"></span>
    <span class="btn-bar"></span>
  </button>
</div>

<nav class="site-nav">
  

  
    <ul id="menu" class="menu">
      
        
        <li class="menu-item menu-item-home">
          <a href="/" rel="section">
            
              <i class="menu-item-icon fa fa-fw fa-home"></i> <br />
            
            Home
          </a>
        </li>
      
        
        <li class="menu-item menu-item-categories">
          <a href="/categories" rel="section">
            
              <i class="menu-item-icon fa fa-fw fa-th"></i> <br />
            
            Categories
          </a>
        </li>
      
        
        <li class="menu-item menu-item-archives">
          <a href="/archives" rel="section">
            
              <i class="menu-item-icon fa fa-fw fa-archive"></i> <br />
            
            Archives
          </a>
        </li>
      
        
        <li class="menu-item menu-item-tags">
          <a href="/tags" rel="section">
            
              <i class="menu-item-icon fa fa-fw fa-tags"></i> <br />
            
            Tags
          </a>
        </li>
      

      
    </ul>
  

  
</nav>



 </div>
    </header>

    <main id="main" class="main">
      <div class="main-inner">
        <div class="content-wrap">
          <div id="content" class="content">
            

  <div id="posts" class="posts-expand">
    

  

  
  
  

  <article class="post post-type-normal " itemscope itemtype="http://schema.org/Article">
  <link itemprop="mainEntityOfPage" href="http://yoursite.com/2017/03/06/Data Mining/">

  <span style="display:none" itemprop="author" itemscope itemtype="http://schema.org/Person">
    <meta itemprop="name" content="Nocis">
    <meta itemprop="description" content="">
    <meta itemprop="image" content="/images/avatar.gif">
  </span>

  <span style="display:none" itemprop="publisher" itemscope itemtype="http://schema.org/Organization">
    <meta itemprop="name" content="Nocis' workshop">
    <span style="display:none" itemprop="logo" itemscope itemtype="http://schema.org/ImageObject">
      <img style="display:none;" itemprop="url image" alt="Nocis' workshop" src="">
    </span>
  </span>

    
      <header class="post-header">

        
        
          <h1 class="post-title" itemprop="name headline">
            
            
              
                What is data?
              
            
          </h1>
        

        <div class="post-meta">
          <span class="post-time">
            
              <span class="post-meta-item-icon">
                <i class="fa fa-calendar-o"></i>
              </span>
              
                <span class="post-meta-item-text">Posted on</span>
              
              <time title="Post created" itemprop="dateCreated datePublished" datetime="2017-03-06T11:45:41+08:00">
                2017-03-06
              </time>
            

            

            
          </span>

          
            <span class="post-category" >
            
              <span class="post-meta-divider">|</span>
            
              <span class="post-meta-item-icon">
                <i class="fa fa-folder-o"></i>
              </span>
              
                <span class="post-meta-item-text">In</span>
              
              
                <span itemprop="about" itemscope itemtype="http://schema.org/Thing">
                  <a href="/categories/data-mining/" itemprop="url" rel="index">
                    <span itemprop="name">data mining</span>
                  </a>
                </span>

                
                
              
            </span>
          

          
            
          

          

          
          

          

          

        </div>
      </header>
    


    <div class="post-body" itemprop="articleBody">

      
      

      
        <h2 id="Data-Object-And-Attribute"><a href="#Data-Object-And-Attribute" class="headerlink" title="Data Object And Attribute"></a>Data Object And Attribute</h2><p><strong>attribute :</strong> dimension, feature, variable</p>
<p><strong>nominal attribute :</strong> hair_color 、 marital_status</p>
<p><strong>binary attribute :</strong> bool</p>
<p><strong>ordinal attribute :</strong> ranking</p>
<p><strong>numeric attribute :</strong></p>
<h2 id="Statistical-Description"><a href="#Statistical-Description" class="headerlink" title="Statistical Description"></a>Statistical Description</h2><p><strong>measure of central tendency :</strong> mean, median, mode, midrange</p>
<p><strong>measure of Data dissemination :</strong> range, quantile, IQR, boxplot, variance, standard deviation</p>
<h2 id="Data-Matrix-And-Dissimilarity-Matrix"><a href="#Data-Matrix-And-Dissimilarity-Matrix" class="headerlink" title="Data Matrix And Dissimilarity Matrix"></a>Data Matrix And Dissimilarity Matrix</h2><p><strong>data matrix :</strong><br>$$<br>\left[<br>\begin{matrix}<br>x_{11}&amp;\cdots&amp;x_{1f}&amp;\cdots&amp;x_{1p}\\<br>\cdots&amp;\cdots&amp;\cdots&amp;\cdots&amp;\cdots\\<br>x_{i1}&amp;\cdots&amp;x_{if}&amp;\cdots&amp;x_{ip}\\<br>\cdots&amp;\cdots&amp;\cdots&amp;\cdots&amp;\cdots\\<br>x_{p1}&amp;\cdots&amp;x_{pf}&amp;\cdots&amp;x_{pp}\\<br>\end{matrix}<br>\right]\\<br>(n objs \times p attributes)<br>$$</p>
<p><strong>Dissimilarity Matrix :</strong><br>$$<br>\left[<br>\begin{matrix}<br>0\\<br>d(2,1)&amp;0\\<br>d(3,1)&amp;d(3,2)&amp;0\\<br>\vdots&amp;\vdots&amp;\vdots\\<br>d(n,1)&amp;d(n,2)&amp;\cdots&amp;\cdots&amp;0\\<br>\end{matrix}<br>\right]\\<br>(n objs \times n objs)<br>$$</p>
<ol>
<li><p><strong>nominal attribute </strong></p>
<p> <strong>mismatch rate :</strong> $d(i,j) = \frac{p - m}{p}$</p>
<p> p:Total attribute</p>
<p> m:match attribute</p>
</li>
</ol>
<ol>
<li><p><strong>binary attribute </strong></p>
<p> <strong>mismatch rate :</strong> $d(i,j) = \frac{r + s}{q + r + s + t}$</p>
<p> q:the num of both i’s and j’s attribute whose value equals 1</p>
<p> t:the num of both i’s and j’s attribute whose value equals 0</p>
<p> s:the num of attributes whose value equals 0 for i and 1 for j</p>
<p> r:the num of attributes whose value equals 1 for i and 0 for j</p>
<p> ignore t: $d(i,j) = \frac{r + s}{q + r + s}$</p>
<p> <strong>Jaccard coefficient :</strong> $d(i,j) = \frac{q}{q + r + s}$</p>
</li>
<li><p><strong>numeric attribute </strong></p>
<p> <strong>Euclid  distance (2-norm):</strong> $d(i,j) = \sqrt{(x_{i1}-x_{j1})^{2}+(x_{i2}-x_{j2})^{2}+\cdots+(x_{ip}-x_{jp})^{2}}$</p>
<p> <strong>Manhattan  distance (1-norm):</strong> $d(i,j) = |x_{i1}-x_{j1}|+|x_{i2}-x_{j2}|+\cdots+|x_{ip}-x_{jp}|$</p>
<p> Euclid and Manhattan’s nature:</p>
<ol>
<li>Non-negative $d(i,j) \ge 0$</li>
<li>$d(i,i) = 0$</li>
<li>Symmetry $d(i,j) = d(j,i)$</li>
<li><p>$d(i,j) \le d(i,k) + d(k,j)$</p>
<p><strong>Minkowski  distance (p-norm):</strong> $d(i,j) = \sqrt[h]{|x_{i1}-x_{j1}|^{h}+|x_{i2}-x_{j2}|^{h}+\cdots+|x_{ip}-x_{jp}|^{h}}$</p>
<p><strong>Chebyshev  distance ($\infty$-norm):</strong> the maximum of each attribute’s distance $$d(i,j) = \lim_{h \to 0} \left( \sum_{f=1}^p |x_{if}-x_{jf}|^{h}\right)^{\frac{1}{h}} = \max_{f}^{p}|x_{if}-x_{jf}|$$</p>
</li>
</ol>
</li>
<li><p><strong>ordinal attribute </strong></p>
<p> mapping [0.0, 1.0]</p>
</li>
</ol>
<ol>
<li><p><strong>mixed type</strong></p>
<p> weighted mean</p>
</li>
<li><p><strong> cosine similarity</strong></p>
<p> $$<br> sim(x,y) = \frac{x \cdot y}{||x|| ||y||}\\<br> Tanimoto Distance: sim(x,y) = \frac{x \cdot y}{x \cdot x + y \cdot y - x \cdot y}\\<br> ||x||:Euclid  distance<br> $$</p>
</li>
</ol>

      
    </div>

    <div>
      
        

      
    </div>

    <div>
      
        

      
    </div>


    <footer class="post-footer">
      
        <div class="post-tags">
          
            <a href="/tags/data-mining/" rel="tag"># data mining</a>
          
        </div>
      

      
        <div class="post-nav">
          <div class="post-nav-next post-nav-item">
            
              <a href="/2017/02/06/我的博客/" rel="next" title="我的博客">
                <i class="fa fa-chevron-left"></i> 我的博客
              </a>
            
          </div>

          <span class="post-nav-divider"></span>

          <div class="post-nav-prev post-nav-item">
            
              <a href="/2017/03/06/TOEFL-writing-01/" rel="prev" title="TOEFL-writing-01-independent-Educatiuon01">
                TOEFL-writing-01-independent-Educatiuon01 <i class="fa fa-chevron-right"></i>
              </a>
            
          </div>
        </div>
      

      
      
    </footer>
  </article>



    <div class="post-spread">
      
    </div>
  </div>

          
          </div>
          


          
  <div class="comments" id="comments">
    
  </div>


        </div>
        
          
  
  <div class="sidebar-toggle">
    <div class="sidebar-toggle-line-wrap">
      <span class="sidebar-toggle-line sidebar-toggle-line-first"></span>
      <span class="sidebar-toggle-line sidebar-toggle-line-middle"></span>
      <span class="sidebar-toggle-line sidebar-toggle-line-last"></span>
    </div>
  </div>

  <aside id="sidebar" class="sidebar">
    <div class="sidebar-inner">

      

      
        <ul class="sidebar-nav motion-element">
          <li class="sidebar-nav-toc sidebar-nav-active" data-target="post-toc-wrap" >
            Table of Contents
          </li>
          <li class="sidebar-nav-overview" data-target="site-overview">
            Overview
          </li>
        </ul>
      

      <section class="site-overview sidebar-panel">
        <div class="site-author motion-element" itemprop="author" itemscope itemtype="http://schema.org/Person">
          <img class="site-author-image" itemprop="image"
               src="/images/avatar.gif"
               alt="Nocis" />
          <p class="site-author-name" itemprop="name">Nocis</p>
          <p class="site-description motion-element" itemprop="description"></p>
        </div>
        <nav class="site-state motion-element">
        
          
            <div class="site-state-item site-state-posts">
              <a href="/archives">
                <span class="site-state-item-count">5</span>
                <span class="site-state-item-name">posts</span>
              </a>
            </div>
          

          
            <div class="site-state-item site-state-categories">
              <a href="/categories">
                <span class="site-state-item-count">3</span>
                <span class="site-state-item-name">categories</span>
              </a>
            </div>
          

          
            <div class="site-state-item site-state-tags">
              <a href="/tags">
                <span class="site-state-item-count">3</span>
                <span class="site-state-item-name">tags</span>
              </a>
            </div>
          

        </nav>

        

        <div class="links-of-author motion-element">
          
        </div>

        
        

        
        

        


      </section>

      
      <!--noindex-->
        <section class="post-toc-wrap motion-element sidebar-panel sidebar-panel-active">
          <div class="post-toc">

            
              
            

            
              <div class="post-toc-content"><ol class="nav"><li class="nav-item nav-level-2"><a class="nav-link" href="#Data-Object-And-Attribute"><span class="nav-number">1.</span> <span class="nav-text">Data Object And Attribute</span></a></li><li class="nav-item nav-level-2"><a class="nav-link" href="#Statistical-Description"><span class="nav-number">2.</span> <span class="nav-text">Statistical Description</span></a></li><li class="nav-item nav-level-2"><a class="nav-link" href="#Data-Matrix-And-Dissimilarity-Matrix"><span class="nav-number">3.</span> <span class="nav-text">Data Matrix And Dissimilarity Matrix</span></a></li></ol></div>
            

          </div>
        </section>
      <!--/noindex-->
      

    </div>
  </aside>


        
      </div>
    </main>

    <footer id="footer" class="footer">
      <div class="footer-inner">
        <div class="copyright" >
  
  &copy; 
  <span itemprop="copyrightYear">2017</span>
  <span class="with-love">
    <i class="fa fa-heart"></i>
  </span>
  <span class="author" itemprop="copyrightHolder">Nocis</span>
</div>


<div class="powered-by">
  Powered by <a class="theme-link" href="https://hexo.io">Hexo</a>
</div>

<div class="theme-info">
  Theme -
  <a class="theme-link" href="https://github.com/iissnan/hexo-theme-next">
    NexT.Muse
  </a>
</div>


        

        
      </div>
    </footer>

    <div class="back-to-top">
      <i class="fa fa-arrow-up"></i>
    </div>
  </div>

  

<script type="text/javascript">
  if (Object.prototype.toString.call(window.Promise) !== '[object Function]') {
    window.Promise = null;
  }
</script>









  




  
  <script type="text/javascript" src="/lib/jquery/index.js?v=2.1.3"></script>

  
  <script type="text/javascript" src="/lib/fastclick/lib/fastclick.min.js?v=1.0.6"></script>

  
  <script type="text/javascript" src="/lib/jquery_lazyload/jquery.lazyload.js?v=1.9.7"></script>

  
  <script type="text/javascript" src="/lib/velocity/velocity.min.js?v=1.2.1"></script>

  
  <script type="text/javascript" src="/lib/velocity/velocity.ui.min.js?v=1.2.1"></script>

  
  <script type="text/javascript" src="/lib/fancybox/source/jquery.fancybox.pack.js?v=2.1.5"></script>


  


  <script type="text/javascript" src="/js/src/utils.js?v=5.1.0"></script>

  <script type="text/javascript" src="/js/src/motion.js?v=5.1.0"></script>



  
  

  
  <script type="text/javascript" src="/js/src/scrollspy.js?v=5.1.0"></script>
<script type="text/javascript" src="/js/src/post-details.js?v=5.1.0"></script>



  


  <script type="text/javascript" src="/js/src/bootstrap.js?v=5.1.0"></script>



  



  




	





  





  

  
      <!-- UY BEGIN -->
      <script type="text/javascript" src="http://v2.uyan.cc/code/uyan.js?uid="></script>
      <!-- UY END --><!-- hexo-inject:begin --><!-- Begin: Injected MathJax -->
<script type="text/x-mathjax-config">
  MathJax.Hub.Config({"tex2jax":{"inlineMath":[["$","$"],["\\(","\\)"]],"skipTags":["script","noscript","style","textarea","pre","code"],"processEscapes":true},"TeX":{"equationNumbers":{"autoNumber":"AMS"}}});
</script>

<script type="text/x-mathjax-config">
  MathJax.Hub.Queue(function() {
    var all = MathJax.Hub.getAllJax(), i;
    for(i=0; i < all.length; i += 1) {
      all[i].SourceElement().parentNode.className += ' has-jax';
    }
  });
</script>

<script type="text/javascript" src="//cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>
<!-- End: Injected MathJax -->
<!-- hexo-inject:end -->
  




  
  

  

  

  

  


</body>
</html>

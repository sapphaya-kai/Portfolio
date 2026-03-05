<!doctype html>
<html lang="en" class="h-full">
 <head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Portfolio kai</title>
  <script src="https://cdn.tailwindcss.com/3.4.17"></script>
  <script src="/_sdk/element_sdk.js"></script>
  <script src="/_sdk/data_sdk.js"></script>
  <link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&amp;family=Outfit:wght@300;400;600;700&amp;display=swap" rel="stylesheet">
  <style>
    * { box-sizing: border-box; }
    html, body { height: 100%; }
    
    .font-outfit { font-family: 'Outfit', sans-serif; }
    .font-mono { font-family: 'Space Mono', monospace; }
    
    .app-wrapper {
      width: 100%;
      height: 100%;
      overflow-y: auto;
      overflow-x: hidden;
      background: linear-gradient(135deg, #ffffff 0%, #f8f7ff 50%, #fff5f8 100%);
    }
    
    /* Navigation */
    nav {
      position: sticky;
      top: 0;
      z-index: 50;
      backdrop-filter: blur(10px);
      background: rgba(255, 255, 255, 0.85);
      border-bottom: 1px solid rgba(200, 100, 200, 0.1);
    }
    
    nav a {
      transition: all 0.3s ease;
      position: relative;
      text-decoration: none;
    }
    
    nav a::after {
      content: '';
      position: absolute;
      bottom: -2px;
      left: 0;
      width: 0;
      height: 2px;
      background: linear-gradient(90deg, #ff006e, #8338ec);
      transition: width 0.3s ease;
    }
    
    nav a:hover::after {
      width: 100%;
    }
    
    /* Hero */
    .hero-gradient {
      background: linear-gradient(135deg, #ff006e 0%, #8338ec 50%, #3a86ff 100%);
    }
    
    .hero-text {
      animation: slideInUp 0.8s ease-out;
    }
    
    @keyframes slideInUp {
      from {
        opacity: 0;
        transform: translateY(30px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }
    
    /* Gallery */
    .gallery-item {
      border-radius: 12px;
      overflow: hidden;
      aspect-ratio: 1;
      background: linear-gradient(135deg, #ff006e, #8338ec);
      cursor: pointer;
      transition: all 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
      position: relative;
    }
    
    .gallery-item:hover {
      transform: translateY(-8px);
    }
    
    .gallery-item::before {
      content: '';
      position: absolute;
      inset: 0;
      background: rgba(255, 255, 255, 0.1);
      opacity: 0;
      transition: opacity 0.3s ease;
    }
    
    .gallery-item:hover::before {
      opacity: 1;
    }
    
    /* Form */
    .form-input {
      background: rgba(255, 255, 255, 0.7);
      border: 2px solid rgba(200, 100, 200, 0.2);
      border-radius: 8px;
      padding: 12px 16px;
      transition: all 0.3s ease;
      font-family: 'Outfit', sans-serif;
    }
    
    .form-input:focus {
      outline: none;
      background: rgba(255, 255, 255, 0.95);
      border-color: #ff006e;
      box-shadow: 0 0 0 3px rgba(255, 0, 110, 0.1);
    }
    
    .submit-btn {
      background: linear-gradient(135deg, #ff006e, #8338ec);
      color: white;
      border: none;
      padding: 12px 32px;
      border-radius: 8px;
      font-weight: 600;
      cursor: pointer;
      transition: all 0.3s ease;
    }
    
    .submit-btn:hover {
      transform: translateY(-2px);
      box-shadow: 0 12px 24px rgba(255, 0, 110, 0.3);
    }
    
    .submit-btn:disabled {
      opacity: 0.6;
      cursor: not-allowed;
      transform: none;
    }
    
    /* Toast notification */
    .toast {
      position: fixed;
      bottom: 20px;
      right: 20px;
      padding: 16px 24px;
      border-radius: 8px;
      background: #333;
      color: white;
      animation: slideIn 0.3s ease-out;
      z-index: 100;
    }
    
    @keyframes slideIn {
      from {
        opacity: 0;
        transform: translateX(100px);
      }
      to {
        opacity: 1;
        transform: translateX(0);
      }
    }
    
    .toast.success {
      background: #10b981;
    }
    
    .toast.error {
      background: #ef4444;
    }
    
    /* Social icons */
    .social-icon {
      width: 44px;
      height: 44px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      background: linear-gradient(135deg, #ff006e, #8338ec);
      color: white;
      text-decoration: none;
      transition: all 0.3s ease;
    }
    
    .social-icon:hover {
      transform: scale(1.1) rotate(5deg);
    }
    
    /* Scroll styles */
    ::-webkit-scrollbar {
      width: 8px;
    }
    
    ::-webkit-scrollbar-track {
      background: transparent;
    }
    
    ::-webkit-scrollbar-thumb {
      background: linear-gradient(180deg, #ff006e, #8338ec);
      border-radius: 4px;
    }
  </style>
  <style>body { box-sizing: border-box; }</style>
 </head>
 <body class="h-full m-0 font-outfit">
  <div class="app-wrapper"><!-- Navigation -->
   <nav class="px-6 md:px-12 py-4">
    <div class="max-w-7xl mx-auto flex justify-between items-center">
     <div class="font-mono font-bold text-lg" style="background: linear-gradient(135deg, #ff006e, #8338ec); -webkit-background-clip: text; -webkit-text-fill-color: transparent;"><span id="nav-name">Portfolio</span>
     </div>
     <div class="flex gap-8"><a href="#work" class="text-sm font-medium">Work</a> <a href="#about" class="text-sm font-medium">About</a> <a href="#contact" class="text-sm font-medium">Contact</a>
     </div>
    </div>
   </nav><!-- Hero Section -->
   <section class="hero-gradient text-white py-20 md:py-32 px-6 md:px-12">
    <div class="max-w-7xl mx-auto">
     <div class="hero-text">
      <h1 id="hero-title" class="font-mono text-5xl md:text-7xl font-bold mb-4">ยินดีต้อนรับ</h1>
      <p id="hero-bio" class="text-lg md:text-xl opacity-90 max-w-2xl mb-8">"Commitment to excellence through purposeful work."<br>มุ่งมั่นสู่ความเป็นเลิศ ผ่านการทำงานอย่างมีจุดมุ่งหมาย</p><a href="#work" class="inline-block bg-white text-purple-600 font-semibold px-8 py-3 rounded-8 hover:shadow-lg transition-all">ผลงานของฉัน</a>
     </div>
    </div>
   </section><!-- Gallery Section -->
   <section id="work" class="py-20 md:py-32 px-6 md:px-12">
    <div class="max-w-7xl mx-auto">
     <h2 class="font-mono text-4xl md:text-5xl font-bold mb-4" style="background: linear-gradient(135deg, #ff006e, #8338ec); -webkit-background-clip: text; -webkit-text-fill-color: transparent;">งานของฉัน</h2>
     <p class="text-gray-600 mb-12 text-lg">ผลงานและโครงการงานต่างๆของฉัน</p>
     <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
      <div class="gallery-item" onclick="showProject(1)">
       <div class="w-full h-full flex items-center justify-center text-white text-6xl">
        🎨
       </div>
      </div>
      <div class="gallery-item" onclick="showProject(2)" style="background: linear-gradient(135deg, #3a86ff, #8338ec);">
       <div class="w-full h-full flex items-center justify-center text-white text-6xl">
        🌐
       </div>
      </div>
      <div class="gallery-item" onclick="showProject(3)" style="background: linear-gradient(135deg, #ff006e, #ffbe0b);">
       <div class="w-full h-full flex items-center justify-center text-white text-6xl">
        📱
       </div>
      </div>
      <div class="gallery-item" onclick="showProject(4)" style="background: linear-gradient(135deg, #8338ec, #ff006e);">
       <div class="w-full h-full flex items-center justify-center text-white text-6xl">
        ✨
       </div>
      </div>
      <div class="gallery-item" onclick="showProject(5)" style="background: linear-gradient(135deg, #3a86ff, #ff006e);">
       <div class="w-full h-full flex items-center justify-center text-white text-6xl">
        🎬
       </div>
      </div>
      <div class="gallery-item" onclick="showProject(6)" style="background: linear-gradient(135deg, #ffbe0b, #8338ec);">
       <div class="w-full h-full flex items-center justify-center text-white text-6xl">
        🚀
       </div>
      </div>
     </div>
    </div>
   </section><!-- About Section -->
   <section id="about" class="py-20 md:py-32 px-6 md:px-12" style="background: rgba(243, 232, 255, 0.5);">
    <div class="max-w-7xl mx-auto">
     <h2 class="font-mono text-4xl md:text-5xl font-bold mb-12" style="background: linear-gradient(135deg, #ff006e, #8338ec); -webkit-background-clip: text; -webkit-text-fill-color: transparent;">About Me</h2>
     <div class="grid md:grid-cols-2 gap-12">
      <div>
       <p class="text-lg text-gray-700 mb-6 leading-relaxed">I'm a creative professional passionate about designing beautiful, functional digital experiences. With expertise in design, web development, and user experience, I help brands tell their stories through compelling visuals and intuitive interfaces.</p>
       <p class="text-lg text-gray-700 leading-relaxed">When I'm not designing, you can find me exploring new design trends, collaborating with creative teams, or working on passion projects that push creative boundaries.</p>
      </div>
      <div class="grid grid-cols-2 gap-6">
       <div class="bg-white p-6 rounded-12 border border-purple-100">
        <div class="text-4xl font-bold text-purple-600 mb-2">
         50+
        </div>
        <p class="text-gray-600">Projects Completed</p>
       </div>
       <div class="bg-white p-6 rounded-12 border border-pink-100">
        <div class="text-4xl font-bold text-pink-600 mb-2">
         30+
        </div>
        <p class="text-gray-600">Happy Clients</p>
       </div>
       <div class="bg-white p-6 rounded-12 border border-blue-100">
        <div class="text-4xl font-bold text-blue-600 mb-2">
         8+
        </div>
        <p class="text-gray-600">Years Experience</p>
       </div>
       <div class="bg-white p-6 rounded-12 border border-yellow-100">
        <div class="text-4xl font-bold text-yellow-600 mb-2">
         ∞
        </div>
        <p class="text-gray-600">Coffee Consumed</p>
       </div>
      </div>
     </div>
    </div>
   </section><!-- Contact Section -->
   <section id="contact" class="py-20 md:py-32 px-6 md:px-12">
    <div class="max-w-3xl mx-auto">
     <h2 class="font-mono text-4xl md:text-5xl font-bold mb-4 text-center" style="background: linear-gradient(135deg, #ff006e, #8338ec); -webkit-background-clip: text; -webkit-text-fill-color: transparent;">Let's Work Together</h2>
     <p class="text-center text-gray-600 mb-12 text-lg">Have a project in mind? Get in touch and let's create something amazing.</p><!-- Contact Form -->
     <form id="contact-form" class="space-y-4 mb-12">
      <div class="grid md:grid-cols-2 gap-4"><input type="text" id="form-name" class="form-input" placeholder="Your Name" required> <input type="email" id="form-email" class="form-input" placeholder="Your Email" required>
      </div><textarea id="form-message" class="form-input w-full h-32 resize-none" placeholder="Your Message" required></textarea> <button type="submit" class="submit-btn w-full" id="submit-btn">Send Message</button>
     </form><!-- Social Links -->
     <div class="text-center">
      <p class="text-gray-600 mb-6">Connect with me</p>
      <div class="flex justify-center gap-4"><a id="social-instagram" href="https://instagram.com" target="_blank" rel="noopener noreferrer" class="social-icon" title="Instagram">📷</a> <a id="social-twitter" href="https://twitter.com" target="_blank" rel="noopener noreferrer" class="social-icon" title="Twitter">𝕏</a> <a id="social-linkedin" href="https://linkedin.com" target="_blank" rel="noopener noreferrer" class="social-icon" title="LinkedIn">💼</a>
      </div>
     </div>
    </div>
   </section><!-- Footer -->
   <footer class="bg-gray-900 text-white py-8 px-6 md:px-12 text-center">
    <p class="opacity-60">© 2024 <span id="footer-name">Creative Portfolio</span>. All rights reserved.</p>
   </footer>
  </div>
  <script>
    // Default configuration
    const defaultConfig = {
      portfolio_name: "Alex Design",
      portfolio_title: "Creative Designer",
      portfolio_bio: "I create beautiful digital experiences through thoughtful design and innovative thinking.",
      social_instagram: "@alexdesign",
      social_twitter: "@alexdesign",
      social_linkedin: "linkedin.com/in/alexdesign",
      primary_color: "#ff006e",
      secondary_color: "#8338ec",
      text_color: "#333333",
      accent_color: "#f3e8ff"
    };

    let config = { ...defaultConfig };
    let contactData = [];

    // Data SDK Handler
    const dataHandler = {
      onDataChanged(data) {
        contactData = data;
      }
    };

    // Initialize Data SDK
    async function initDataSDK() {
      const result = await window.dataSdk.init(dataHandler);
      if (!result.isOk) {
        console.error('Failed to initialize data SDK');
      }
    }

    // Show toast notification
    function showToast(message, type = 'success') {
      const toast = document.createElement('div');
      toast.className = `toast ${type}`;
      toast.textContent = message;
      document.body.appendChild(toast);
      setTimeout(() => toast.remove(), 3000);
    }

    // Handle form submission
    document.getElementById('contact-form').addEventListener('submit', async (e) => {
      e.preventDefault();

      const name = document.getElementById('form-name').value;
      const email = document.getElementById('form-email').value;
      const message = document.getElementById('form-message').value;

      if (contactData.length >= 999) {
        showToast('Contact limit reached. Please try again later.', 'error');
        return;
      }

      const submitBtn = document.getElementById('submit-btn');
      submitBtn.disabled = true;
      submitBtn.textContent = 'Sending...';

      const result = await window.dataSdk.create({
        name,
        email,
        message,
        submittedAt: new Date().toISOString()
      });

      submitBtn.disabled = false;
      submitBtn.textContent = 'Send Message';

      if (result.isOk) {
        document.getElementById('contact-form').reset();
        showToast('Thanks for reaching out! I\'ll get back to you soon.', 'success');
      } else {
        showToast('Failed to send message. Please try again.', 'error');
      }
    });

    // Gallery interaction
    function showProject(id) {
      showToast(`Project ${id} clicked! (Demo mode)`, 'success');
    }

    // Element SDK Implementation
    async function onConfigChange(newConfig) {
      config = { ...config, ...newConfig };

      // Update text content
      const name = config.portfolio_name || defaultConfig.portfolio_name;
      document.getElementById('nav-name').textContent = name;
      document.getElementById('hero-title').textContent = config.portfolio_title || defaultConfig.portfolio_title;
      document.getElementById('hero-bio').textContent = config.portfolio_bio || defaultConfig.portfolio_bio;
      document.getElementById('footer-name').textContent = name;

      // Update social links
      const instagramHandle = config.social_instagram || defaultConfig.social_instagram;
      const twitterHandle = config.social_twitter || defaultConfig.social_twitter;
      const linkedinUrl = config.social_linkedin || defaultConfig.social_linkedin;

      const instagramUrl = instagramHandle.startsWith('http') ? instagramHandle : `https://instagram.com/${instagramHandle.replace('@', '')}`;
      const twitterUrl = twitterHandle.startsWith('http') ? twitterHandle : `https://twitter.com/${twitterHandle.replace('@', '')}`;
      const linkedinUrlFull = linkedinUrl.startsWith('http') ? linkedinUrl : `https://${linkedinUrl}`;

      document.getElementById('social-instagram').href = instagramUrl;
      document.getElementById('social-twitter').href = twitterUrl;
      document.getElementById('social-linkedin').href = linkedinUrlFull;
    }

    function mapToCapabilities(currentConfig) {
      return {
        recolorables: [
          {
            get: () => currentConfig.primary_color || defaultConfig.primary_color,
            set: (value) => { 
              config.primary_color = value; 
              window.elementSdk.setConfig({ primary_color: value }); 
            }
          },
          {
            get: () => currentConfig.secondary_color || defaultConfig.secondary_color,
            set: (value) => { 
              config.secondary_color = value; 
              window.elementSdk.setConfig({ secondary_color: value }); 
            }
          },
          {
            get: () => currentConfig.text_color || defaultConfig.text_color,
            set: (value) => { 
              config.text_color = value; 
              window.elementSdk.setConfig({ text_color: value }); 
            }
          },
          {
            get: () => currentConfig.accent_color || defaultConfig.accent_color,
            set: (value) => { 
              config.accent_color = value; 
              window.elementSdk.setConfig({ accent_color: value }); 
            }
          }
        ],
        borderables: [],
        fontEditable: undefined,
        fontSizeable: undefined
      };
    }

    function mapToEditPanelValues(currentConfig) {
      return new Map([
        ["portfolio_name", currentConfig.portfolio_name || defaultConfig.portfolio_name],
        ["portfolio_title", currentConfig.portfolio_title || defaultConfig.portfolio_title],
        ["portfolio_bio", currentConfig.portfolio_bio || defaultConfig.portfolio_bio],
        ["social_instagram", currentConfig.social_instagram || defaultConfig.social_instagram],
        ["social_twitter", currentConfig.social_twitter || defaultConfig.social_twitter],
        ["social_linkedin", currentConfig.social_linkedin || defaultConfig.social_linkedin]
      ]);
    }

    // Initialize SDKs
    if (window.elementSdk) {
      window.elementSdk.init({
        defaultConfig,
        onConfigChange,
        mapToCapabilities,
        mapToEditPanelValues
      });
    }

    initDataSDK();
  </script>
 <script>(function(){function c(){var b=a.contentDocument||a.contentWindow.document;if(b){var d=b.createElement('script');d.innerHTML="window.__CF$cv$params={r:'9d33b546133ad023',t:'MTc3MTk4NTg2NS4wMDAwMDA='};var a=document.createElement('script');a.nonce='';a.src='/cdn-cgi/challenge-platform/scripts/jsd/main.js';document.getElementsByTagName('head')[0].appendChild(a);";b.getElementsByTagName('head')[0].appendChild(d)}}if(document.body){var a=document.createElement('iframe');a.height=1;a.width=1;a.style.position='absolute';a.style.top=0;a.style.left=0;a.style.border='none';a.style.visibility='hidden';document.body.appendChild(a);if('loading'!==document.readyState)c();else if(window.addEventListener)document.addEventListener('DOMContentLoaded',c);else{var e=document.onreadystatechange||function(){};document.onreadystatechange=function(b){e(b);'loading'!==document.readyState&&(document.onreadystatechange=e,c())}}}})();</script></body>
</html>

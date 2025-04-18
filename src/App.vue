<template>  
  <div class="portfolio-container">  
    <div class="background" :style="{ backgroundImage: 'url(' + backgroundImage + ')' }"></div>  
    <div class="overlay">  
      <div class="avatar-container">  
        <img :src="avatarImage" alt="Avatar" class="avatar">  
      </div>  
      <div class="info-container">  
        <h1>{{ name }}</h1>  
        <p>{{ bio }}</p>  
        <div class="contact-info">  
          <p><strong>哔哩哔哩:</strong> <a :href="website" target="_blank">{{ biliname }}</a></p>  
          <p><strong>QQ</strong> <a :href="qqurl" target="_blank">{{ qq }}</a></p> 
          <p><strong>邮箱:</strong><a :href="joinemail" target="_blank">{{ email }}</a></p>  
          <p><strong>友情链接</strong></p>
          <p><a :href="skyfurry" target="_blank">风羽阁 | SkyFurry</a></p>
          <p><a :href="fsg" target="_blank">枫兽阁官方活动网</a></p>
        </div>  
        <footer id="footer">
						<div class="inner">
							<ul class="copyright">
								<li>© 2025 皪澄_Tiking</li>
								<li><a style="text-decoration: none;" href="https://beian.miit.gov.cn/" target="_blank">浙ICP备2025165329号-1</a></li>
							</ul>
						</div>
					</footer>
      </div>  
    </div>  
  </div>  
</template>  
  
<script>  
export default {  
  data() {  
    return {  
      name: '🐾皪澄_Tiking🐾',  
      biliname: '皪澄_Tiking',
      avatarImage: 'https://q1.qlogo.cn/g?b=qq&nk=1727435899&s=640', // 头像路径或URL  
      backgroundImage: 'https://uapis.cn/api/imgapi/furry/img4k.php', // 背景API  
      bio: '你好呀~咱名字是皪澄（lì chéng），是一只猫狐龙哦~',  
      website: 'https://space.bilibili.com/432065554',  
      email: 'tiking@skyfurry.cn',  
      joinemail: 'mailto:tiking@skyfurry.cn',
      skyfurry: 'https://www.skyfurry.top',
      fsg: 'https://www.shmaplefurry.top',
      qq: '1727435899',
      qqurl: 'https://qm.qq.com/q/ubu1JsWK2Y'
    };  
  },  
  created() {  
    this.fetchBackgroundImage();  
  },  
  methods: {  
    async fetchBackgroundImage() {  
      try {  
        const response = await fetch('https://uapis.cn/api/imgapi/furry/img4k.php'); // API URL  
        const data = await response.json();  
        this.backgroundImage = data.image_url; // API返回一个包含image_url的对象  
      } catch (error) {  
        console.error('Error fetching background image:', error);  
      }  
    }  
  }  
};  
</script>  
  
<style scoped>  
.portfolio-container {  
  position: relative;  
  width: 100%;  
  height: 100vh; /* 视口高度 */  
  overflow: hidden;  
}  
  
.background {  
  position: absolute;  
  top: 0;  
  left: 0;  
  width: 100%;  
  height: 100%;  
  background-size: cover;  
  background-position: center;  
  filter: blur(1px); /* 模糊效果 */  
  opacity: 0.7; /* 半透明 */  
}  
  
.overlay {  
  position: relative;  
  z-index: 1;  
  color: rgb(63, 80, 98);  
  text-align: center;  
  padding: 20px;  
}  
  
.avatar-container {  
  margin-top: 50px;  
}  
  
.avatar {  
  width: 150px;  
  height: 150px;  
  border-radius: 50%;  
  border: 3px solid rgb(72, 221, 201);  
}  
  
.info-container {  
  margin-top: 20px;  
}  
  
h1 {  
  font-size: 2.5em;  
  margin-bottom: 10px;  
}  
  
p {  
  font-size: 1.2em;  
  line-height: 1.5;  
}  
  
.contact-info {  
  margin-top: 20px;  
}  
  
.contact-info p {  
  margin: 5px 0;  
}  
  
a {  
  color: rgb(92, 110, 10);  
  text-decoration: none;  
}  
  
a:hover {  
  text-decoration: underline;  
}  
</style>

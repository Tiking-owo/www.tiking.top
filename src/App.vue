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
          <p><strong>哔哩哔哩:</strong> <a :href="website" target="_blank">{{ website }}</a></p>  
          <p><strong>邮箱:</strong> {{ email }}</p>   
        </div>  
      </div>  
    </div>  
  </div>  
</template>  
  
<script>  
export default {  
  data() {  
    return {  
      name: '🐾皪澄_Tiking🐾',  
      avatarImage: 'https://foruda.gitee.com/avatar/1729174790527229522/11531684_tiking-010_1729174790.png', // 头像路径或URL  
      backgroundImage: 'https://www.loliapi.com/acg/', // 背景API  
      bio: '阿巴阿巴……正在施工……',  
      website: 'https://space.bilibili.com/432065554',  
      email: 'Tiking@bclcraft.com',  
      phone: '123-456-7890'  
    };  
  },  
  created() {  
    this.fetchBackgroundImage();  
  },  
  methods: {  
    async fetchBackgroundImage() {  
      try {  
        const response = await fetch('https://www.loliapi.com/acg/'); // API URL  
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
  filter: blur(0px); /* 模糊效果 */  
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
  border: 3px solid rgb(72, 147, 221);  
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
  color: rgb(72, 147, 221);  
  text-decoration: none;  
}  
  
a:hover {  
  text-decoration: underline;  
}  
</style>
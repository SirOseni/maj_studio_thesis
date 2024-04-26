<template>
<div>
  <div class="heroImage" data-step="0">
    <img src="heroImage.png" alt="Image description">
  </div>
  <el-row>
  <div class="introduction">
    <div class="image-container">
      <img src="introImage.png" alt="sportswashing is global">
    </div>
    <div class="text-container">
      <p class="introText">
      Sportswashing is the use of sports by 
      <span class="bold-text">nations, corporations and wealthy individuals</span> 
      to improve negative reputations. Through 
      <span class="bold-text">hosting</span> 
      sporting events, 
      <span class="bold-text">acquiring</span> 
      sporting teams and 
      <span class="bold-text">sponsoring</span> 
      teams and events.
      </p>
    </div>
</div>
    </el-row>
    
    <div>
      <el-row>
        <div class="container">
          <div id="imageContainer"></div> 
        </div>
      </el-row>
    </div>
</div>
</template>

<script>
  const imageFiles = ['headline1.png', 'headline2.png', 'headline3.png','headline4.png','headline5.png','headline6.png','headline7.png','headline8.png','headline9.png','headline10.png'];


export default {
  name: "App",
  data() {
    return {
     
    };
  },
  computed: {

  },
  methods: {
   createImageElements() {
      const container = document.querySelector('.container');

      imageFiles.forEach((fileName, index) => {
        
          setTimeout(() => {
            const img = new Image();
        img.src = `images/${fileName}`; // images folder is in the root directory
        img.className = `image image${index + 1}`; // class for each image
        img.onload = () => {
            // img.style.transform = `translate(${index * 50}px, ${index * 30}px)`; // transition to set position
          };
          container.appendChild(img);}
          , index * 1000); //timing for the transition delay
        });

    }
  },
  mounted() {
   this.createImageElements();
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;  
}

@media (max-width: 768px) {
}

.heroImage {
    width: 100%;
    overflow: hidden;
    display: block;
}
.heroImage img {
    width: 100%; /* Makes the image fill the width of its container */
    display: block; /* Ensures proper display and sizing */
}

.introduction {
  display: flex; /* Use flexbox */
  height: 100vh; /* Full height of the viewport */
}
.image-container,
.text-container {
  flex: 1; /* Equal flex distribution */
  display: flex; /* Nested flex containers */
  align-items: center; /* Center content vertically */
  justify-content: center; /* Center content horizontally */
}

.image-container img {
  max-width: 100%; /* Ensure image fits within container */
  max-height: 100%; /* Ensure image fits within container */
}

.introText {
  /* margin-left: 30px; */
 font-family: Verdana, Geneva, Tahoma, sans-serif;
 font-size: 24px;
 border: 2px solid #bf23a0;
 padding: 20px; 
 margin-right: 30px;
 text-align: center;
 
}

.bold-text {
  font-weight: bold;
  color: #0D99FF;
  font-style: italic;
}



.container {
  margin: 60px auto;
  width: 960px; 
  height: 540px; 
  position: relative; 
  border: 0.5rem solid black;
  overflow: hidden;
}

.image {
  position: absolute; 
  max-width: 100%; 
  max-height: 100%; 

}

/* Individual styles for specific images */
.image1 {
  height:200px;
  object-fit: contain;
  position: relative;
  transform: translate(600px, 0px);
  
}
.image2 {
  width: 540px;
  height:80px;
  object-fit: contain; 
  position: absolute; 
  transform: rotateZ(4.5deg) translate(20%, 510%);
  transition: transform 3s ease; 

}
.image3 {
  width: 510px;
  height:75px;
  object-fit: contain;
  transition: transform 9s ease;  
  position: absolute; 
  transform: rotateZ(-4.5deg) translate(20%, 460%);
  transition: transform 5s ease; 
}
.image4 {
  width: 600px;
  height:150px;
  object-fit: contain;
  position: absolute;  
  transform: rotateZ(7deg) translate(28%, 100%);
  transition: transform 8s ease; 
}
.image5 {
  width: 400px;
  height:200px;
  object-fit: contain;
  position: relative;
  transform: rotateZ(0deg) translate(-90%, 200%);
  transition: transform 11s ease; 

}
.image6 {
  width: 400px;
  height:200px;
  object-fit: contain;
  position: relative;
  transform: rotateZ(0deg) translate(0%, 40%);
  transition: transform 14s ease;
}
.image7 {
  width: 400px;
  height:200px;
  object-fit: contain;
  position: relative;
  transform: rotateZ(0deg) translate(-100%, -130%);
  transition: transform 17s ease; 
}
.image8 {
  width: 450px;
  height:200px;
  object-fit: contain;
  position: relative;
  transform: rotateZ(-7deg) translate(10%, -190%);
  transition: transform 18s ease; 
}
.image9 {
 width: 450px;
  height:200px;
  object-fit: contain;
  position: relative;
  transform: rotateZ(-15deg) translate(-80%, -180%);
  transition: transform 21s ease;
}

.image10 {
  width: 540px;
  height:120px;
  object-fit: contain; 
  position: absolute; 
  transform: rotateZ(0deg) translate(-130%, -180%);
  transition: transform 24s ease; 
}

</style>

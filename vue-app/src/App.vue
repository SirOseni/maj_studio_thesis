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


 
  <div class="method">
      <div class="methodContainer">
        <img src="processImg/method0.svg" alt="method">
      </div>
      <div class="method-container">
        <img src="processImg/method1.svg" alt="method">
     </div>
  </div>
 
  <div>
      <el-row>
        <div class="costContainer">
          <div class="flourish-embed flourish-scatter" data-src="visualisation/17855266"></div>  
        </div>
      </el-row>
  </div>

   <div>
        <div class="statContainer">
          <div class="flourish-embed flourish-radar" data-src="visualisation/17857173"></div> 
        </div>
  </div>

 <div>
      <div class="aftermathText">
        <p>In the aftermath of the 2018 World Cup and the controversy surrounding Russia, penalties were handed out to the major offenders.</p>
      </div>

       <div class = "dataTableContainer">
        <table class = "dataTable">
          <thead>
            <tr>
              <th>Offenders</th>
              <th>Fines</th>
              <th>Sanctions</th>
            </tr>
          </thead>
            <tr>
              <td><a href="https://inside.fifa.com/tournaments/mens/worldcup/qatar2022/media-releases/fifa-uefa-suspend-russian-clubs-and-national-teams-from-all-competitions" target = "blank"><img src="img/russia.jpg" alt="Russia"></a></td>
              <td>❌</td>
              <td>✔️</td>
            </tr>
            <tr>
              <td><a href="khttps://www.standard.co.uk/news/uk/roman-abramovich-chelsea-added-to-uk-sanctions-list-russian-oligarch-b987187.html" target = "blank"><img src="img/gazprom.jpg" alt="Gazprom"></a></td>
              <td>✔️</td>
              <td>❌</td>
            </tr>
            <tr>
              <td><a href="https://www.espn.com/soccer/story/_/id/37625797/man-united-cut-sponsorship-russian-airline-aeroflot-amid-ukraine-invasion" target = "blank"><img src="img/aeroflot.png" alt="Aeroflot"></a></td>
              <td>✔️</td>
              <td>❌</td>
            </tr>
            <tr>
              <td><a href="https://www.standard.co.uk/news/uk/roman-abramovich-chelsea-added-to-uk-sanctions-list-russian-oligarch-b987187.html" target = "blank"><img src="img/abrahmovic.png" alt="Abrahmovic"></a></td>
              <td>✔️</td>
              <td>❌</td>
            </tr>
            <tr>
              <td><a href="https://www.sportspromedia.com/news/everton-alisher-usmanov-usm-megafon-yota-sponsors-russia-ukraine/" target = "blank"><img src="img/usmanov.png" alt="Usmanov"></a></td>
              <td>❌</td>
              <td>✔️</td>
            </tr>
            <tr>
              <td><a href="https://www.treasury.gov/resource-center/sanctions/OFAC-Enforcement/Pages/20180406.aspx"><img src="img/kerimov.png" alt="Kerimov" target = "blank"></a></td>
              <td>✔️</td>
              <td>❌</td>
            </tr>
            <tr>
              <td><a href="chttps://www.goal.com/en-us/news/chelsea-transfer-ban-why-fifa-sanctioned-blues-what-appeal-process/tt4ejezxvltd1k8r5symf4rkn" target = "blank"><img src="img/chelsea.png" alt="Chelsea"></a></td>
              <td>✔️</td>
              <td>❌</td>
            </tr>
            <tr>
              <td><a href="https://www.cbssports.com/soccer/news/everton-face-10-point-penalty-after-premier-league-financial-fair-play-rules-breach/" target = "blank"><img src="img/everton.jpg" alt="Everton"></a></td>
              <td>✔️</td>
              <td>❌</td>
            </tr>
            <tr>
              <td><a href="https://www.sportspromedia.com/news/everton-alisher-usmanov-usm-megafon-yota-sponsors-russia-ukraine/" target = "blank"><img src="img/megafon.jpg" alt="Megafon"></a></td>
              <td>✔️</td>
              <td>❌</td>
            </tr>
            <tr>
              <td><a href="https://www.sportspromedia.com/news/everton-alisher-usmanov-usm-megafon-yota-sponsors-russia-ukraine/" target = "blank"><img src="img/usm.png" alt="Usm Holdings"></a></td>
              <td>✔️</td>
              <td>❌</td>
            </tr>
        </table>
      </div>
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

    // Embed Flourish script
    const flourishScript = document.createElement('script');
    flourishScript.src = "https://public.flourish.studio/resources/embed.js";
    document.body.appendChild(flourishScript);
    
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
  transform: translate(500px, 0px);
  
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
  position: absolute; 
  transform: rotateZ(-4.5deg) translate(15%, 460%);
  transition: transform 5s ease; 
}
.image4 {
  width: 600px;
  height:150px;
  object-fit: contain;
  position: absolute;  
  transform: rotateZ(7deg) translate(14%, 95%);
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
  transform: rotateZ(0deg) translate(-15%, 40%);
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
  transform: rotateZ(-7deg) translate(5%, -190%);
  transition: transform 18s ease; 
}
.image9 {
 width: 450px;
  height:200px;
  object-fit: contain;
  position: relative;
  transform: rotateZ(-15deg) translate(-85%, -180%);
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

.aftermathText {
  padding: 20px;
  text-align: center;
}

.aftermathText p {
  text-align: center;
  display:block;
}


.dataTableContainer {
  max-width: 800px;
  margin: 0 auto;
}

/* Table styles */
.dataTable {
  border-collapse: collapse;
  width: 100%;
  height: 300px;
  top: 20; bottom: 20; left: 30px; right: 30;
  border-spacing: 10px;
  padding-left: 50px;
}

.dataTable th, .dataTable td {
  padding: 10px;
  text-align: center;
  border-bottom: 1px solid #ddd;
}

.dataTable th {
  background-color: #f0f0f0;
  color: #333;
}

/* Link styles */
.dataTable a {
  text-decoration: none;
  color: #007bff;
}

.dataTable a:hover {
  text-decoration: underline;
   transform: scale(1.5);
  transition: ease-in;
 }

/* Image styles */
.dataTable img {
  max-width: 100px; /* Adjust image width as needed */
  height: auto;
  border-radius: 5px;
  margin-bottom: 5px;
}

.method {
  display: flex; /* Use flexbox */
  height: 100vh; /* Full height of the viewport */
}

.methodContainer,
.method-container {
  flex: 1; /* Equal flex distribution */
  display: flex; /* Nested flex containers */
  align-items: center; /* Center content vertically */
  justify-content: center; /* Center content horizontally */
}

.methodContainer img {
  max-width: 100%; 
  max-height: 100%; 
}

.method-container img {
  max-width: 100%; 
  max-height: 100%; 
}

.statContainer{
  margin: 60px auto;
  width: 960px; 
  position: relative; 
  border: 0.1rem solid pink;
  overflow: hidden;
}

.costContainer{
  margin: 60px auto;
  width: 960px; 
  height: 600px; 
  position: relative; 
  border: 0.1rem solid blue;
  overflow: hidden;
}


</style>

<template >
    <div>
        <div class="welcomeImg">
            <img :src="welcomeData.hdurl" alt="a">
        </div>
        <div class="title">{{welcomeData.title}}</div>
        <div class="text">{{ welcomeData.explanation }}</div>
        
    </div>
</template>
<script>
export default {
    name: 'WelcomeScreen',
    data() {
        return {
            welcomeData: {
                hdurl:'',
                title: '',
                explanation: ''
            }
        }
    },
    created() {
        const apiKey = process.env.VUE_APP_API_KEY
        fetch(`https://api.nasa.gov/planetary/apod?api_key=${apiKey}`)
        .then((result)=>result.json())
       
        .then((data)=>{
          this.welcomeData = {
            hdurl : data.hdurl,
            title : data.title,
            explanation : data.explanation
        
          }
          console.log(data)

        })
    }
    
}
</script>
<style scoped>
.welcomeImg{
    width: 100vw;
    height: 100vh;
    position: relative;

}
.welcomeImg > img {
    width: 100vw;
    height: 100vh;
}
.title {
    font-size: 35px;
    position: absolute;
    top: 20px;
    left: 25%;
    font-weight: 600;
    
}
.text {
    font-size: 18px;
    position: absolute;
    top: 60px;
    left: 25%;
    font-weight: 500;
    
}
    
</style>
<template>
      <div>
    <div class="container">
      <p class="date">{{ month }} {{ day }}</p>
      <p class="date">{{dates}}</p>
      <br>
      <div class="time">
        <p class="time-item hours">{{ hours }}</p>
        <p class="colon"> : </p>
        <p class="time-item minutes">{{ minutes }}</p>
        <p class="ampm">{{ ampm}}</p>
      </div>
    </div>
  </div>
</template>

<script>

const zeroPadding = (num, digit) =>{
    return (Array(digit).join("0")+num).slice(-digit)
}
export default {
    data(){
        return {
            date:new Date(),
        }
    },
    computed:{
        year(){
            return this.date.getFullYear()
        },
        month(){
            const months =["Jan","Feb","Mar","Apr","May","Jun","Jul","Aug","Sep","Oct","Nov","Dec"];
            const test=months[this.date.getMonth()];
            console.log(test);
            return test;
            // zeroPadding(this.date.getMonth()+1,2)
        },
        day(){
            return this.date.getDate();
        },
        dates(){
            const datelist=["Sun","Mon","Tue","Wed","Thr","Fri","Sat"];
            return datelist[this.date.getDay()];
        },
        hours(){
            var hour = this.date.getHours();
            return (hour ==0) ? 12 : ((hour >12) ? (hour-12) : hour);
        
        },
        minutes(){
            return zeroPadding(this.date.getMinutes(),2)
        },
        ampm(){
           var date = new Date();
           var midday = "am";
           var hour = date.getHours();
           midday= (hour >=12) ? "pm" : "am";
           return midday;
        }
    },
    mounted(){
        this.setDate()
        setInterval(() => this.setDate(),1000)
    },
    methods:{
        setDate(){
            this.date=new Date()
        },
    },
}
</script>

<style scoped>
.container {
  background-color: #333333;
  padding: 2%;
  width: 1000px;
  height: 500px;
}
 
 
.date {
  text-align: left;
  color: #fff;
  font-family: 'Montserrat', sans-serif;
  font-size: 4rem;
  letter-spacing: .1em;
  margin: .0em 0;
  line-height: 1;
  padding-bottom: 50px;
}
 
 
.time {
  display: flex;
}
 
 
.time-item {
  display: flex;
  justify-content: center;
  align-items: center;
  /* flex: 1 1; */
  height: 200px;
  position: relative;
  z-index: 1;
  padding: 0.3em;
  margin: 3px;
  color: #fff;
  font-family: 'Montserrat', sans-serif;
  font-size: 8rem;
  line-height: 1;
 
  box-sizing: border-box;
}
 
 
.time-item:before {
  position: absolute;
  right: 5px;
  bottom: 1px;
  z-index: 1;
  color: #3a4a5e;
  font-family: 'Montserrat', sans-serif;
  font-size: 1.4rem;
  letter-spacing: .05em;
}
 
 .colon{
     -webkit-animation: blink 1s ease-in-out infinite alternate;
     -moz-animation: blink 1s ease-in-out infinite alternate;
     animation: blink 1s ease-in-out infinite alternate;
      display: flex;
  justify-content: center;
  align-items: center;
  padding-bottom:10px;
  /* flex: 1 1; */
  height: 200px;
  position: relative;
  z-index: 1;
  /* padding: 0.3em; */
  margin: 3px;
  color: #fff;
  font-family: 'Montserrat', sans-serif;
  font-size: 8rem;
  line-height: 1;
 
  box-sizing: border-box;
 }

.ampm{
    justify-content: center;
  align-items: center;
  padding-top:80px;
  /* flex: 1 1; */
  height: 200px;
  position: relative;
  z-index: 1;
  margin: 3px;
  color: #fff;
  font-family: 'Montserrat', sans-serif;
  font-size: 5rem;
  line-height: 1;

}

@-webkit-keyframes blink {
    0%{ color: #fff}
    100% { color:#333333}
}
 
@-moz-keyframes blink{

   0%{ color: #fff}
    100% { color:#333333}
}

@keyframes blink{

    0%{ color: #fff}
    100% { color:#333333}

}

</style>
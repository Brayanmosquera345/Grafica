<template>
    <div>
        <div class="container-graph">
            <div class="head-graph">
                <div>
                    <p>My balance</p>
                    <h2>$900.550</h2>
                </div>
                <img src="../assets/img/logo.svg" alt="">
            </div>
            <div class="body-graph">
                <div >
                    <h1>Spending - Last 7 days</h1>
                </div>
                <main>
                    <ul>
                        <li v-for="day,index in data" :key="index">
                                <div :style="{height:calcularAltura(day.amount)}" @click="day.selcted=!day.selcted" :class="day.selcted?'selected':'noSelected'" class="bar">
                                    <div>
                                        {{ day.amount }}
                                    </div>
                                </div>
                                <p>{{ day.day }}</p>
                        </li>
                    </ul>
                </main>
                <footer>
                    <div>
                        <p>Total this month</p>
                        <h1>${{ total }}</h1>
                    </div>
                    <div>
                        <strong>+2.4%</strong>
                        <p>from last month</p>
                    </div>
                </footer>
            </div>
        </div>
    </div>
</template>
<script setup>
import { onMounted, ref } from "vue";

const total=ref(0)
const data= ref([
  {
    "day": "mon",
    "amount": 17.45
  },
  {
    "day": "tue",
    "amount": 34.91
  },
  {
    "day": "wed",
    "amount": 52.36
  },
  {
    "day": "thu",
    "amount": 31.07
  },
  {
    "day": "fri",
    "amount": 23.39
  },
  {
    "day": "sat",
    "amount": 43.28
  },
  {
    "day": "sun",
    "amount": 25.48
  }
])

const calcular=()=>{
    data.value.forEach((day)=>{
        total.value+=day.amount;
    })
}
const calcularAltura=(valor)=>{
    let altura= (valor/total.value)*100;
    return altura+'%';
}
onMounted(()=>{
    calcular();
});
</script>
<style scoped>
.container-graph{
    gap: 2rem;
    height: 100%;
    padding: 10%;
}
.head-graph{
    background-color: hsl(10, 79%, 65%);
    padding: 1rem;
    width: 600px;
    height: 80px;
    border-radius: 10px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.head-graph p, h2{
    color: white;
}
.body-graph{
    margin-top: 1rem;
    background-color: white;
    width: 600px;
    padding: 1rem;
    border-radius: 10px;
    height: 27rem;
}
.body-graph h1{
    color: hsl(25, 47%, 15%);
}
.body-graph :first-child{
    padding-left: .5rem;
}
.body-graph main{
    height: 55%;
    border-bottom: 1px solid hsl(26, 12%, 76%);
    display: flex;
    align-items: end;
}
.body-graph main ul{
    display: flex;
    height: 600px;
}
.body-graph main li {
    list-style: none;
    margin-left: 1rem;
    margin-right: 1rem;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: end;
}
.body-graph main p{
    color: hsl(28, 5%, 51%);
}
.bar{
    width: 40px;
    border-radius: 7px;
    cursor: pointer;
    transition-property: background-color;
    transition-duration: .3s;
    position: relative;
}
.bar div{
    background-color: hsl(25, 47%, 15%);
    color: antiquewhite;
    padding: 6px;
    border-radius: 4px;
    position: absolute;
    top: -40px;
    left: 0px;
    display: none;
}
.bar:hover div{
    display: block;
}
.selected{
    background-color: hsl(186, 34%, 60%);
    border-radius: 7px;
    animation: barUp 2s ease;
}
.selected div{
    display: block;
}
.noSelected{
    background-color: hsl(10, 79%, 65%);
}
.bar::after {
  content: '';
  position: absolute;
  border-radius: 7px;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 0;
  background-color: hsl(186, 34%, 60%);
  transition: height 0.5s ease;
}

.noSelected::after {
  height: 0;
}

.selected::after {
  height: 100%;
  animation: fillWater 1.5s ease forwards; 
}

@keyframes fillWater {
  0% {
    height: 0;
  }
  100% {
    height: 100%;
  }
}
.noSelected:hover{
    background-color: hsl(9, 66%, 70%)
}
.body-graph footer{
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.body-graph footer p{
    color: hsl(28, 5%, 51%);
}
.body-graph footer :last-child{
    display: flex;
    justify-content: end;
    flex-direction: column;
    align-items: end;
}
@keyframes barUp {
    0%{
        background-color: transparent;
        
    }
    100%{
        background-color: transparent;
        
    }
}
@media (max-width: 600px) {
    .container-graph{
        padding: 1%;
        margin-top: 10%;
    }

    .head-graph,
    .body-graph{
        width: 330px;
    }
    .body-graph main li{
        margin-left: .2rem;
    }
    .bar{
        width: 20px;
    }
}
@media ((min-width: 601px) and (max-width: 1024px)) {
    .container-graph{
        padding: 2%;
        margin-top: 10%;
    }

    .head-graph,
    .body-graph{
        width: 500px;
    }
    .body-graph main li{
        margin-left: .6rem;
    }
    .bar{
        width: 35px;
    }
}



</style>
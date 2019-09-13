<template>
    <div class="container">
        <div class="row">
            <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
                <h1>Animations</h1>

                  <select v-model="slct" class="form-control">
                    <option value="fade">fade</option>
                    <option value="slide">slide</option>
                  </select>
                  <button class="btn btn-primary" @click = "show=!show">Show</button>

                <transition :name= "slct">
                  <div class="alert alert-danger" v-if = "show">Danger!</div>
                </transition>
                <transition name= "slct" type="animation">
                   <div class="alert alert-warning" v-if = "show">Danger!</div>
                </transition>
                <transition name="rte">
                  <div class ="rnd">Rotate</div>
                </transition>
                <hr>
                <button class="btn btn-primary" @click="selectedC=='app-danger'?selectedC='app-success':selectedC='app-danger'">Toggle</button>
                <hr>
                <transition name ="fade" mode="out-in">
                  <component :is="selectedC"></component>
                </transition>
                <hr>
                <input type="text" name="" id="" class="form-control" v-model= "item">
                <hr>
                <button class="btn btn-warning" @click= "addItem" >Add</button>
                <hr>
                <ol class="list-group">
                  <transition-group name="slide">
                     <li class="list-group-item" :key="i" v-for="(i,index) in items" @click="removeItem(index)" >{{i}}</li>
                  </transition-group>
                </ol>

            </div>
        </div>
    </div>
</template>

<script>
import danger from "./assets/components/Danger.vue"
import success from "./assets/components/Success.vue"
    export default {
        data() {
            return {
              item:'',
              show:false,slct:'slide',
              selectedC :"app-success",
              items:['Apple','Banana','Mango','Berry']
            }
        },
        components:{
          appDanger:danger,
          appSuccess:success
        },
        methods:{
          addItem(){
            if(this.item ==''){
              selectedC = 'app-danger'
            }
            else{
              this.items.push(this.item);
              this.item='';
            }
          },
          removeItem(index){
            this.items.splice(index,1);
          }
        }
    }
</script>

<style scoped>


  /* v-enter{} */
  .fade-enter{
    opacity: 0;
  }
  .fade-enter-active{
    transition: opacity 2s;
  }
  .fade-leave{
     opacity:1;
     }
  .fade-leave-acticlickve{
     transition: opacity 2s;
     opacity: 0;

  }
  li{
    cursor: pointer;
    color:white;
    background-color: rgb(62, 9, 112);
  }

  .slide-enter-active{
    animation: slide-in .5s ease-out forwards;
    transition: opacity .5s;
  }

  .slide-leave-active{
    animation: slide-out .5s ease-out forwards;
    transition: opacity .5s;
    opacity: 0;
  }
  @keyframes slide-in {
    from{
      transform: translateX(100px);
    }
    to{
       transform: translateX(0);
    }

  }
  @keyframes slide-out {
    from{
      transform: translateX(0);
    }
    to{
      transform: translateX(-100px);
    }
  }
.rnd{
  width:100px;
  height:100px;
  border-radius: 100px;
  background-color:brown;
  color:white;
  text-align: center;
  font-size: 25px;
  padding-top:30px;
  transition:1s;
  cursor: pointer;



}
.rnd:hover{
  color:crimson;
  transform: rotate(145deg);

}

</style>



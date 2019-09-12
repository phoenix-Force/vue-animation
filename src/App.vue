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
                <br></br>
                <transition :name= "slct">
                  <div class="alert alert-danger" v-if = "show">Danger!</div>
                </transition>
                <transition name= "slct" type="animation">
                   <div class="alert alert-warning" v-if = "show">Danger!</div>
                </transition>
                <transition name="rte">
                  <div class ="rnd">Rotate</div>
                </transition>

            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
              show:false,slct:'slide'
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
  /* .fade-leave{
    /* opacity:1 */

  .fade-leave-active{
     transition: opacity 2s;
     opacity: 0;

  }

  .slide-enter-active{
    animation: slide-in 1s ease-out forwards;
    transition: opacity 1s;
  }

  .slide-leave-active{
    animation: slide-out 1s ease-out forwards;
    transition: opacity 1s;
    opacity: 0;
  }
  @keyframes slide-in {
    from{
      transform: translateY(20px);
    }
    to{
       transform: translateY(0);
    }

  }
  @keyframes slide-out {
    from{
      transform: translateY(0);
    }
    to{
      transform: translateY(20px);
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



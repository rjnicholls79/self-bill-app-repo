<template>
  <div class="outer_div">
    <main>
      <nav>
        <div class="container d-flex">
          <p class="" @click="isShow['Star'] = !isShow['Star']"><i class="fas fa-bars"></i> &nbsp; Menu</p>
          <img src="../assets/lifetimelegal_logo_white.png" class="img-fluid logo ml-auto">
        </div>
      </nav>
      <transition name="slide">
      <div class="sideBar" v-if="isShow['Star']">
        <ul>
          <router-link to="/"><li>Self Billing</li></router-link>
          <router-link to="/setup"><li>Form Two</li></router-link>
        </ul>
      </div><!-- End Sidebar -->
    </transition>
    </main>
  </div><!-- End Outer Div -->
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      isShow: {
        'Star': false,
        'Diehard': false,
        'Predator': false,
      },
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>

$blue: #016BA8;
$orange: #FFB715;
$white: #fff;

nav{
  background: $blue;
  border-bottom: 2px solid $orange;
  padding: 10px 0px;
  p{
    margin-top: 10px;
    color: $white;
    margin-bottom: 0px;
  }
  .logo{
    width: 20%;
  }
  .fa-bars{
    cursor: pointer;
  }
}

.sideBar{
  background: $blue;
  color: $white;
  position: absolute;
  padding: 1rem 1.5rem;
  ul{
    padding-left: 0px !important;
  }
  li{
    list-style: none;
    padding-top: 15px;
  }
}

.slide-enter-active {
}

.slide-leave-active {
    transition-timing-function: cubic-bezier(0, 1, 0.5, 1);
}

.slide-enter-to,
.slide-leave {
    max-height: 100px;
    overflow: hidden;
}

.slide-enter,
.slide-leave-to {
    overflow: hidden;
    max-height: 0;
}

</style>

<template>
  <h1>{{title}}</h1>
  <input type="text" ref="name">
  <button @click="handleClick">click me</button>

  <teleport to=".modals" v-if="showModal">
    <!-- <Modal :header="header" :text="text" theme="sale" @close="handleModal"/> -->
    <!--***********First Component *******-->
    <Modal theme="sale" @close="handleModal">
      <template #links>
        <a href="#">Sign Up now</a>
        <a href="#">more Info</a>
      </template>
      
      <h1>Ninja Givaway</h1>
      <p>Grab your ninja swag for half price!</p>
    </Modal>
  </teleport>
  <!--*****************************************************-->
  <teleport to=".modals" v-if="showModal2">
    <!-- <Modal :header="header" :text="text" theme="sale" @close="handleModal"/> -->
    <!--***********First Component *******-->
    <Modal theme="sale" @close="handleModal2">
        <template #links>
            <a href="#">faceBook</a>
            <a href="#">Twitter</a>
            <a href="#">Instgram</a>
        </template>
        <h1>Second Modal Challenge</h1>
    </Modal>

  </teleport>

  <!--***********Second Component *******-->



  <p>Welcome...</p>
  <!-- @click.shift kandiro bach ngolo khass ykun mpressi 3la shift 3ad yclicki sinon maghatkhdemch-->
  <button @click.shift="handleModal">Open Modal (Shift)</button>
  <button @click="handleModal2">Open Modal 2 (right)</button>
</template>

<script>
import Modal from './components/Modal.vue'


export default {
  name: 'App',
  components:{
    Modal,
  },
  data() {
    return{
      title: " My First Vue App :)",
      header: "Sign up for the Giveaway!",
      text: "Grab your ninja swag for half price!",
      showModal : false,
      showModal2 : false,
    }
  },
  methods:{
    handleClick(){
        console.log(this.$refs.name)
        console.log(this.$refs.name.value)
        this.$refs.name.classList.add('active')
        this.$refs.name.focus()

    },
    handleModal(){
      this.showModal = !this.showModal
    },
    handleModal2(){
      this.showModal2 = !this.showModal2;
    }
  }
}
</script>

<style>
#app, .modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1{
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>

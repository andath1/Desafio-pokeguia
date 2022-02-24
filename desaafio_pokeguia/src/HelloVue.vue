<template>
  <div class="hellovue">
      {{message}}
       <img class="helloimg" src="https://images.vectorhq.com/images/previews/1ba/bart-and-lisa-psd-446281.png" />
      <button class="hello-response" @click="clickResponse">Responder</button>
  </div>
</template>

<script>
   export default {
    name: 'hellovue',
    props: {
     message: {
        type: String,
        required: true,
        }
    },
      methods: {
      clickResponse(event) {
      this.$emit('clickedResponse', 'Ay! Caramba !!!');
      }
    }
};
</script>
<style scoped>
.hellovue {
display: flex;
flex-flow: column nowrap;
padding: 300px;
margin: 300px;
}
.helloimg {
width: 25%;
height: 25%;
}
.hello-response {
width: 20%;
color: red;
}
</style>

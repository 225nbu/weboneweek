<template>
  <div class="hello">
    <h1>ワックワック</h1>
    <p>
      {{timer}}
    </p>
    <button @click="timerbtn"></button>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class HelloWorld extends Vue {
  @Prop() private msg!: string;
  data(){
    return{
      min: 59,
      sec: 59,
      timerbtn: false,
      timer: null
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

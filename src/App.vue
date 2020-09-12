<template>
  <div id="app">
    <h3>猫ボタン</h3>
    <img alt="Vue logo" :src="imgUrl"  height="100px" /><br/>
    <div>
      <div>{{message}}</div>
      <div>{{ count }}</div>
      <button @click="increment" @click.once="start" v-bind:style="{color:btncolor}">押す</button>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component({
  components: {}
})
export default class App extends Vue {
  count = 0;
  imgUrl = "/img/logo.82b9c7a5.png";
  message="ボタンを押してね";
  n1=0;
  n2=0;
  n3=0;
  n4=0;
  startTime=new Date();
  startTimea=0;
  stopTime=new Date();
  stopTimea=0;
  btncolor="black";

  start(){
    this.startTime=new Date();
  }
  increment() {
    this.count++;
    this.n1 = Math.floor(this.count / 1) % 10; //1桁目
    this.n2 = Math.floor(this.count / 10) % 10; //2桁目
    this.n3 = Math.floor(this.count / 100) % 10; //3桁目
    this.n4 = Math.floor(this.count / 1000) % 10; //4桁目
    if(this.n1==2){
      this.imgUrl="/img/cat_smile.png";
      this.message="にゃー";
      if(this.n2==2){
        this.stopTime = new Date();
        this.startTimea=(this.stopTime.getTime()-this.startTime.getTime())/1000;
        this.message="にゃー"+this.startTimea+"秒";
        this.imgUrl="/img/cat_laugh.png";
        this.message="たくさん押してすごいのにゃー。今"+this.startTimea+"秒たったのにゃ。";
        if(this.n3==2){
          this.stopTime = new Date();
          this.startTimea=(this.stopTime.getTime()-this.startTime.getTime())/1000;
          this.message="にゃー"+this.startTimea+"秒";
          this.btncolor="#ccc";
          this.imgUrl="/img/cat_sing.png";
          this.message="なぜそんなに押すにゃ？";
          if(this.n4==2){
            this.imgUrl="/img/cat_matatabi.png";
            this.message="もう押さなくていいにゃ…";
          }
        }
      }
    }else{
      this.imgUrl="/img/logo.82b9c7a5.png";
      this.message="もっと押せ！";
      if(this.count>22){
      this.message="まだ押すの？";
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

<template>
  <div class="container">
    <h1 class="alert alert-dark">โปรแกรมทายเลขจากสี</h1>
    <div class="colorinput">
      <label for="exampleColorInput"
        >สีที่ชอบมากที่สุด</label
      >
      <input
        type="color"
        class="form-control form-control-color"
        id="exampleColorInput"
        title="Choose your color"
        v-on:input="myInput"
      />
    </div>
    <ul class="list-group">
      <li class="list-group-item row" :style="{ color }">เลขที่คุณได้คือ: {{ number }}</li>
      <div class="row" >
        <li :style="{ color }" class="list-group-item col">{{last2Num}}</li>
        <li :style="{ color }" class="list-group-item col">{{first2Num}}</li>
        <li :style="{ color }" class="list-group-item col">{{last3Num}}</li>
        <li :style="{ color }" class="list-group-item col">{{first3Num}}</li>
      </div>
    </ul>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "crud",
  data() {
    return {
      number: "",
      last2Num: "",
      first2Num: "",
      last3Num: "",
      first3Num: "",
      color: "",
    };
  },
  methods: {
    myInput(event) {
      let hex = event.target.value;
      if (hex != "#ffffff") {
        this.color = hex;
        } else {this.color = "#7a7a7a";}
      hex = hex.replace("#", "");
      let decimal = parseInt(hex, 16);
      decimal = decimal.toString().slice(0, 6);
      if (decimal.length == 6 || decimal == 0) {
        if (decimal == 0) {
          this.number = "ไม่เอาสีดำสิจะหน้าเบื่อไปไหนเนียน???🥱";
        } else {
          this.number = decimal;
        }
      } else {
        this.number = Math.floor(Math.random() * (999999 + 1) );
        console.log("random");
      }
      this.last2Num = this.number.slice(4, 6);
      this.first2Num = this.number.slice(0, 2);
      this.last3Num = this.number.slice(3, 6);
      this.first3Num = this.number.slice(0, 3);
    },
  },
};
</script>

<style scope>
h1 {
  margin-top: 2rem;
}
.colorinput {
  margin-top: 1rem;
  margin-bottom: 1rem;
  display: flex;
  align-items: center;
}
.colorinput label {
  margin-right: 1rem;
}
</style>

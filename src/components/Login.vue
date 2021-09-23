<template>
  <div class="container">
    <h2>¡Bienvenido criptocoins!</h2>
    <form class="form" @submit.prevent="logIn()">
      <div class="element">
        <label class="user">Usuario</label>
        <input type="text" class="user" v-model="user" @input="validateUser" />
      </div>
      <transition>
        <label class="alert" v-if="validation"
          ><i>Ingrese un usuario alfanumérico</i></label
        >
      </transition>
      <div class="element">
        <input type="submit" value="Enviar" :disabled="validation" />
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "Login",
  data() {
    return {
      validation: true,
      user: "",
    };
  },
  methods: {
    logIn() {
      this.$emit("log-in", this.user);
    },
    validateUser() {
      let expReg = /^[a-zA-Z0-9]*$/;
      if (expReg.test(this.user)) {
        this.validation = false;
      } else {
        this.validation = true;
      }
    },
  },
};
</script>

<style scoped>
.container {
  margin: 50px auto;
  width: 400px;
  padding: 30px;
  background: rgba(0, 0, 0, 0.5);
  border-radius: 10px;
  background: linear-gradient(#7209b7, #3f37);
  text-align: center;
}
.container h2 {
  margin: 0 0 30px;
  padding: 0;
  font-size: 28px;
  color: aquamarine;
  text-align: center;
}
.container .element label {
  color: #fff;
  font-size: 20px;
}
.container .element input {
  width: 100%;
  padding: 10px 0;
  color: #fff;
  background: transparent;
  border: none;
  border-bottom: 1px solid #fff;
  margin-bottom: 10px;
  margin-top: 10px;
}
.container .element input[type="submit"] {
  background-color: #f72585;
  border: none;
  letter-spacing: 5px;
  font-size: 18px;
  text-transform: uppercase;
  cursor: pointer;
  padding: 15px;
  margin-top: 30px;
}
.alert i {
  color: rgb(218, 5, 5);
  font-size: 14px;
}
</style>

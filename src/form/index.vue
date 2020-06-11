<template>
  <div>
    <CustomForm :model="model" :rules="rules" ref="loginForm">
      <CustomFormItem label="用户名" prop="username">
        <CustomInput v-model="model.username" />
      </CustomFormItem>
      <CustomFormItem label="密码" prop="password">
        <CustomInput v-model="model.password" type="password" />
      </CustomFormItem>
      <CustomFormItem>
        <button @click="onLogin">登录</button>
      </CustomFormItem>
      {{model}}
    </CustomForm>
  </div>
</template>

<script>
import CustomInput from "./CustomInput";
import CustomFormItem from "./CustomFormItem";
import CustomForm from "./CustomForm";
export default {
  components: {
    CustomInput,
    CustomFormItem,
    CustomForm
  },
  data() {
    return {
      model: {
        username: "tom",
        password: ""
      },
      rules: {
        username: [{ required: true, errorMessage: "123" }],
        password: [{ required: true, errorMessage: "456" }]
      }
    };
  },
  methods: {
    onLogin() {
      this.$refs.loginForm.validate(isValid => {
        if (isValid) {
          alert("cc");
        } else {
          alert("bb");
        }
      });
    }
  }
};
</script>

<style>
</style>
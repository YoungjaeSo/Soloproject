<template>
  <header>
    <h2>안녕하세요 영재의 프로젝트입니다</h2>
  </header>
  <main>
    <div class="container">
      <article class="login">
        <input type="text" v-model="emailvalue" placeholder="아이디를 입력해주세요" />
        <input type="password" v-model="passwordvalue" placeholder="비밀번호를 입력해주세요" />
      </article>
      <article class="button">
        <div class="loginbutton">
          <button @click="login">로그인</button>
        </div>
        <div class="subbutton">
          <button>회원가입</button>
          <button>아이디 찾기</button>
          <button>비밀번호 찾기</button>
        </div>
      </article>
    </div>
  </main>
</template>
<script setup>
import { ref } from "vue";
import axios from "axios";

const emailvalue = ref("");
const passwordvalue = ref("");

const login = async () => {
  try {
    const response = await axios.get(`http://localhost:3000/users?email=${emailvalue.value}`);
    const users = response.data;

    if (users.length === 0) {
      alert("아이디가 존재하지 않습니다");
    } else {
      const user = users[0];
      if (user.password === passwordvalue.value) {
        alert("환영합니다");
      } else {
        alert("비밀번호가 틀렸습니다");
      }
    }
  } catch (error) {
    console.error("로그인 중 에러 발생: ", error);
  }
};
</script>
<style scoped>
@font-face {
  font-family: "CookieRun-Regular";
  src: url("https://fastly.jsdelivr.net/gh/projectnoonnu/noonfonts_2001@1.1/CookieRun-Regular.woff")
    format("woff");
  font-weight: normal;
  font-style: normal;
}
* {
  padding: 0;
  background-color: #f0f8ff;
}

.login {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-top: 50px;
  gap: 30px;
}
.login input {
  width: 500px;
  height: 30px;
  border-radius: 10px;
  border: 2px solid #969696;
}
.loginbutton {
  display: flex;
  justify-content: center;
  margin: 20px;
}
.subbutton {
  display: flex;
  justify-content: space-around;
}

button {
  width: 100px;
  height: 30px;
  border-radius: 10px;
  background-color: #abdcff;
  border: none;
  color: white;
}

h2 {
  font-family: "CookieRun-Regular";
  font-size: 3em;
  text-align: center;
}
</style>

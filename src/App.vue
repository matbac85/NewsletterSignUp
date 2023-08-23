<script setup>
import Illustration from "./components/Illustration.vue";
import Header from "./components/Header.vue";
import List from "./components/List.vue";
import SuccessMessage from "./components/SuccessMessage.vue";
import { ref } from "vue";

const showSuccessMessage = ref(false);
const email = ref("");
const error = ref("");

const validateEmail = (value) => {
  const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  return emailPattern.test(value) && value.trim() !== "";
};

const submitForm = () => {
  if (validateEmail(email.value)) {
    showSuccessMessage.value = true;
  } else {
    error.value = "valid email required";
  }
};

const dismissSuccessMessage = () => {
  showSuccessMessage.value = false;
  email.value = "";
};
</script>

<template>
  <div class="background">
    <form
      class="container"
      @submit.prevent="submitForm"
      v-if="!showSuccessMessage"
    >
      <div class="illustration">
        <Illustration />
      </div>
      <div class="content">
        <Header /><List />
        <div>
          <div class="label">
            <label for="email">Email address</label>
            <p v-if="error">{{ error }}</p>
          </div>
          <input
            :class="{ 'input-error': error }"
            type="email"
            name="email"
            placeholder="email@company.com"
            v-model="email"
          />
        </div>
        <button type="submit">Subscribe to monthly newsletter</button>
      </div>
    </form>
    <SuccessMessage
      v-else
      :email="email"
      @closeMessage="dismissSuccessMessage"
    />
  </div>
</template>

<style scoped>
.content {
  margin: 2.5rem 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.label {
  display: flex;
  justify-content: space-between;
}

label {
  margin-bottom: 0.5rem;
  font-size: 0.75rem;
  line-height: 150%;
  font-weight: 700;
}

.label p {
  margin-bottom: 0.5rem;
  font-size: 0.75rem;
  line-height: 150%;
  font-weight: 700;
  color: #ff6155;
}

input {
  width: 100%;
  padding: 1rem 1.5rem;
  border-radius: 0.5rem;
  border: 1px solid #19182b40;
}

input:focus {
  outline: none;
  border: 1px solid var(--darkNavy);
}

.input-error {
  width: 100%;
  padding: 1rem 1.5rem;
  border-radius: 0.5rem;
  border: 1px solid #ff6155;
  background-color: #ff615526;
}

::placeholder {
  color: #24274280;
}

.input-error::placeholder {
  color: #ff6155;
}

button {
  background-color: var(--darkNavy);
  color: var(--white);
  border-radius: 10px;
  width: 100%;
  padding: 1rem 0;
  border: none;
  font-weight: 700;
}

button:hover {
  background: linear-gradient(
    180deg,
    rgba(255, 106, 58, 1) 0%,
    rgba(255, 82, 115, 1) 100%
  );
  filter: drop-shadow(0px 16px 32px #ff615580);
}

button:focus {
  background-color: var(--darkNavy);
}

@media screen and (min-width: 375px) {
  .background {
    background-color: var(--darkNavy);
    height: 100vh;
    width: 100vw;
    display: grid;
    place-content: center;
  }
  .container {
    display: flex;
    flex-direction: row-reverse;
    align-items: center;
    padding: 1.5rem;
    border-radius: 2.25rem;
    background-color: white;
    max-width: 58rem;
    filter: drop-shadow(0px 15px 60px rgba(0, 0, 0, 0.25));
  }

  .content {
    padding: 0 4rem 0 2.5rem;
    margin: 0;
  }
}
</style>

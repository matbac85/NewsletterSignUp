<script setup>
const props = defineProps(["email"]);
</script>

<template>
  <div class="wrapper">
    <div class="content">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="64"
        height="64"
        viewBox="0 0 64 64"
      >
        <defs>
          <linearGradient id="a" x1="100%" x2="0%" y1="0%" y2="100%">
            <stop offset="0%" stop-color="#FF6A3A" />
            <stop offset="100%" stop-color="#FF527B" />
          </linearGradient>
        </defs>
        <g fill="none">
          <circle cx="32" cy="32" r="32" fill="url(#a)" />
          <path
            stroke="#FFF"
            stroke-width="4"
            d="m18.286 34.686 8.334 7.98 19.094-18.285"
          />
        </g>
      </svg>
      <h2>Thanks for subscribing!</h2>
      <p>
        A confirmation email has been sent to
        <strong>{{ email }}</strong
        >. Please open it and click the button inside to confirm your
        subscription
      </p>
    </div>
    <button class="button" @click="$emit('closeMessage')">
      Dismiss message
    </button>
  </div>
</template>

<style scoped>
.wrapper {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 9.375rem 1.5rem 2.5rem 1.5rem;
}

h2 {
  font-size: 2.5rem;
  font-weight: 700;
  margin-top: 2.5rem;
  margin-bottom: 1.5rem;
  line-height: 1em;
}

p {
  line-height: 150%;
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

@media screen and (min-width: 375px) {
  .wrapper {
    max-width: 31.5rem;
    max-height: 32.5rem;
    background-color: var(--white);
    border-radius: 2.25rem;
    padding: 3rem 4rem 4rem 4rem;
    filter: drop-shadow(0px 15px 60px rgba(0, 0, 0, 0.25));
  }

  h2 {
    font-size: 3.5rem;
    line-height: 100%;
  }
}
</style>

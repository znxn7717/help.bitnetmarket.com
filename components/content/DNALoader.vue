<template>
  <div
    class="dna-loader"
    style="
      position: absolute;
      margin: 0;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      width: 5rem;
    "
  >
    <div class="dna-wave top-dna-wave">
      <div></div>
      <div></div>
      <div></div>
      <div></div>
      <div></div>
      <div></div>
      <div></div>
      <div></div>
      <div></div>
      <div></div>
    </div>
    <div class="dna-wave bottom-dna-wave">
      <div></div>
      <div></div>
      <div></div>
      <div></div>
      <div></div>
      <div></div>
      <div></div>
      <div></div>
      <div></div>
      <div></div>
    </div>
  </div>
</template>

<style scoped>
/* 30px */
@keyframes move {
  0% {
    transform: translateY(0px);
  }
  25% {
    transform: translateY(120px);
  }
  50% {
    transform: translateY(0px);
  }
  75% {
    transform: translateY(120px);
  }
  100% {
    transform: translateY(0px);
  }
}

@keyframes grow {
  0%,
  50%,
  75%,
  100% {
    transform: scaleX(0.7) scaleY(0.7);
  }
  10%,
  60% {
    transform: scaleX(1) scaleY(1);
  }
  35%,
  85% {
    transform: scaleX(0.4) scaleY(0.4);
  }
}

.dna-loader {
  display: flex;
  position: absolute;
  width: 100%;
}

.dna-wave {
  display: flex;
  justify-content: space-between;
  position: absolute;
  left: 0;
  top: 0;
  height: 100%;
  width: 100%;
  perspective: 20px;
}

/* 6px */
.dna-wave > div {
  position: relative;
  width: 24px;
  height: 24px;
  border-radius: 100%;
}

.dna-wave > div::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: hsl(var(--primary));
  border-radius: 50%;
}

.top-dna-wave > div::before {
  background-color: hsl(var(--primary));
}

.top-dna-wave > div {
  animation: move 3s ease-in-out infinite reverse;
}

.top-dna-wave > div::before {
  animation: grow 3s linear infinite reverse;
}

.bottom-dna-wave > div {
  animation: move 3s ease-in-out infinite;
}

.bottom-dna-wave > div::before {
  animation: grow 3s linear infinite;
}

.dna-wave > div:nth-child(10) {
  animation-delay: 0s;
}
.dna-wave > div:nth-child(9) {
  animation-delay: -0.1s;
}
.dna-wave > div:nth-child(8) {
  animation-delay: -0.2s;
}
.dna-wave > div:nth-child(7) {
  animation-delay: -0.3s;
}
.dna-wave > div:nth-child(6) {
  animation-delay: -0.4s;
}
.dna-wave > div:nth-child(5) {
  animation-delay: -0.5s;
}
.dna-wave > div:nth-child(4) {
  animation-delay: -0.6s;
}
.dna-wave > div:nth-child(3) {
  animation-delay: -0.7s;
}
.dna-wave > div:nth-child(2) {
  animation-delay: -0.8s;
}
.dna-wave > div:nth-child(1) {
  animation-delay: -0.9s;
}

.bottom-dna-wave > div:nth-child(10) {
  animation-delay: 0.75s;
}
.bottom-dna-wave > div:nth-child(9) {
  animation-delay: 0.65s;
}
.bottom-dna-wave > div:nth-child(8) {
  animation-delay: 0.55s;
}
.bottom-dna-wave > div:nth-child(7) {
  animation-delay: 0.45s;
}
.bottom-dna-wave > div:nth-child(6) {
  animation-delay: 0.35s;
}
.bottom-dna-wave > div:nth-child(5) {
  animation-delay: 0.25s;
}
.bottom-dna-wave > div:nth-child(4) {
  animation-delay: 0.15s;
}
.bottom-dna-wave > div:nth-child(3) {
  animation-delay: 0.05s;
}
.bottom-dna-wave > div:nth-child(2) {
  animation-delay: -0.05s;
}
.bottom-dna-wave > div:nth-child(1) {
  animation-delay: -0.15s;
}
</style>

<template>
  <div class="main-container">
    <div class="phone-container">
      <div class="swipper-container">
        <div class="swipper" ref="swipperRef">
          <div class="sections">
            <img
              src="https://www.simoptions.com/wp/wp-content/uploads/2023/06/easy-to-use-1.svg"
            />
          </div>
          <div class="sections">
            <img
              src="https://www.simoptions.com/wp/wp-content/uploads/2023/06/easy-to-use-2.svg"
              class="section-img"
            />
          </div>
          <div class="sections">
            <img
              src="https://www.simoptions.com/wp/wp-content/uploads/2023/06/easy-to-use-3.svg"
              class="section-img"
            />
          </div>
        </div>
      </div>

      <div class="phone-wrapper"></div>
    </div>
    <div class="multi-step-container">
      <div class="progress-bar">
        <div class="passed-progress" ref="passedProgressBarRef"></div>
      </div>
      <div class="steps-container">
        <div class="step-paragraph" @click="() => handleClickStep(0)">
          concac
        </div>
        <div class="step-paragraph" @click="() => handleClickStep(1)">
          concac
        </div>
        <div class="step-paragraph" @click="() => handleClickStep(2)">
          concac
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, watch } from "vue";
const curretStep = ref<number>(0);
const swipperRef = ref<HTMLDivElement | null>(null);
const passedProgressBarRef = ref<HTMLDivElement | null>(null);

const handleClickStep = (step: number) => {
  curretStep.value = step;
};

watch(curretStep, () => {
  if (swipperRef.value) {
    swipperRef.value.style.transform = `translateY(${
      -340 * curretStep.value
    }px)`;
  }
  if(passedProgressBarRef.value) {
    passedProgressBarRef.value.style.height = `${curretStep.value * 100 / 2}%`;
  }
  console.log(curretStep.value);
});
</script>

<style lang="scss" scoped>
@import "./MultiStep.scss";
</style>

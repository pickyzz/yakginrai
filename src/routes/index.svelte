<script lang="ts">
  import { onMount } from 'svelte'
  import {MEAL_TO_EAT} from "$lib/Meals"

  const meals = MEAL_TO_EAT
  const shareUrl = 'https://yakginrai.pickyzz.dev'

  let meal = ''
  let choosenMeal = ''

  onMount(() => {
		meal = 'ถ้าคิดไม่ออกให้เราช่วยสิ'
    choosenMeal = 'อะไรก็ได้'

		document.addEventListener('keypress', (e) => {
			if (e.key === ' ') {
				random()
			}
		});
	});

	function random() {
		meal = meals[Math.floor(Math.random() * meals.length)]
    choosenMeal = meal
	}
</script>

<div class="w-full h-screen flex flex-col justify-center items-center">
  <span class="text-5xl flex flex-col">อยากกินไร ?.. </span>
  <h1 class="text-6xl flex flex-col">
    <section class="select-none text-3xl font-sans text-center w-full h-full">
      {#key meal}
        <h1 class="w-full text-3xl font-bold py-[3em]">{meal}</h1>
      {/key}
      <button on:click={random} class="btn btn-outline btn-primary mx-1">จัดมา</button>
      <a href="https://twitter.com/intent/tweet?text=วันนี้อยากกิน..&nbsp;{choosenMeal}&nbsp;-&nbsp;&url={shareUrl}&hashtags=อยากกินไร" target="_blank" rel="noreferrer">
        <button class="btn btn-outline btn-primary mx-1">ทวีต</button>
      </a>
      <p class="text-[14px] text-center pt-2">หรือกด <kbd class="kbd kbd-xs">Spacebar</kbd> เพื่อสุ่ม</p>
    </section>
  </h1>
</div>

<script setup>
import { onMounted, useTemplateRef } from 'vue'

const theP = useTemplateRef('the-p')

onMounted(() => {
  console.log(theP.value.innerHTML)
  colorMod3Numbers(theP.value)
})

function colorMod3Numbers(paragraph) {
    const text = paragraph.textContent;
    const numbers = text.split(', ');
    
    const coloredHTML = numbers.map(num => {
        const number = parseInt(num.trim());
        if (number % 3 === 0) {
            return `<span style="color: blue;">${number}</span>`;
        }
        return number.toString();
    }).join(', ');
    
    paragraph.innerHTML = coloredHTML;
}
</script>

<template>
  <main class="main cont">
    <section class="section" style="margin-bottom: 4.5rem; text-align: center;">
      <p>1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30</p>

      <hr>

      <p ref="the-p">1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30</p>
    </section>
  </main>
</template>

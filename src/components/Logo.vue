<template>
  <div
    :class="`col-${col}`"
    class="flex self-center"
  >
    <img
      height="80%"
      class="self-center flip-horizontal"
      alt="Quasar logo"
      src="~assets/quasar-logo-full.png"
    />
  </div>
</template>
 <script>
 export default {
   props: {
     col: {
       type: String,
       default: '8',
     },
   }
 }
 </script>
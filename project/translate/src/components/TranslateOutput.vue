<template>
  <div class="showOut" id="translate-output">
    {{translatedText}}
  </div>
</template>

<script>
export default {
  name: 'translate-output',
  props:[
    "translatedText"
  ]
}
</script>

<style>
.showOut{
	font-size: 45px;
}
</style>

<template>
    <div class="techno-details">
        <h3>{{techno.name}}</h3>
        <div>{{techno.details}}</div>
    </div>
</template>

<script>
export default {
  name: 'Techno',
  props: ['techno']
}
</script>

<style>

</style>


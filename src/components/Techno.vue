<template>
    <div class="techno-details">
        <h3>{{techno.name}}</h3>
        <div>{{techno.details}}</div>
        <div><small>ajoutée le : {{techno.dateCreation | dateAndTime}}</small></div>
        <div><small>à faire le : {{techno.dateStudy | dateAndTime}}</small></div>
    </div>
</template>

<script>
import format from 'date-fns/format';

export default {
  name: "Techno",
  props: ["techno"],
  filters: {
    dateAndTime(value) {
      return format(value, "DD/MM/YYYY à HH:mm");
    }
  }
};
</script>

<style>

</style>


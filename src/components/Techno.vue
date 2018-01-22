<template>
    <div class="techno-details">
        <h3 v-bind:class="[techno.isPrioritary ? prioritaryClass: '']">{{techno.name}}</h3>
        <div>{{techno.details}}</div>
        <div>Temps consacré {{techno.timeSpentStudying}} minutes</div>
        <div v-if="!isTogglingPriority">{{priorityLevel}}</div>
        <div v-else v-bind:class="[isTogglingPriority ? 'spinner' : '']">
            <div class="bounce1"></div>
            <div class="bounce2"></div>
            <div class="bounce3"></div>
        </div>
        <div>
            <a href="#" v-on:click="togglePriority(techno)">{{priorityText}}</a>
        </div>
        <div><small>ajoutée le : {{techno.dateCreation | dateAndTime}}</small></div>
        <div><small>à faire le : {{techno.dateStudy | dateAndTime}}</small></div>
    </div>
</template>

<script>
import format from "date-fns/format";

export default {
  name: "Techno",
  props: ["techno"],
  data: function() {
    return {
      prioritaryClass: "prioritary",
      priorityText: "modifier la prioriété",
      url: `https://nodetestapi-pnmjtlievk.now.sh/techno/${
        this.techno._id
      }/toggle_priority`,
      isTogglingPriority: false,
      priorityLevel: this.techno.isPrioritary
        ? "Priorité haute"
        : "Priorité basse"
    };
  },
  methods: {
    togglePriority(techno) {
      this.isTogglingPriority = true;
      this.axios.get(this.url).then(response => {
        console.log(response);
        techno.isPrioritary = !techno.isPrioritary;
        if (techno.isPrioritary) {
          this.priorityLevel = "Priorité haute";
          this.priorityText = "Abaisser priorité";
        } else {
          this.priorityLevel = "Priorité basse";

          this.priorityText = "Augmenter priorité";
        }
        this.isTogglingPriority = false;
      });
    }
  },
  filters: {
    dateAndTime(value) {
      return format(value, "DD/MM/YYYY à HH:mm");
    }
  }
};
</script>

<style>
.prioritary {
  background-color: yellow;
}

.spinner {
  margin: 5px auto 0;
  width: 70px;
  text-align: center;
}

.spinner > div {
  width: 5px;
  height: 5px;
  background-color: rgb(10, 218, 27);

  border-radius: 100%;
  display: inline-block;
  -webkit-animation: sk-bouncedelay 1.4s infinite ease-in-out both;
  animation: sk-bouncedelay 1.4s infinite ease-in-out both;
}

.spinner .bounce1 {
  -webkit-animation-delay: -0.32s;
  animation-delay: -0.32s;
}

.spinner .bounce2 {
  -webkit-animation-delay: -0.16s;
  animation-delay: -0.16s;
}

@-webkit-keyframes sk-bouncedelay {
  0%, 80%, 100% { -webkit-transform: scale(0) }
  40% { -webkit-transform: scale(1.0) }
}

@keyframes sk-bouncedelay {
  0%, 80%, 100% { 
    -webkit-transform: scale(0);
    transform: scale(0);
  } 40% { 
    -webkit-transform: scale(1.0);
    transform: scale(1.0);
  }
}
</style>


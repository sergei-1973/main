<template>
  <div class="project" :class="{ complete: project.complete }">
    <div class="actions">
      <h3 @click="showDetails = !showDetails">{{ project.title }}</h3>
      <div class="i">
        <span class="material-icons"> edit </span>
        <span class="material-icons" @click="deleteProject"> delete </span>
        <span class="material-icons done" @click="completeProject"> done </span>
      </div>
    </div>
    <div v-if="showDetails" class="details">
      <p>{{ project.details }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "SingleProject",
  props: ["project"],
  data() {
    return {
      showDetails: false,
      uri: "http://localhost:3000/projects/" + this.project.id,
    };
  },
  methods: {
    deleteProject() {
      fetch(this.uri, { method: "DELETE" })
        .then(() => this.$emit("delete", this.project.id))
        .catch((err) => console.log(err.message));
    },
    completeProject() {
      fetch(this.uri, {
        method: "PATCH",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ complete: !this.project.complete }),
      })
        .then(() => this.$emit("complete", this.project.id))
        .catch((err) => console.log(err.message));
    },
  },
};
</script>

<style>
.project {
  background: white;
  margin: 20px auto;
  padding: 10px 20px;
  border-left: 4px solid crimson;
  border-radius: 6px;
  box-shadow: 1px 2px 3px rgba(0, 0, 0, 0.05);
}
.project .actions h3 {
  cursor: pointer;
}
.project .actions {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.actions .material-icons {
  color: #ccc;
  margin-left: 10px;
  cursor: pointer;
}
.actions .material-icons:hover {
  color: #777;
}
.project.complete {
  border-left: 4px solid teal;
}
.project.complete .done {
  color: teal;
}
</style>

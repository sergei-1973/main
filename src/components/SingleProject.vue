<template>
  <div class="project">
    <div class="actions">
      <h3 @click="showDetails = !showDetails">{{ project.title }}</h3>
      <div class="i">
        <span class="material-icons"> edit </span>
        <span class="material-icons"> delete </span>
        <span class="material-icons"> done </span>
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
    };
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
</style>

<template>
  <div class="form">
    <form @submit.prevent="addProject">
      <label>Title:</label>
      <input v-model="title" type="text" required />

      <label>Details:</label>
      <textarea v-model="details" required></textarea>

      <button>Add Project</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "AddProject",
  data() {
    return {
      title: "",
      details: "",
    };
  },
  methods: {
    addProject() {
      let project = {
        title: this.title,
        details: this.details,
        complete: false,
      };
      fetch("http://localhost:3000/projects", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(project),
      })
        .then(() => this.$router.push("/"))
        .catch((err) => console.log(err.message));
    },
  },
};
</script>

<style>
.form form {
  background: white;
  padding: 20px;
  border-radius: 10px;
}
.form form label {
  display: block;
  margin: 20px 0 10px 0;
  letter-spacing: 1px;
  font-weight: bold;
  text-transform: uppercase;
  color: #bbb;
  font-size: 14px;
}
.form form input {
  width: 100%;
  box-sizing: border-box;
  padding: 10px;
  border: 0;
  border-bottom: 1px solid #ddd;
}
.form form textarea {
  height: 100px;
  width: 100%;
  box-sizing: border-box;
  padding: 10px;
  border: 1px solid #ddd;
}
.form form button {
  display: block;
  padding: 10px;
  margin: 20px auto 0;
  background: teal;
  color: white;
  font-size: 16px;
  border: 0;
  border-radius: 6px;
}
</style>

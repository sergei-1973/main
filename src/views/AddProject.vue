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
  margin: 40px auto;
  padding: 20px;
  border-radius: 10px;
}
.form form label {
  display: block;
  margin: 20px 0 10px 0;
  letter-spacing: 1px;
  font-weight: bold;
  text-transform: uppercase;
  color: #ddd;
  font-size: 14px;
}
.form form input {
  display: inline;
  width: 100%;
  box-sizing: border-box;
  padding: 10px;
  border: 0;
  border-bottom: 1px solid #ddd;
}
.form form textarea {
  display: block;
  height: 100px;
  width: 100%;
  box-sizing: border-box;
  padding: 10px;
  border: 0;
  border-bottom: 1px solid #ddd;
  margin-bottom: 20px;
}
.form form button {
  display: block;
  padding: 8px 16px;
  margin: 30px auto;
  background: teal;
  color: white;
  font-size: 16px;
  border: 0;
  font-weight: bold;
  border-radius: 4px;
}
</style>

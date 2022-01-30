<template>
  <div>
    <h1>
      {{
        edit ? "Edit" : "Add"
      }} Chatroom
    </h1>
    <form @submit.prevent="submit">
      <div class="form-field">
        <label for="name">Name</label>
        <br />
        <input v-model="form.name" type="text" name="name" />
      </div>
      <div>
        <input type="submit" />
      </div>
    </form>
  </div>
</template>

<script>
import axios from "axios";
import { APIURL } from "../constants";
export default {
  name: "ChatroomForm",

  async created() {
    if (this.edit) {
      const { data } = await axios.get(`${APIURL}/api/chat/${this.id}`);
      this.form = data;
    }
  },
};
</script>

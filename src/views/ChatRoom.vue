<template>
  <div>
    <NavBar></NavBar>
    <h1>Chatroom</h1>
    <div id="chat-messages" ref="container">
      <div class="row" v-for="m of chatMessages" :key="m.id">
        <div>
          <b>{{ m.user.name }} - {{ m.created_at }}</b>
        </div>
        <div>{{ m.message }}</div>
      </div>
    </div>
    <form @submit.prevent="sendChatMessage">
      <div class="form-field">
        <label for="message">Message</label>
        <br />
        <input v-model="message" type="text" name="message" />
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
import NavBar from "@/components/NavBar";

export default {
  name: "Chatroom",
  components: {
    NavBar,
  },
  beforeMount() {
    this.getChatMessages();
    this.addChatListener();
  },
  data() {
    return {
      chatMessages: [],
      message: "",
    };
  },
}
</script>

<template>
  <div>
    <h1>
      {{
        edit ? "Edit" : "Add
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

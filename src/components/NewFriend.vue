<template>
  <form @submit.prevent="submitData">
    <div>
      <label for="name">Name</label>
      <input type="text" id="name" v-model="enteredName" />
    </div>
    <div>
      <label for="phone"> Phone </label>
      <input type="tel" id="phone" v-model="enteredPhone" />
    </div>
    <div>
      <label for="email">Email</label>
      <input type="email" v-model="enteredEmail" />
    </div>
    <div>
      <button>Add Contact</button>
    </div>
  </form>
</template>

<script>
export default {
  emits: ['add-contact'],
  data() {
    return {
      enteredName: '',
      enteredPhone: '',
      enteredEmail: '',
    };
  },
  methods: {
    submitData() {
      const newContact = {
        id: new Date().toISOString(),
        name: this.enteredName,
        phone: this.enteredPhone,
        email: this.enteredEmail,
        isFavorite: false,
      };
      this.$emit('add-contact', newContact);
    },
  },
};
</script>

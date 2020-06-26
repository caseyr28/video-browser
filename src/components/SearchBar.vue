<template>
    <div>
        <input v-model.lazy="userInput"
        placeholder="Hey buddy, wydontcha search for a video?"
        />
        <button @click="searchQuery">Search</button>
    </div>
</template>

<script>
export default {
  name: 'SearchBar',
  methods: {
      searchQuery: function() {
        this.$emit('termChange', this.userInput);
      },
    //   onInput: function(event) {
    //     //   console.log(event.target.value);
    //       this.$emit('termChange', event.target.value);
    //   },
  },
  data() {
      return{
          userInput: ''
      }
  }
};
</script>

<style scoped>
    input {
        flex-grow: 2;
        font-size: 30px;
        margin-right: 1rem;
        border: 1px solid #a0e6d9;
        border-radius: 4px;
    }
    ::placeholder{
        color: #6b9991;
    }
    input:focus{
        outline: 1px solid #405c57;
    }
    div {
        display: flex;
        padding: 6rem 20%;
        text-align: center;
        background-color: #b2fff1;
    }
    button {
      border: none;
      background-color: #6b9991;
      color: #f7fffe;
      font-size: 2rem;
      font-weight: normal;
      letter-spacing: .2rem;
    }
    button:hover {
      background-color: #243330;
    }

</style>
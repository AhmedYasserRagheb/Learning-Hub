<template>
    <button :class="mode">
      <slot></slot>
    </button>
  </template>
  
  <script>
  export default {
    props: ['mode']
  }
  </script>
  
  <style scoped>
  button {
    /* padding: 0.75rem 1.5rem; */
    padding: 8px 10px;
    font-family: inherit;
    background-color: #da0c5b;
    border: 1px solid #da0c5b;
    color: white;
    cursor: pointer;
    border-radius: 10px;
    margin-right: 20px;
  }
  
  button:hover,
  button:active {
    background-color: #da0c5b;
    border-color: #da0c5b;
  }
  
  .flat {
    background-color: transparent;
    color: #3a0061;
    border: none;
  }
  
  .flat:hover,
  .flat:active {
    background-color: #edd2ff;
  }
  </style>
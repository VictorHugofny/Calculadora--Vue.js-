<template>
  <button class="button" :class = "{double, triple, operation}">
      {{label}}
  </button>
</template>

<script>
export default {
    props: {
        label: {},
        operation: {type: Boolean},
        double: {type: Boolean},
        triple: {type : Boolean}
    }
}
</script>

<style>
:root{
    --bg-button: rgb(204, 204, 204);
    --border-button: solid 1px #888;

}

.button{
    font-size: 1.4em;
    background-color: var(--bg-button) ;
    border: none;
    border-right: var(--border-button);
    border-bottom: var(--border-button);
    outline:none;
}

.button:active{
    background-color: rgb(143, 143, 143);
}

.button.double{
    grid-column: span 2;
}
.button.triple{
    grid-column: span 3;
}
.button.operation{
    background-color: #fa8231;
    color: #fff;
}
.button.operation:active{
    background-color: #c35104;
}
</style>
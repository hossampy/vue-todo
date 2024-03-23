<template>
  <div class="project">
    <div class="action">
        <h3>{{proj.title}}</h3>
    </div>
    <div class="details">
        <p>{{ proj.details }}</p>
    </div>
  </div>
</template>

<script>
export default {
props:['proj']
}
</script>

<style>
.project{
    margin: 20px auto;
    background: white;
    padding: 10px 20px;
    border-radius: 4px;
    box-shadow: 1px 2px 3px rgba(0, 0, 0, 0.5);
}
h3{
    cursor: pointer;
}
</style>
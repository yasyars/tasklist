<template>
<div class="header">
    <h1>My Task</h1>
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
</div>
</template>

<script>
export default{
    name: "Header"
}
</script>

<style scoped>
    .header{
        background-color : #4F6151;
        text-align: center;
        color : white;
        text-align : center;
        padding : 30px;
        height: 100px;
        width: 600px;
        margin:auto;
        border-radius: 25px 25px 0px 0px;

    }

    .header a{
        color : white;
    }

</style>
<template>
  <div id="app" class="container">
    <Header />
    <router-view/>
  </div>
</template>

<script>
import Header from './components/layout/Header';

export default{
  name : "app",
  components : {
    Header
  }
}

</script>


<style>
  *{
    box-sizing: border-box;
    margin:0;
    padding: 0;
  }

  body{
    font-family: Arial, Helvetica, sans-serif;
    line-height:1.4;
  }

  .btn{
    display: inline-block;
    padding: 7px 20px;
    color : white;
    background: #7D9569;
    border: none;
    cursor: pointer;
  }

  .btn:hover{
    background: #9FAA95;
  }

  .container{
    padding-bottom: 30px;
    background: #f4f4f4;
    border-radius :25px;
    width: 600px;
    margin: auto;
    margin-bottom:20px !important;
    margin-top: 10px !important;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
  }

</style>

<template>
  <div>
    <header>
    <p>我的购物车</p>
    <img src="../static/img/icon_244qi8g9iz3/daohanggouwuche.png">
    </header>
    <goods></goods>
  </div>
</template>

<script>
import goods from './components/goods'

export default {
  name: 'App',
  components: {
    goods
  }
}
</script>

<style>
  *{
    margin: 0;
    padding: 0;
  }
  header{
    width: 100%;
    height: 30px;
    background: rgba(170,20,20);
    position: relative;
  }
  header p{
    width: 100px;
    font-family: "微软雅黑 Light";
    color: #ffffff;
    font-weight: bold;
    font-size: 16px;
    text-align: center;
    line-height: 30px;
    position: absolute;
    left: 600px;
  }
  header img{
    width: 25px;
    height: 25px;
    margin-top: 3px;
    position: absolute;
    left: 693px;
  }

</style>

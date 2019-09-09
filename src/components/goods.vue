<template>
  <div>
    <table>
      <thead class="thead">
        <div class="font t-checkbox"><input type="checkbox" v-model="AllChecked" @change="allCheckChange()"></div>
        <div class="font All-choose">全选</div>
        <div class="font t-goods">商品</div>
        <div class="font t-price">单价</div>
        <div class="font t-quantity">数量</div>
        <div class="font t-sum">小计</div>
      </thead>
      <tbody class="shoppingList">
        <tr class="item" v-for="(item, index) in items">
          <td class="checkbox"><input type="checkbox" class="itemCheck" v-model="checkArray[index]" @change="checkedGoodsSum()"></td>
          <td class="goods">
            <a href=""><img :src="item.src" class="g-img"></a>
            <a href="" class="g-name">{{ item.name }}</a>
          </td>
          <td class="price"><p class="g-price">¥{{item.price}}</p></td>
          <td class="quantity">
            <a href="" @click.prevent="item.quantity = decreaseQuantity(item.quantity)"><img src="../../static/img/icon_244qi8g9iz3/jian.png" class="decreas"></a>
            <input type="text" :value="item.quantity" >
            <a href="" @click.prevent="item.quantity = increaseQuantity(item.quantity)"><img src="../../static/img/icon_244qi8g9iz3/jia.png" class="increas"></a>
          </td>
          <td class="p-sum"><p class="priceSum">¥{{ item.quantity*item.price }}</p></td>
          <td class="delete" @click="DeleteGoods(index)">删除</td>
        </tr>
      </tbody>
    </table>
    <div class="footer">
      <div class="amount">已选择<span>{{ checkedGoodsSum() }}</span>件商品</div>
      <div class="SumPrice">总价：<span>¥{{ checkedPriceSum() }}</span></div>
      <div class="submit"><a href="" class="submit">去结算</a></div>
    </div>
  </div>
</template>

<script>
    export default {
      name: "goods",
      data() {
        return {
          checkArray: ['', '', '', '', ''],
          AllChecked: false,
          checkedItems : [],
          items: [
            {
              name: 'Sony/索尼 WI-SP500 无线防水运动蓝牙耳机 免提通话',
              src: '../../static/img/earphone.jpg',
              price: '719.21',
              quantity: 1
            },
            {
              name: '派克威雅官方商务签字笔男女学生钢笔礼品笔威雅黑色胶杆墨水笔',
              src: '../../static/img/pen.jpg',
              price: '135.50',
              quantity: 1
            },
            {
              name: 'Intel/英特尔酷睿i7 8700k盒装 处理器i7 9700K/KF 8700 电脑CPU',
              src: '../../static/img/IntelCPU.jpg',
              price: '1599.20',
              quantity: 1
            },
            {
              name: '微软 Surface Pro 6 i5 8GB 128GB 12.3英寸 笔记本电脑 平板电脑二合一',
              src: '../../static/img/surfacePro.jpg',
              price: '8719.00',
              quantity: 1
            },
            {
              name: 'Casio卡西欧手表男G-SHOCK未来战士白武士白虎限定男表 GA-400-7A',
              src: '../../static/img/watch.jpg',
              price: '499.50',
              quantity: 1
            }
          ]
        }
      },
      methods: {
        increaseQuantity(num) {
          num++;
          return num;
        },
        decreaseQuantity(num) {
          if (num <= 1) {
            alert("不能在减少啦");
          } else {
            num--;
          }
          return num;
        },
        allCheckChange() {
          this.checkArray.fill(this.AllChecked)
        },
        checkedGoodsSum() {
          let sum = 0;
          for (let i = 0; i < this.checkArray.length; i++) {
            if (this.checkArray[i] == true) {
              sum++;
            }
          }
          return sum;
        },
        checkedPriceSum(){
          let price = 0;
          for(let i = 0; i < this.checkArray.length; i++){
            if (this.checkArray[i] == true) {
              price += this.items[i].price*this.items[i].quantity;
            }
          }
          return price
        },
        DeleteGoods (i) {
          this.items.splice(i,1);
          this.checkArray.splice(i,1)
        }
      }
    }

</script>

<style scoped>
  a{
    text-decoration: none;
    color: #000000;
  }
  input[type='checkbox']{
    width: 16px;
    height: 16px;
  }
  .thead{
    display: block;
    height: 40px;
    width: 1081px;
    background-color: #f5f5f5;
    position: relative;
    left: 8%;
    right: 8%;
  }
  .thead .font{
    font-family: "微软雅黑";
    font-size: 14px;
    float: left;
  }
  .thead > input{
  }
  .thead .t-checkbox{
    position: absolute;
    left: 10px;
    top: 12px;
  }
  .thead .All-choose{
    position: absolute;
    left: 29px;
    top: 10px;
  }
  .thead .t-goods{
    position: absolute;
    left: 215px;
    top: 10px;
  }
  .thead .t-price{
    position: absolute;
    left: 531px;
    top: 10px;
  }
  .thead .t-quantity{
    position: absolute;
    left: 718px;
    top: 10px;
  }
  .thead .t-sum{
    position: absolute;
    left: 877px;
    top: 10px;
  }
  .shoppingList{
    display: block;
    width: 1080px;
    background: #ffffff;
    position: relative;
    left: 8%;
    right: 8%;
    border: .8px solid rgba(240,240,240);
    overflow: hidden;
  }
  .item{
    display: block;
    width: 1080px;
    height: 120px;
    background: #ffffff;
    left: 8%;
    right: 8%;
    border-bottom: 0.9px solid #c0c0c0;
  }
  .checkbox{
    width: 40px;
    height: 120px;
    float: left;
  }
  .itemCheck{
    margin: 10px;
  }
  .goods{
    width: 300px;
    height: 120px;
    float: left;
    position: relative;
  }
  .goods .g-img{
    height: 80px;
    width: 80px;
    position: absolute;
    left: 60px;
    top: 17px;
    border: .8px solid #e3e4e5 ;
  }
  .g-name{
    width: 200px;
    height: 40px;
    display: block;
    position: absolute;
    top: 16px;
    left: 150px;
    font-family: "微软雅黑";
    font-size: 13px;
    line-height: 20px;
  }
  .g-name:hover{
    color: #d40112;
  }
  .price{
    width: 300px;
    height: 120px;
    float: left;
    position: relative;
  }
  .price .g-price{
    position: absolute;
    left: 180px;
    top: 30px;
    font-family: "Microsoft YaHei";
    font-size: 14px;
  }
  .quantity{
    width: 200px;
    height: 120px;
    float: left;
    position: relative;
  }
  .quantity .decreas{
    width: 25px;
    height: 25px;
    position: absolute;
    left: 50px;
    top: 30px;
  }
  input[type='text']{
    width: 40px;
    height: 12px;
    position: absolute;
    left: 70px;
    top: 34.3px;
    text-align: center;
  }
  .quantity .increas{
    width: 25px;
    height: 25px;
    position: absolute;
    left: 109px;
    top: 30px;
  }
  .p-sum{
    width: 150px;
    height: 120px;
    float: left;
    position: relative;
  }
  .p-sum .priceSum{
    position: absolute;
    left: 20px;
    top: 30px;
    font-family: "Microsoft YaHei";
    font-size: 14px;
  }
  .delete {
    font-family: "Microsoft YaHei";
    font-size: 14px;
    padding-top: 25px;
  }
  .delete:hover{
    color: #d40112;
    cursor: pointer;
  }
  .footer{
    height: 45px;
    background: #f5f5f5;
    position: relative;
    font-family: "Microsoft YaHei";
  }
  .amount{
    float: right;
    position: absolute;
    right: 260px;
    top: 10px;
    font-family: "微软雅黑";
    font-size: 14px;
    color: #7c7d7f;
  }
  .amount span{
    color: rgba(178,34,34);
    font-weight: bold;
    display: inline-block;
    margin: 0 2px;
  }
  .SumPrice{
    float: right;
    position: absolute;
    right: 120px;
    top: 8px;
    font-family: "微软雅黑";
    font-size: 14px;
    color: #7c7d7f;
  }
  .SumPrice span{
    font-size: 16px;
    font-weight: bold;
    color: rgba(178,34,34);
  }
  .submit{
    float: right;
    width: 100px;
    height: 45px;
    background-color: #e2231a;
    font-family: "微软雅黑";
    font-weight: bold;
    font-size: 18px;
    line-height: 45px;
    text-align: center;
    color: white;
    letter-spacing: 1px;
  }

</style>

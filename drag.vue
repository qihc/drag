<template>
  <div class="wrap">
    <ul v-for="(itemData,index) in dragData" :key="index">
      <li v-for="(item,index) in itemData" :key="index" :class="{'drag':nodrag(item.id)}">{{item.name}}</li>
    </ul>
    <!-- :class="{'drag':nodrag(item.id)}" -->
  </div>
</template>

<script>
export default {
  name: "drag",
  data() {
    return {
      msg: "Welcome to Your Vue.js App",
      dragData: [
        [
          {
            id: 1,
            name: "苹果"
          },
          {
            id: 2,
            name: "香蕉"
          }
        ],
        [
          {
            id: 7,
            name: "小狗"
          }
        ],
        [
          {
            id: 3,
            name: "beijing"
          },
          {
            id: 4,
            name: "shanghai"
          }
        ],
        [
          {
            id: 5,
            name: "黄瓜"
          },
          {
            id: 6,
            name: "柿子"
          }
        ],
        
      ]
    };
  },
  methods: {
    //当数组中有一个元素时不能拖拽，此时移除class=drag
    arrFindArr(arrlist, key, value) {
      return arrlist.find(element => element[key] == value);
    },
    nodrag(value) {
      let obj = {};
      let ifdrag=true;
      this.dragData.forEach((item, index) => {
        obj = this.arrFindArr(item, "id", value);
        if(obj){
            
            if(item.length<2){
                ifdrag=false;
                console.log(ifdrag)
            } 
        }

       
      });
      return ifdrag
    }
  },
  created() {}
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* {
  margin: 0;
  padding: 0;
  list-style: none;
}
.wrap {
  width: 1000px;
  margin: 20px auto;
}
.wrap ul {
  width: 200px;
  border: 1px solid #eeeeee;
  min-height: 200px;
  margin-right: 10px;
  float: left;
}
li {
  padding: 8px 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
  float: left;
  margin-right: 4px;
  background: #ddd;
}
li.drag {
  background: #fff;
}
</style>

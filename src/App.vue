<template>
  <div class="red">
    <div class="count">第{{count}}手</div>
    <div class="row">
      <Cell @click="onClickCell(0,$event)" :count="count"></Cell>
      <Cell @click="onClickCell(1,$event)" :count="count"></Cell>
      <Cell @click="onClickCell(2,$event)" :count="count"></Cell>
    </div>
    <div class="row">
      <Cell @click="onClickCell(3,$event)" :count="count"></Cell>
      <Cell @click="onClickCell(4,$event)" :count="count"></Cell>
      <Cell @click="onClickCell(5,$event)" :count="count"></Cell>
    </div>
    <div class="row">
      <Cell @click="onClickCell(6,$event)" :count="count"></Cell>
      <Cell @click="onClickCell(7,$event)" :count="count"></Cell>
      <Cell @click="onClickCell(8,$event)" :count="count"></Cell>
    </div>
    <div class="result" v-show="result !==''">{{result}}赢了！！</div>
  </div>
</template>

<script>
import Cell from '@/components/Cell'
export default {
  components:{Cell},
  data(){
    return{
      count:0,
      map:[
        [null,null,null],
        [null,null,null],
        [null,null,null]
      ],
      result:''
    }
  },
  methods:{
    onClickCell(index,text){
      // 3的倍数
      this.map[Math.floor(index/3)][index%3] = text
      this.count++
      this.cell()
    },
    cell(){

      const map = this.map
      // 横排校验
      for(let i = 0;i<=2;i++){
        if( 
           map[i][0] !== null &&
           map[i][0] === map[i][1] &&
           map[i][1]=== map[i][2]){
          this.result =map[i][0]
        }
      }
      // 竖列校验
      for(let j =0; j<=2;j++){
        if( 
           map[0][j] !== null &&
           map[0][j] === map[1][j] &&
           map[1][j]=== map[2][j]){
           this.result = map[0][j] 
        }        
      }
      // 交叉校验
      if(
           map[0][0] !== null &&
           map[0][0] === map[1][1] &&
           map[1][1]=== map[2][2]        
      ){
          this.result = map[0][0]
      }
      // 交叉校验
      if(
           map[0][2] !== null &&
           map[0][2] === map[1][1] &&
           map[1][1]=== map[2][0]        
      ){
          this.result = map[0][2]
      }
      // 验证结果
      if(this.result !==''){
        setTimeout(()=>{
           alert(this.result+'赢了')
        },100)
      }
    }
  }
}
</script>
<style lang="scss">
  .row{
    display:flex;
    justify-content: center;
    align-items: center;
  }
  .count,.result{
    padding:20px 0;
    text-align:center;
  }  
</style>

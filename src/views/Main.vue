<template>
  <div class="wrapper">
    <div class="inner">
      <div class="main">
        <input
          class="mainInput"
          type="text"
          placeholder="나는 이번 여름에 이것을 꼭!!!"
          :value="text"
          @keydown.enter="sendText"
          @input="text = $event.target.value"
        >
        <div
          class="mainButton"
          @click="sendText"
        >
          한다
        </div>
      </div>
      <div class="list">
        <div
          v-for="(item, idx) in list"
          :key="idx"
          class="listItem"
        >
          <input
            type="text"
            class="listInput"
            :value="item.text"
            :readonly="item.readonly"
            @input="item.text = $event.target.value"
          >
          <div class="listButton">
            <div class="modify">
              수정
            </div>
            <div class="delete">
              삭제
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
    name: 'Main',
    data () {
      return {
        text: '',
        list: []
      }
    },
    created() {
      this.getData();
    },
    methods: {
      emptyCheck(val){
        if(val === '' || val === undefined || val === null) return false
        else return true
      },
      sendText () {
        if(this.emptyCheck(this.text)) {
          let text = this.text
          this.text = ''
          this.postData(text)
        }
        else{
          alert('이번 여름에 하고 싶은 일을 적어보세요~')
        }
      },
      getData () {
        axios.get('http://localhost:3000/api/todo/get')
        .then((response) => {

          let list = response.data

          for(let item of list){
            item.readonly = false
          }

          this.list = list

          console.log(list)
        })
        .catch((error) => {
          console.log(error)
        })
      },
      postData (text) {
        axios.post('http://localhost:3000/api/todo/post', {text: text})
        .then((response) => {
          console.log(response)
          this.getData();
        })
        .catch((error) => {
          console.log(error)
        })        
      }
    }
}
</script>

<style scoped>
.wrapper {
  width: calc(100% - 40px);
  margin-left:auto;
  margin-right:auto;
  margin-top: 20px;
}

.inner {
  width: 100%;
}

.main {
  width: 100%;
  margin-left:auto;
  margin-right:auto;
  height: 50px;
  line-height: 50px;
}

.mainInput {
  width: 200px;
  height: inherit;
  line-height: inherit;
  padding-left: 10px;
  padding-right: 10px;
  display: block;
  float: left;
  box-sizing: border-box;
  width: calc(100% - 80px);
  border: none;
  border-bottom: 1px solid rgb(79, 44, 250);
  font-size: 20px;
}

.mainButton {
  float: right;
  text-align: center;
  background-color: rgb(79, 44, 250);
  color: white;
  border-radius: 4px;
  height: 38px;
  line-height: 38px;
  margin-top: 6px;
  width: 60px;
  color: rgb(79, 44, 250);
  border: 1px solid rgb(79, 44, 250);
  background-color: white;
}

.list { 
  width: 100%;
  margin-top: 30px;
}

.listItem {
  height: 40px;
  margin-bottom: 20px;
}

.listInput {
  height: 40px;
  line-height: 40px;
  box-sizing: border-box;
  float: left;
  width: calc(100% - 100px);
  font-size: 18px;
}

.listButton {
  float: left;
  height: 40px;
  width: 80px;
}

.modify {
  width: 40px;
  height: 40px;
  line-height: 40px;
  float: left;
  text-align: center;
}

.delete {
  width: 40px;
  height: 40px;
  line-height: 40px;
  float: right;
  text-align: center;
}
</style>
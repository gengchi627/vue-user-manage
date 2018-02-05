<template>
  <div class="manage tc">
    <el-button class="addBtn" v-on:click="add">新增</el-button>
    <div class="input-area" v-show="showAdd">
      <el-input type="text" placeholder="请输入人员姓名" class="input" v-model="nameValue"></el-input>
      <el-button v-on:click="addUser">确定</el-button>
      <el-button v-on:click="cancel">取消</el-button>
    </div>
    <table class="userTable">
      <tr>
        <th>姓名</th>
        <th>操作</th>
      </tr>
      <tr v-for="(item,index) in users" :key="index">
        <td>{{item.name}}</td>
        <td v-bind:id="index"><span v-on:click="edit" class="pointer">编辑    
          </span><span v-on:click="del" class="pointer">删除</span></td>
      </tr>
    </table>
    <div class="wrap" v-show="showEdit">
      <div class="content">
        <el-input type="text" placeholder="请输入人员姓名" class="input" v-model="newName"></el-input>
        <el-button v-on:click="cancel">取消</el-button>
        <el-button v-on:click="editName">确定</el-button>
      </div>
    </div>
    <footer-nav v-bind:class="{'isManage':isNowPage}"></footer-nav>
  </div>
</template>

<script>import FooterNav from '../../components/footer.vue'
export default{
  components: {
    FooterNav
  },
  data () {
    return {
      isNowPage: true,
      showAdd: false,
      showEdit: false,
      nameValue: '',
      newName: '',
      users: [{'name': 'joe'}, {'name': 'tom'}],
      editId: 0
    }
  },
  methods: {
    add () {
      this.showAdd = true
      this.showEdit = false
    },
    addUser () {
      var name = this.nameValue
      if (name.trim() === '') {
        alert('请添加人员')
      } else {
        var data = {}
        data.name = name
        this.users.push(data)
      }
    },
    del (e) {
      var id = e.target.offsetParent.id
      this.users.splice(id, 1)
    },
    edit (e) {
      this.showAdd = false
      this.showEdit = true
      var id = e.target.offsetParent.id
      this.editId = id
      this.newName = ''
    },
    cancel () {
      this.showEdit = false
      this.showAdd = false
    },
    editName () {
      var name = this.newName
      if (name.trim() === '') {
        alert('请添加人员')
      } else {
        this.users[this.editId].name = this.newName
        this.showEdit = false
      }
    }
  }
}
</script>

<style>
  .addBtn {
    width: 200px;
    background-color: #41b883;
    margin-bottom: 10px;
  }

  .input-area {
    width: 500px;
    margin: 0 auto;
    margin-bottom: 10px;
  }

  .input {
    width: 200px;
  }

  .userTable {
    width: 500px;
    margin: 0 auto;
  }

  .pointer {
    cursor: pointer;
  }
</style>

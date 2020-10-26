<template>
  <el-container class="home-container">
    <el-header>
      <div>
        <img src="https://avatars1.githubusercontent.com/u/9919" alt="">
        <span>admin</span>
      </div>
      <el-button type="info" @click="logout">退出</el-button>
    </el-header>
    <el-container>
      <el-aside :width="isCollapse ? '64px' : '200px'">
        <div class="toggle-button" @click="toggleCollapse">|||</div>
        <el-menu
          background-color="#333744"
          text-color="#fff"
          active-text-color="#409eff" :unique-opened="true" :collapse="isCollapse" :collapse-transition="false">
          <el-submenu :index="item.id + ''" v-for="item in menulist" :key="item.id">
            <template slot="title">
              <i :class="iconsObj[item.id]"></i>
              <span>{{ item.authName }}</span>
            </template>
            <el-menu-item :index="subitem.id + ''"  v-for="subitem in item.children" :key="subitem.id">
              <template slot="title">
                <i class="el-icon-menu"></i>
                <span>{{ subitem.authName }}</span>
              </template>
            </el-menu-item>
          </el-submenu>
        </el-menu>
      </el-aside>
      <el-main>Main</el-main>
    </el-container>
  </el-container>
</template>

<script>
export default {
  data() {
    return {
      menulist: [],
      iconsObj: {
        125: 'iconfont icon-user',
        103: 'iconfont icon-tijikongjian',
        101: 'iconfont icon-shangpingouwudai2',
        102: 'iconfont icon-danju-tianchong',
        145: 'iconfont icon-baobiao'
      },
      isCollapse: false
    }
  },
  created () {
    this.getMenuList()
  },
  methods: {
    logout () {
      window.sessionStorage.clear()
      this.$router.push('/login')
    },
    async getMenuList () {
      const { data: res } = await this.$http.get('menus')
      if (res.meta.status !== 200) return this.$message.error(res.meta.msg)
      this.menulist = res.data
      console.log(res)
    },
    toggleCollapse () {
      this.isCollapse = !this.isCollapse
    }
  }
}
</script>

<style lang="scss" scope>
.el-header{
  background-color: #373d4e;
  display: flex;
  justify-content: space-between;
  padding-left: 0!important;
  align-items: center;
  color: #fff;
  font-size: 20px;
  > div{
    display: flex;
    align-items: center;
  }
  img{
    height: 60px;
    border-radius: 100%;
    margin-right: 10px;
  }
}
.el-aside{
  background-color: #333744;
  .el-menu{
    border-right: none;
  }
  .toggle-button{
    background-color: #4a5064;
    font-size: 10px;
    color: #fff;
    text-align: center;
    letter-spacing: .2em;
    cursor: pointer;
    line-height: 24px;
  }
}
.el-main{
  background-color: #eaedf1;
}
.home-container{
  height: 100%;
}
.iconfont{
  margin-right: 10px;
}
</style>

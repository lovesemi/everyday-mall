<template>
  <div class="home">
    <div class="menu-list">
      <a-menu
        :default-selected-keys="['1']"
        :default-open-keys="['sub1']"
        mode="inline"
        theme="dark"
        :inline-collapsed="collapsed"
      >
        <a-menu-item key="1">
          <a-icon type="pie-chart" />
          <span>Option 1</span>
        </a-menu-item>
        <a-menu-item key="2">
          <a-icon type="desktop" />
          <span>Option 2</span>
        </a-menu-item>
        <a-menu-item key="3">
          <a-icon type="inbox" />
          <span>Option 3</span>
        </a-menu-item>
        <a-sub-menu key="sub1">
          <span slot="title"
            ><a-icon type="mail" /><span>Navigation One</span></span
          >
          <a-menu-item key="5"> Option 5 </a-menu-item>
          <a-menu-item key="6"> Option 6 </a-menu-item>
          <a-menu-item key="7"> Option 7 </a-menu-item>
          <a-menu-item key="8"> Option 8 </a-menu-item>
        </a-sub-menu>
        <a-sub-menu key="sub2">
          <span slot="title"
            ><a-icon type="appstore" /><span>Navigation Two</span></span
          >
          <a-menu-item key="9"> Option 9 </a-menu-item>
          <a-menu-item key="10"> Option 10 </a-menu-item>
          <a-sub-menu key="sub3" title="Submenu">
            <a-menu-item key="11"> Option 11 </a-menu-item>
            <a-menu-item key="12"> Option 12 </a-menu-item>
          </a-sub-menu>
        </a-sub-menu>
      </a-menu>
    </div>
    <div :class="{ 'main-app': true, 'menu-unfold': collapsed }">
      <div class="main-header">
        <a-button
          type="primary"
          style="margin-bottom: 16px"
          @click="toggleCollapsed"
        >
          <a-icon :type="collapsed ? 'menu-unfold' : 'menu-fold'" />
        </a-button>
        <div class="breadcrumb">
          <template>
            <a-breadcrumb>
              <a-breadcrumb-item>首页</a-breadcrumb-item>
              <a-breadcrumb-item><a href="">统计</a></a-breadcrumb-item>
            </a-breadcrumb>
          </template>
        </div>
        <ul class="user-info">
          <li>欢迎您，杰克马<a-icon type="down" /></li>
          <li>退出登录</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      collapsed: false,
    };
  },
  methods: {
    toggleCollapsed() {
      this.collapsed = !this.collapsed;
    },
  },
};
</script>

<style scoped lang='less'>
.home {
  .menu-list {
    width: 180px;
    position: fixed;
    height: 100%;
    .ant-menu {
      height: 100%;
    }
  }
  .main-app {
    margin-left: 180px;
    transition: all 0.3s;
    &.menu-unfold {
      margin-left: 80px;
    }
    .main-header {
      padding-left: 10px;
      height: 50px;
      line-height: 50px;
      border-bottom: 1px solid #eee;
      .breadcrumb {
        display: inline-block;
        margin-left: 20px;
      }
      .user-info {
        float: right;
        cursor: pointer;
        text-align: center;
        li:not(:first-child) {
          display: none;
          &:hover {
            background-color: #eee;
            color: #f40;
            font-weight: 800;
          }
        }
        &:hover {
          li {
            display: block;
          }
        }
      }
    }
  }
}
</style>
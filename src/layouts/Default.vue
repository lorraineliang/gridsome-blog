<template>
  <div >
    <el-container>
       <!-- <section class="page-header" :style="'background-image: linear-gradient(120deg, '+backgroundColorLeft+', '+backgroundColorRight+');color: '+fontColor+';'">
            <div >
              {{ general}}
              
            </div>
        </section> -->

 
      <section class="main-content">
        <div class="el-row">
          <div class="el-col el-col-6" style="padding-right: 10px">
            <div>
              <div class="el-card is-never-shadow">
                <!---->
                <div class="el-card__body">
                  <ul role="menubar" class="el-menu">
                    <li
                      role="menuitem"
                      tabindex="-1"
                      class="el-menu-item is-active"
                      style="padding-left: 20px"
                    >
                     <g-link  to="/"><i class="el-icon-star-off"></i> 最新动态</g-link>
                    
                    </li>
                    <li
                      role="menuitem"
                      tabindex="-1"
                      class="el-menu-item"
                      style="padding-left: 20px"
                    >
                         <g-link to="/social"><i class="el-icon-mobile-phone"></i> <span>社交圈</span></g-link>
                      <!-- <g-link to="/social"><i class="el-icon-mobile-phone"></i> <span>社交圈</span></g-link> -->
                    </li>
                    <li
                      role="menuitem"
                      tabindex="-1"
                      class="el-menu-item"
                      style="padding-left: 20px"
                    >
                      <!-- <i class="el-icon-edit-outline"></i> <span>博客列表</span> -->
                       <g-link to="/blog"><i class="el-icon-edit-outline"></i> <span>博客列表</span></g-link>
                    </li>
                    <li
                      role="menuitem"
                      tabindex="-1"
                      class="el-menu-item"
                      style="padding-left: 20px"
                    >
                      <g-link to="/project"> <i class="el-icon-service"></i> <span>开源项目</span></g-link>
                    </li>
             
                    <!----><!----><!----><!----><!----><!----><!---->
                  </ul>
                </div>
              </div>
             
              <div>
                <div class="el-dialog__wrapper" style="display: none">
                  <div class="el-dialog" style="width: 500px; margin-top: 15vh">
                    <div class="el-dialog__header">
                      <span class="el-dialog__title">绑定Token</span
                      ><button
                        type="button"
                        aria-label="Close"
                        class="el-dialog__headerbtn"
                      >
                        <i class="el-dialog__close el-icon el-icon-close"></i>
                      </button>
                    </div>
                    <!---->
                    <div class="el-dialog__footer">
                      <span class="dialog-footer"
                        ><button
                          type="button"
                          class="el-button el-button--default"
                        >
                          <!----><!----><span>取 消</span>
                        </button>
                        <button
                          type="button"
                          class="el-button el-button--primary"
                        >
                          <!----><!----><span>确 定</span>
                        </button></span
                      >
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        <slot></slot>
        </div>
      </section>
      <el-footer></el-footer>
    </el-container>
  </div>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>
<script>
export default {
  computed:{
    general(){
      return this.$page.general.edges[0].node
    }
  }
}
</script>
<style>
body {
  font-family: -apple-system, system-ui, BlinkMacSystemFont, "Segoe UI", Roboto,
    "Helvetica Neue", Arial, sans-serif;
  margin: 0;
  padding: 0;
  line-height: 1.5;
}

.layout {
  max-width: 760px;
  margin: 0 auto;
  padding-left: 20px;
  padding-right: 20px;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
  height: 80px;
}

.nav__link {
  margin-left: 20px;
}
.page-header {
  padding: 5rem 6rem;
  color: #fff;
  text-align: center;
  background-color: #159957;
  background-image: linear-gradient(120deg, #155799, #159957);
}

.project-name {
  font-size: 3.25rem;
  margin-top: 0;
  margin-bottom: 0.1rem;
}

.project-tagline {
  font-size: 1.25rem;
  margin-bottom: 2rem;
  font-weight: normal;
  opacity: 0.7;
}

.btn:hover {
  color: rgba(255, 255, 255, 0.8);
  text-decoration: none;
  background-color: rgba(255, 255, 255, 0.2);
  border-color: rgba(255, 255, 255, 0.3);
}

a:hover {
  text-decoration: underline;
}

a:active,
a:hover {
  outline: 0;
}

.btn {
  padding: 0.75rem 1rem;
  display: inline-block;
  margin-bottom: 1rem;
  color: rgba(255, 255, 255, 0.7);
  background-color: rgba(255, 255, 255, 0.08);
  border-color: rgba(255, 255, 255, 0.2);
  border-style: solid;
  border-width: 1px;
  border-radius: 0.3rem;
  transition: color 0.2s, background-color 0.2s, border-color 0.2s;
}

a {
  color: #1e6bb8;
  text-decoration: none;
}

.btn + .btn {
  margin-left: 1rem;
}

.main-content {
  max-width: 64rem;
  padding: 30px 0px 30px 0px;
  margin: 0 auto;
  font-size: 1.1rem;
  word-wrap: break-word;
  min-height: 800px;
  width: 100%;
}

.foot {
  max-width: 67rem;
  margin: 0 auto;
  font-size: 12px !important;
  color: #586069 !important;
  word-wrap: break-word;
}
</style>

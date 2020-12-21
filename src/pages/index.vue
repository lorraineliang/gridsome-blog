<template>
<div>
    <section class="page-header" :style="'background-image: linear-gradient(120deg, '+backgroundColorLeft+', '+backgroundColorRight+');color: '+fontColor+';'">
            <div style="position:absolute; top:20px; right:20px; z-index:2;">
                <!-- <el-tooltip effect="dark" :content="fullButton.full?'退出':'全屏'" placement="bottom-end">
                    <el-button @click="full" :icon="fullButton.full?'el-icon-close':'el-icon-rank'" circle></el-button>
                </el-tooltip> -->
            </div>
           
            <h1 class="project-name">{{general.title}}</h1>
            <h2 class="project-tagline">{{general.description}}</h2>
            <a :href="'https://github.com/'+janetwu1" class="btn" target="_blank">GitHub主页</a>
            <a href="https://github.com/janetwu1/vblog" class="btn" target="_blank" v-if="!mini">博客源码</a>
        </section>
  <Layout>
    
         <div class="el-col el-col-18" style="padding-left: 10px;">
            <section>
              <div class="" style="min-height: 600px">
                <div class="el-card is-never-shadow" style="min-height: 400px">
                  <div class="el-card__header">
                    <div><span>{{ $page.posts.edges[0].node.title }}</span></div>
                  </div>
                  <div class="el-card__body">
                    <div
                      style="
                        font-size: 0.9rem;
                        line-height: 1.5;
                        color: rgb(96, 108, 113);
                      "
                    >
                     发布：{{ $page.posts.edges[0].node.created_at }}
                      <br />
                     更新：{{ $page.posts.edges[0].node.updated_at }}
                    </div>
                    <div
                      style="
                        font-size: 1.1rem;
                        line-height: 1.5;
                        color: rgb(48, 49, 51);
                        border-bottom: 1px solid rgb(228, 231, 237);
                        padding: 5px 0px;
                      "
                    >
                      <!-- <pre style="font-family: 微软雅黑">
{{ $page.posts.edges[0].node.description }}
</pre
                      > -->
                    </div>
                    <div class="markdown-body" style="padding-top: 20px" v-html="mdHtml($page.posts.edges[0].node.content)" >
                 
                    </div>
                  </div>
                </div>
                <!---->
                <div class="el-loading-mask" style="display: none">
                  <div class="el-loading-spinner">
                    <svg viewBox="25 25 50 50" class="circular">
                      <circle
                        cx="50"
                        cy="50"
                        r="20"
                        fill="none"
                        class="path"
                      ></circle></svg
                    ><!---->
                  </div>
                </div>
              </div>
            </section>
          </div>
  </Layout>
  </div>
</template>
<page-query>
query{
  posts:allStrapiPost(order:DESC){
    edges{
      node{
        id,
        title,
        content,
        created_at,
        updated_at
      }
    }
  }
  general: allStrapiGeneral{
    edges{
      node{
        id,
        title,
        description,
        cover{
          url
        }
      }
    }
  }

}
</page-query>
<script>
import Layout from '../../src/layouts/Default'
import markdownIt from 'markdown-it'
const md=new markdownIt()

export default {
    name:'homePage',
    components: { Layout },
    computed:{
    general(){
      return this.$page.general.edges[0].node
    }
  },
    methods:{
      mdHtml(markdown){
        return md.render(markdown)
      }
    }

}
</script>

<style>

</style>
<template>

<div>
          
     <!-- <section class="page-header" v-for="edge in $page.general.edges" :key="edge.node[1]" >
     
           
            <h1 class="project-name"> {{ edge.node.title}}</h1>
            <h2 class="project-tagline"> {{ edge.node.description}} </h2>
            <a :href="'https://github.com/'+janetwu1" class="btn" target="_blank">GitHub主页</a>
            <a href="https://github.com/janetwu1/vblog" class="btn" target="_blank" v-if="!mini">博客源码</a>
        </section> -->

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


}
</page-query>
<script>
import Layout from '../../src/layouts/Default'
import markdownIt from 'markdown-it'
const md=new markdownIt()

export default {
    name:'homePage',
    components: { Layout }, 
    methods:{
      mdHtml(markdown){
        return md.render(markdown)
      }
    }

}
</script>

<style>

</style>
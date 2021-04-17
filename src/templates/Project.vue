<template>
  <Layout>
    <el-card shadow="never" style="min-height: 400px">
      <div slot="header">
        <el-row>
          <el-col :span="12">
            <span>{{ $page.project.title }}</span>
          </el-col>
          <!-- <el-col :span="12">
                        <div style="text-align: right;">
                            <el-button @click="$share()" style="padding: 3px 0" type="text" icon="el-icon-share">分享</el-button>
                            <el-button @click="goGithub(project.url)" style="padding: 3px 0" type="text" icon="el-icon-back">前往GitHub</el-button>
                            <el-button @click="more" style="padding: 3px 0" type="text" icon="el-icon-more-outline">更多项目</el-button>
                        </div>
                    </el-col> -->
        </el-row>
      </div>
      <div style="font-size: 0.9rem; line-height: 1.5; color: #606c71">
        发布 {{ $page.project.created_at | date }} <br />
        更新 {{ $page.project.updated_at | date }}
      </div>
      <div
        style="
          font-size: 1.1rem;
          line-height: 1.5;
          color: #303133;
          padding: 20px 0px 0px 0px;
        "
      >
        {{ $page.project.description }}
      </div>

      <div
        v-html="mdHtml($page.project.content)"
        class="markdown-body"
        style="padding-top: 20px"
      ></div>
    </el-card>
  </Layout>
</template>
<page-query>
query($id:ID!){
 project:strapiProject(id:$id){
    id,
    title,
    updated_at,
    description,
    content,
    url,
    star,
    watch,
    fork
  }
}
</page-query>
<script>
import Layout from '../layouts/Default'
import markdownIt from 'markdown-it'
const md=new markdownIt()

export default {
  name:'projectDetailPage',
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
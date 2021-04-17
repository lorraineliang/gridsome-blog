<template>
  <Layout>
    <div class="el-col el-col-18">
      <div v-for="edge in $page.projects.edges" :key="edge.node.id">
        <el-card>
          <div class="el-card__header">
            <el-row>
              <el-col :span="16">
                <span>
                  <g-link
                    :to="'/projectDetail/' + edge.node.id"
                    style="text-decoration: none; cursor: pointer"
                  >
                    {{ edge.node.title }}
                  </g-link>
                </span>
              </el-col>
              <el-col :span="8">
                <div style="text-align: right">
                  <g-link
                    style="padding: 3px 0"
                    type="text"
                    class="el-button el-button--text"
                    icon="el-icon-back"
                    :to="edge.node.url"
                    >项目地址</g-link
                  >
                </div>
              </el-col>
            </el-row>
          </div>
          <div class="el-card__body">
            <div style="font-size: 0.9rem; line-height: 1.5; color: #606c71">
              最近更新 {{ edge.node.updated_at | date }}
            </div>
            <div
              style="
                font-size: 1.1rem;
                line-height: 1.5;
                color: #303133;
                padding: 10px 0px 0px 0px;
              "
            >
              {{ edge.node.description }}
            </div>
          </div>
          <div
            style="font-size: 1.1rem; color: #303133; padding: 10px 15px 0px"
          >
            <el-row>
              <el-col :span="16" style="padding-top: 5px">
                <el-tooltip
                  effect="dark"
                  :content="'star ' + edge.node.star"
                  placement="bottom"
                >
                  <i
                    class="el-icon-star-off"
                    style="margin: 0px 5px 0px 0px"
                  ></i>
                </el-tooltip>
                {{ edge.node.star }}
                <el-tooltip
                  effect="dark"
                  :content="'watch ' + edge.node.watch"
                  placement="bottom"
                >
                  <i class="el-icon-view" style="margin: 0px 5px 0px 15px"></i>
                </el-tooltip>
                {{ edge.node.watch }}
                <el-tooltip
                  effect="dark"
                  :content="'fork ' + edge.node.fork"
                  placement="bottom"
                >
                  <i class="el-icon-bell" style="margin: 0px 5px 0px 15px"></i>
                </el-tooltip>
                {{ edge.node.fork }}
              </el-col>
            </el-row>
          </div>
        </el-card>
      </div>
      <!-- 分页 -->
      <Pager :info="$page.projects.pageInfo" />
    </div>
  </Layout>
</template>
<page-query>
query($page: Int){
 projects: allStrapiProject(perPage:2,page:$page) @paginate{
     pageInfo {
      totalPages
      currentPage
    }

    edges{
      node{
        id,
        title,
        updated_at,
        description,
        url,
        content,
        star,
        watch,
        fork      
      }
    }
  }
}
</page-query>
<script>

import { Pager } from 'gridsome'
export default {
name:"projectPage",
 components: {
    Pager
  },

}
</script>

<style>
.el-card {
  margin-bottom: 10px;
}
</style>
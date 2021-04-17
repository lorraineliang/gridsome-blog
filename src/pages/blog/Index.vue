<template>
  <Layout>
    <div class="el-col el-col-18">
      <div v-for="edge in $page.posts.edges" :key="edge.node.id">
        <el-card>
          <div class="el-card__header">
            <el-row>
              <el-col>
                <span>
                  <g-link :to="'/post/' + edge.node.id">
                    {{ edge.node.title }}
                  </g-link>
                </span>
              </el-col>
            </el-row>
          </div>
          <div class="el-card__body">
            <div style="font-size: 0.9rem; line-height: 1.5; color: #606c71">
              {{ edge.node.updated_at | date }}
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
        </el-card>
      </div>
      <!-- 分页 -->
      <Pager :info="$page.posts.pageInfo" />
    </div>
  </Layout>
</template>
<page-query>
 query($page: Int){
  posts:allStrapiPost(perPage:3,page:$page) @paginate{
     pageInfo {
      totalPages
      currentPage
    }

    edges{
      node{
        id,
        title,
        description,
        content,
        created_at,
        updated_at
      }
    }
  }
}
</page-query>
<script>
import { Pager } from 'gridsome'
export default {
name:"blog",
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
<template>
  <Layout>
     
       <el-card shadow="never" style="min-height: 400px;margin-bottom: 20px;padding: 0px 0px 20px 0px">
                            <el-row style="min-height: 200px; ">
                                <el-col :span="8" v-for="edge in $page.social.edges" :key="edge.node.id" style="padding: 10px">
                                    <el-card shadow="hover" style="font-size: 13px;color: #606266;line-height: 20px">
                                        <i class="el-icon-star-off"></i>&emsp;
                                        <!-- <a @click="$router.push(`/user/social/details/${item.name}`)" style=" text-decoration:none;cursor:pointer">{{item.name}}</a> -->
                                        <!-- <g-link to="">
                                             {{ edge.node.username }}
                                        </g-link> -->
                                        
                                          <g-link :to="edge.node.url" target="_blank" style=" text-decoration:none;cursor:pointer"> {{ edge.node.username }}</g-link>
                                        <br>
                                        <i class="el-icon-message"></i>&emsp;
                                        <g-link :to="edge.node.url" target="_blank" style=" text-decoration:none;cursor:pointer">TA的主页</g-link>
                                        <br>
                                        <img :src="GRIDSOME_API_URL+edge.node.avatar.url" style="width: 100%;border-radius:5px;margin-top: 5px">
                                    </el-card>
                                </el-col>
                            </el-row>
                            <div style="text-align: center;margin-top: 10px">
                                <!-- <el-pagination @current-change="onSelect" background layout="prev, pager, next" :current-page.sync="followers.query.page"
                                    :page-size="followers.query.pageSize" :total="followers.query.pageNumber*followers.query.pageSize">
                                </el-pagination> -->
                            </div>
                      
                        <!-- <div style="min-height: 300px;margin-bottom: 20px;padding: 20px 0px 20px 0px;text-align: center" v-else>
                            <font style="font-size: 30px;color:#dddddd ">
                                <b>(￢_￢) 没有一个粉丝</b>
                            </font>
                        </div> -->
                    
         
        </el-card>
  
  </Layout>

</template>
<page-query>
query{
  social:allStrapiSocial{
    edges{
      node{
        id,
        username,
        url,
        avatar{
          id,
          url
        }
        updated_at
      }
    }
  }
}
</page-query>

<script>
import Layout from '../../../src/layouts/Default'
export default {
  name:'socialPage',
  components: { Layout },

}
</script>

<style>

</style>
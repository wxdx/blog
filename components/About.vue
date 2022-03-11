<template>
<div class="container">
    <div class="content">
      <NotionRenderer :blockMap="blockMap" fullPage />
    </div>
    
    <div class="footer">
       <p>
            © Xiaodong 2020-2021 &nbsp;&nbsp;&nbsp;&nbsp; <a href="https://beian.miit.gov.cn/">皖ICP备2021017870号</a>
        </p>
    </div>
</div>
</template>

<script>
import {
    NotionRenderer,
    getPageBlocks
} from "vue-notion";

export default {
    components: {
        NotionRenderer
    },
    data: () => ({
        blockMap: null
    }),
    async created() {
        // get Notion blocks from the API via a Notion pageId
        this.blockMap = await getPageBlocks("f89ef6bb0f39414b969e9ec9c14f0237");
    },
};
</script>

<style>
@import "vue-notion/src/styles.css";
/* optional Notion-like styles */
.container{
  height: 98vh;
  width: 100%;
  display: grid;
  grid-template-rows:  1fr 40px;
  grid-template-areas: 
    "content"
    "footer";
  gap: 1px;
  
}
.content{
  grid-area: content;
}
.footer{
  grid-area: footer;
  text-align: center;
  
}
p{
  color:#9c9c9c;
}
a {
    text-decoration: none;
    color:#9c9c9c;
}
</style>

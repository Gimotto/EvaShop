<template>
  <b-container fluid>
    <b-row class="header2">
      <b-col xl="3" lg="2" md="2" sm="1">	
	      <div class="slider_vert">
          <template v-if="item && item._links">
            <div v-for="(items,i) in item._links.images_small" :key="i">
              <template v-if="i < 5">
                <img :src="items.href"  :class="{ 'active': activeIndex === i }"  @click="setActive(items, i)"  class="img-thumbnail item_leftslider">
              </template>
            </div>
          </template>
		    </div>
      </b-col>   
      <b-col xl="9" lg="10" md="10" sm="11">	
	      <div class="slider_info">
          <template v-if="item && item._links">
            <div v-for="(items,i) in item._links.images_large" :key="'image_large'+i">
              <template v-if="i < 5">
                <img :class="{ 'active': activeIndex === i }"  @blur="setActive(i)" :src="items.href" :id="'image_large'+i" class="img-thumbnail item_rightslider">
              </template>
            </div>
          </template>
		    </div>
      </b-col>  
    </b-row>
    <hr>
    <div class="item_info">
      <h2>{{item.product_name}}</h2><br>
      <p>{{item.description_headline}}</p>
    </div>
  </b-container>
</template>

<script>
export default {
  name: "ListItemDetailsInfo",
  components: {},
  methods: {
      setActive(items,index){ 
      this.activeIndex = index;
      },

  },
  props: ["item"],
  computed: { 
  },
  data() {
    return {
        activeIndex: 0,
        displayslider:false,
    };
  }
};
</script>

<style scoped>
.header2 {
  margin-top: 50px;
}
.item_leftslider{
    margin-bottom:20px;
    width:100px;
}
.item_rightslider{
    width:650px;
    height:580px;
    display:none;
}
.item_info{
    text-align:center;
    margin-top: 20px;
    margin-bottom: 50px;
}
.active{
 display:block;
 border: 1px solid gray;
}
</style>
<template>
  <div class="menus">        
    <categories v-on:relay="category = arguments[0]"    
      :category="category" :menus="menuCategories" />
    <helper-table :menus="menus" :category="category" v-if="category != ''" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      menus: [], 
      component: '',
      category: '',
    }
  },
  computed: {
    menuCategories() {
      return this.menus.map(menu => menu.category)
      .filter( (val, index, self) => self.indexOf(val) === index )
      .filter(m => m != 'header')
      .filter(m => m != 'category')
      .filter(m => m != '')
    },
  },
  methods: {
    setCategory(value) {
      this.category = value
    }
  },
  mounted() {
    this.$axios.$get('https://nazs.net/api/menus')
    .then(data => {
      this.menus = data
      console.log(this.menus);
    })
  }
}
</script>


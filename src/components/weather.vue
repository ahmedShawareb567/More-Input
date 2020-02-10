<template>
  <div>
    <section class="addingItemsSec">
      <div class="container">
        <div class="row">
          <div class="col-12">
            <h2>More Items: add skills with auto scroll</h2>
            <input
              type="text"
              placeholder="Add"
              v-model="itemTag"
              @keyup.32="addItemFunc()"
              @keyup.13="addItemFunc()"
            />
            <span>
              <li v-for="(item, index) in itemSet" :key="index">
                <i class="fa fa-close" @click="removeItem(index)"></i>
                {{item}}
              </li>
            </span>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>
<script>
export default {
  created() {},
  mounted() {},
  updated() {},
  data() {
    return {
      itemTag: "",
      sets: new Set(),
      itemSet: []
    };
  },
  watch: {},
  methods: {
    addItemFunc() {
      if (this.itemTag != "") {
        this.sets.add(this.itemTag);
        this.itemSet = [...this.sets];
      }
      this.itemTag = "";
    },
    removeItem(elemetIndex) {
      this.sets.delete(this.itemSet[elemetIndex]);
      this.itemSet.splice(elemetIndex, 1);
    }
  }
};
</script>

<template>
  <h2>{{ title }}</h2>
	<div class="total-show">
		<select name="" id="" @change="changeTotalShow">
			<option value="">All</option>
			<option value="5">5</option>
			<option value="10">10</option>
			<option value="20">20</option>
		</select>
	</div>
  <div class="row">
    <template v-for="meme in memes" :key="meme.id">
      <Meme :meme="meme"/>
    </template>
  </div>
</template>

<script>
import { useStore } from "vuex";
import { onMounted, computed } from "vue";
import Meme from "./Meme.vue";

export default {
  components: {
    Meme,
  },
  setup() {
    const store = useStore();
    const memes = computed(() => store.state.memes);

    onMounted(() => {
      store.dispatch("getMemes");
    });

		const changeTotalShow = (e)=> {
			store.dispatch("getMemes", {
				total: e.target.value
			});
		}



    return {
      title: store.state.titleApp,
      memes,
			changeTotalShow
    };
  },
};
</script>

<style scoped>
	.total-show {
		display: flex;
		justify-content: flex-end;
		margin-bottom: 5px;
	}
</style>

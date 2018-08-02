<template>
	<div class="layout">
		<count-num :end="end"></count-num>
	</div>
</template>
<script>
import count from '@/components/count.vue'
export default {
	components:{'count-num':count},
	data () {
		return {
			end:13444
		}
	},
	mounted () {
		setInterval(() => {
			this.end += 3;
		},5000)
	}
}
</script>
<style scoped>
	
</style>
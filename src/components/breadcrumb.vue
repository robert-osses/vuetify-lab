<template>
	<v-breadcrumbs
		v-if="route.meta.breadcrumb ? true : false"
		:items="breadcrumb"
	>
		<template v-slot:prepend>
			<span class="breadCrumbTitle">{{ titulo?.toUpperCase() }}</span>
			<span class="breadCrumbTitle">|</span>
			<router-link
				:to="{name: 'home'}"
				title="Página de Inicio"
				class="homeLink"
			>
				<v-icon size="small" icon="mdi-home"></v-icon>
			</router-link>
			<v-icon icon="mdi-chevron-right"></v-icon>
		</template>
		<template v-slot:divider>
			<v-icon icon="mdi-chevron-right"></v-icon>
		</template>
	</v-breadcrumbs>
</template>

<script setup lang="ts">
	import { computed, ref } from 'vue';
	import { useRoute } from 'vue-router';

	const route = useRoute()
	const titulo = computed(() => <string|null>route.meta.pageTitle)
	const breadcrumb = computed(() => <any|null>route.meta.breadcrumb)
</script>

<style scoped>
.breadCrumbTitle {
	padding-right: 10px;
	font-weight: bold;
}
.homeLink {
	text-decoration: none;
	display: contents;
}
</style>

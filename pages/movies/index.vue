<template>
	<Discover media-type="movie" />
</template>

<script>
import Discover from '~/components/Discover';

export default {
	name: 'DiscoverMovie',
	components: {
		Discover
	},
	head: {
		titleTemplate: 'Discover Movie'
	}
};
</script>

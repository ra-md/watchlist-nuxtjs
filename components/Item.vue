<template>
	<div
		class="bg-white text-black rounded-md overflow-hidden shadow-md"
		:class="{'hover:shadow-outline': !loading}"
	>
		<nuxt-link
			:class="{'cursor-not-allowed': loading}"
			:event="loading ? 'disabled' : 'click'"
			:to="`/${item.title ? 'movies':'tv-show'}/${slug(item)}`"
		>
			<SkeletonLoading
				v-if="loading"
				:height="`${skeletonLoadingHeight} md:h-64`"
				:width="skeletonLoadingWidth"
			/>
			<img
				v-else
				loading="lazy"
				width="500"
				height="750"
				class="rounded-t-md"
				:alt="item.title||item.name"
				:src="`https://image.tmdb.org/t/p/w500/${item.poster_path}`"
			>
			<div class="relative" :class="[loading ? 'p-1' : 'px-1 md:px-2']">
				<SkeletonLoading v-if="loading" height="h-6" rounded="rounded-b-md" />
				<div v-else class="white-space-shadow">
					<p class="text-sm font-medium whitespace-no-wrap md:text-base">
						{{ index ? `${index}. ` : '' }}{{ item.title || item.name }}
					</p>
				</div>
			</div>
		</nuxt-link>
	</div>
</template>

<script>
import SkeletonLoading from './SkeletonLoading';
import convertToSlug from '~/utils/convertToSlug';

export default {
	name: 'Item',
	components: {
		SkeletonLoading
	},
	props: {
		item: {
			type: Object,
			required: true
		},
		loading: {
			type: Boolean,
			required: true
		},
		index: {
			type: Number,
			default: 0
		},
		skeletonLoadingHeight: {
			type: String,
			default: 'h-28'
		},
		skeletonLoadingWidth: {
			type: String,
			default: 'w-full'
		}
	},
	methods: {
		slug(item) {
			return convertToSlug(item);
		}
	}
};
</script>

<template>
    <Filters :filters="filters" />
    <div class="grid grid-cols-1 md:grid-cols-2 xl:grid-cols-3 gap-4">
        <Box v-for="listing in listings.data" :key="listing.id">
            <div>
                <Link :href="route('listing.show', listing.id)">
                    <Price :price="listing.price" class="text-2xl font-bold" />
                    <ListingSpace :listing="listing" class="text-lg" />
                    <ListingAddress :listing="listing" class="text-gray-50" />
                </Link>
            </div>
        </Box>
        <div v-if="listings.data.length" class="w-full flex justify-center mt-4 mb-4">
    <Pagination :links="listings.links"/>
    </div>
    </div>
</template>

<script setup>
    import { Link } from '@inertiajs/vue3';
    import ListingSpace from '@/Components/ListingSpace.vue';
    import ListingAddress from '@/Components/ListingAddress.vue';
    import Box from '@/Components/UI/Box.vue';
    import Price from '@/Components/Price.vue';
    import Pagination from '@/Components/UI/Pagination.vue';
    import Filters from '@/Pages/Index/Components/Filters.vue';

    defineProps({
        listings: Object,
        filters: Object
    })
</script>
<template>
    <section class="text-gray-700 body-font">
        <div class="container mx-auto flex px-5 py-12 items-center justify-center flex-col">
            <img
                class="lg:w-2/6 md:w-3/6 w-5/6 mb-10 object-cover object-center rounded"
                :src="`${photo.url}`"
                :alt="`${title}`"
            />
            <div class="lg:w-2/3 w-full">
                <h1
                    class="title-font sm:text-4xl text-3xl mb-4 font-medium text-gray-900 text-center"
                >
                    {{ title }}
                </h1>
                <div class="post" v-html="body"></div>
            </div>
        </div>
    </section>
</template>

<script>
import axios from 'axios';

export default {
    async asyncData({ params }) {
        const { data } = await axios.get(`https://jam.microcms.io/api/v1/blog/${params.slug}`, {
            headers: { 'X-API-KEY': '272dfa5a-85c6-42c0-9476-0b9a2b47992e' },
        });
        return data;
    },
};
</script>

<style>
</style>
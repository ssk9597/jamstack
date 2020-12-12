<template>
    <div class="mx-auto">
        <div>
            <Header />
            <div class="bg-white py-20 font-sans">
                <div class="text-center pb-12">
                    <h2 class="border-b-2 inline-block text-2xl mx-0 ml-auto">作品</h2>
                </div>
                <div class="flex flex-wrap justify-center align-center">
                    <div
                        v-for="content in contents"
                        :key="content.id"
                        class="container w-full md:w-1/2"
                    >
                        <nuxt-link :to="`/${content.id}`">
                            <div class="overflow-hidden bg-white rounded-lg shadow">
                                <img
                                    class="w-full"
                                    :src="`${content.photo.url}`"
                                    :alt="`${content.title}`"
                                />
                                <div class="p-6 flex flex-col justify-between">
                                    <h3 class="font-medium text-gray-900 mb-4 leading-normal">
                                        {{ content.title }}
                                    </h3>
                                    <p class="inline-flex items-center">
                                        <span class="text-gray-700 text-sm">詳細はこちら</span>
                                    </p>
                                </div>
                            </div>
                        </nuxt-link>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    async asyncData() {
        const { data } = await axios.get('https://jam.microcms.io/api/v1/blog', {
            headers: { 'X-API-KEY': '272dfa5a-85c6-42c0-9476-0b9a2b47992e' },
        });
        return data;
    },
};
</script>

<style>
</style>

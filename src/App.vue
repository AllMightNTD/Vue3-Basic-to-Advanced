<script setup>
import HelloWorld from './components/HelloWorld.vue';
</script>

<template>
    <div>
        <!-- Binding text -->
        <h1 class="text-red-500">hello {{ author.name }}</h1>
        <p>Has published books:</p>
        <span>{{ publishedBooksMessage }}</span>
        <!-- v-text : thay thế dữ liệu hiển thị trong thẻ  -->
        <!-- v-text : không thể ghi đè dữ liệu con ở trong thẻ  -->
        <p v-text="author.channel"></p>
        <!-- Hiển thị HTML trong trình duyệt -->
        <p v-html="author.channelHTML"></p>
        <!-- Liên kết id đến thẻ qua v-bind:id -->
        <h1 v-bind:id="author.headingId">Heading</h1>
        <button v-bind:disabled="author.isDisable" class="border border-red-500">Disable</button>
        <!-- v-bind:class , có nhiều class thì thêm dưới dạng mảng  -->
        <p v-bind:class="author.isSold ? 'sold-out' : 'sold-exit'">Sold Class</p>
        <div :style="customStyles">helloo</div>
    </div>
    <!-- v-if , v-else , v-else-if , v-show -->
    <div>
        <h1 class="text-xl , font-bold text-red-500">v-if , v-else , v-else-if , v-show</h1>
        <!-- Hiển thị h1 nếu num===0 , sử dụng lệnh v-if -->
        <h1 v-if="num === 0">The num is zero</h1>
        <h1 v-else-if="num < 0">The num is relative</h1>
        <h1 v-else-if="num > 0">The num is positive</h1>
        <!-- Dùng v-else ngay sau v-if  -->
        <h1 v-else>Not a number</h1>
        <div v-if="display">
            <h2>Hello</h2>
            <h2>Hi</h2>
            <h2>Name</h2>
        </div>
        <h2 v-show="show">Using V-show</h2>
    </div>

    <div>
        <h1 class="text-xl font-bold text-red-500">Lists Rendering</h1>
        <h2 class="text-md font-bold">v-for</h2>
    </div>
    <!-- v-for with v-if -->
    <template v-for="(data, index) in dataProduct" :key="index">
        <!-- Chỉ mục của các phần tử : index , index bắt đầu từ 0 -->
        <div v-if="data.price > 100">
            <span>{{ index }}</span>
            <h3>{{ data.name }}</h3>
            <p>{{ data.description }}</p>
        </div>
    </template>
</template>

<script>
export default {
    data() {
        return {
            author: {
                name: 'John Doe',
                books: ['Vue 2 - Advanced Guide', 'Vue 3 - Basic Guide', 'Vue 4 - The Mystery'],
                channel: 'Dior',
                channelHTML: '<b>Hello world</b>',
                headingId: 'heading',
                isDisable: true,
                isSold: false,
                isStyle: 'red',
            },
            customStyles: {
                backgroundColor: 'blue',
                color: 'white',
                padding: '10px',
                borderRadius: '5px',
            },

            num: 1,
            display: true,
            show: false,

            dataProduct: [
                {
                    name: 'iphone',
                    description: 'Iphone 13 promax',
                    price: 200,
                },
                {
                    name: 'iphone',
                    description: 'Iphone 12 promax',
                    price: 300,
                },
                {
                    name: 'iphone',
                    description: 'Iphone 11 promax',
                    price: 400,
                },
                {
                    name: 'iphone',
                    description: 'Iphone 10 promax',
                    price: 100,
                },
                {
                    name: 'iphone',
                    description: 'Iphone 09 promax',
                    price: 50,
                },
            ],
        };
    },
    // Xử lý các thay đổi dựa trên tính toán
    computed: {
        publishedBooksMessage() {
            return this.author.books.length > 0 ? 'Yes' : 'No';
        },
    },
};
</script>
<style>
.sold-out {
    color: red;
}
.sold-exit {
    color: yellow;
}
</style>

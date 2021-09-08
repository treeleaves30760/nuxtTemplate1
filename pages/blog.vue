<template>
    <div class="flex">
        <div class="topDescript">
            <v-row align="center">
                <v-col cols="4">
                    <h1>部落格</h1>
                </v-col>
                <v-spacer />
                <v-col cols="4">
                    <v-select
                        v-model="Pages.value"
                        :items="totalPages"
                    >
                    </v-select>
                </v-col>
            </v-row>
            <div v-if="Pages.value == '顯示全部'">
                <h2>{{ Pages.value }}</h2>
            </div>
            <div v-else>
                <h2>目前在第 {{ Pages.value }} 頁</h2>
            </div>
        </div>
        <div v-if="Pages.value == '顯示全部'">
            <div v-for="post in Post_data" :key="post.id">
                <div class="blog_card">
                    <h2>{{ post.title }}</h2>
                    <p>{{ post.body }}</p>
                    <div class="userName">
                        <h5>{{ post.id }} {{ post.userId }}</h5>
                    </div>
                </div>
            </div>
        </div>
        <div v-else>
            <div v-for="post in Post_data" :key="post.id">
                <div v-if="0 >= post.id - Pages.value * 10 && post.id - Pages.value * 10 >= -10" class="blog_card">
                    <h2>{{ post.title }}</h2>
                    <p>{{ post.body }}</p>
                    <div class="userName">
                        <h5>{{ post.id }} {{ post.userId }}</h5>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

export default ({
    data () {
        return {
            Post_data: [],
            Pages: {
                value: 1
            },
            totalPages: ["顯示全部"]
        }
    },
    created() {
        fetch('https://jsonplaceholder.typicode.com/posts')
            .then(response => {
                return response.json();
                })
            .then(json => {
                this.Post_data = json;
                let i = 0;
                for (i in json);
                return i;
                }).then(index => {
                    let i;
                    for(i = 0; i < index / 10; i++) {
                        this.totalPages.push(i + 1);
                    }
                })
    },
    methods: {
    },
})
</script>

<style>
.blog_card{
    margin: 5px 10% 5px 10%;
    padding: 1em;
    background-color: #CCCCCC;
    font-family: Microsoft JhengHei;
    color: black;
};

.userName{
    text-align: right;
}

.PagesChoicer{
    width: 6em;
    background-color: white;
}
</style>
<script setup>

defineProps({
    list: [{
        name: String,
        url: String
    }]
})

</script>

<template>
    <div class="channelExtension">
        <ul class="content">
            <li v-for="(item, index) in list" :key="index">
                <a href="{{ item.url }}">{{ item.name }}</a>
            </li>
        </ul>
    </div>
</template>

<style>
.channelExtension {
    background-color: white;
    border-radius: 6;
    padding: 10px;
}

.content {
    display: flex;
    flex-wrap: wrap;
}

.content li a {
    color: black;
    font-size: 14px;
    text-align: left;
}

</style>
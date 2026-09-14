<script setup>
import axios from 'axios';
import { ref } from 'vue';
const moods = ref(['Happy', 'Sad', 'Angry']);
const subject = ref('');
const entry = ref('');
const mood = ref('Happy');
const message = ref('');


async function submitPost() {
    try {
        await axios.post('http://localhost:8000/posts', {
            subject: subject.value,
            entry: entry.value,
            mood: mood.value
        });
        message.value = 'Post created successfully!';
        subject.value = '';
        entry.value = '';
        mood.value = 'Happy';
    } catch (error) {
        message.value = 'Error: ' + error.message;
    }
}


</script>

<template>
    <div class="table m-2">
        <h3>Add a New Blog Post</h3>

        Subject: <input type='text' size='30' v-model='subject' required>
        <br>

        Entry: <br>
        <textarea name='entry' cols='80' rows='5' v-model='entry' required></textarea>
        <br>

        Mood:
        <select v-model="mood">
            <option v-for="m in moods" :key="m" :value="m">{{ m }}</option>
        </select>
        <br>

        <br>
        <button @click="submitPost">Submit New Post</button>

        <div v-if="message" style="margin-top: 8px;">
            <p>{{ message }}</p>
        </div>

        <hr>
        <RouterLink to="/ViewPosts/">Click here to return to View Posts</RouterLink>
       
    </div>
</template>


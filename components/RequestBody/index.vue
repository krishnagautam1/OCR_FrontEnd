<template>
  <div class="grid justify-items-center">
    <div class="mt-2 flex justify-center rounded-lg border border-dashed border-gray-900/25 px-6 py-10">
      <div class="text-center">
        <div class="mt-4 flex justify-center text-sm leading-6 text-gray-600">
          <label
            for="file-upload"
            class="relative cursor-pointer rounded-md bg-white font-semibold text-indigo-600 focus-within:outline-none focus-within:ring-2 focus-within:ring-indigo-600 focus-within:ring-offset-2 hover:text-indigo-500"
          >
            <span>Upload a file</span>
            <input id="file-upload" name="file-upload" type="file" class="sr-only" @change="handleFileChange" />
          </label>
        </div>
        <p class="text-xs leading-5 text-gray-600">PNG, JPG, GIF up to 10MB</p>
      </div>
    </div>
    <div class="mt-4">
      <button
        @click="uploadFile"
        class="px-4 py-2 bg-blue-500 text-white rounded-md hover:bg-blue-600 focus:outline-none focus:ring focus:border-blue-300"
      >
        Upload File
      </button>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      file: null,
    };
  },
  methods: {
    handleFileChange(event) {
      // Update the 'file' property when a file is selected
      this.file = event.target.files[0];
    },
    uploadFile() {
      // Basic validation
      if (!this.file) {
        alert('Please select a file');
        return;
      }

      // Prepare form data for POST request
      const formData = new FormData();
      formData.append('file', this.file);

      // Perform POST request using axios
      axios
        .post('/api/upload', formData)
        .then((response) => {
          // Handle successful response
          console.log('File uploaded successfully:', response.data);

          // Clear the file input after upload
          this.file = null;
        })
        .catch((error) => {
          // Handle error
          console.error('Error uploading file:', error);
        });
    },
    getJson() {
      // Perform GET request for JSON using axios
      axios
        .get('/api/json')
        .then((response) => {
          // Handle successful response
          console.log('JSON data retrieved successfully:', response.data);
        })
        .catch((error) => {
          // Handle error
          console.error('Error retrieving JSON data:', error);
        });
    },
  },
};
</script>

<style scoped>
/* Add your component-specific styles here */
</style>
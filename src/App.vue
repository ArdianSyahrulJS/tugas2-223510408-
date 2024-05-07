<template>
  <div class="container">
    <h1 :class="{ 'text-red': isRed }" style="font-size: 1.5rem;">WEB SEDERHANA VUE</h1>
    <p :style="{ 'font-size': fontSize + 'px' }">HAI SELAMAT DATANG</p>
    <div class="buttons">
      <button @click="toggleRed">Toggle</button>
      <button @click="increaseFontSize">Tambah Ukuran Font</button>
      <button @click="decreaseFontSize">Kurangi Ukuran Font</button> <!-- Tombol perkecil font -->
    </div>
    
    <input 
      type="text" 
      v-model="inputText" 
      placeholder="Masukkan data"
      @keyup.enter="saveText"
      style="font-size: 0.8rem;"
    >

    <div v-if="savedTexts.length > 0" class="saved-texts">
      <div v-for="(text, index) in savedTexts" :key="index" class="saved-text">
        <p style="font-size: 0.8rem;">{{ text }}</p>
        <button @click="deleteText(index)" style="font-size: 0.8rem;">Hapus</button>
      </div>
    </div>
    
    <div v-if="inputText" class="real-time-text">
      <h2 style="font-size: 1rem;">Mengetik:</h2>
      <p style="font-size: 0.8rem;">{{ inputText }}</p>
    </div>
  

  
  </div>
</template>

<script>
export default {
  data() {
    return {
      isRed: false,
      fontSize: 16,
      totalSavedData: 0,
      inputText: '',
      savedTexts: [],
      showTotal: false, // Tambahkan properti untuk menampilkan total data
    };
  },
  methods: {
    toggleRed() {
      this.isRed = !this.isRed;
    },
    increaseFontSize() {
      this.fontSize += 2;
    },
    decreaseFontSize() {
      if (this.fontSize > 8) {
        this.fontSize -= 2;
      }
    },
    saveText() {
      if (this.inputText.trim() !== '') {
        this.savedTexts.push(this.inputText);
        this.inputText = '';
        this.totalSavedData = this.savedTexts.length;
      }
    },
    deleteText(index) {
      this.savedTexts.splice(index, 1);
      this.totalSavedData = this.savedTexts.length;
    },
    showTotalData() {
      this.showTotal = !this.showTotal; // Toggle showTotal untuk memunculkan atau menyembunyikan total data
    }
  }
};
</script>

<style scoped>
.container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  background-image: url('https://img.freepik.com/free-vector/natural-background-with-mountains-landscape_23-2148258612.jpg?t=st=1715051003~exp=1715054603~hmac=b037e32be47c541c80dd062d7c535bebd2fccb7f5d6795d2ea34f43a2185da0d&w=1060');
  background-size: cover;
  background-position: center;
}

.text-red {
  color: #7469B6;
}

.buttons {
  margin-bottom: 20px;
}

.buttons button {
  padding: 10px 20px;
  margin-right: 10px;
  background-color: #7469B6;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.buttons button:hover {
  background-color: #7469B6;
}

.total-clicks {
  font-weight: bold;
  margin-bottom: 10px;
}

input[type="text"] {
  width: 100%;
  padding: 10px;
  margin-bottom: 20px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.saved-texts {
  margin-bottom: 20px;
}

.saved-text {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 4px;
}

.saved-text button {
  padding: 5px 10px;
  background-color: #7469B6;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.saved-text button:hover {
  background-color: #c82333;
}

.real-time-text {
  padding: 10px;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 4px;
}
.container {
  text-align: center;
}

.quick-count-button {
  padding: 10px 20px;
  background-color: rgb(255, 193, 204);
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  font-size: 16px;
  transition: background-color 0.3s ease;
}

.quick-count-button:hover {
  background-color: #AD88C6;
}
</style>
<template>
  <div class="escitala-container">
    <h1 :style="titleStyles">Cifrado Escítala</h1>
    <div class="form-group">
      <label for="inputText" class="escitala-label">Texto</label>
      <textarea
        class="escitala-textarea"
        id="inputText"
        rows="4"
        v-model="inputText"
      ></textarea>
    </div>
    <div class="form-group">
      <label for="numRounds" class="escitala-label">Número de Vueltas</label>
      <input
        type="number"
        class="escitala-input"
        id="numRounds"
        v-model="numRounds"
      />
    </div>
    <button :class="primaryButtonClass" @click="transformText('encrypt')">Cifrar Texto</button>
    <button :class="secondaryButtonClass" @click="transformText('decrypt')">Descifrar Texto</button>
    <h3 :style="resultTitleStyles">Resultado</h3>
    <p v-if="outputText" class="escitala-result-text">{{ outputText }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputText: '',
      outputText: '',
      numRounds: 2
    };
  },
  computed: {
    titleStyles() {
      return {
        textAlign: 'center',
        fontSize: '24px'
      };
    },
    primaryButtonClass() {
      return {
        'escitala-button': true,
        'primary': true
      };
    },
    secondaryButtonClass() {
      return {
        'escitala-button': true,
        'secondary': true
      };
    },
    resultTitleStyles() {
      return {
        fontSize: '20px',
        marginTop: '20px'
      };
    }
  },
  methods: {
    transformText(action) {
      const text = this.inputText.replace(/\s/g, '');
      const numRows = Math.ceil(text.length / this.numRounds);
      const matrix = Array.from({ length: numRows }, () => Array(this.numRounds).fill(''));

      for (let i = 0; i < numRows; i++) {
        for (let j = 0; j < this.numRounds; j++) {
          const index = action === 'encrypt' ? i * this.numRounds + j : i + j * numRows;
          if (index < text.length) {
            matrix[i][j] = text[index];
          }
        }
      }

      const result = matrix.map(row => row.join('')).join('');
      this.outputText = result;
    }
  }
};
</script>

<style scoped>
.escitala-container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
}

.escitala-label {
  font-size: 18px;
  margin-top: 10px;
}

.escitala-textarea {
  width: 100%;
  padding: 10px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.escitala-input {
  width: 100%;
  font-size: 16px;
}

.escitala-button {
  padding: 10px 20px;
  font-size: 18px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  margin-top: 10px;
}

.primary {
  background-color: #007bff;
  color: #fff;
}

.secondary {
  background-color: #6c757d;
  color: #fff;
  margin-left: 10px;
}

.escitala-result-text {
  background-color: #f2f2f2;
  padding: 10px;
  border-radius: 5px;
  font-size: 16px;
}
</style>

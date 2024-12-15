 Kamu bisa menambahkan fitur **history chat** dan juga memungkinkan pengguna untuk menginputkan pesan melalui terminal (menggunakan `readline` di Node.js). Berikut adalah cara untuk melakukannya:

1. **Menggunakan `readline`**: Kita akan menggunakan `readline` untuk memungkinkan pengguna menginput pesan melalui terminal.
2. **Mempertahankan History Percakapan**: Riwayat percakapan akan disimpan dalam array `messages` yang akan dikirimkan ke API pada setiap permintaan, sehingga percakapan dapat dipahami secara kontekstual.
3. **Menampilkan Respons Secara Dinamis**: Setelah pengguna mengirim pesan, respons dari AI akan ditampilkan, dan percakapan akan terus berlanjut.

### Kode Lengkap dengan History Chat dan Input dari Terminal:

```javascript
import { OpenAI } from "openai";
import readline from "readline";

// Setup OpenAI client
const client = new OpenAI({
  baseURL: "https://api-inference.huggingface.co/v1/",
  apiKey: "hf_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"  // Gantilah dengan API key kamu
});

// Setup readline untuk input terminal
const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout
});

// Riwayat percakapan (akan berlanjut)
let messages = [];

const getResponse = async (userMessage) => {
  // Menambahkan pesan pengguna ke riwayat percakapan
  messages.push({
    role: "user",
    content: userMessage
  });

  // Mengirim permintaan ke OpenAI dengan riwayat percakapan
  const chatCompletion = await client.chat.completions.create({
    model: "Qwen/Qwen2.5-72B-Instruct",  // Ganti dengan model yang diinginkan
    messages: messages, 
    max_tokens: 500
  });

  // Mendapatkan respons dari AI dan menambahkannya ke riwayat
  const aiResponse = chatCompletion.choices[0].message.content;
  messages.push({
    role: "assistant",
    content: aiResponse
  });

  // Mengembalikan respons dari AI
  return aiResponse;
};

// Fungsi utama untuk menjalankan percakapan
const chatLoop = () => {
  rl.question("User: ", async (userMessage) => {
    if (userMessage.toLowerCase() === "exit") {
      console.log("Ending chat...");
      rl.close();
      return;
    }

    // Mendapatkan respons AI untuk pesan pengguna
    const aiResponse = await getResponse(userMessage);

    // Menampilkan respons AI
    console.log("AI: ", aiResponse);

    // Menyuruh pengguna untuk mengirim pesan berikutnya
    chatLoop();
  });
};

// Mulai percakapan
console.log("Chat started! Type 'exit' to end the conversation.");
chatLoop();
```

### Penjelasan Kode:

1. **Menyimpan Riwayat Percakapan**:
   - `messages` adalah array yang menyimpan semua pesan dalam percakapan, baik dari pengguna maupun AI. Setiap kali ada pesan baru dari pengguna atau respons AI, kita menambahkannya ke dalam array `messages`.
   
2. **Menggunakan `readline`**:
   - `readline` memungkinkan kita untuk menerima input dari pengguna melalui terminal. Setiap kali pengguna mengirimkan pesan, kita memanggil `rl.question()` untuk meminta input dan memprosesnya.
   
3. **Loop Percakapan**:
   - Fungsi `chatLoop()` akan terus meminta input pengguna, mengirimkan pesan tersebut ke OpenAI, dan menampilkan respons AI. Ini akan berlanjut hingga pengguna mengetik "exit" untuk mengakhiri percakapan.

4. **Mengirimkan Riwayat Percakapan**:
   - Setiap kali kita mengirim permintaan ke OpenAI API, kita menyertakan riwayat percakapan yang ada pada parameter `messages`. Dengan demikian, OpenAI akan memahami konteks percakapan secara berkelanjutan.

5. **Exit Chat**:
   - Jika pengguna mengetik "exit", percakapan akan berhenti dan program akan keluar.

### Cara Penggunaan:

1. Jalankan kode ini di terminal.
2. Pengguna akan diminta untuk mengirim pesan.
3. Setelah mengetikkan pesan, OpenAI akan memberikan respons berdasarkan pesan yang telah dikirim sebelumnya, mempertahankan konteks percakapan.
4. Ketik "exit" untuk mengakhiri percakapan.

### Contoh Interaksi:

```
Chat started! Type 'exit' to end the conversation.
User: What is the capital of France?
AI: The capital of France is Paris.
User: Can you tell me more about Paris?
AI: Paris is known for its iconic landmarks like the Eiffel Tower and the Louvre Museum.
User: How far is Paris from Germany?
AI: The distance between Paris and Germany depends on the location, but it’s approximately 500 kilometers from the French-German border.
User: exit
Ending chat...
```

Dengan cara ini, percakapan akan terasa lebih alami dan tetap terstruktur, dan pengguna dapat mengirimkan pesan langsung melalui terminal tanpa perlu menulisnya manual dalam kode.

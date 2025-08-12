<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>URL Shortener</title>
<style>
  body {
    font-family: 'SolaimanLipi', Arial, sans-serif;
    background: #f0f2f5;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
  }
  .container {
    background: white;
    padding: 30px 40px;
    border-radius: 10px;
    box-shadow: 0 4px 15px rgba(0,0,0,0.1);
    width: 400px;
    text-align: center;
  }
  h1 {
    color: #333;
    margin-bottom: 25px;
  }
  input[type="text"] {
    width: 100%;
    padding: 12px 15px;
    border-radius: 6px;
    border: 1px solid #ddd;
    font-size: 16px;
    margin-bottom: 15px;
  }
  button {
    background: #4caf50;
    color: white;
    border: none;
    padding: 12px 20px;
    font-size: 16px;
    border-radius: 6px;
    cursor: pointer;
    width: 100%;
  }
  button:hover {
    background: #45a049;
  }
  .result {
    margin-top: 20px;
    font-size: 16px;
    word-break: break-all;
    color: #333;
  }
  .result a {
    color: #2196f3;
    text-decoration: none;
  }
</style>
</head>
<body>

<div class="container">
  <h1>URL Shortener</h1>
  <input type="text" id="urlInput" placeholder="আপনার লম্বা URL এখানে লিখুন" />
  <button onclick="shortenURL()">Shorten করুন</button>
  <div class="result" id="result"></div>
</div>

<script>
  function shortenURL() {
    const urlInput = document.getElementById('urlInput').value.trim();
    const resultDiv = document.getElementById('result');

    if (!urlInput) {
      resultDiv.innerHTML = '<span style="color:red;">অনুগ্রহ করে একটি URL দিন।</span>';
      return;
    }

    // Simple URL validation
    try {
      new URL(urlInput);
    } catch {
      resultDiv.innerHTML = '<span style="color:red;">সঠিক URL দিন।</span>';
      return;
    }

    // Generate short code - random 6 character string
    const chars = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789';
    let shortCode = '';
    for (let i = 0; i < 6; i++) {
      shortCode += chars.charAt(Math.floor(Math.random() * chars.length));
    }

    // Short URL base (এখানে আপনার ডোমেইন বা গুগলের মতো ব্যবহার করতে পারেন)
    const baseURL = 'https://yourdomain.com/'; // পরিবর্তন করুন আপনার ডোমেইন দিয়ে

    const shortURL = baseURL + shortCode;

    // Since এই ফ্রন্টএন্ড কোড, এটা শুধু random কোড বানাবে। ডাটাবেজ ছাড়া এটা কার্যকর শর্টেনার না।

    resultDiv.innerHTML = `আপনার শর্ট URL: <a href="${urlInput}" target="_blank">${shortURL}</a>`;
  }
</script>

</body>
</html>

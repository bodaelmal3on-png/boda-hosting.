mkdir -p server/public

cat > server/public/index.html <<'EOF'
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Boda Hosting</title>
<style>
  body{margin:0;font-family:sans-serif;background:#0d1117;color:#fff;
       display:flex;flex-direction:column;align-items:center;
       justify-content:center;min-height:100vh;text-align:center}
  h1{font-size:2.5rem;margin:0}
  p{color:#8b949e}
  .btn{margin-top:20px;padding:14px 28px;background:#238636;color:#fff;
       border:0;border-radius:10px;font-size:1.1rem}
</style>
</head>
<body>
  <h1>🚀 Boda Hosting</h1>
  <p>استضافة مشاريع Node.js و Python والبوتات</p>
  <button class="btn">ابدأ مشروعك</button>
</body>
</html>
EOF

cat > server/index.js <<'EOF'
const express = require('express');
const path = require('path');
const app = express();
app.use(express.json());
app.use(express.static(path.join(__dirname, 'public')));
app.get('/api/status', (req, res) => res.json({ status: 'running' }));
app.listen(3000, () => console.log('Server on port 3000'));
EOF

node server/index.js


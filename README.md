<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>My Minimal App</title>
</head>
<body>
  <h1>Hello from Vercel!</h1>
  <p>This is a minimal deployed app.</p>
</body>
</html>

from pathlib import Path
import zipfile

# 디렉터리 및 파일 구조 정의
base_path = Path("/mnt/data/minimal_ai_app")
pages_path = base_path / "pages" / "api"
public_path = base_path / "public"

# 디렉터리 생성
pages_path.mkdir(parents=True, exist_ok=True)
public_path.mkdir(parents=True, exist_ok=True)

# 프론트엔드 코드: index.js
index_js_code = """\
import { useState } from "react";

export default function Home() {
  const [question, setQuestion] = useState("");
  const [answer, setAnswer] = useState("");

  const askQuestion = async () => {
    const res = await fetch("/api/ask", {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({ question }),
    });
    const data = await res.json();
    setAnswer(data.answer);
  };

  return (
    <div style={{ padding: 20 }}>
      <h1>질문 앱</h1>
      <textarea
        rows={4}
        value={question}
        onChange={(e) => setQuestion(e.target.value)}
        placeholder="질문을 입력하세요"
        style={{ width: "100%", marginBottom: 10 }}
      />
      <br />
      <button onClick={askQuestion}>질문하기</button>
      <p><strong>답변:</strong> {answer}</p>
    </div>
  );
}
"""

# 백엔드 코드: ask.js
ask_js_code = """\
export default async function handler(req, res) {
  if (req.method !== "POST") {
    return res.status(405).json({ error: "허용되지 않은 메서드입니다." });
  }

  const { question } = req.body;

  if (!question || question.trim() === "") {
    return res.status(400).json({ error: "질문이 비어 있습니다." });
  }

  const fakeAnswer = `당신의 질문: "${question}" 에 대한 답변은 곧 추가될 예정입니다.`;
  res.status(200).json({ answer: fakeAnswer });
}
"""

# 파일 저장
(base_path / "pages" / "index.js").write_text(index_js_code, encoding="utf-8")
(pages_path / "ask.js").write_text(ask_js_code, encoding="utf-8")

# ZIP 파일 생성
zip_path = Path("/mnt/data/minimal-ai-app.zip")
with zipfile.ZipFile(zip_path, "w") as zipf:
    for path in base_path.rglob("*"):
        if path.is_file():
            zipf.write(path, path.relative_to(base_path))

zip_path.name

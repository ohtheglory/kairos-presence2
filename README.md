// /pages/api/ask.js
export default async function handler(req, res) {
  if (req.method !== "POST") {
    return res.status(405).json({ error: "허용되지 않은 메서드입니다." });
  }

  const { question } = req.body;

  if (!question || question.trim() === "") {
    return res.status(400).json({ error: "질문이 비어 있습니다." });
  }

  // 임시 응답: 실제 AI 응답 대신
  const fakeAnswer = `당신의 질문: "${question}" 에 대한 답변은 곧 추가될 예정입니다.`;

  res.status(200).json({ answer: fakeAnswer });
}


- Utilizaremos Gemini de Google, ya que [permite un uso bastante extensivo para prototipos o aplicaciones con poca demanda](https://ai.google.dev/gemini-api/docs/pricing), hasta 1500 req/day.
- https://aistudio.google.com/

Código de ejemplo:

```js
import React, { useState } from "react";
import { GoogleGenerativeAI } from "@google/generative-ai";
import { Form, Button, Card, Spinner } from "react-bootstrap";

const genAI = new GoogleGenerativeAI("YOUR_API_KEY");
const model = genAI.getGenerativeModel({ model: "gemini-1.5-flash" });

const AIChat = () => {
  const [prompt, setPrompt] = useState("");
  const [response, setResponse] = useState("");
  const [loading, setLoading] = useState(false);

  const handleGenerate = async () => {
    if (!prompt) return;
    setLoading(true);
    try {
      const result = await model.generateContent(prompt);
      setResponse(result.response.text());
    } catch (error) {
      console.error("Error generating response:", error);
      setResponse("Failed to generate response.");
    }
    setLoading(false);
  };

  return (
    <div className="container mt-4" style={{ maxWidth: "500px" }}>
      <Card>
        <Card.Body>
          <Form.Group className="mb-3">
            <Form.Control
              type="text"
              value={prompt}
              onChange={(e) => setPrompt(e.target.value)}
              placeholder="Enter a prompt..."
            />
          </Form.Group>
          <Button variant="primary" onClick={handleGenerate} disabled={loading}>
            {loading ? <Spinner as="span" animation="border" size="sm" /> : "Generate"}
          </Button>
          {response && (
            <Card className="mt-3 p-3 bg-light">
              <Card.Body>{response}</Card.Body>
            </Card>
          )}
        </Card.Body>
      </Card>
    </div>
  );
};

export default AIChat;

```

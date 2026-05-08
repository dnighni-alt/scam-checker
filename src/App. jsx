import { useState } from "react";

const styles = `
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap');

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
    background: #f5f5f7;
    color: #1d1d1f;
    min-height: 100vh;
    -webkit-font-smoothing: antialiased;
  }

  .app { min-height: 100vh; background: #f5f5f7; }

  /* NAV */
  .nav {
    background: rgba(255,255,255,0.75);
    backdrop-filter: saturate(180%) blur(20px);
    border-bottom: 1px solid rgba(0,0,0,0.08);
    height: 52px;
    display: flex;
    align-items: center;
    justify-content: center;
    position: sticky;
    top: 0;
    z-index: 100;
  }

  .nav-inner {
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .shield {
    font-size: 20px;
  }

  .nav-title {
    font-size: 17px;
    font-weight: 600;
    color: #1d1d1f;
    letter-spacing: -0.3px;
  }

  /* HERO */
  .hero {
    text-align: center;
    padding: 56px 24px 40px;
  }

  .hero-badge {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    background: #fff;
    border: 1px solid #e5e5ea;
    border-radius: 20px;
    padding: 5px 14px;
    font-size: 13px;
    font-weight: 500;
    color: #6e6e73;
    margin-bottom: 20px;
    box-shadow: 0 1px 4px rgba(0,0,0,0.06);
  }

  .hero-title {
    font-size: clamp(32px, 7vw, 58px);
    font-weight: 800;
    letter-spacing: -2px;
    line-height: 1.05;
    color: #1d1d1f;
    margin-bottom: 14px;
  }

  .hero-title span { color: #ff3b30; }

  .hero-sub {
    font-size: 17px;
    color: #6e6e73;
    font-weight: 400;
    letter-spacing: -0.2px;
    max-width: 420px;
    margin: 0 auto;
    line-height: 1.55;
  }

  /* STATS ROW */
  .stats {
    display: flex;
    justify-content: center;
    gap: 32px;
    padding: 0 24px 40px;
    flex-wrap: wrap;
  }

  .stat {
    text-align: center;
  }

  .stat-num {
    font-size: 24px;
    font-weight: 700;
    color: #1d1d1f;
    letter-spacing: -1px;
  }

  .stat-label {
    font-size: 12px;
    color: #6e6e73;
    font-weight: 400;
    margin-top: 2px;
  }

  /* CONTAINER */
  .container {
    max-width: 680px;
    margin: 0 auto;
    padding: 0 20px 80px;
  }

  /* CARD */
  .card {
    background: #fff;
    border-radius: 18px;
    padding: 26px;
    margin-bottom: 12px;
    box-shadow: 0 2px 12px rgba(0,0,0,0.06);
  }

  .card-title {
    font-size: 13px;
    font-weight: 600;
    color: #6e6e73;
    text-transform: uppercase;
    letter-spacing: 0.5px;
    margin-bottom: 14px;
  }

  /* TYPE SELECTOR */
  .type-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 8px;
    margin-bottom: 0;
  }

  @media(max-width: 400px) { .type-grid { grid-template-columns: 1fr; } }

  .type-btn {
    background: #f5f5f7;
    border: 1.5px solid transparent;
    border-radius: 11px;
    color: #1d1d1f;
    cursor: pointer;
    font-family: inherit;
    font-size: 13px;
    font-weight: 500;
    padding: 11px 12px;
    text-align: left;
    transition: all 0.15s;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .type-btn:hover { background: #ebebed; }

  .type-btn.active {
    background: #fff0ef;
    border-color: #ff3b30;
    color: #ff3b30;
  }

  /* TEXTAREA */
  .field { display: flex; flex-direction: column; gap: 7px; }

  label {
    font-size: 13px;
    font-weight: 500;
    color: #1d1d1f;
  }

  textarea {
    background: #f5f5f7;
    border: 1.5px solid transparent;
    border-radius: 12px;
    color: #1d1d1f;
    font-family: inherit;
    font-size: 15px;
    font-weight: 400;
    line-height: 1.65;
    outline: none;
    padding: 14px;
    resize: vertical;
    transition: all 0.15s;
    width: 100%;
    min-height: 140px;
    letter-spacing: -0.1px;
  }

  textarea:focus {
    background: #fff;
    border-color: #ff3b30;
  }

  textarea::placeholder { color: #adadb8; }

  /* ANALYSE BUTTON */
  .analyse-btn {
    width: 100%;
    background: #ff3b30;
    border: none;
    border-radius: 14px;
    color: #fff;
    cursor: pointer;
    font-family: inherit;
    font-size: 17px;
    font-weight: 600;
    letter-spacing: -0.3px;
    padding: 17px;
    transition: all 0.15s;
    margin-top: 4px;
  }

  .analyse-btn:hover:not(:disabled) { background: #e0342a; }
  .analyse-btn:active:not(:disabled) { transform: scale(0.99); }
  .analyse-btn:disabled { background: #adadb8; cursor: not-allowed; }

  /* LOADING */
  .loading {
    text-align: center;
    padding: 44px 20px;
  }

  .spinner {
    width: 28px;
    height: 28px;
    border: 2.5px solid #f0f0f0;
    border-top-color: #ff3b30;
    border-radius: 50%;
    animation: spin 0.75s linear infinite;
    margin: 0 auto 14px;
  }

  @keyframes spin { to { transform: rotate(360deg); } }

  .loading-text {
    font-size: 15px;
    color: #6e6e73;
  }

  /* RESULT */
  .result-card {
    background: #fff;
    border-radius: 18px;
    overflow: hidden;
    box-shadow: 0 2px 12px rgba(0,0,0,0.08);
    margin-top: 4px;
    animation: fadeUp 0.3s ease;
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(12px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* RISK BANNER */
  .risk-banner {
    padding: 24px;
    text-align: center;
  }

  .risk-banner.low { background: linear-gradient(135deg, #e8f5e9, #f1f8e9); }
  .risk-banner.medium { background: linear-gradient(135deg, #fff8e1, #fff3cd); }
  .risk-banner.high { background: linear-gradient(135deg, #ffebee, #fce4e4); }

  .risk-icon { font-size: 44px; margin-bottom: 10px; }

  .risk-label {
    font-size: 12px;
    font-weight: 600;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    margin-bottom: 4px;
  }

  .risk-label.low { color: #2e7d32; }
  .risk-label.medium { color: #f57f17; }
  .risk-label.high { color: #c62828; }

  .risk-title {
    font-size: 22px;
    font-weight: 700;
    letter-spacing: -0.5px;
    margin-bottom: 6px;
  }

  .risk-title.low { color: #2e7d32; }
  .risk-title.medium { color: #f57f17; }
  .risk-title.high { color: #c62828; }

  .risk-subtitle {
    font-size: 14px;
    color: #6e6e73;
    font-weight: 400;
  }

  /* SCORE BAR */
  .score-section {
    padding: 20px 24px;
    border-bottom: 1px solid #f5f5f7;
  }

  .score-row {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 10px;
  }

  .score-label {
    font-size: 13px;
    font-weight: 500;
    color: #6e6e73;
  }

  .score-num {
    font-size: 13px;
    font-weight: 700;
    color: #1d1d1f;
  }

  .bar-track {
    background: #f0f0f0;
    border-radius: 8px;
    height: 8px;
    overflow: hidden;
  }

  .bar-fill {
    height: 100%;
    border-radius: 8px;
    transition: width 0.8s ease;
  }

  .bar-fill.low { background: #4caf50; }
  .bar-fill.medium { background: #ff9800; }
  .bar-fill.high { background: #f44336; }

  /* DETAILS */
  .details-section {
    padding: 20px 24px;
  }

  .details-title {
    font-size: 13px;
    font-weight: 600;
    color: #6e6e73;
    text-transform: uppercase;
    letter-spacing: 0.5px;
    margin-bottom: 14px;
  }

  .flag-item {
    display: flex;
    gap: 12px;
    padding: 12px 0;
    border-bottom: 1px solid #f5f5f7;
    align-items: flex-start;
  }

  .flag-item:last-child { border-bottom: none; }

  .flag-dot {
    width: 8px;
    height: 8px;
    border-radius: 50%;
    margin-top: 6px;
    flex-shrink: 0;
  }

  .flag-dot.red { background: #ff3b30; }
  .flag-dot.orange { background: #ff9500; }
  .flag-dot.green { background: #34c759; }

  .flag-text {
    font-size: 14px;
    color: #1d1d1f;
    line-height: 1.55;
    letter-spacing: -0.1px;
  }

  /* ACTION SECTION */
  .action-section {
    padding: 20px 24px;
    background: #f9f9f9;
    border-top: 1px solid #f0f0f0;
  }

  .action-title {
    font-size: 13px;
    font-weight: 600;
    color: #6e6e73;
    text-transform: uppercase;
    letter-spacing: 0.5px;
    margin-bottom: 10px;
  }

  .action-text {
    font-size: 14px;
    color: #1d1d1f;
    line-height: 1.6;
    letter-spacing: -0.1px;
  }

  .result-footer {
    padding: 14px 24px;
    display: flex;
    justify-content: flex-end;
    gap: 8px;
    border-top: 1px solid #f0f0f0;
  }

  .footer-btn {
    background: #f5f5f7;
    border: none;
    border-radius: 8px;
    color: #ff3b30;
    cursor: pointer;
    font-family: inherit;
    font-size: 13px;
    font-weight: 500;
    padding: 7px 14px;
    transition: background 0.15s;
  }

  .footer-btn:hover { background: #ebebed; }

  /* ERROR */
  .error {
    background: #fff2f2;
    border: 1.5px solid #ffcdd2;
    border-radius: 12px;
    color: #c62828;
    font-size: 14px;
    padding: 14px 18px;
    margin-top: 10px;
  }
`;

const TYPES = [
  { id: "email", label: "Email", icon: "📧" },
  { id: "text", label: "Text / SMS", icon: "💬" },
  { id: "job", label: "Job Offer", icon: "💼" },
  { id: "website", label: "Website / Link", icon: "🔗" },
];

export default function App() {
  const [type, setType] = useState("email");
  const [input, setInput] = useState("");
  const [result, setResult] = useState(null);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState("");

  const analyse = async () => {
    if (!input.trim()) { setError("Please paste some content to analyse."); return; }
    setError(""); setLoading(true); setResult(null);

    const prompt = `You are a scam detection expert. Analyse the following ${type} content for scam indicators.

Content to analyse:
"""
${input}
"""

Respond ONLY with a valid JSON object in this exact format (no markdown, no extra text):
{
  "score": <number 0-100 representing scam likelihood>,
  "level": "<low|medium|high>",
  "summary": "<one sentence verdict>",
  "flags": [
    { "type": "<red|orange|green>", "text": "<specific observation about this content>" },
    { "type": "<red|orange|green>", "text": "<specific observation>" },
    { "type": "<red|orange|green>", "text": "<specific observation>" }
  ],
  "action": "<clear practical advice on what the person should do>"
}

Rules:
- red = scam red flag found in the content
- orange = suspicious element worth noting
- green = legitimate signal found
- Be specific to the actual content, not generic
- score 0-30 = low risk, 31-65 = medium risk, 66-100 = high risk
- level must match the score range
- Give 3-5 flags total`;

    try {
      const res = await fetch("https://api.anthropic.com/v1/messages", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({
          model: "claude-sonnet-4-20250514",
          max_tokens: 1000,
          messages: [{ role: "user", content: prompt }],
        }),
      });
      const data = await res.json();
      if (data.error) throw new Error(data.error.message);
      const text = data.content?.map((b) => b.text || "").join("") || "";
      const clean = text.replace(/```json|```/g, "").trim();
      setResult(JSON.parse(clean));
    } catch {
      setError("Something went wrong. Please try again.");
    } finally {
      setLoading(false);
    }
  };

  const reset = () => { setResult(null); setInput(""); setError(""); };

  const riskMeta = {
    low: { icon: "✅", title: "Looks Legitimate", subtitle: "No major scam indicators found" },
    medium: { icon: "⚠️", title: "Proceed with Caution", subtitle: "Some suspicious elements detected" },
    high: { icon: "🚨", title: "Likely a Scam", subtitle: "Multiple scam indicators found" },
  };

  const meta = result ? riskMeta[result.level] : null;

  return (
    <>
      <style>{styles}</style>
      <div className="app">

        <div className="nav">
          <div className="nav-inner">
            <span className="shield">🛡️</span>
            <span className="nav-title">Scam Checker</span>
          </div>
        </div>

        <div className="hero">
          <div className="hero-badge">🤖 Powered by AI</div>
          <h1 className="hero-title">Is it a <span>scam?</span></h1>
          <p className="hero-sub">Paste any suspicious message, email, or job offer. Get an instant AI-powered verdict.</p>
        </div>

        <div className="stats">
          <div className="stat">
            <div className="stat-num">3.4B</div>
            <div className="stat-label">Phishing emails sent daily</div>
          </div>
          <div className="stat">
            <div className="stat-num">€47B</div>
            <div className="stat-label">Lost to scams in 2024</div>
          </div>
          <div className="stat">
            <div className="stat-num">90%</div>
            <div className="stat-label">Are preventable</div>
          </div>
        </div>

        <div className="container">

          <div className="card">
            <div className="card-title">What are you checking?</div>
            <div className="type-grid">
              {TYPES.map((t) => (
                <button key={t.id} className={`type-btn ${type === t.id ? "active" : ""}`} onClick={() => setType(t.id)}>
                  <span>{t.icon}</span> {t.label}
                </button>
              ))}
            </div>
          </div>

          <div className="card">
            <div className="field">
              <label>Paste the content here</label>
              <textarea
                placeholder={`Paste the suspicious ${type} content here...`}
                value={input}
                onChange={(e) => setInput(e.target.value)}
              />
            </div>
          </div>

          {error && <div className="error">{error}</div>}

          <button className="analyse-btn" onClick={analyse} disabled={loading}>
            {loading ? "Analysing…" : "🔍 Check for Scam"}
          </button>

          {loading && (
            <div className="loading">
              <div className="spinner" />
              <div className="loading-text">Analysing for scam indicators…</div>
            </div>
          )}

          {result && meta && (
            <div className="result-card">
              <div className={`risk-banner ${result.level}`}>
                <div className="risk-icon">{meta.icon}</div>
                <div className={`risk-label ${result.level}`}>{result.level} risk</div>
                <div className={`risk-title ${result.level}`}>{meta.title}</div>
                <div className="risk-subtitle">{result.summary}</div>
              </div>

              <div className="score-section">
                <div className="score-row">
                  <span className="score-label">Scam Risk Score</span>
                  <span className="score-num">{result.score}/100</span>
                </div>
                <div className="bar-track">
                  <div className={`bar-fill ${result.level}`} style={{ width: `${result.score}%` }} />
                </div>
              </div>

              <div className="details-section">
                <div className="details-title">What we found</div>
                {result.flags?.map((f, i) => (
                  <div key={i} className="flag-item">
                    <div className={`flag-dot ${f.type}`} />
                    <div className="flag-text">{f.text}</div>
                  </div>
                ))}
              </div>

              <div className="action-section">
                <div className="action-title">What you should do</div>
                <div className="action-text">{result.action}</div>
              </div>

              <div className="result-footer">
                <button className="footer-btn" onClick={analyse}>Recheck</button>
                <button className="footer-btn" onClick={reset}>Check Another</button>
              </div>
            </div>
          )}
        </div>
      </div>
    </>
  );
}

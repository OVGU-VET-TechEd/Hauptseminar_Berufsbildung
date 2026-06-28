<!--
author:   Seminar für Lehrerbildung – Berufliche Schulen Sachsen-Anhalt
email:    ki-seminar@example.org
version:  1.0.0
language: de
narrator: Deutsch Female

comment:  KI im Unterricht – Hauptseminar für Lehramtsanwärter:innen an Beruflichen Schulen.
          120 Min. Inhalt + 30 Min. Diskussion. Themen: Grundbegriffe, Kompetenzrahmen,
          Prompting, Datenschutz & Local AI, KI-Agenten.
          Öffnen mit: https://liascript.github.io/course/?URL

@style
/* ── Globale Stile für den Workshop ── */
/* Flip cards: inline styles used — no CSS class rules needed */
.flip-def   { font-size: .88rem; line-height: 1.55; color: #d0e8ff; }
.flip-tag   { display: inline-block; font-size: .7rem; font-weight: 600;
              background: rgba(96,200,255,.15); color: #60c8ff;
              padding: 2px 8px; border-radius: 20px; margin-top: 8px; }

.amp-row { display: flex; align-items: flex-start; gap: 14px; padding: 12px 16px;
           border-radius: 12px; margin-bottom: 10px; border: 1px solid transparent; }
.amp-row.gruen { background: rgba(16,185,129,.1); border-color: rgba(16,185,129,.35); }
.amp-row.gelb  { background: rgba(245,158,11,.1);  border-color: rgba(245,158,11,.35); }
.amp-row.rot   { background: rgba(248,113,113,.1); border-color: rgba(248,113,113,.35); }
.amp-led { width: 18px; height: 18px; border-radius: 50%; flex-shrink: 0; margin-top: 3px; }
.amp-row.gruen .amp-led { background: #10b981; box-shadow: 0 0 10px #10b981; }
.amp-row.gelb  .amp-led { background: #f59e0b; box-shadow: 0 0 10px #f59e0b; }
.amp-row.rot   .amp-led { background: #f87171; box-shadow: 0 0 10px #f87171; }
.amp-title  { font-weight: 700; font-size: .9rem; margin-bottom: 3px; }
.amp-row.gruen .amp-title { color: #10b981; }
.amp-row.gelb  .amp-title { color: #f59e0b; }
.amp-row.rot   .amp-title { color: #f87171; }
.amp-text { font-size: .83rem; color: #8aa8c0; line-height: 1.5; }

.agent-box { background: #1a2744; border: 1px solid rgba(100,160,255,.2); border-radius: 10px;
             padding: 10px 14px; text-align: center; min-width: 90px; }
.agent-box.hl { border-color: #60c8ff; background: rgba(96,200,255,.1); }
.agent-icon { font-size: 1.4rem; }
.agent-name { font-size: .8rem; font-weight: 700; color: #60c8ff; margin-top: 4px; }
.agent-role { font-size: .68rem; color: #5a7a99; margin-top: 2px; }

.info-box { background: rgba(96,200,255,.07); border-left: 4px solid #60c8ff;
            border-radius: 0 10px 10px 0; padding: 12px 16px; margin: 12px 0; }
.warn-box { background: rgba(245,158,11,.07); border-left: 4px solid #f59e0b;
            border-radius: 0 10px 10px 0; padding: 12px 16px; margin: 12px 0; }
.ok-box   { background: rgba(16,185,129,.07); border-left: 4px solid #10b981;
            border-radius: 0 10px 10px 0; padding: 12px 16px; margin: 12px 0; }

.pb-row { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-bottom: 10px; }
.pb-row label { display: block; font-size: .75rem; font-weight: 600;
                color: #5a7a99; text-transform: uppercase; margin-bottom: 4px; }
.pb-row input, .pb-row select, .pb-row textarea {
  width: 100%; background: rgba(0,0,0,.25); border: 1px solid rgba(100,160,255,.2);
  border-radius: 8px; padding: 8px 10px; color: #d0e8ff; font-size: .85rem;
  transition: .2s; resize: vertical; }
.pb-row input:focus, .pb-row select:focus, .pb-row textarea:focus {
  outline: none; border-color: #60c8ff; }
#pb-out { background: rgba(0,0,0,.3); border: 1px solid rgba(100,160,255,.2);
          border-radius: 10px; padding: 14px 16px; font-family: monospace;
          font-size: .8rem; line-height: 1.65; white-space: pre-wrap;
          color: #80c8e8; min-height: 80px; margin-top: 10px; }

.cw-btn { padding: 6px 13px; border-radius: 8px; border: 1px solid rgba(100,160,255,.2);
          background: #1a2744; color: #8aa8c0; font-size: .78rem; cursor: pointer;
          font-weight: 600; margin: 3px; transition: .2s; }
.cw-btn.act { background: #1a4a88; border-color: #60c8ff; color: #fff; }
.cw-grid { display: grid; grid-template-columns: repeat(4,1fr); gap: 8px; margin: 12px 0; }
.cw-col { background: #1a2744; border-radius: 10px; padding: 12px;
          border-top: 4px solid #60c8ff; font-size: .78rem; }
.cw-col-hd { font-size: .68rem; font-weight: 700; text-transform: uppercase;
             letter-spacing: .04em; margin-bottom: 4px; }
.cw-col-lvl { font-size: .68rem; color: #5a7a99; font-style: italic; margin-bottom: 6px; }
.cw-col-txt { line-height: 1.5; color: #c0d8ef; }
.cw-tag { display: inline-block; font-size: .62rem; background: rgba(96,200,255,.12);
          color: #60c8ff; padding: 1px 5px; border-radius: 4px; margin: 2px 1px; }
.cw-synth { background: rgba(16,185,129,.08); border-left: 4px solid #10b981;
            border-radius: 0 10px 10px 0; padding: 12px 16px; font-size: .8rem;
            line-height: 1.55; color: #c0d8ef; margin-top: 10px; }

.disc-card { background: #1a2744; border: 1px solid rgba(100,160,255,.2); border-radius: 12px;
             padding: 14px 16px; cursor: pointer; margin-bottom: 10px; transition: .2s; }
.disc-card:hover { border-color: rgba(167,139,250,.5); }
.disc-q { font-weight: 700; font-size: .9rem; color: #a78bfa;
          display: flex; justify-content: space-between; }
.disc-body { display: none; margin-top: 10px; font-size: .82rem; color: #8aa8c0; line-height: 1.6; }
.disc-body.open { display: block; }
.disc-min { font-size: .7rem; color: #f59e0b; }

@end
-->

# KI im Unterricht

> **Hauptseminar Berufliche Schulen · Sachsen-Anhalt 2025/26**
>
> 120 Min. Inhalt + 30 Min. Diskussion
>
> 🎧 TTS: Drücke `▶` für Sprechtext (oben rechts)

                          --{{0}}--
Herzlich willkommen! Heute erkunden wir KI aus der Lehrerperspektive:
von den Grundbegriffen bis zu KI-Agenten, die Unterrichtsmaterial fast
selbstständig erstellen. Ihr bekommt am Ende ein konkretes Handlungsprodukt.
Klickt auf die Pfeile rechts oben, um weiterzumachen.

                          {{1}}
| Block | Inhalt | Zeit |
|:-----:|--------|-----:|
| 1 | KI-Grundbegriffe + Quiz | 35 Min |
| 2 | Kompetenzrahmen + Crosswalk | 25 Min |
| 3 | Prompten & Materialerstellung | 20 Min |
| 4 | Datenschutz & Local AI | 15 Min |
| 5 | KI-Agenten & BMAD-Methode | 15 Min |
| 6 | Handlungsprodukt | 10 Min |
| 💬 | Diskussion | 30 Min |

---

## Block 1: KI-Grundbegriffe

> 📖 **11 Begriffe · 3 Seiten Flip Cards · 1 Quiz**
>
> Klick auf eine Karte → sie dreht sich und zeigt die Erklärung.

                          --{{0}}--
Im ersten Block klären wir die wichtigsten Begriffe.
Nicht als Frontalvortrag — ihr klickt euch durch interaktive Flip Cards.
Das schafft ein gemeinsames Vokabular für alles, was danach kommt.

---

### Grundbegriffe I – Prompt & Token

                          --{{0}}--
Fangen wir mit den vier Grundbausteinen an, die ihr bei jeder KI-Arbeit braucht:
Prompt, Token, Systemprompt und Interaktionsprompt.

<div style="display:grid;grid-template-columns:1fr 1fr;gap:14px;margin-top:8px;">

<div onclick="(function(w){var f=w.querySelector('.fc');var b=w.querySelector('.bc');if(f.style.display==='none'){f.style.display='flex';b.style.display='none';}else{f.style.display='none';b.style.display='flex';}}) (this)" style="cursor:pointer;margin-bottom:0;">
  <div class="fc" style="display:flex;flex-direction:column;justify-content:center;padding:18px 20px;background:#1a2744;border:1px solid rgba(100,160,255,.25);border-radius:12px;min-height:150px;">
    <div style="font-size:2rem;margin-bottom:8px;">💬</div>
    <div style="font-size:1.1rem;font-weight:700;color:#60c8ff;">Prompt</div>
    <div style="font-size:.72rem;color:#5a7a99;margin-top:6px;">👆 Klicken zum Aufdecken</div>
  </div>
  <div class="bc" style="display:none;flex-direction:column;justify-content:center;padding:18px 20px;background:#0f3060;border:1px solid rgba(100,200,255,.4);border-radius:12px;min-height:150px;">
    <div style="font-size:.88rem;line-height:1.55;color:#d0e8ff;">Der <strong>Text oder die Anweisung</strong>, den du an ein KI-Modell schickst. Er legt fest, was die KI tun soll — von „Erkläre mir…" bis zu komplexen Aufgabenbeschreibungen.</div>
    <div style="display:inline-block;font-size:.7rem;font-weight:600;background:rgba(96,200,255,.15);color:#60c8ff;padding:2px 8px;border-radius:20px;margin-top:8px;">Eingabe → Verarbeitung → Ausgabe</div>
  </div>
</div>

<div onclick="(function(w){var f=w.querySelector('.fc');var b=w.querySelector('.bc');if(f.style.display==='none'){f.style.display='flex';b.style.display='none';}else{f.style.display='none';b.style.display='flex';}}) (this)" style="cursor:pointer;margin-bottom:0;">
  <div class="fc" style="display:flex;flex-direction:column;justify-content:center;padding:18px 20px;background:#1a2744;border:1px solid rgba(100,160,255,.25);border-radius:12px;min-height:150px;">
    <div style="font-size:2rem;margin-bottom:8px;">🔢</div>
    <div style="font-size:1.1rem;font-weight:700;color:#60c8ff;">Token</div>
    <div style="font-size:.72rem;color:#5a7a99;margin-top:6px;">👆 Klicken zum Aufdecken</div>
  </div>
  <div class="bc" style="display:none;flex-direction:column;justify-content:center;padding:18px 20px;background:#0f3060;border:1px solid rgba(100,200,255,.4);border-radius:12px;min-height:150px;">
    <div style="font-size:.88rem;line-height:1.55;color:#d0e8ff;">Die <strong>kleinste Verarbeitungseinheit</strong> eines Sprachmodells. Auf Englisch ≈ ¾ Wort, auf Deutsch oft noch weniger. „Unterrichtsmaterial" = 4–5 Tokens. Bestimmt Kosten und Kontextlänge.</div>
    <div style="display:inline-block;font-size:.7rem;font-weight:600;background:rgba(96,200,255,.15);color:#60c8ff;padding:2px 8px;border-radius:20px;margin-top:8px;">~0,75 Wörter/Token (EN) · Deutsch oft kürzer</div>
  </div>
</div>

<div onclick="(function(w){var f=w.querySelector('.fc');var b=w.querySelector('.bc');if(f.style.display==='none'){f.style.display='flex';b.style.display='none';}else{f.style.display='none';b.style.display='flex';}}) (this)" style="cursor:pointer;margin-bottom:0;">
  <div class="fc" style="display:flex;flex-direction:column;justify-content:center;padding:18px 20px;background:#1a2744;border:1px solid rgba(100,160,255,.25);border-radius:12px;min-height:150px;">
    <div style="font-size:2rem;margin-bottom:8px;">⚙️</div>
    <div style="font-size:1.1rem;font-weight:700;color:#60c8ff;">Systemprompt</div>
    <div style="font-size:.72rem;color:#5a7a99;margin-top:6px;">👆 Klicken zum Aufdecken</div>
  </div>
  <div class="bc" style="display:none;flex-direction:column;justify-content:center;padding:18px 20px;background:#0f3060;border:1px solid rgba(100,200,255,.4);border-radius:12px;min-height:150px;">
    <div style="font-size:.88rem;line-height:1.55;color:#d0e8ff;">Eine <strong>versteckte Hintergrundanweisung</strong>, die vor dem Gespräch definiert: Rolle, Ton, Sprache, Grenzen. Lernende sehen ihn nicht. Entwickler:innen nutzen ihn, um KI zu konfigurieren.</div>
    <div style="display:inline-block;font-size:.7rem;font-weight:600;background:rgba(167,139,250,.15);color:#a78bfa;padding:2px 8px;border-radius:20px;margin-top:8px;">„Du bist ein freundlicher Lernassistent…"</div>
  </div>
</div>

<div onclick="(function(w){var f=w.querySelector('.fc');var b=w.querySelector('.bc');if(f.style.display==='none'){f.style.display='flex';b.style.display='none';}else{f.style.display='none';b.style.display='flex';}}) (this)" style="cursor:pointer;margin-bottom:0;">
  <div class="fc" style="display:flex;flex-direction:column;justify-content:center;padding:18px 20px;background:#1a2744;border:1px solid rgba(100,160,255,.25);border-radius:12px;min-height:150px;">
    <div style="font-size:2rem;margin-bottom:8px;">🗣️</div>
    <div style="font-size:1.1rem;font-weight:700;color:#60c8ff;">Interaktionsprompt</div>
    <div style="font-size:.72rem;color:#5a7a99;margin-top:6px;">👆 Klicken zum Aufdecken</div>
  </div>
  <div class="bc" style="display:none;flex-direction:column;justify-content:center;padding:18px 20px;background:#0f3060;border:1px solid rgba(100,200,255,.4);border-radius:12px;min-height:150px;">
    <div style="font-size:.88rem;line-height:1.55;color:#d0e8ff;">Die <strong>sichtbare Nutzereingabe</strong> im laufenden Gespräch. Jede Nachricht erweitert den Kontext. Anders als der Systemprompt: dynamisch, sichtbar, nutzerseitig.</div>
    <div style="display:inline-block;font-size:.7rem;font-weight:600;background:rgba(96,200,255,.15);color:#60c8ff;padding:2px 8px;border-radius:20px;margin-top:8px;">Sichtbar · Dynamisch · Kontextbildend</div>
  </div>
</div>

</div>

---

### Grundbegriffe II – Modelle & Formate

                          --{{0}}--
Jetzt geht es technischer: LLM, Parameter, Kontextfenster und der Unterschied zwischen
Text- und PDF-Formaten — besonders wichtig für die Arbeit mit eigenen Materialien.

<div style="display:grid;grid-template-columns:1fr 1fr;gap:14px;margin-top:8px;">

<div onclick="(function(w){var f=w.querySelector('.fc');var b=w.querySelector('.bc');if(f.style.display==='none'){f.style.display='flex';b.style.display='none';}else{f.style.display='none';b.style.display='flex';}}) (this)" style="cursor:pointer;margin-bottom:0;">
  <div class="fc" style="display:flex;flex-direction:column;justify-content:center;padding:18px 20px;background:#1a2744;border:1px solid rgba(100,160,255,.25);border-radius:12px;min-height:150px;">
    <div style="font-size:2rem;margin-bottom:8px;">🧠</div>
    <div style="font-size:1.1rem;font-weight:700;color:#60c8ff;">LLM</div>
    <div style="font-size:.72rem;color:#5a7a99;margin-top:6px;">👆 Klicken zum Aufdecken</div>
  </div>
  <div class="bc" style="display:none;flex-direction:column;justify-content:center;padding:18px 20px;background:#0f3060;border:1px solid rgba(100,200,255,.4);border-radius:12px;min-height:150px;">
    <div style="font-size:.88rem;line-height:1.55;color:#d0e8ff;"><strong>Large Language Model</strong> — ein neuronales Netz, trainiert auf riesigen Textmengen, um die nächste wahrscheinlichste Token-Folge vorherzusagen. Es „versteht" nicht — es berechnet Wahrscheinlichkeiten. ChatGPT, Claude, Gemma sind LLMs.</div>
    <div style="display:inline-block;font-size:.7rem;font-weight:600;background:rgba(96,200,255,.15);color:#60c8ff;padding:2px 8px;border-radius:20px;margin-top:8px;">Kein Verstehen · Mustervorhersage</div>
  </div>
</div>

<div onclick="(function(w){var f=w.querySelector('.fc');var b=w.querySelector('.bc');if(f.style.display==='none'){f.style.display='flex';b.style.display='none';}else{f.style.display='none';b.style.display='flex';}}) (this)" style="cursor:pointer;margin-bottom:0;">
  <div class="fc" style="display:flex;flex-direction:column;justify-content:center;padding:18px 20px;background:#1a2744;border:1px solid rgba(100,160,255,.25);border-radius:12px;min-height:150px;">
    <div style="font-size:2rem;margin-bottom:8px;">📊</div>
    <div style="font-size:1.1rem;font-weight:700;color:#60c8ff;">Parameter</div>
    <div style="font-size:.72rem;color:#5a7a99;margin-top:6px;">👆 Klicken zum Aufdecken</div>
  </div>
  <div class="bc" style="display:none;flex-direction:column;justify-content:center;padding:18px 20px;background:#0f3060;border:1px solid rgba(100,200,255,.4);border-radius:12px;min-height:150px;">
    <div style="font-size:.88rem;line-height:1.55;color:#d0e8ff;">Die <strong>lernbaren Gewichte</strong> des neuronalen Netzes. Beim Training angepasst, bis das Modell nützlich antwortet. GPT-4: ~1,8 Billionen · Gemma 3 9B: 9 Milliarden. Mehr ≠ immer besser.</div>
    <div style="display:inline-block;font-size:.7rem;font-weight:600;background:rgba(16,185,129,.15);color:#10b981;padding:2px 8px;border-radius:20px;margin-top:8px;">9B ≈ 5 GB RAM lokal nutzbar!</div>
  </div>
</div>

<div onclick="(function(w){var f=w.querySelector('.fc');var b=w.querySelector('.bc');if(f.style.display==='none'){f.style.display='flex';b.style.display='none';}else{f.style.display='none';b.style.display='flex';}}) (this)" style="cursor:pointer;margin-bottom:0;">
  <div class="fc" style="display:flex;flex-direction:column;justify-content:center;padding:18px 20px;background:#1a2744;border:1px solid rgba(100,160,255,.25);border-radius:12px;min-height:150px;">
    <div style="font-size:2rem;margin-bottom:8px;">📄 vs 📝</div>
    <div style="font-size:1.1rem;font-weight:700;color:#60c8ff;">Text vs. PDF</div>
    <div style="font-size:.72rem;color:#5a7a99;margin-top:6px;">👆 Klicken zum Aufdecken</div>
  </div>
  <div class="bc" style="display:none;flex-direction:column;justify-content:center;padding:18px 20px;background:#0f3060;border:1px solid rgba(100,200,255,.4);border-radius:12px;min-height:150px;">
    <div style="font-size:.88rem;line-height:1.55;color:#d0e8ff;"><strong>Reiner Text (Markdown, TXT)</strong> ist für KI optimal: direkt verarbeitbar, kein Layout-Overhead. <strong>PDFs</strong> enthalten Rendering-Daten — KI muss erst extrahieren, was fehleranfällig ist. Für eigene Materialien: immer Textformate!</div>
    <div style="display:inline-block;font-size:.7rem;font-weight:600;background:rgba(96,200,255,.15);color:#60c8ff;padding:2px 8px;border-radius:20px;margin-top:8px;">Markdown &gt; PDF für KI-Verarbeitung</div>
  </div>
</div>

<div onclick="(function(w){var f=w.querySelector('.fc');var b=w.querySelector('.bc');if(f.style.display==='none'){f.style.display='flex';b.style.display='none';}else{f.style.display='none';b.style.display='flex';}}) (this)" style="cursor:pointer;margin-bottom:0;">
  <div class="fc" style="display:flex;flex-direction:column;justify-content:center;padding:18px 20px;background:#1a2744;border:1px solid rgba(100,160,255,.25);border-radius:12px;min-height:150px;">
    <div style="font-size:2rem;margin-bottom:8px;">🪟</div>
    <div style="font-size:1.1rem;font-weight:700;color:#60c8ff;">Kontextfenster</div>
    <div style="font-size:.72rem;color:#5a7a99;margin-top:6px;">👆 Klicken zum Aufdecken</div>
  </div>
  <div class="bc" style="display:none;flex-direction:column;justify-content:center;padding:18px 20px;background:#0f3060;border:1px solid rgba(100,200,255,.4);border-radius:12px;min-height:150px;">
    <div style="font-size:.88rem;line-height:1.55;color:#d0e8ff;">Die <strong>maximale Token-Zahl</strong>, die ein Modell gleichzeitig „sehen" kann — inklusive Systemanweisung, Gesprächsverlauf und Antwort. Claude 3.5: 200.000 Tokens. Was außerhalb liegt, existiert für das Modell nicht.</div>
    <div style="display:inline-block;font-size:.7rem;font-weight:600;background:rgba(96,200,255,.15);color:#60c8ff;padding:2px 8px;border-radius:20px;margin-top:8px;">Kurzzeitgedächtnis · Pro Anfrage neu</div>
  </div>
</div>

</div>

---

### Grundbegriffe III – Grenzen & Zukunft

                          --{{0}}--
Abschluss der Grundbegriffe: Halluzination, KI-Agent, Bit und Byte.
Besonders der Agenten-Begriff ist für den letzten Block zentral.

<div style="display:grid;grid-template-columns:1fr 1fr 1fr;gap:14px;margin-top:8px;">

<div onclick="(function(w){var f=w.querySelector('.fc');var b=w.querySelector('.bc');if(f.style.display==='none'){f.style.display='flex';b.style.display='none';}else{f.style.display='none';b.style.display='flex';}}) (this)" style="cursor:pointer;margin-bottom:0;">
  <div class="fc" style="display:flex;flex-direction:column;justify-content:center;padding:18px 20px;background:#1a2744;border:1px solid rgba(100,160,255,.25);border-radius:12px;min-height:160px;">
    <div style="font-size:2rem;margin-bottom:8px;">🌀</div>
    <div style="font-size:1.1rem;font-weight:700;color:#60c8ff;">Halluzination</div>
    <div style="font-size:.72rem;color:#5a7a99;margin-top:6px;">👆 Klicken</div>
  </div>
  <div class="bc" style="display:none;flex-direction:column;justify-content:center;padding:18px 20px;background:#0f3060;border:1px solid rgba(100,200,255,.4);border-radius:12px;min-height:160px;">
    <div style="font-size:.88rem;line-height:1.55;color:#d0e8ff;"><strong>Selbstsicheres Erfinden</strong> von Fakten, Quellen oder Daten durch LLMs. Ursache: Das Modell interpoliert Muster, keine Fakten. Immer kritisch prüfen — vor allem Zahlen und Zitate!</div>
    <div style="display:inline-block;font-size:.7rem;font-weight:600;background:rgba(96,200,255,.15);color:#60c8ff;padding:2px 8px;border-radius:20px;margin-top:8px;">Quellen immer verifizieren!</div>
  </div>
</div>

<div onclick="(function(w){var f=w.querySelector('.fc');var b=w.querySelector('.bc');if(f.style.display==='none'){f.style.display='flex';b.style.display='none';}else{f.style.display='none';b.style.display='flex';}}) (this)" style="cursor:pointer;margin-bottom:0;">
  <div class="fc" style="display:flex;flex-direction:column;justify-content:center;padding:18px 20px;background:#1a2744;border:1px solid rgba(100,160,255,.25);border-radius:12px;min-height:160px;">
    <div style="font-size:2rem;margin-bottom:8px;">🤖</div>
    <div style="font-size:1.1rem;font-weight:700;color:#60c8ff;">KI-Agent</div>
    <div style="font-size:.72rem;color:#5a7a99;margin-top:6px;">👆 Klicken</div>
  </div>
  <div class="bc" style="display:none;flex-direction:column;justify-content:center;padding:18px 20px;background:#0f3060;border:1px solid rgba(100,200,255,.4);border-radius:12px;min-height:160px;">
    <div style="font-size:.88rem;line-height:1.55;color:#d0e8ff;">Ein <strong>autonomes KI-System</strong>, das Ziele verfolgt, plant und handelt — ohne bei jedem Schritt Eingaben zu brauchen. Nutzt Werkzeuge: Web-Suche, Code, APIs. <em>Chatbot = fragt, Agent = handelt.</em></div>
    <div style="display:inline-block;font-size:.7rem;font-weight:600;background:rgba(96,200,255,.15);color:#60c8ff;padding:2px 8px;border-radius:20px;margin-top:8px;">Ziel → Plan → Aktion → Feedback</div>
  </div>
</div>

<div onclick="(function(w){var f=w.querySelector('.fc');var b=w.querySelector('.bc');if(f.style.display==='none'){f.style.display='flex';b.style.display='none';}else{f.style.display='none';b.style.display='flex';}}) (this)" style="cursor:pointer;margin-bottom:0;">
  <div class="fc" style="display:flex;flex-direction:column;justify-content:center;padding:18px 20px;background:#1a2744;border:1px solid rgba(100,160,255,.25);border-radius:12px;min-height:160px;">
    <div style="font-size:2rem;margin-bottom:8px;">💾</div>
    <div style="font-size:1.1rem;font-weight:700;color:#60c8ff;">Bit &amp; Byte</div>
    <div style="font-size:.72rem;color:#5a7a99;margin-top:6px;">👆 Klicken</div>
  </div>
  <div class="bc" style="display:none;flex-direction:column;justify-content:center;padding:18px 20px;background:#0f3060;border:1px solid rgba(100,200,255,.4);border-radius:12px;min-height:160px;">
    <div style="font-size:.88rem;line-height:1.55;color:#d0e8ff;"><strong>Bit</strong> = 0 oder 1. <strong>Byte</strong> = 8 Bit. KI-Relevanz: Modellgewichte brauchen Speicher. Durch 4-Bit-Quantisierung laufen 9B-Modelle mit ~5 GB RAM — das ermöglicht Local AI auf Schulrechnern!</div>
    <div style="display:inline-block;font-size:.7rem;font-weight:600;background:rgba(16,185,129,.15);color:#10b981;padding:2px 8px;border-radius:20px;margin-top:8px;">Quantisierung = Local AI möglich</div>
  </div>
</div>

</div>

---

### Quiz: Grundbegriffe prüfen

> ❓ Vier Fragen — direkt im Dokument beantworten

                          --{{0}}--
Kleiner Selbsttest. Nehmt euch eine Minute, beantwortet die Fragen und schaut dann
gemeinsam die Lösungen durch.

**Frage 1:** Was ist ein Token in einem Sprachmodell?

[( )] Ein vollständiges deutsches Wort
[(X)] Die kleinste Verarbeitungseinheit, auf EN ≈ ¾ Wort
[( )] Eine GPU-Recheneinheit
[( )] Ein Zeichen (Buchstabe)
***
Token sind keine ganzen Wörter. „Unterrichtsmaterial" kann 4–5 Tokens sein.
Das hat direkte Auswirkungen auf Kosten und Kontextlimits.
***

**Frage 2:** Was unterscheidet Systemprompt und Interaktionsprompt?

[(X)] Systemprompt: versteckt, global wirkend. Interaktionsprompt: sichtbare Nutzereingabe.
[( )] Beide sind identisch, nur verschiedene Bezeichnungen.
[( )] Systemprompts sind immer länger.
[( )] Interaktionsprompts gibt es nur in ChatGPT.
***
Der Systemprompt setzt den unsichtbaren Rahmen. Der Interaktionsprompt ist
das, was Lernende tatsächlich eintippen.
***

**Frage 3:** Was ist eine KI-Halluzination?

[( )] Grafische Fehler bei der Bildausgabe
[(X)] Selbstsicheres Erfinden falscher Informationen durch ein LLM
[( )] Ein Modell, das sich selbst widerspricht
[( )] Zu langsame Antwortgeschwindigkeit
***
Halluzinationen sind eine Kernschwäche heutiger LLMs.
Das Modell kann nicht unterscheiden, ob etwas wahr ist — es berechnet
nur die wahrscheinlichste Fortsetzung. Quellen immer prüfen!
***

**Frage 4:** Was macht einen KI-Agenten von einem Chatbot unterschiedlich?

[( )] Agenten antworten schneller.
[( )] Agenten kennen keine Grenzen.
[(X)] Agenten können eigenständig Schritte planen und Werkzeuge nutzen, ohne bei jedem Schritt Eingaben zu benötigen.
[( )] Agenten sind immer cloudbasiert.
***
Chatbot = antwortet auf Fragen. Agent = verfolgt Ziele, plant selbstständig,
nutzt Werkzeuge (Code, Web, APIs). Das ist die Basis für Block 5.
***

---

## Block 2: Kompetenzrahmen

> 📐 **KMK 2024 · DigCompEdu · UNESCO AI-CFT 2025 · OECD AILit 2026**
>
> Alle zeigen dieselbe Richtung — nur auf verschiedenen Ebenen.

                          --{{0}}--
Vier Frameworks, entwickelt in verschiedenen Ländern und Organisationen —
aber mit einer erstaunlich konsistenten Botschaft: Lehrkräfte müssen KI nicht
nur nutzen können, sondern kritisch verstehen, pädagogisch einbetten
und ethisch verantworten.

                          {{1}}
<div class="info-box">
💡 <strong>Die gemeinsame Achse</strong> aller vier Rahmenwerke: von <em>Basiswissen</em>
über <em>pädagogische Integration</em> bis zu <em>ethischer Führungsrolle</em>.
Die Labels unterscheiden sich — die Richtung nicht.
</div>

---

### Überblick: Vier Ebenen, eine Richtung

                          --{{0}}--
Hier ein kompakter Überblick — danach geht es in den interaktiven Crosswalk,
wo ihr selbst klicken und vergleichen könnt.

| Rahmen | Ebene | Stufen | KI-Fokus |
|--------|-------|--------|-----------|
| 🇩🇪 **KMK 2024** | National (DE) | Pre-Service → Referendariat → Fortbildung | 5 Kompetenzbereiche, EU AI Act verankert |
| 🇪🇺 **DigCompEdu + AI-Supplement** | Europäisch | Newcomer → Pioneer (6 Stufen) | 6 Bereiche × AI-spezifisch erweitert |
| 🌍 **UNESCO AI-CFT 2025** | Global | Acquire → Deepen → Create | 5 Bereiche, menschenzentriert |
| 🌐 **OECD AILit 2026** | Global | Basic → Intermediate → Advanced | 4 Domains, Basis für PISA 2029 |

                          {{1}}
**KMK 2024 — Die 5 Kompetenzbereiche (Themenbereich 3):**

> **2.1** Technisches Verstehen · **2.2** Kritisch-reflexive Kompetenz · **2.3** Rechtliche Kenntnisse (EU AI Act, DSGVO) · **2.4** Pädagogisch-didaktische Integration · **2.5** Adaptive Haltung als Dauerlernende:r

---

### Interaktiver Crosswalk

> 🖱️ **Thema wählen → Schieberegler bewegen → Vier Spalten vergleichen**

                          --{{0}}--
Das ist das Herzstück: ihr könnt jedes Thema auf drei Kompetenzniveaus
durch alle vier Rahmenwerke gleichzeitig lesen.
Wählt ein Thema, das euch interessiert — und schiebt dann den Regler.

<div id="crosswalk-app">

<div style="margin-bottom:10px;font-size:.8rem;color:#8aa8c0;">Thema wählen:</div>
<div id="cw-themes"></div>

<div style="background:rgba(96,200,255,.06);border:1px solid rgba(96,200,255,.15);
     border-radius:10px;padding:12px 16px;margin:12px 0;">
  <div id="cw-stagename" style="font-size:1.05rem;font-weight:800;color:#60c8ff;margin-bottom:6px;">–</div>
  <input type="range" id="cw-stage" min="0" max="2" step="1" value="0" style="width:100%;accent-color:#60c8ff;">
  <div style="display:flex;justify-content:space-between;font-size:.72rem;color:#5a7a99;margin-top:4px;">
    <span>Einsteiger</span><span>Fortgeschritten</span><span>Expert:in</span>
  </div>
</div>

<div class="cw-grid" id="cw-cols">
  <div class="cw-col" id="cw-col-de"  style="border-top-color:#2a4090;"></div>
  <div class="cw-col" id="cw-col-eu"  style="border-top-color:#003399;"></div>
  <div class="cw-col" id="cw-col-ict" style="border-top-color:#2e7d32;"></div>
  <div class="cw-col" id="cw-col-un"  style="border-top-color:#0077c8;"></div>
</div>

<div class="cw-synth"><strong style="color:#10b981;">🔗 Gemeinsamer Kern aller vier:</strong><br><span id="cw-synth">–</span></div>

</div>

<script>
(function(){
  var STAGES={
    de:['Phase 1 — Ausbildung','Phase 2 — Referendariat','Phase 3 — Fort-/Weiterbildung'],
    eu:['Newcomer/Explorer (A1–A2)','Integrator/Expert (B1–B2)','Leader/Pioneer (C1–C2)'],
    ict:['L1 — Knowledge Acquisition','L2 — Knowledge Deepening','L3 — Knowledge Creation'],
    un:['Acquire','Deepen','Create']
  };
  var SNAMES=['Einsteiger — Erstkontakt','Fortgeschritten — sichere Anwendung','Expert:in — Führung & Gestaltung'];
  var COLS=['de','eu','ict','un'];
  var COLORS={de:'#2a4090',eu:'#003399',ict:'#2e7d32',un:'#0077c8'};
  var DNAME={de:'🇩🇪 KMK (DE)',eu:'🇪🇺 DigCompEdu',ict:'🌐 UNESCO ICT-CFT',un:'🌍 UNESCO AI-CFT'};

  var THEMES=[
    {id:'mindset',label:'🧭 Menschenzentrierte Haltung',
     de:[
       {s:'Digitalem Lernen liegt soziales Lernen zugrunde; KI darf die unverzichtbare Rolle der Lehrkraft nicht schwächen.',tags:['Medienkompetenz','digitale Mündigkeit']},
       {s:'Lehrkräfte behalten die Steuerung; beurteilen Chancen, Grenzen und Risiken von KI mit echter kritischer Reflexion.',tags:['Lernbegleitung','kritische Reflexion']},
       {s:'Lehrkräfte als Dauerlernende: aktive Reflexion und Neugestaltung der eigenen Berufsrolle im KI-Wandel.',tags:['Selbstreflexion','Rollenwandel']}
     ],
     eu:[
       {s:'KI als Werkzeug erkennen, das unterstützt — nicht ersetzt; Grundbewusstsein für KI in der Lehrpraxis entwickeln.',tags:['Professional Engagement','Newcomer']},
       {s:'KI-Ausgaben kritisch bewerten; professionelles Urteilsvermögen bei KI-gestützten Entscheidungen bewahren.',tags:['Kritisches Denken','Expert']},
       {s:'Menschenzentrierte KI-Nutzung auf Institutions- und Systemebene anleiten und vertreten.',tags:['Leadership','Pioneer']}
     ],
     ict:[
       {s:'ICTs Rolle in der Bildungsreform verstehen; Klassenraumpraxis an schulweite und nationale Ziele anpassen.',tags:['Politikawareness','ICT-CFT Area 1']},
       {s:'Analysieren, wie digitale Politik Lehrverpflichtungen und Schüler:innenagentur beeinflusst.',tags:['Politikanalyse','ICT-CFT Areas 1–3']},
       {s:'Für kontextsensible ICT-Richtlinien eintreten; evidenzbasierte Reformen mit Lehrerurteil im Zentrum formulieren.',tags:['Advocacy','ICT-CFT L3']}
     ],
     un:[
       {s:'Human Agency: KI ist menschengemacht; Unternehmensentscheidungen prägen Rechte und Autonomie — das verstehen.',tags:['1.1 Human Agency']},
       {s:'Human Accountability: Menschen bleiben rechtlich verantwortlich in Mensch-KI-Entscheidungsschleifen.',tags:['1.2 Accountability']},
       {s:'Social Responsibility: KI-Folgen für Gesellschaft und Planet bewerten; aktiv zu inklusiver KI-Governance beitragen.',tags:['1.3 Social Responsibility']}
     ],
     synth:'Alle vier Rahmen bestehen darauf: der Mensch behält die Kontrolle. KMK nennt es digitale Mündigkeit und die unersetzliche Lehrerrolle; DigCompEdu betont kritische Bewertung von KI-Outputs; die ICT-CFT verankert Policy-Kompetenz; UNESCO AI-CFT strukturiert dies als Agency → Accountability → Social Responsibility.'
    },
    {id:'ethics',label:'⚖️ Ethik & Datenschutz',
     de:[
       {s:'Für rechtliche Rahmenbedingungen sensibilisieren (DSGVO, EU AI Act) und mögliche Risiken im Schulkontext benennen.',tags:['Datenschutz','Medienethik']},
       {s:'Qualität und ethische Wirkung von KI-Outputs beurteilen; informationelle Selbstbestimmung von Schüler:innen schützen.',tags:['informationelle Selbstbestimmung']},
       {s:'Schulweite Regulierung und Fehlerkultur mitgestalten; Datensouveränität auf Institutionsebene sichern.',tags:['EU AI Act','DSGVO Art. 22']}
     ],
     eu:[
       {s:'Ethisches Bewusstsein: Datenschutz, Datensicherheit und Fairness-Implikationen von KI-Tools verstehen.',tags:['Ethical awareness','Newcomer']},
       {s:'Algorithmische Verzerrungen erkennen; verantwortungsvolle Nutzungspraktiken anwenden; Datenschutz im Lehrworkflow.',tags:['bias','responsible use','Expert']},
       {s:'Institutionsweite Kultur verantwortungsvoller KI-Nutzung fördern; Lernende und Kolleg:innen begleiten.',tags:['Empowering Learners','Pioneer']}
     ],
     ict:[
       {s:'Digitale Staatsbürgerschaft, Online-Sicherheit und ethischen ICT-Einsatz als Kernprofessionalisierung verstehen.',tags:['Digital citizenship','ICT-CFT 4.1']},
       {s:'Schüler:innendaten in schulischen Systemen verantwortungsvoll verwalten; datenschutzbewusste Praktiken etablieren.',tags:['Data management','ICT-CFT Area 5']},
       {s:'Institutionelle Digitalethik anleiten; für verantwortungsvolle Datennutzung und Gerechtigkeit eintreten.',tags:['Ethics leadership','ICT-CFT L3']}
     ],
     un:[
       {s:'Ethische Grundprinzipien: Do-no-harm, Proportionalität, Nicht-Diskriminierung, Nachhaltigkeit, Transparenz.',tags:['2.1 Ethical Principles']},
       {s:'Sicherer und verantwortungsvoller Einsatz: Datenprivatsphäre, Datensouveränität, IP-Compliance durch den ganzen Datenlebenszyklus.',tags:['2.2 Safe Use']},
       {s:'Ethische Regeln mitgestalten; Anbieter-Guidance kritisch prüfen; Verhandlungen zu KI-Ethik in Bildung mitführen.',tags:['2.3 Co-creation']}
     ],
     synth:'Datenschutz ist das gemeinsame Rückgrat. Die ICT-CFT setzt digitale Staatsbürgerschaft als Norm; KMK benennt DSGVO und EU AI Act explizit; DigCompEdu macht ethisches Bewusstsein zur Querschnittkompetenz; UNESCO AI-CFT widmet einen gesamten Kompetenzbereich der Ethik. „Datensouveränität" (UNESCO 2.2) ist das zentrale Argument für Local AI auf eigener Hardware.'
    },
    {id:'pedagogy',label:'🎓 KI-Pädagogik',
     de:[
       {s:'KI zur Unterrichtsvorbereitung und Differenzierung nutzen; KI als adaptive Lernumgebung und Tutor kennen.',tags:['Lehr-Lernsituationen']},
       {s:'Didaktisch begründete Entscheidungen für UND gegen KI-Einsatz treffen; personalisiertes Feedback gestalten.',tags:['Individualisierung','Feedback']},
       {s:'Reiches pädagogisches Repertoire aus KI und analogen Methoden entwickeln; bildungsspezifische KI-Lösungen ko-kreieren.',tags:['Ko-Kreation','Pilotprojekte']}
     ],
     eu:[
       {s:'Teaching & Learning: KI-gestützte adaptive Systeme und Intelligent Tutoring für individuelle Lernbegleitung einsetzen.',tags:['Teaching & Learning','Newcomer']},
       {s:'Assessment: KI-assistierte adaptive und formative Prüfformate; Analytics für Lernlücken und personalisiertes Feedback.',tags:['Assessment','Expert']},
       {s:'Empowering Learners: personalisierte, inklusive, lernzentrierte Strategien mit KI; selbstreguliertes Lernen fördern.',tags:['Empowering Learners','Pioneer']}
     ],
     ict:[
       {s:'ICT für Direktunterricht und Materialbereitstellung einsetzen; verschiedene Lehrformen mit Technologie unterstützen.',tags:['Pedagogy L1','ICT-CFT Area 3']},
       {s:'Kooperatives, forschendes, problemorientiertes Lernen mit ICT; höherwertige Denkprozesse fördern.',tags:['Student-centred','ICT-CFT 3.2']},
       {s:'Transformative ICT-Lernumgebungen gestalten; Emerging Tools ausprobieren; Kolleg:innen innovativ begleiten.',tags:['Pedagogical innovation','ICT-CFT L3']}
     ],
     un:[
       {s:'KI-gestütztes Unterrichten: Design-Implementations-Reflexions-Zyklus anwenden; Nutzen und Risiken abwägen.',tags:['4.1 Assisted']},
       {s:'KI-Pädagogik-Integration: KI in schüler:innenzentrierte Praktiken einbetten; menschlich verantwortete Bewertungsschleifen.',tags:['4.2 Integration']},
       {s:'Pädagogische Innovation: KI-immersive Szenarien; triangulare Lehrer-Schüler-KI-Interaktion gestalten.',tags:['4.3 Innovation']}
     ],
     synth:'Pädagogik ist das reichhaltigste und konsistenteste Feld. Die ICT-CFT setzt die schüler:innenzentrierte Baseline; KMK verlangt Entscheidungskompetenz für UND gegen KI; DigCompEdu betont adaptive Bewertung und Lernendenbefähigung; UNESCO AI-CFT synthetisiert alles in der triangularen Lehrer-Schüler-KI-Interaktion. Der Bogen — Direktunterricht → kooperatives Lernen → innovative Szenarien — zieht sich durch alle vier.'
    },
    {id:'profdev',label:'🌱 Professionelle Entwicklung',
     de:[
       {s:'KI-Kompetenzen in alle drei Phasen der Lehramtsausbildung einbetten; kontinuierliche Professionalisierung strukturell verankern.',tags:['Lehrkräftebildung']},
       {s:'Fortbildungsformate an KI-Entwicklung anpassen; regionale Kompetenzzentren aufbauen.',tags:['Fortbildung','Kompetenzzentren']},
       {s:'Lehrkräften Zeit, Ressourcen und Freiräume für kontinuierliches Lernen geben; konstruktive Fehlerkultur vorleben.',tags:['Ressourcen','Freiräume']}
     ],
     eu:[
       {s:'Lifelong Learning: KI-Wissen und -Kompetenzen kontinuierlich aktualisieren; Upskilling als professionelle Dauerpflicht.',tags:['Lifelong learning','Newcomer']},
       {s:'Über KI-Tools kollaborieren; Best Practices in Communities of Practice teilen und ko-kreieren.',tags:['Professional Engagement','Expert']},
       {s:'Institutionelle KI-Politik mitgestalten; CPD-Initiativen leiten; verantwortungsvolle KI auf Systemebene vertreten.',tags:['policy','Pioneer']}
     ],
     ict:[
       {s:'ICT-Tools für persönliche Professionalisierung identifizieren; selbstgesteuertes digitales CPD als Norm etablieren.',tags:['Self-directed CPD','ICT-CFT Area 6']},
       {s:'An ICT-gestützten Communities of Practice teilnehmen; reflektiertes Peer-Learning und fachspezifisches Wachstum.',tags:['Communities of practice','ICT-CFT 6.2']},
       {s:'ICT-gestützte Professionalisierungsprogramme gestalten und leiten; systemische Innovation in der Lehrerbildung vertreten.',tags:['PD leadership','ICT-CFT L3']}
     ],
     un:[
       {s:'Kontinuierliche Fortbildung: KI-Plattformen für persönliche Professionalisierung; KI für Wissensmanagement.',tags:['5.1 Continuous']},
       {s:'Kollaborative Fortbildung: mit Peers über KI-Plattformen vernetzen; Materialien ko-kreieren; IP und Datenschutz wahren.',tags:['5.2 Collaborative']},
       {s:'Führung in der Professionalisierung: KI-gestützte CPD-Programme gestalten; Kolleg:innen begleiten; Institutionspolitik mitentwickeln.',tags:['5.3 Leadership']}
     ],
     synth:'Die Lehrkraft als Dauerlernende ist die universellste Idee aller vier Rahmen. ICT-CFT setzt digitales CPD und Communities of Practice als Norm; KMK verankert KI-Lernen in allen drei Ausbildungsphasen; DigCompEdu nennt Lifelong Learning als Querschnittkompetenz; UNESCO AI-CFT krönt das mit Führung, Mentoring und Institutionspolitik. Dieser Workshop ist genau das — Kompetenz 5.1 bis 5.3 in Aktion.'
    }
  ];

  var cur=THEMES[0], si=0;

  function renderCol(w){
    var el=document.getElementById('cw-col-'+w);
    var d=cur[w][si];
    var c=COLORS[w];
    el.innerHTML='<div class="cw-col-hd" style="color:'+c+'">'+DNAME[w]+'</div>'
      +'<div class="cw-col-lvl">'+STAGES[w][si]+'</div>'
      +'<div class="cw-col-txt">'+d.s+'</div>'
      +'<div style="margin-top:8px;">'+d.tags.map(function(t){return'<span class="cw-tag">'+t+'</span>';}).join('')+'</div>';
  }

  function update(){
    document.getElementById('cw-stagename').textContent=SNAMES[si];
    COLS.forEach(function(w){renderCol(w);});
    document.getElementById('cw-synth').textContent=cur.synth;
  }

  var tb=document.getElementById('cw-themes');
  THEMES.forEach(function(t,i){
    var b=document.createElement('button');
    b.className='cw-btn'+(i===0?' act':'');
    b.textContent=t.label;
    b.onclick=function(){
      cur=t;si=0;
      document.getElementById('cw-stage').value=0;
      document.querySelectorAll('.cw-btn').forEach(function(x){x.classList.remove('act');});
      b.classList.add('act');
      update();
    };
    tb.appendChild(b);
  });

  document.getElementById('cw-stage').addEventListener('input',function(e){
    si=parseInt(e.target.value);update();
  });
  update();
})();
</script>

---

## Block 3: Prompten & Materialerstellung

> ✍️ **Prompt-Anatomie · Live-Builder · LiaScript TTS-Demo**

                          --{{0}}--
Jetzt wird's praktisch: Wie baut man einen wirklich guten Prompt?
Wir schauen uns die Anatomie an, dann nutzt ihr den interaktiven Builder
und zuletzt zeige ich, wie LiaScript Text-to-Speech funktioniert.

### Prompt-Anatomie

                          --{{0}}--
Ein guter Prompt hat fünf Teile. Ihr braucht nicht alle immer — aber je mehr
ihr bewusst einsetzt, desto besser das Ergebnis.

| Baustein | Frage | Beispiel |
|----------|-------|---------|
| 🎭 **Rolle** | Wer soll die KI sein? | „Du bist eine erfahrene Lehrkraft an einer Berufsschule…" |
| 📋 **Kontext** | Was ist die Situation? | „…für den Bildungsgang Straßenwärter, Klasse 11…" |
| 🎯 **Aufgabe** | Was soll getan werden? | „…erstelle einen Lückentext zu Verkehrszeichen…" |
| 📐 **Format** | Wie soll die Ausgabe aussehen? | „…im Markdown-Format, mit 10 Lücken, Lösung am Ende." |
| 🚫 **Einschränkung** | Was soll die KI NICHT tun? | „Keine Fachbegriffe, die über Klasse 9 hinausgehen." |

                          {{1}}
<div class="warn-box">
⚡ <strong>Prompt-Tipps:</strong>
Iteriere! Selten ist der erste Prompt perfekt. Starte einfach, schau das Ergebnis an,
und verfeinere gezielt. „Mach es kürzer." „Füge Beispiele hinzu." „Schreib einfacher."
</div>

---

### Interaktiver Prompt-Builder

> 🛠️ **Felder ausfüllen → Prompt wird live erzeugt → Kopieren & ausprobieren**

                          --{{0}}--
Hier könnt ihr euren eigenen Prompt bauen. Füllt die Felder aus —
der Prompt entsteht unten in Echtzeit. Dann einfach kopieren und in ChatGPT
oder Claude einfügen.

<div id="pb-wrap" style="margin-top:8px;font-family:sans-serif;">

  <div style="display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:10px;">
    <div>
      <label style="display:block;font-size:.75rem;font-weight:700;color:#80b8d8;text-transform:uppercase;letter-spacing:.04em;margin-bottom:5px;">🎭 Rolle der KI</label>
      <input id="pb-role" type="text" placeholder="z.B. erfahrene Berufsschullehrkraft"
        style="width:100%;background:#0e2040;border:1px solid #2a5080;border-radius:8px;
               padding:9px 12px;color:#d8eeff;font-size:.9rem;box-sizing:border-box;outline:none;">
    </div>
    <div>
      <label style="display:block;font-size:.75rem;font-weight:700;color:#80b8d8;text-transform:uppercase;letter-spacing:.04em;margin-bottom:5px;">📋 Kontext / Bildungsgang</label>
      <input id="pb-ctx" type="text" placeholder="z.B. Straßenwärter, Klasse 11"
        style="width:100%;background:#0e2040;border:1px solid #2a5080;border-radius:8px;
               padding:9px 12px;color:#d8eeff;font-size:.9rem;box-sizing:border-box;outline:none;">
    </div>
  </div>

  <div style="display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:10px;">
    <div>
      <label style="display:block;font-size:.75rem;font-weight:700;color:#80b8d8;text-transform:uppercase;letter-spacing:.04em;margin-bottom:5px;">🎯 Aufgabe</label>
      <input id="pb-task" type="text" placeholder="z.B. Lückentext zu Verkehrszeichen erstellen"
        style="width:100%;background:#0e2040;border:1px solid #2a5080;border-radius:8px;
               padding:9px 12px;color:#d8eeff;font-size:.9rem;box-sizing:border-box;outline:none;">
    </div>
    <div>
      <label style="display:block;font-size:.75rem;font-weight:700;color:#80b8d8;text-transform:uppercase;letter-spacing:.04em;margin-bottom:5px;">📐 Gewünschtes Format</label>
      <select id="pb-fmt"
        style="width:100%;background:#0e2040;border:1px solid #2a5080;border-radius:8px;
               padding:9px 12px;color:#d8eeff;font-size:.9rem;box-sizing:border-box;outline:none;cursor:pointer;">
        <option style="background:#0e2040;color:#d8eeff;">Markdown mit Überschriften</option>
        <option style="background:#0e2040;color:#d8eeff;">Lückentext mit Lösungsschlüssel</option>
        <option style="background:#0e2040;color:#d8eeff;">Multiple-Choice-Test (5 Fragen)</option>
        <option style="background:#0e2040;color:#d8eeff;">Unterrichtsskizze (tabellarisch)</option>
        <option style="background:#0e2040;color:#d8eeff;">Erklärvideo-Skript</option>
        <option style="background:#0e2040;color:#d8eeff;">LiaScript-Kurs-Abschnitt</option>
      </select>
    </div>
  </div>

  <div style="margin-bottom:10px;">
    <label style="display:block;font-size:.75rem;font-weight:700;color:#80b8d8;text-transform:uppercase;letter-spacing:.04em;margin-bottom:5px;">🚫 Einschränkungen (optional)</label>
    <input id="pb-limit" type="text" placeholder="z.B. max. Klasse 9 Wortschatz, kein Fachlatein"
      style="width:100%;background:#0e2040;border:1px solid #2a5080;border-radius:8px;
             padding:9px 12px;color:#d8eeff;font-size:.9rem;box-sizing:border-box;outline:none;">
  </div>

  <div style="display:flex;align-items:center;justify-content:space-between;margin-bottom:8px;">
    <span style="font-size:.75rem;font-weight:700;color:#80b8d8;text-transform:uppercase;letter-spacing:.04em;">✨ Generierter Prompt:</span>
    <button id="pb-copy-btn"
      style="font-size:.8rem;padding:5px 14px;border-radius:7px;cursor:pointer;
             background:rgba(0,200,230,.15);border:1px solid rgba(0,200,230,.4);
             color:#00c8e6;font-weight:600;transition:.2s;">📋 Kopieren</button>
  </div>

  <pre id="pb-out"
    style="background:#060f20;border:1px solid #1a4060;border-radius:10px;
           padding:14px 16px;font-family:monospace;font-size:.82rem;line-height:1.7;
           white-space:pre-wrap;color:#7dd0f0;min-height:90px;margin:0;
           box-sizing:border-box;">[Felder ausfüllen → Prompt erscheint hier]</pre>

</div>

<script>
(function(){
  function buildPrompt(){
    var role  = document.getElementById('pb-role').value  || 'einer erfahrenen Lehrkraft an einer Berufsschule';
    var ctx   = document.getElementById('pb-ctx').value   || '[Bildungsgang und Jahrgangsstufe]';
    var task  = document.getElementById('pb-task').value  || '[Aufgabe beschreiben]';
    var fmt   = document.getElementById('pb-fmt').value;
    var limit = document.getElementById('pb-limit').value;
    var p = 'Du bist ' + role + '.\n\n'
          + 'Kontext: ' + ctx + '.\n\n'
          + 'Aufgabe: ' + task + '.\n\n'
          + 'Format: ' + fmt + '.';
    if(limit) p += '\n\nEinschränkungen: ' + limit + '.';
    document.getElementById('pb-out').textContent = p;
  }

  ['pb-role','pb-ctx','pb-task','pb-limit'].forEach(function(id){
    var el = document.getElementById(id);
    if(el) el.addEventListener('input', buildPrompt);
  });
  var sel = document.getElementById('pb-fmt');
  if(sel) sel.addEventListener('change', buildPrompt);

  var copyBtn = document.getElementById('pb-copy-btn');
  if(copyBtn) copyBtn.addEventListener('click', function(){
    var t = document.getElementById('pb-out').textContent;
    if(navigator.clipboard){
      navigator.clipboard.writeText(t).then(function(){ copyBtn.textContent='✅ Kopiert!'; setTimeout(function(){copyBtn.textContent='📋 Kopieren';},2000); });
    } else {
      var ta = document.createElement('textarea');
      ta.value = t; document.body.appendChild(ta); ta.select();
      document.execCommand('copy'); document.body.removeChild(ta);
      copyBtn.textContent='✅ Kopiert!'; setTimeout(function(){copyBtn.textContent='📋 Kopieren';},2000);
    }
  });

  buildPrompt();
})();
</script>

---

### LiaScript & Text-to-Speech

                          --{{0}}--
Das hier ist bereits ein LiaScript-Kurs. Dieser Text wird vorgelesen, wenn ihr den
Play-Button drückt. Das macht LiaScript ideal für barrierefreie OER — ohne
Zusatz-Software, direkt im Browser.

LiaScript ist ein **kostenloser Open-Source Markdown-Dialekt**, der aus einer einfachen `.md`-Datei einen vollständigen interaktiven Kurs erzeugt:

- 🎧 **Text-to-Speech** mit Sprecher:innen-Annotationen
- ❓ **Native Quizze** (Single/Multiple Choice, Freitext)
- 💻 **Ausführbarer Code** direkt im Kurs
- 🌐 **Kein Server** — läuft komplett im Browser

**TTS-Syntax:**

```markdown
--{{0}}--
Dieser Text wird beim Öffnen der Folie gesprochen.

--{{1}}--
Das hier wird nach dem ersten Klick vorgelesen.

Inhalt, der auf Schritt 1 eingeblendet wird.
```

                          {{1}}
**Live-Demo** — Drücke den ▶-Button oben rechts, um diesen Abschnitt vorlesen zu lassen:

> *„LiaScript verbindet die Einfachheit von Markdown mit der Interaktivität einer Lernplattform —
> und läuft dabei vollständig offline, ohne Login, ohne Server."*

                          --{{1}}--
LiaScript verbindet die Einfachheit von Markdown mit der Interaktivität einer
Lernplattform und läuft dabei vollständig offline, ohne Login, ohne Server.
Das ist das Prinzip der Offenen Bildungsressourcen — OER — in Reinform.

---

## Block 4: Datenschutz & Local AI

> 🔒 **Was darf in die Cloud? Was bleibt lokal? Welche Tools sind erlaubt?**

                          --{{0}}--
Datenschutz ist kein Hindernis für KI-Einsatz — aber er setzt klare Grenzen.
Das Ampel-Modell hilft euch, schnell zu entscheiden, welche Daten
ihr in welche KI-Tools geben dürft.

### Das Datenschutz-Ampel-Modell

<div class="amp-row gruen">
  <div class="amp-led"></div>
  <div>
    <div class="amp-title">🟢 Grün — Freie Nutzung</div>
    <div class="amp-text">Allgemeine Anfragen ohne Personenbezug · Selbst erstellte Beispieltexte · Öffentlich verfügbare Materialien · Eigene Fachkonzepte und Lehrplaninhalte</div>
    <div class="amp-text" style="margin-top:6px;font-style:italic;">Beispiel: „Erstelle einen Lückentext zum Thema Verkehrszeichen."</div>
  </div>
</div>

<div class="amp-row gelb">
  <div class="amp-led"></div>
  <div>
    <div class="amp-title">🟡 Gelb — Nur mit Vorsicht / Local AI</div>
    <div class="amp-text">Anonymisierte Schüler:innenarbeiten · Eigene Unterrichtsmaterialien mit Schulbezug · Schulinterne Dokumente ohne Namen</div>
    <div class="amp-text" style="margin-top:6px;font-style:italic;">→ Für diese Fälle: Local AI auf eigener Hardware (Ollama + Gemma)</div>
  </div>
</div>

<div class="amp-row rot">
  <div class="amp-led"></div>
  <div>
    <div class="amp-title">🔴 Rot — Niemals in Cloud-KI</div>
    <div class="amp-text">Schüler:innennamen · Noten & Beurteilungen · Gesundheitsdaten · Erziehungsberechtigte-Kontakte · Sozialberichte · Alles unter DSGVO Art. 9 (besondere Kategorien)</div>
    <div class="amp-text" style="margin-top:6px;"><strong style="color:#f87171;">EU AI Act Art. 5:</strong> Emotionserkennung in Schulen verboten. Hochrisiko-KI (Bewerbungsfilter, Bewertungs-KI) braucht Transparenz + Menschliche Kontrolle.</div>
  </div>
</div>

---

### Local AI: Ollama + Gemma

                          --{{0}}--
Local AI bedeutet: das KI-Modell läuft auf eurem eigenen Rechner.
Kein Daten-Upload, keine Cloud, keine Datenschutz-Problematik.
Mit Ollama und Gemma geht das sogar auf einem normalen Schulrechner.

**Warum Local AI?**

- 🔒 **Datensouveränität:** Kein Byte verlässt euren Rechner
- 🌐 **Offline-fähig:** Läuft auch ohne Internet
- 💰 **Kostenfrei:** Kein Abo, keine API-Kosten
- 📚 **OER-konform:** Open-Source-Modelle (Gemma, Llama, Mistral)

**Schnellstart mit Ollama:**

```bash
# 1. Ollama installieren (ollama.com)
# 2. Modell laden (einmalig, ~5 GB)
ollama pull gemma3:9b

# 3. Im Terminal chatten
ollama run gemma3:9b

# 4. In VS Code (mit Continue.dev) nutzen
# → settings.json: model: "gemma3:9b", provider: "ollama"
```

                          {{1}}
<div class="ok-box">
✅ <strong>Empfehlung für Berufliche Schulen:</strong>
Gemma 3 9B (Google, Apache 2.0 Lizenz) läuft auf Rechnern mit 8 GB RAM.
Für Unterrichtsvorbereitung, Differenzierung und anonymisierte Textarbeit vollständig geeignet.
</div>

---

## Block 5: KI-Agenten & Zukunft

> 🤖 **Von Chatbots zu Agenten · BMAD-Methode · Teaching-Agent für LiaScript**

                          --{{0}}--
Der letzte inhaltliche Block blickt in die nahe Zukunft — und die ist schon da.
KI-Agenten können heute schon komplette Unterrichtseinheiten erstellen,
wenn man ihnen die richtige Struktur gibt.

### Chatbot vs. KI-Agent

| | Chatbot | KI-Agent |
|---|---------|----------|
| **Aktion** | Antwortet auf Fragen | Plant und handelt autonom |
| **Schritte** | Ein Schritt | Mehrere Schritte, sequenziell |
| **Werkzeuge** | Nur Textausgabe | Web-Suche, Code, APIs, Dateien |
| **Beispiel** | „Erkläre mir X" | „Erstelle einen vollständigen LiaScript-Kurs zu X" |
| **Kontrolle** | 100% menschlich | Teilautonom, Mensch überwacht |

                          {{1}}
**Agent-Schleife (ReAct-Prinzip):**

<div style="overflow-x:auto;margin-top:12px;">
<table style="border-collapse:separate;border-spacing:0;width:100%;table-layout:fixed;">
<tbody>
<tr>

<td style="text-align:center;vertical-align:top;padding:0 2px;">
  <div style="background:#0d2a50;border:2px solid #00c8e6;border-radius:12px;
              padding:14px 10px;text-align:center;">
    <div style="font-size:1.8rem;line-height:1;">🎯</div>
    <div style="font-weight:700;font-size:.85rem;color:#00c8e6;margin-top:6px;">Ziel</div>
    <div style="font-size:.72rem;color:#6a9ab8;margin-top:3px;">Aufgabe erhalten</div>
  </div>
</td>

<td style="text-align:center;vertical-align:middle;width:36px;padding:0;">
  <div style="font-size:1.4rem;color:#2a5878;font-weight:700;line-height:1;">→</div>
</td>

<td style="text-align:center;vertical-align:top;padding:0 2px;">
  <div style="background:#101e38;border:1px solid #2a4a68;border-radius:12px;
              padding:14px 10px;text-align:center;">
    <div style="font-size:1.8rem;line-height:1;">🤔</div>
    <div style="font-weight:700;font-size:.85rem;color:#a0c8e8;margin-top:6px;">Denken</div>
    <div style="font-size:.72rem;color:#6a9ab8;margin-top:3px;">Plan erstellen</div>
  </div>
</td>

<td style="text-align:center;vertical-align:middle;width:36px;padding:0;">
  <div style="font-size:1.4rem;color:#2a5878;font-weight:700;line-height:1;">→</div>
</td>

<td style="text-align:center;vertical-align:top;padding:0 2px;">
  <div style="background:#101e38;border:1px solid #2a4a68;border-radius:12px;
              padding:14px 10px;text-align:center;">
    <div style="font-size:1.8rem;line-height:1;">⚡</div>
    <div style="font-weight:700;font-size:.85rem;color:#a0c8e8;margin-top:6px;">Handeln</div>
    <div style="font-size:.72rem;color:#6a9ab8;margin-top:3px;">Tool nutzen</div>
  </div>
</td>

<td style="text-align:center;vertical-align:middle;width:36px;padding:0;">
  <div style="font-size:1.4rem;color:#2a5878;font-weight:700;line-height:1;">→</div>
</td>

<td style="text-align:center;vertical-align:top;padding:0 2px;">
  <div style="background:#101e38;border:1px solid #2a4a68;border-radius:12px;
              padding:14px 10px;text-align:center;">
    <div style="font-size:1.8rem;line-height:1;">👀</div>
    <div style="font-weight:700;font-size:.85rem;color:#a0c8e8;margin-top:6px;">Beobachten</div>
    <div style="font-size:.72rem;color:#6a9ab8;margin-top:3px;">Ergebnis prüfen</div>
  </div>
</td>

<td style="text-align:center;vertical-align:middle;width:36px;padding:0;">
  <div style="font-size:1.4rem;color:#2a5878;font-weight:700;line-height:1;">→</div>
</td>

<td style="text-align:center;vertical-align:top;padding:0 2px;">
  <div style="background:#0d2a50;border:2px solid #00c8e6;border-radius:12px;
              padding:14px 10px;text-align:center;">
    <div style="font-size:1.8rem;line-height:1;">✅</div>
    <div style="font-weight:700;font-size:.85rem;color:#00c8e6;margin-top:6px;">Abschließen</div>
    <div style="font-size:.72rem;color:#6a9ab8;margin-top:3px;">oder weiter ↺</div>
  </div>
</td>

</tr>
</tbody>
</table>
</div>

---

### BMAD-Methode & Teaching-Agent

                          --{{0}}--
Dr. André Dietrich von der TU Freiberg hat die BMAD-Methode auf Bildung übertragen.
BMAD steht für „Business Minded Agile Development" — ein strukturierter Ansatz,
bei dem spezialisierte KI-Agenten arbeitsteilig zusammenwirken, wie ein echtes Team.

**BMAD = Business Minded Agile Development**

Entwickelt für Software-Teams — von Dr. André Dietrich (TU Bergakademie Freiberg / LiaScript) auf **Bildungsinhalte übertragen**:

> *„Ein Prompt ist kein Team."* — Dietrich, 2025

Kernidee: Statt einem großen Prompt an eine KI → **spezialisierte Agenten** mit klaren Rollen, die sequenziell Artefakte übergeben.

                          {{1}}
<div style="display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-top:10px;">

<div style="background:#1a2744;border:1px solid rgba(167,139,250,.25);border-radius:12px;padding:14px;border-left:4px solid #a78bfa;">
  <div style="font-size:.7rem;font-weight:700;color:#a78bfa;text-transform:uppercase;margin-bottom:4px;">Phase 1 — Analyse</div>
  <div style="font-weight:700;margin-bottom:6px;">Business Analyst Agent</div>
  <div style="font-size:.82rem;color:#8aa8c0;">Analysiert Lernziele, Bildungsgang, Vorkenntnisse. Erzeugt: <em>Lernbedarfsanalyse + Kompetenzprofil</em></div>
</div>

<div style="background:#1a2744;border:1px solid rgba(96,200,255,.25);border-radius:12px;padding:14px;border-left:4px solid #60c8ff;">
  <div style="font-size:.7rem;font-weight:700;color:#60c8ff;text-transform:uppercase;margin-bottom:4px;">Phase 2 — Planung</div>
  <div style="font-weight:700;margin-bottom:6px;">Curriculum Designer Agent</div>
  <div style="font-size:.82rem;color:#8aa8c0;">Erstellt Grobstruktur, Lernpfad, Zeitplanung. Erzeugt: <em>Kurs-Outline + Lernzielmatrix</em></div>
</div>

<div style="background:#1a2744;border:1px solid rgba(16,185,129,.25);border-radius:12px;padding:14px;border-left:4px solid #10b981;">
  <div style="font-size:.7rem;font-weight:700;color:#10b981;text-transform:uppercase;margin-bottom:4px;">Phase 3 — Erstellung</div>
  <div style="font-weight:700;margin-bottom:6px;">Teaching Agent (Kern)</div>
  <div style="font-size:.82rem;color:#8aa8c0;">Begleitet durch alle Phasen der Kurserstellung bis zum fertigen LiaScript-Kurs. Nutzt Outline + Lernziele als Vertrag.</div>
</div>

<div style="background:#1a2744;border:1px solid rgba(245,158,11,.25);border-radius:12px;padding:14px;border-left:4px solid #f59e0b;">
  <div style="font-size:.7rem;font-weight:700;color:#f59e0b;text-transform:uppercase;margin-bottom:4px;">Phase 4 — Qualität</div>
  <div style="font-weight:700;margin-bottom:6px;">QA Agent</div>
  <div style="font-size:.82rem;color:#8aa8c0;">Prüft Lernzielabdeckung, Barrierefreiheit, LiaScript-Syntax. Erzeugt: <em>Qualitätsbericht + Korrekturliste</em></div>
</div>

</div>

---

### Praxis: Straßenwärter-Agent-Workflow

                          --{{0}}--
Ein konkretes Beispiel: Wie könnte ein Agenten-Workflow für den Bildungsgang
Straßenwärter aussehen? Hier ist ein erster Prototyp-Prompt für den Teaching-Agent.

**Systemprompt für einen Straßenwärter-Lehr-Agenten:**

```markdown
Du bist ein spezialisierter Lehr-Agent für den Bildungsgang Straßenwärter
an beruflichen Schulen in Deutschland.

DEINE ROLLE:
- Erstelle Unterrichtsmaterialien im LiaScript-Format
- Orientiere dich an den Lernfeldern der KMK-Rahmenlehrplan Straßenwärter
- Zielgruppe: Auszubildende im 1.–3. Lehrjahr

DEINE WERKZEUGE:
- Lernfeld-Datenbank (Reparatur, Winterdienst, Verkehrssicherung, ...)
- LiaScript-Syntax-Cheatsheet
- DGUV-Vorschriften für Straßenwärter

ABLAUF PRO AUFGABE:
1. Frage nach Lernfeld und Jahrgangsstufe
2. Schlage 3 Lernziele vor (Anderson/Bloom)
3. Erstelle eine LiaScript-Sektion mit Quiz
4. Frage nach Feedback und iteriere

Antworte immer auf Deutsch. Nutze praxisnahe Beispiele aus dem Straßenbau.
```

                          {{1}}
**Ausprobieren:** Gebt diesen Systemprompt in Claude.ai oder ChatGPT ein und startet dann mit:

> *„Erstelle eine Unterrichtseinheit zu Lernfeld 3: Absicherung von Arbeitsstellen, Klasse 1."*

---

## Block 6: Handlungsprodukt

> 🎯 **Jetzt seid ihr dran — 10 Minuten, ein konkretes Ergebnis**

                          --{{0}}--
Am Ende jedes Workshops steht ein Handlungsprodukt. Wählt eines der Tools,
das ihr gerade kennengelernt habt, und erstellt in 10 Minuten einen ersten Entwurf
für euren eigenen Unterricht.

**Wählt euer Tool und startet:**

| Tool | Einstieg | Ergebnis |
|------|----------|---------|
| 🤖 **Claude.ai / ChatGPT** | Prompt-Builder-Ausgabe verwenden | Unterrichtsmaterial-Entwurf |
| 📓 **NotebookLM** | Eigene Unterlagenmappe hochladen | Quellenbasierte Zusammenfassung |
| 🎨 **Gamma App** | Prompt: „Erstelle Präsentation zu [Thema]" | Fertige Slide-Deck |
| 📝 **LiaScript** | Diese Datei als Vorlage nehmen | Eigener interaktiver Kurs |
| 💻 **GitHub Copilot** | VS Code öffnen, `.md` anlegen | Code-assistierte Materialien |

                          {{1}}
**Starter-Prompt (anpassen und loslegen):**

```
Du bist eine erfahrene Lehrkraft an einer Berufsschule.

Kontext: [Euer Bildungsgang], [Jahrgangsstufe], 
Thema: [Euer Thema aus dem Lehrplan].

Aufgabe: Erstelle einen Unterrichtseinstieg (10 Min.) mit:
- Einem Impulsbild oder Einstiegsfrage
- 3 Lernziele (SMART-formuliert)
- Einem kurzen Erklärteil (max. 200 Wörter)
- Einer Sicherungsaufgabe (Lückentext oder Multiple Choice)

Format: Markdown, klar gegliedert, direkt einsetzbar.
Einschränkungen: Kein Fachlatein, Niveau Berufsschule.
```

---

## 💬 Diskussion

> 30 Minuten · 6 Leitfragen · Klappt auf, was euch interessiert

                          --{{0}}--
Jetzt ist Raum für eure Fragen, Bedenken und Erfahrungen.
Die sechs Karten enthalten Leitfragen — klappt sie auf, diskutiert,
und kommt gern mit eigenen Themen.

<div id="disc-container" style="margin-top:8px;">

<div class="disc-card" onclick="(function(c){var b=c.querySelector('.disc-body');b.style.display=b.style.display==='block'?'none':'block';})(this)" style="cursor:pointer;">
  <div class="disc-q">🛡️ Datenschutz im Schulalltag — wo zieht ihr die Grenze?<span class="disc-min">8 Min</span></div>
  <div class="disc-body" style="display:none;margin-top:10px;font-size:.82rem;color:#8aa8c0;line-height:1.6;">
    <ul>
      <li>Habt ihr schon KI-Tools im Unterricht genutzt? Mit welchen Daten?</li>
      <li>Wie erklärt ihr Lernenden, welche Daten in Cloud-KI fließen?</li>
      <li>Was wäre euer schulinternes Ampel-Modell?</li>
      <li>Wie positioniert ihr euch bei „BYOD"-Szenarien (Schüler nutzen eigene KI-Apps)?</li>
    </ul>
  </div>
</div>

<div class="disc-card" onclick="(function(c){var b=c.querySelector('.disc-body');b.style.display=b.style.display==='block'?'none':'block';})(this)" style="cursor:pointer;">
  <div class="disc-q">🎓 KI und Leistungsbeurteilung — wie verändert das die Schule?<span class="disc-min">7 Min</span></div>
  <div class="disc-body" style="display:none;margin-top:10px;font-size:.82rem;color:#8aa8c0;line-height:1.6;">
    <ul>
      <li>Welche Prüfungsformate sind noch sinnvoll, wenn KI verfügbar ist?</li>
      <li>Wie gestaltet ihr Aufgaben, die KI als legitimes Hilfsmittel einschließen?</li>
      <li>EU AI Act Art. 5: Automatische Verhaltensüberwachung in Prüfungen verboten — was bedeutet das für Klausuransichten?</li>
      <li>Was bedeutet Kompetenz in einer Welt mit KI-Assistenz?</li>
    </ul>
  </div>
</div>

<div class="disc-card" onclick="(function(c){var b=c.querySelector('.disc-body');b.style.display=b.style.display==='block'?'none':'block';})(this)" style="cursor:pointer;">
  <div class="disc-q">🤖 KI-Agenten im Schulkontext — Chance oder Risiko?<span class="disc-min">5 Min</span></div>
  <div class="disc-body" style="display:none;margin-top:10px;font-size:.82rem;color:#8aa8c0;line-height:1.6;">
    <ul>
      <li>Würdet ihr einen Teaching-Agent für euren Bildungsgang einsetzen?</li>
      <li>Welche Aufgaben sollten Lehrkräfte niemals an KI-Agenten delegieren?</li>
      <li>Wie bleibt pädagogisches Urteilsvermögen erhalten, wenn Agenten Materialien erstellen?</li>
      <li>Schüler:innen-Agenten: sinnvoll oder problematisch?</li>
    </ul>
  </div>
</div>

<div class="disc-card" onclick="(function(c){var b=c.querySelector('.disc-body');b.style.display=b.style.display==='block'?'none':'block';})(this)" style="cursor:pointer;">
  <div class="disc-q">📐 Kompetenzrahmen — welcher hilft euch am meisten?<span class="disc-min">4 Min</span></div>
  <div class="disc-body" style="display:none;margin-top:10px;font-size:.82rem;color:#8aa8c0;line-height:1.6;">
    <ul>
      <li>KMK, DigCompEdu, UNESCO — habt ihr vorher von diesen Rahmen gewusst?</li>
      <li>Welcher Bereich fühlt sich für euch am dringlichsten an?</li>
      <li>Wie integriert ihr KI-Kompetenzen in euer Fach?</li>
      <li>Seminarleitung: Wie verankern wir das strukturell in der Ausbildung?</li>
    </ul>
  </div>
</div>

<div class="disc-card" onclick="(function(c){var b=c.querySelector('.disc-body');b.style.display=b.style.display==='block'?'none':'block';})(this)" style="cursor:pointer;">
  <div class="disc-q">🌱 OER und LiaScript — wie nachhaltig ist Open Educational Content?<span class="disc-min">4 Min</span></div>
  <div class="disc-body" style="display:none;margin-top:10px;font-size:.82rem;color:#8aa8c0;line-height:1.6;">
    <ul>
      <li>Welche Bedingungen müssen erfüllt sein, damit ihr Materialien als OER teilt?</li>
      <li>GitHub als Schulinfrastruktur — realistisch oder zu technisch?</li>
      <li>LiaScript vs. PowerPoint: Wo seht ihr Vorteile, wo Hürden?</li>
      <li>Wie stellt ihr sicher, dass KI-generierte Materialien korrekt sind?</li>
    </ul>
  </div>
</div>

<div class="disc-card" onclick="(function(c){var b=c.querySelector('.disc-body');b.style.display=b.style.display==='block'?'none':'block';})(this)" style="cursor:pointer;">
  <div class="disc-q">🔮 Ausblick: Wie sieht Schule in 5 Jahren aus?<span class="disc-min">2 Min</span></div>
  <div class="disc-body" style="display:none;margin-top:10px;font-size:.82rem;color:#8aa8c0;line-height:1.6;">
    <ul>
      <li>Was von heute bleibt in eurer Praxis? Was verändert sich?</li>
      <li>Welche Fähigkeiten werden für Schüler:innen noch wichtiger?</li>
      <li>Eure dringlichste Frage an die KI-Forschung?</li>
    </ul>
  </div>
</div>

</div>

---

## 📚 Ressourcen & Links

> Alles, was ihr zum Weitermachen braucht

**Kompetenzrahmen:**

- 🇩🇪 [KMK 2024 – Handlungsempfehlung KI](https://www.kmk.org/themen/schule/digitale-bildung.html)
- 🇪🇺 [DigCompEdu AI Supplement (Erasmus+, 2023)](https://joint-research-centre.ec.europa.eu)
- 🌍 [UNESCO AI Competency Framework for Teachers (2025)](https://www.unesco.org/en/digital-education/ai-in-education)
- 🌐 [OECD AILit Framework (2026)](https://ailiteracyframework.org)

**Tools aus dem Workshop:**

- 🤖 [Claude.ai](https://claude.ai) · [ChatGPT](https://chatgpt.com) · [NotebookLM](https://notebooklm.google)
- 🎨 [Gamma App](https://gamma.app) – KI-Präsentationen
- 📝 [LiaScript](https://liascript.github.io) – Interaktive OER
- 🦙 [Ollama](https://ollama.com) – Local AI
- 💻 [GitHub Copilot (Schullizenz)](https://github.com/features/copilot/plans) – kostenlos für Bildung
- 🎓 [emuKI-Fortbildung](https://ki.bildung-lsa.de) – Sachsen-Anhalt

**LiaScript starten:**

```
https://liascript.github.io/course/?https://raw.githubusercontent.com/
[dein-github-name]/[repo]/main/ki-workshop-liv.md
```

                          --{{0}}--
Danke für eure Aufmerksamkeit und aktive Teilnahme!
Diese Präsentation ist eine LiaScript-Datei und damit selbst ein Handlungsprodukt —
eine OER, die ihr mitnehmen, anpassen und weitergeben könnt.
Lizenz: CC BY-SA 4.0. Viel Erfolg im Seminar und im Referendariat!

---

> **Lizenz:** CC BY-SA 4.0 — Frei verwendbar, anpassbar und weiterzugeben mit Quellenangabe.
>
> **Erstellt mit:** LiaScript · Claude.ai · OvGU Magdeburg · Seminar für Lehrerbildung Sachsen-Anhalt


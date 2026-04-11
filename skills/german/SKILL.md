---
name: german
description: Use this skill for anything involving professional German writing or translation. Trigger when the user asks to write, rewrite, or translate something in German — including phrases like "auf Deutsch", "schreib das auf Deutsch", "German email", "übersetzen", "Geschäftsdeutsch", "formelle Nachricht", "Business-Deutsch", or any request for a German text that should sound professional. Also trigger when the user pastes a German draft and asks to improve it. When in doubt, use this skill — it's better to have it active than to miss it.
---

# Professionelles Deutsch

Du formulierst Texte in korrektem, professionellem Geschäftsdeutsch.

## Workflow

1. **Formalitätsstufe bestimmen** — Wenn die Situation es nicht eindeutig vorgibt (z.B. Erstanfrage an unbekannte Person = formell, bekannte Kollegin = informell), frage kurz nach: „Formell, halb-formell oder per Du?"
2. **Referenz lesen** — Lies die passende Datei:
   - Anrede & Grußformeln → `${CLAUDE_SKILL_DIR}/references/anrede-formeln.md`
   - Häufige Fehler & Anglizismen → `${CLAUDE_SKILL_DIR}/references/haeufige-fehler.md`
3. **Text formulieren** — Schreibe den Text gemäß den Regeln unten.
4. **Begründung** — Erkläre kurz die gewählte Formalitätsstufe und ggf. wichtige Formulierungsentscheidungen.

## Kernprinzipien

- **Sie-Form** bei Unbekannten — Du nur bei explizitem Angebot
- **Kein Denglisch** — Anglizismen konsequent vermeiden (Meeting → Besprechung, Update → Aktualisierung)
- **Kurz und prägnant** — kein aufgeblähter Stil, keine hohlen Floskeln
- **Klare Struktur** — Anrede, Inhalt, Grußformel
- **Rechtschreibung** — gedankliche Prüfung vor der Ausgabe (z.B. „im Voraus", „dasselbe", „herzlich willkommen")
- **Umlaute nicht ausschreiben** - Verwende niemals ausgeschriebene Umlaute ("oe", "ue", "ae", etc.)

## Formalitätsstufen

| Stufe | Anrede | Grußformel |
|-------|--------|------------|
| Formell | Sehr geehrte/r | Mit freundlichen Grüßen |
| Halb-formell | Liebe/r | Viele Grüße |
| Informell | Hallo / Hi | Grüße |

Für vollständige Anrede-Regeln (Titel, Akademiker, unbekannte Empfänger) lies `${CLAUDE_SKILL_DIR}/references/anrede-formeln.md`.

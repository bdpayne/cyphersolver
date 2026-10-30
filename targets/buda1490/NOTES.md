# Maffeo da Treviglio to Tamás Bakócz, Milan 30 Nov 1490 (MNL OL DL 46150), catalogue 1235

Status: in progress. Key recovered from external plaintext (the clear minute in Milan); the letter is read in part:
544 of 624 words (87.2%) read as sense by `measure.py`, under the 95% read bar. The 39 transcription suspects were
checked on the image (29 Oct 2026: 11 fixed, 19 confirmed as writer departures, 9 ambiguous; transcription/suspects.md);
the open words are writer slips, damage, a few unvalued signs and the 9 ambiguous signs (below). The write-up page is not made yet.

## The document

Hungarian National Archives (MNL OL), Diplomatikai Levéltár, DL 46150 (Q 10, Véghely collection; Hungaricana charter
228061, <https://archives.hungaricana.hu/en/charters/228061/>, viewer `/en/charters/view/228061/`). Four paper pages
in cipher, with the closing, date, signature ("Filius Mapheus Triuliensis") and the address in clear on p. 4
(`transcription/p4_clear.txt`): to Tamás Bakócz, bishop of Győr (Jaurinensis), chancellor of the King of Hungary.
The salutation "In christo pater et domine pater honorande" opens p. 1 in clear.

The writer is Maffeo da Treviglio, the Milanese agent who had negotiated the Sforza-Corvinus match since 1489 (the
Milan copies of his cipher letters are `../buda1489`). He writes from Milan on 30 November 1490 (feast of St Andrew;
the minute is dated "Ultimo Novembris 1490") after reaching Duke Gian Galeazzo Sforza ("my Most Illustrious Prince")
on the 20th (the minute says the 24th). After King Matthias's death (April 1490) the planned marriage of Bianca Maria
Sforza, the Duke's sister, to John Corvinus had lapsed; the new king, Vladislas II, took up the "affinity" himself.
The letter:

- reports Maffeo's audience in Buda with the king, Bianca Maria's part ("medio Illustrissime Domine Blance") and the
  Chancellor of Bohemia, and the Duke's warm reception of the offer; the Duke now counts Bakócz among his foremost
  friends;
- presents the alliance as the continuation of the bond with King Matthias;
- on the dowry: the King's demand seemed to exceed all measure and made the Duke hesitate (no king had ever received
  such a sum); still, having come down to 150,000 ducats, he now goes to 200,000, in jewels or money as the King
  chooses; if money, 10,000 of it goes to the bride's trousseau ("in uestitu sponse"); the King is to provide the
  jewels honourably;
- asks Bakócz to send the courier back at once: either envoys with a proper mandate come to Milan, or Milanese envoys
  go to conclude; otherwise Bakócz is to report the new king's will and decision.

Full texts: `reading/latin.md` (Latin), `reading/english.md` (translation), `reading/p1.md`-`p4.md` (line by line).

## The system

A homophonic Latin cipher of letter-like signs, figures and marks: 76 labels in 3,199 tokens (14 lost to damage),
about 60 signs that carry the text (`transcription/signs.md`, `key.md`). It is not Maffeo's 1489 key R5411 of
`../buda1489` (there a = r, 1, f and e = ꝛ, 4, //; here a = to, F (φ), L (⊥) and e = o, w, E, B), nor Somogyi's
reconstruction of it. `../buda1489/key_R5411.md` notes a second key "Cum Mafeo Triviliensi", ASMi cart. 1597 no. 107
(DECODE R5407), "a different alphabet (A = ⊥ ...)": ⊥ (L) is a homophone of a here, so R5407 may be this cipher's key.
Not checked.

- Homophones: e has five signs (o, w, E, B, q), i four (2, 4, m, ni), a four, s five, t four, u three.
- Polyphonic signs: qB = u (157) / s (14) / f (7); ooA = u (61) / s (7); s = h / f; 3 = n (g six times, probably 3G
  misread); tp = b (a twice); gA = o (t twice).
- Pair units: Ho = p, oH = q, n + u-sign = q (else i), 6/6A + gA = ll.
- Doubled-letter signs: X = ss, LL = ll, Ob = mm, sl = cc, wL = tt, Od = dd; & = et.
- Code signs: ff = Serenissimus Dominus Rex (Hungarie), ve = Illustrissimus Princeps / Dominus meus (the Duke), Tx =
  Maiestas sua, Ga = affinitas, Gp = non, dt / dx = quod, K = quoniam, fo = centum quinquaginta milia; y probably 200,000
  (2 cases, left unvalued).
- Nulls: A, al, aN, Rx, e.
- No word division. Spelling of the cipher writer: double consonants often single (afinitatem, suma, comunem), h
  dropped (retraere).

## How the key was obtained

1. **Images.** The 28 Oct stub could not get past the Hungaricana viewer (CORS in the built-in browser; a 403 to direct
   requests). The user supplied the three image files (p. 1, the pp. 2-3 spread, p. 4) from their own browser; they stay
   out of git (link above).
2. **Transcription** by Claude agents from crops, then shape-only split passes (q into qA/qB/4; g, oo, h, 8, 6) and two
   rounds of key-guided image repairs where every change had to be visible on the image (`transcription/signs.md`,
   per-page fix logs in the working folder).
3. **Ciphertext-only break.** Simulated annealing (`scripts/hsolve.py`, Latin 4-gram model, letter-frequency penalty;
   a synthetic control text by `scripts/control.py`) gave a first key; cribs (reuerendissimam dominationem uestram)
   fixed D = m; then six reading rounds, each decrypting, word-dividing, finding where the Latin broke, checking those
   signs on the images and adjusting the key (`scripts/dec14.py`, `scripts/measure14.py`). Strict words read rose
   from 23% to 79.2% (key14).
4. **External plaintext.** The clear minute of the same letter was then found in Vestigia (<https://www.vestigia.hu>, search by date with `scripts/vsearch.py`): document 194 = ASMi
   Sforzesco 642, "novembre no. 8" (`reading/clear_minute.txt`, read from the Vestigia images). An EM dynamic-
   programming alignment of the cipher with the minute (`scripts/ext/em_align.py`, `report.py`) gave the key sign by
   sign (`key.json`, `key.md`), the alignment (`reading/align.md`) and the list of isolated disagreements
   (`transcription/suspects.md`).
5. **Check of the ciphertext-only work.** Of the 424 words the blind key14 reading had read (not marked doubtful),
   396 = 93.4% match the minute exactly; key14 was right on 60 of 81 signs, 96.2% of tokens. It had missed the code
   signs (taken as nulls) and had ooB as u instead of s.

## The reading

`measure.py` counts the words of the cipher letter (the minute's words the cipher enciphers, plus the words it adds)
and calls a word read when its signs give a Latin word that fits the sentence, including where the wording differs
from the minute. It does not count a word that rests on an unchecked suspect sign, an unvalued sign or damage.

| page | words | read | % | of undamaged | suspect | unvalued | no sense | damage |
|---|---|---|---|---|---|---|---|---|
| 1 | 202 | 172 | 85.1 | 85.6 | 3 | 13 | 13 | 1 |
| 2 | 198 | 176 | 88.9 | 89.3 | 1 | 1 | 19 | 1 |
| 3 | 185 | 158 | 85.4 | 90.3 | 4 | 10 | 3 | 10 |
| 4 | 39 | 38 | 97.4 | 97.4 | 0 | 0 | 1 | 0 |
| all | 624 | 544 | **87.2** | 88.9 | 8 | 24 | 36 | 12 |

Read = 510 exact, 18 spelling variants, 9 different wording (with extendet and condiciones, confirmed on the image) (uigesimam, audiitque, uestitu, euenit, debebit, the order
"habere uelit tantum"), 7 added words. Strict agreement with the minute (`reading/measure_external.txt`): tokens
3047/3199 = 95.2%, minute words 503/616 = 81.7%. Under the 95% bar the letter is read in part.

## The cipher and the minute

The cipher was made from the corrected minute: every interlinear insertion is enciphered (precipue inclinare, bonis
operibus, summa / expeti, conditiones, ut spero, the caret "centum"), and so is the long marginal addition (et eo minus
quoniam ... communem habere solet), in its reading position; none of the deleted passages is ("ne tam immodica petitio
...", "bona habere"). The cipher writer added "et" three times and "non" in "amabat non mediocriter", where the minute
has a doubtful word, and "quoniam" where the minute is illegible. `reading/clear_vs_cipher.md` lists the differences.

## Remaining gaps

- 33 words resting on the 41 transcription suspects (two of them, P3L04 #26 and P3L05 #1, are alignment artefacts: the cipher has "habere uelit tantum") (`transcription/suspects.md`: one sign disagrees while both
  neighbours agree, e.g. P1L05 qA in "afinitasem", P2L27 F in "ragi") - blocker: needs an image check sign by sign; not
  done in this session.
- 23 words on unvalued signs: the title of Bianca Maria (P1L06), the Chancellor of Bohemia (P1L10) and "Serenissimi
  Domini Regis sui necnon" (P1L17), each where a letter sign stands for a phrase once; y (200,000, P3L02, P3L12);
  8C (4 tokens: i, x, ii); the "A qB s tp" group at "summa ducentorum milium" (P3L08) - blocker: single occurrences, no
  second case to fix a value.
- 22 words that give no fitting Latin: writer slips (proter, presenis, prefatu, cotraxerat) and the stretch "imo uideat
  quod ambobus" (P2L22), which the signs give as "neq uuieat a quibus"; "s p" at the end of P4L05 - blocker: not
  resolved from the key; image check pending.
- 12 words with a lost sign (P3L15-21 above all), filled from the minute in ⟨⟩ - blocker: illegible (damage).

## Escalation

- [x] siblings: `../buda1489` (Milan copies of Maffeo's letters) and key R5411: a different alphabet
- [x] clear-pages: the closing and address on p. 4 are in clear; the clear minute is ASMi Sforzesco 642 (Vestigia 194)
- [x] known-keys: R5411 and Somogyi's key ruled out; R5407 (second Maffeo key, A = ⊥) not yet compared
- [x] print: no edition of DL 46150 found; Vestigia 194 prints the minute
- [x] key-rebuild: ciphertext-only (key14, 79.2% strict) and from the minute (key.json)
- [ ] retry: image check of the 41 suspects, 8C and "s p" - blocker: not-attempted

## History

### 28 Oct 2026: not attempted, blocked (claude-sonnet-5-5)
1. Read buda1489 NOTES, key_R5411.md and the 1235 verification record.
2. Hungaricana viewer: five images (colour target, orig_1 p. 1 3668x3739 px, orig_2 spread of pp. 2-3, orig_3 p. 4,
   seal). The viewer's tile requests are blocked by CORS in the built-in browser and the tile URLs are encrypted
   client-side; only 829 px thumbnails were reachable, too small to transcribe. Nothing was bypassed.

### 29 Oct 2026: transcription, ciphertext-only break, key from the minute (claude-opus-5-5)
See `WORKLOG.md`.

## Files

- `transcription/p1.txt`-`p4.txt` (final), `signs.md`, `suspects.md`, `p4_clear.txt`
- `key.json`, `key.md`; `scripts/build_key.py` writes them from `scripts/data/key_external.json`
- `reading/p1.md`-`p4.md`, `latin.md`, `english.md`; `clear_minute.txt`, `clear_minute_running.txt`,
  `clear_vs_cipher.md`, `align.md`, `measure_external.txt`
- `measure.py` -> `measure.txt` and the reading files
- `scripts/`: `hsolve.py` (annealer), `refine.py`, `control.py`, `dec14.py`, `build14.py`, `measure14.py` (the
  ciphertext-only rounds; they ran from the working folder and expect its files), `ext/` (alignment with the minute),
  `data/` (alignment.json, key_external.json, key14.json)

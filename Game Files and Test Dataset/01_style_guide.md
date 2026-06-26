# Sparks of November — Localization Style Guide

**Source language:** English
**Target language:** Polish
**Document version:** 1.2
**Status:** Internal — distribute to vendor leads only
**Last update:** Q3 2026
**Owners:** Localization Director (Studio), Polish LSP Lead, Historical Consultant

---

## 1. Project overview

*Sparks of November* is a narrative-driven isometric RPG set in Warsaw and the surrounding Mazovian countryside in autumn 1830, in the weeks leading up to the November Uprising. The player guides one of three protagonists — **Marianne Dembowska** (impoverished noblewoman), **Tadeusz Lipiński** (townsman doctor), or **Count Antoni Sobański** (Russian-aligned magnate) — through interlocking storylines of romance, conspiracy, and political crisis. The game is rated 16+ for thematic content, period-appropriate violence, and mild sexual content.

The Polish localization is the most sensitive market for this title. Polish players are the primary audience for whom this is a story about *their* history. We expect heightened scrutiny of tone, vocabulary, and historical detail, including from press, streamers, and academic reviewers.

The localization should read as *Polish prose set in the period*, not as a translation of a foreign text. Faithfulness to the source meaning is essential, but transliteration of English idiom, English sentence structure, or anachronistic phrasing is unacceptable.

---

## 2. General principles

**Faithfulness over literalness.** Translate meaning and tone, not word order. If a literal rendering would produce a clumsy or inauthentic Polish sentence, rewrite. The English source is final for facts and plot points but advisory for phrasing.

**Period appropriateness within reason.** The target register is *educated 21st-century Polish with the flavor of the early 19th century*, not pastiche of period prose. The player must be able to read dialogue at conversational speed. Avoid words that did not exist in 1830 (see §8 below). Equally avoid heavy archaisms that would slow the reader down. When in doubt, ask in the project Q&A sheet rather than guessing.

**Playability.** Translation length must respect UI constraints (see §10). Subtitles must be readable at the speech rate of the voice acting. Names and key terms must remain consistent across the corpus.

**Single voice per character.** Each character has a defined voice. Translators handling different parts of the corpus must adhere to that voice consistently. The character bible governs voice; this guide governs language-level rules.

**Flag, don't guess.** Where context is missing, do not invent it. Use the project Q&A sheet (linked in vendor portal) and the project's reference RAG tool (when available) before resorting to an interpretive guess. A flagged string with a clear note is always preferable to a confidently wrong one.

---

## 3. Tone and register

The corpus contains four broad registers, with significant code-switching even within a single conversation. Get the register right and the rest tends to follow.

**Salon register.** Polite, allusive, ironic. The default for noble interactions in social settings. French phrases interspersed (kept in French — see §6). Sentences are full and grammatical. Direct emotion is rare; meaning is implied. *Marianne in salon scenes; Antoni almost always; Anna Sobańska always.*

**Domestic register.** Warm, plain, less formal. Used within families, between trusted servants and masters, in the rural Dembowski household. *Marianne with her mother; Tadeusz with his parents; Father Wiśniewski with parishioners.*

**Officer register.** Direct, military, salted with technical terms and cadet slang. *Stefan Dembowski, his fellow officers, Wysocki, Józef Dembowski when reminiscing.*

**Townsman register.** Practical, sometimes blunt, peppered with trade vocabulary. *Wojciech Lipiński, the apothecary's customers, hospital staff, Café Honoratka regulars.*

A single conversation may move between registers. Tadeusz code-switches constantly: medical Latin with patients, polished salon Polish with Marianne, plain townsman Polish with his father, and a private register of self-doubt in his interior monologue lines. Translators should track the register cues in the source text (formality of vocabulary, sentence length, presence of French/Latin) and reproduce them.

---

## 4. Forms of address — the staircase of intimacy

This is the area where Polish localization will be most carefully judged by reviewers. Get it wrong and the relationship dynamics break.

### 4.1 Default forms

- **Pan / Pani** — universal respectful default for adults. Used between strangers, across class lines, in formal settings.
- **Pan + first name (Panie Tadeuszu)** — friendly but still respectful. Adopted between acquaintances who have established cordiality but not intimacy.
- **First name alone (familiar/intimate)** — only between family, very close friends, lovers, or from a clear social superior to a clear social inferior in informal speech (e.g., a noble employer addressing a long-serving servant by first name).
- **Ty (informal pronoun)** — implies the same intimacy threshold as first-name address.

### 4.2 The romance arcs

The Marianne–Antoni arc moves through the staircase across the game. It is critical to track the transition correctly.

- **Acts I–II early:** strict *Pan/Pani*. Even at the salon, where they exchange witty banter, the polite forms are preserved. Antoni's dialogue may use *Pani Marianno* once he has been formally introduced (a deliberate forwardness on his part).
- **Mid Act II:** after the Łazienki walk, Antoni shifts to *Pani Marianno* consistently; Marianne remains at *panie hrabio* (Count) in formal address but uses *Pan Antoni* in private moments.
- **Late Act II / Act III:** in private scenes only, both move to first-name address and *ty*. In any scene where they are observed by others, they revert to formal address. This stratification is character-defining and must be preserved.
- **Crisis and resolution:** in the climactic Act III scenes, the pronoun choice itself becomes a dramatic signal. The exact strings affected are flagged in the source with `[INTIMATE]` or `[FORMAL]` register tags. Do not override these tags.

The Marianne–Tadeusz interaction stays at *Pan/Pani* throughout. They are friends; they are not romantically connected. A breach of this would re-write character relationships.

### 4.3 Family forms

- Marianne addresses her father as *Ojciec* or *Tato* (the latter in private, warm moments). Her mother as *Mama* or *Mateczko* in tender moments.
- Stefan addresses Marianne as *Marianno* or *Maniu* (diminutive, in tender moments). She addresses him as *Stefciu* (diminutive) only in private; otherwise *Stefanie* or *Stefan*.
- Helenka calls Marianne *Maniu* always.
- The Lipiński household is similar: *Tato, Mamo, Tadku* (diminutive of Tadeusz, used by his mother in private).

### 4.4 Forms toward authority

- Constantine: *Wasza Wysokość* (Your Highness) when addressed; *Wielki Książę* in narration.
- Princess Joanna: *Wasza Książęca Mość* in formal speech; *Księżna* in narration.
- Russian senior officers: their formal Russian rank in transliterated form is acceptable in narration; in dialogue, a Polish character would say *Pan Generał* (general) or *Wasza Ekscelencja* (Excellency) according to the actual relationship.

---

## 5. Names and proper nouns

### 5.1 Character names

- **Polish characters** retain their Polish form in target text. *Marianna Dembowska, Tadeusz Lipiński, Antoni Sobański, Stefan Dembowski, Helenka, Józef, Zofia,* etc.
- **Marianne (note):** the source text uses the French form *Marianne* throughout, reflecting her family's Francophile salon habit. The target text also uses *Marianne* in salon and high-society scenes (with Antoni, Anna Sobańska, etc.), but uses *Marianna* or *panna Marianna* in family and rural scenes. The source-text [SALON] and [DOMESTIC] tags indicate which form to use; if no tag is present, default to *Marianna*.
- **Russian characters** keep their Russian names. Transliterate from Cyrillic following standard Polish conventions (e.g., *Mikołaj* for *Nikolai* is *not* used; we use *Nikołaj Nowosilcow* per established Polish historical usage). See §5.4 for the canonical list.
- **German names** kept as-is (Hufeland remains Hufeland).

### 5.2 Place names

- All Warsaw streets, squares, and buildings use their canonical Polish forms. *Krakowskie Przedmieście*, *Plac Saski*, *Belweder*, *Łazienki*, etc.
- Foreign cities receive standard Polish forms where these exist: *Petersburg*, *Wiedeń*, *Berlin* (no change), *Paryż*.

### 5.3 Titles and ranks

- **Polish:** *hrabia* (count), *książę* (prince/duke), *baron* (rare in Poland), *kasztelan*, *podkomorzy*, *podchorąży* (cadet), *porucznik* (lieutenant), *kapitan*, *major*, *pułkownik*, *generał*.
- **Russian:** keep formal rank in narration in the Russian form (*senator*, *generał-gubernator*, *gienierał-major* — note the deliberate Russian-flavored spelling preserved in some narrative voice).
- **Religious:** *ksiądz* for parish priest; *biskup* for bishop; *brat* for monastic brother; *siostra* for sister/nun.

### 5.4 Canonical name list

This list is binding. Any new character must be added here through the Q&A process before localization begins.

| Source (EN) | Target (PL) | Notes |
|---|---|---|
| Marianne / Marianna Dembowska | Marianna Dembowska / Marianne (in salon scenes only) | See §5.1 |
| Tadeusz Lipiński | Tadeusz Lipiński | Diminutive *Tadek* in family use |
| Count Antoni Sobański | hrabia Antoni Sobański | Title precedes name in narration; "panie hrabio" in dialogue address |
| Stefan Dembowski | Stefan Dembowski | Diminutive *Stefcio* (intimate only) |
| Helenka Dembowska | Helenka Dembowska | Always diminutive |
| Józef Dembowski | Józef Dembowski | Marianne's father |
| Zofia Dembowska | Zofia Dembowska | Marianne's mother |
| Wojciech Lipiński | Wojciech Lipiński | Tadeusz's father |
| Maria Lipińska | Maria Lipińska | Tadeusz's mother |
| Dr. Henryk Reszka | dr Henryk Reszka | Note "dr" lowercase, no period in Polish convention |
| Sister Cecylia | siostra Cecylia | |
| Anna Sobańska | Anna Sobańska | |
| Captain Pavel Volkov | kapitan Paweł Wołkow | Polonized form per §5.1; Russian original retained in occasional Russian dialogue |
| Father Marek Wiśniewski | ksiądz Marek Wiśniewski | |
| Grand Duke Constantine | Wielki Książę Konstanty | Historical Polish form |
| Joanna Grudzińska, Princess of Łowicz | Joanna Grudzińska, księżna łowicka | |
| Lt. Piotr Wysocki | porucznik Piotr Wysocki | |
| Senator Novosiltsev | senator Mikołaj Nowosilcow | Established Polish historical spelling |
| General Józef Chłopicki | generał Józef Chłopicki | |

---

## 6. Multi-language utterances

Several characters code-switch between Polish, French, Russian, German, and Latin. Code-switching is character-defining.

### 6.1 French

Used by upper-class characters in salon settings. Source-text French phrases are preserved unchanged in target text. *Comment dirais-je*, *mon cher*, *en passant*, *tant pis*, etc., remain French. Do not translate to Polish, do not italicize unless the source did.

### 6.2 Russian

Antoni, Volkov, and Russian-aligned characters use occasional Russian. In source, these are written in Latin transliteration with brackets, e.g., `[RU]душа моя[/RU]`. In target text, retain the Cyrillic and the tags; the engine renders these in italic. Do not transliterate to Polish letters.

### 6.3 German

Tadeusz uses occasional German tags from his Berlin years. Preserve in German.

### 6.4 Latin

Medical and ecclesiastical Latin. Preserve in Latin.

### 6.5 Tags

The source uses `[FR]...[/FR]`, `[RU]...[/RU]`, `[DE]...[/DE]`, `[LAT]...[/LAT]` to mark multi-language utterances. These tags must be preserved exactly. The localization tool will validate them; mismatched tags will fail QA.

### 6.6 Unit tags and the one/few/many/other plural structure

When a string contains a **count placeholder** (`{QUANTITY}`, `{count}`, `{n}`, …) attached to a counted noun, the noun must agree with the number. Wrap the counted phrase in a **unit tag** `[u]…[/u]` and provide one block per plural category the target language needs, using the CLDR category tags **`[one]` / `[few]` / `[many]` / `[other]`**. The count placeholder stays inside every variant.

```
[u][one]{QUANTITY} sztuka[/one][few]{QUANTITY} sztuki[/few][many]{QUANTITY} sztuk[/many][other]{QUANTITY} sztuki[/other][/u]
```

Which categories to populate (do not invent forms a language does not use):

- **English, German:** `one` (n = 1) and `other` (everything else) — two blocks.
- **Polish:** `one` (1), `few` (2–4, but **not** 12–14), `many` (0, 5–21, and 12–14), `other` (decimals only). In practice supply `one` + `few` + `many`; add `other` only if fractional counts can occur.
- **Russian, Ukrainian, Czech:** same four-way split as Polish.

Examples:

- EN — `[u][one]{QUANTITY} dose[/one][other]{QUANTITY} doses[/other][/u] remaining.`
- PL — `Pozostało [u][one]{QUANTITY} dawka[/one][few]{QUANTITY} dawki[/few][many]{QUANTITY} dawek[/many][/u].`

The `[u]` form is the **authoring shorthand for the bilingual sheet**; it maps 1:1 to the ICU `{count, plural, …}` form in §9.3 that the engine consumes. Either form is acceptable in the sheet. QA fails a string if a required category is missing for the target language, or if the count placeholder is dropped from any variant. **Do not** leave a bare `{QUANTITY} doses` in the target — that is a hard-coded English plural and will fail QA.

### 6.7 Gender-variant tags for mob nouns — `[ms]` / `[fs]`

Mob strings (creatures, enemies, and ambient units that wander the map) are a list of **nouns**. The same entry is shown for a male or a female unit, so each mob noun must carry **both gendered forms**; the engine picks one by the unit's gender flag — e.g. whether it is rendering a *wieśniak* or a *wieśniaczka*.

Write the male form and the female form, each preceded by its tag and separated by a semicolon:

```
[ms]<male noun>;[fs]<female noun>
```

Examples:

```
[ms]arystokrata;[fs]arystokratka
[ms]mieszczanin;[fs]mieszczanka
```

Rules:

- Every mob-noun string must contain **both** `[ms]` and `[fs]` forms. A string with only one form fails QA.
- **Nouns only** — the mob's name/label. This does **not** apply to sentences, dialogue, or verbs; never use `[ms]`/`[fs]` to inflect a verb or a whole clause.
- The source (English) is normally a single genderless noun; the two Polish forms are produced in translation.

---

## 7. Profanity, oaths, and religious invocation

The game contains mild profanity by design. The Polish target should be **period-appropriate**, not modern street slang.

**Permitted period oaths and exclamations:**
*do diabła*, *na Boga*, *na rany Pańskie*, *psia krew*, *bodajby cię*, *tam do licha*, *jezdem* (regional dialect, Mazovian, used by some peasant NPCs), *do stu piorunów*.

**Prohibited (anachronistic):**
*kurwa*, *jeb-* roots, modern slangy variants. These would have existed in some form in 1830 but their modern colloquial spread is post-1945. Their use breaks the period feel for Polish ears.

**Religious invocation** by characters is period-typical and not censored. Marianne genuinely prays in moments of crisis. Józef Dembowski swears by the Black Madonna. Father Wiśniewski blesses people. Treat these reverently in target text.

**Ethnic slurs:** *Moskal* is canonically used by patriotic characters (Józef, Stefan, the conspirators) when referring to Russians. It should be preserved in target text exactly where it appears. The source uses *Muscovite* in English, with a footnote-style developer comment indicating that the period Polish equivalent is intended; render as *Moskal* always.

---

## 8. Period vocabulary — what to use and what to avoid

### 8.1 Encouraged period flavor (used naturally, not heavy-handedly)

*kontusz, żupan, czamara* (period clothing); *austeria, karczma* (inn); *parobek* (farm hand); *rządca, ekonom* (estate steward); *kareta, bryczka, dorożka* (carriage types); *rękopis* (manuscript); *pojedynek* (duel); *honor, słowo* in their period weight.

### 8.2 Words to avoid (anachronisms)

- Words referring to post-1830 inventions, institutions, concepts. *Telegraf, fotografia, fabryka* in the modern sense, *nacjonalizm* (the term, not the phenomenon), *demokracja* in the modern political sense.
- Modern slang and colloquial register for any character. *Spoko, ekstra, super, mega, hej.*
- 20th-century political vocabulary. *Reakcyjny, postępowy, klasa robotnicza* — not in this period in this sense.
- Soviet-era usages that may feel Polish but are post-1945. *Towarzysz* in the political sense; *kolega* for a wider range of relationships than would have been used in 1830.

### 8.3 Borderline cases

- *Naród* in 1830 already has its modern resonance — usable freely.
- *Ojczyzna* — universally usable, weighty.
- *Patriota* — already established in 1830 — usable.
- *Konstytucja* — already a political reality (the Constitution of 1815) — usable.

When in doubt, ask. The Q&A sheet will be reviewed daily during the active translation phase.

---

## 9. Polish-specific issues

### 9.1 Inflection and termbase markers

The project's memoQ termbase uses `|` and `*` markers to indicate stem/inflection boundaries. Translators should apply these markers when adding new terms, particularly proper nouns that will inflect across the corpus (*Marianna*, *Sobański*, *Belweder*, *Dembowo*, etc.). Untagged terms produce false-positive QA errors and missed real inconsistencies.

If your version of memoQ does not validate inflection markers correctly, see the project's *Polish QA Companion* document for the workaround procedure.

### 9.2 Gender and grammatical agreement with player choice

The player may choose Marianne, Tadeusz, or Antoni at game start — i.e. the protagonist can be **male or female**. Therefore any string that refers to the protagonist, and in particular **any string containing `{character.firstName}` (or another player-name placeholder), must be written GENDER-NEUTRAL in Polish.**

Polish past-tense verbs are gendered (*zdobył / zdobyła*, *poprawił / poprawiła*), so they **cannot** be used in these strings. Do **not** use:

- a gendered past-tense form chosen for one gender (e.g. *{character.firstName} zdobył nową umiejętność*);
- bracketed double forms such as *zdobył(a)* or *poprawił/poprawiła* — these never ship in-game and are not acceptable.

Instead, rephrase to a wording that is identical for both genders. Two reliable techniques:

- **Present tense** — the Polish 3rd-person singular present is not gendered: *{character.firstName} zdobywa nową umiejętność.* / *{character.firstName} doskonali {skill.name}.*
- **Nominal / impersonal phrasing** — e.g. *Nowa umiejętność: {character.firstName}.*

Where the engine *does* provide gender placeholders (`{PRONOUN_HE_SHE}`, `{ARTICLE_NOM_M_F}`, …) for elements it resolves at runtime, use them and do not flatten them; see the engine's placeholder reference (`/loc/placeholders.md`). But for verbs and adjectives that have no such placeholder, a gender-neutral rewrite is mandatory. (`[ms]`/`[fs]` from §6.7 are **mob-noun** tags and must **not** be used for the protagonist.)

### 9.3 Plural and case-aware placeholders

Numeric strings use ICU MessageFormat plurals: `{count, plural, one {# kula} few {# kule} many {# kul} other {# kuli}}`. Translators must populate all four Polish plural categories where they apply. The build pipeline rejects strings missing categories. In the bilingual sheet you may instead use the equivalent `[u][one]…[/one][few]…[/few][many]…[/many][/u]` unit-tag shorthand from §6.6; it compiles to this ICU form.

---

## 10. UI text rules

- **Buttons:** maximum 18 characters in target text, ideally under 14. If a longer Polish equivalent is unavoidable, flag it.
- **Tooltips:** maximum 280 characters per panel. Avoid line breaks unless source had them.
- **Subtitles:** maximum 42 characters per line, two lines per subtitle, no more. Subtitle reading speed is 17 characters per second. The voice timing is fixed; if your translation runs long, flag it for the audio team.
- **Item names:** maximum 32 characters.
- **Quest titles:** maximum 36 characters. Period flavor encouraged.
- **Inventory categories** are hard-coded in the engine and are non-translatable. (Build pipeline will reject changes to these strings.)

---

## 11. Placeholders, tags, and special content

- `{playerName}`, `{character.firstName}`, `{location.name}`, etc. — never translate. Position in the target sentence may move; identifier must not change.
- `<i>...</i>`, `<b>...</b>`, `<color=#...>...</color>` — preserve markup exactly. Be aware that nested or mismatched markup will fail QA.
- `[FR]...[/FR]`, `[RU]...[/RU]`, etc. — see §6.
- `[u]...[/u]` with `[one]/[few]/[many]/[other]` — unit/plural tags, see §6.6. Keep every category the target language requires and keep the count placeholder inside each variant.
- `[ms]…;[fs]…` — male/female **noun** forms for mob names, see §6.7. Nouns only; always supply both forms.
- Newlines (`\n`) — preserve exactly. Do not introduce new line breaks; do not collapse existing ones.
- Empty strings — leave empty. Do not "translate" by inserting placeholder text.
- Descriptions should end with full stops.

---

## 12. What to flag in Q&A

Flag any string where:

- The source contains slang or idiom whose target equivalent is uncertain.
- The string ID, comment, or surrounding context appear inconsistent with the canonical lore.
- Period appropriateness is doubtful.
- Inflection or gender agreement is ambiguous because of unknown speaker gender.
- A placeholder behavior is unclear.
- A French/Russian/German fragment appears without its expected tag.
- The string seems out of register for the speaker.

Use the Q&A spreadsheet (project portal) for all queries. Future versions of the project will integrate the in-tool RAG query system, and this guide will update accordingly.

---

## 13. Reference quick list

Default forms for repeating concepts:

| Concept | Target |
|---|---|
| New Game | Nowa gra |
| Continue | Kontynuuj |
| Save | Zapisz |
| Load | Wczytaj |
| Settings | Ustawienia |
| Inventory | Ekwipunek |
| Quest | Zadanie |
| Quest log | Dziennik zadań |
| Map | Mapa |
| Codex | Kompendium |
| Character | Postać |
| Health | Zdrowie |
| Stamina | Wytrzymałość |
| Resolve (game stat) | Hart ducha |
| Reputation | Reputacja |
| Skill | Umiejętność |
| Level up | Awansuj |
| Choose | Wybierz |
| Confirm | Potwierdź |
| Cancel | Anuluj |
| Yes / No | Tak / Nie |

---

*End of Style Guide v1.2.*

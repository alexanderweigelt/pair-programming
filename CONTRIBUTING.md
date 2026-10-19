# Mitwirken an Pair Programming

Danke für Ihr Interesse. Die oberste Grundlage sind die Skill-Anweisungen in [skills/pair-programming/SKILL.md](skills/pair-programming/SKILL.md) und das Sicherheitsmodell im [README](README.md#security-model): Was dort steht, gilt. Prüfen Sie jede Änderung daran.

## Regeln für den Skill

- Der Skill bleibt reine Anweisung: keine Skripte, ausführbaren Dateien, MCP-Server oder vorausgesetzten externen Dienste.
- Das Frontmatter von `SKILL.md` legt Name, Beschreibung und Aufrufverhalten fest. Die Beschreibung sagt, wann der Skill passt und wann nicht.
- Der Kern ist anbieterneutral. Agentenspezifisches gehört in eigene Dateien unter `agents/`, zum Beispiel `agents/openai.yaml`, und muss zu `SKILL.md` passen.
- Assets unter `assets/` werden nur aufgenommen, wenn eine Agentenkonfiguration sie referenziert.
- Freigabe- und Stopp-Grenzen (Netzwerk, Installationen, Commits, Pushes, Sicherheitsprüfungen) werden nicht aufgeweicht. Jede Lockerung braucht eine ausdrückliche Begründung im Pull Request.
- Keine Entstehungsgeschichte, Schulungsbezüge oder Änderungshistorien in `SKILL.md`.
- Nichts erfinden: keine Funktionen, Fakten, Befehle oder Prüfergebnisse. Was nicht geprüft werden konnte, wird als ungeprüft gekennzeichnet.

## Sprache

- Anweisungen für Agenten (`SKILL.md`, `agents/openai.yaml`, `CLAUDE.md`), das `README`, Dateinamen und Code sind englisch.
- Dieser Leitfaden ist deutsch.
- Formulierungen werden wörtlich gelesen: „sollte“ ist optional, „muss“ ist Pflicht. Nicht verschärfen.

## Branch-Modell (Gitflow)

- `main` enthält nur veröffentlichte, stabile Stände. Es wird nicht direkt darauf gearbeitet.
- `develop` sammelt fertige Änderungen für die nächste Version.
- `feature/<short-name>` für jede Änderung, abgezweigt von `develop` und dorthin zurückgeführt.
- `release/<version>` zur Vorbereitung einer Version, danach nach `main` und `develop`.
- `hotfix/<short-name>` für dringende Korrekturen, abgezweigt von `main`, danach nach `main` und `develop`.
- Branch-Namen sind immer englisch, Kleinbuchstaben, mit Bindestrichen, zum Beispiel `feature/handoff-format`.

## Commits (Conventional Commits)

- Commit-Nachrichten folgen [Conventional Commits](https://www.conventionalcommits.org/) und sind immer englisch: `<type>: <description>`, zum Beispiel `fix: tighten approval boundaries`.
- Erlaubte Typen: `feat`, `fix`, `docs`, `refactor`, `ci`, `chore`.
- Die Beschreibung steht im Imperativ, ohne Punkt am Ende. Eine Begründung kann in den Nachrichtentext.
- Eine logische Änderung pro Commit. Ein Breaking Change wird mit `!` hinter dem Typ und `BREAKING CHANGE:` im Nachrichtentext gekennzeichnet.

## Änderungen einreichen

- Halten Sie Änderungen klein und begründen Sie sie mit dem Zweck des Skills. Weniger ist besser: Lassen Sie weg, was keinen Nutzen hat.
- Ändert sich das Verhalten des Skills, prüfen Sie, ob `README.md`, `CLAUDE.md` und `agents/openai.yaml` angepasst werden müssen.
- Prüfen Sie lokal, dass der Skill gefunden wird: `npx skills add . --list`.
- Probieren Sie geänderte Anweisungen in einem Wegwerf-Testprojekt mit einem echten Agenten aus. Nur Angewendetes gilt als geprüft.
- Der Workflow „Mondoo SkillCheck“ muss auf dem Pull Request grün sein.

## Releases

- Ein Release ist ein geprüfter Git-Tag im Format `v0.1.0` mit zugehörigem GitHub-Release. Es gibt keine Release-Automatisierung.
- Vor jedem Release wird die Checkliste unter [Maintainer checks and releases](README.md#maintainer-checks-and-releases) abgearbeitet.

## Mit Agenten arbeiten

Agenten, die an diesem Repository arbeiten, folgen [CLAUDE.md](CLAUDE.md) und den Branch- und Commit-Regeln oben. Sie committen, pushen oder löschen nicht ohne ausdrücklichen Auftrag.

## Lizenz

Mit Ihrem Beitrag stimmen Sie zu, dass er unter der [MIT-Lizenz](LICENSE) steht.

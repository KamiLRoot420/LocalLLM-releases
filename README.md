# LocalLLM — kanał dystrybucji

To repo jest **publicznym kanałem dystrybucji** aplikacji LocalLLM dla Androida.

* **Kod źródłowy** pozostaje prywatny: [`KamiLRoot420/LocalLLM`](https://github.com/KamiLRoot420/LocalLLM)
* Tutaj publikowane są wyłącznie **gotowe pliki APK** jako release’y.

## Jak sprawdzić najnowsze wydanie

```bash
curl https://api.github.com/repos/KamiLRoot420/LocalLLM-releases/releases/latest
```

Aplikacja korzysta dokładnie z tego endpointu — wartość jest wstrzykiwana jako
`BuildConfig.GITHUB_REPO` w `app/build.gradle.kts`, więc źródło aktualizacji nie
może się rozjechać z faktycznym kanałem publikacji.

## Pobieranie

Każdy release ma załącznik `app-debug.apk`. Pliki release’ów w repo publicznym
pobierają się **bez logowania**:

<https://github.com/KamiLRoot420/LocalLLM-releases/releases/latest>

## Weryfikacja integralności

```bash
sha256sum app-debug.apk
```

Wartość SHA256 jest wypisywana przez workflow w logu kroku *„Publish GitHub
release”* i w treści release’a.

## Jak wygenerować nowe wydanie

W prywatnym repo [`KamiLRoot420/LocalLLM`](https://github.com/KamiLRoot420/LocalLLM):
**Actions → Build → Run workflow**, `version` = np. `1.0.1`, `publish_release` = `true`.

Workflow buduje APK i publikuje release w tym repo. Wymaga sekretu
`RELEASES_TOKEN` (fine-grained PAT z uprawnieniem *Contents: read & write*,
ograniczonym wyłącznie do `KamiLRoot420/LocalLLM-releases`) — token
`GITHUB_TOKEN` z workflow jest ograniczony do repo, w którym działa.

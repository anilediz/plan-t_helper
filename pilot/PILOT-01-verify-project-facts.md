# PILOT-01 — Proje bilgilerini doğrulama

Bu, sistemin ilk deneme oturumu. Kodda hiçbir şey değişmez; ajan yalnızca okur, kontrol eder ve rapor yazar. Amaç iki şey: agentic/PROJECT.md içindeki bilgilerin senin reponla uyuştuğunu doğrulamak ve oturum döngüsünün (brief → çalışma → rapor → günlük) baştan sona çalıştığını görmek.

## Nasıl kullanılır

1. Önce README'deki "İlk kurulum" adımlarını yap (agentic/ klasörü, AGENTS.md, CLAUDE.md).
2. Codex'te yeni bir oturum aç.
3. Aşağıdaki brief bloğunu olduğu gibi kopyalayıp Codex'e yapıştır. Başına tek bir cümle ekleyebilirsin: "Bu brief ile bir oturum başlat."
4. Ajanın önerdiği PROJECT.md değişikliklerini tek tek oku. Doğru olanlara "onaylıyorum" de; emin olmadıklarını reddet.
5. Oturum bitince raporu sohbet asistanına (ChatGPT) yapıştır ve kararını iste.

## Brief (Codex'e yapıştırılacak kısım)

```
SESSION: <today's date YYYY-MM-DD>-pilot-verify-project-facts
GOAL: Verify every fact in agentic/PROJECT.md against this working repository, and propose corrections. Read-only session except for the session file, the project log row, and PROJECT.md edits the owner explicitly confirms.
FILES IN SCOPE: agentic/PROJECT.md; the repository tree (directory listing and file sizes only); package.json; scripts/ (file names and the first lines of each script); docs/testing/TESTING.md; docs/Plan-T-development-launcher.md; frontend/prototype/app-config.js; tests/frontend/disabled-features.test.js; git metadata (git status, git branch -a, git remote -v, git log -1).
OUT OF SCOPE: any change to application code, tests, scripts, docs or configuration; any file under agentic/ other than PROJECT.md and the log; opening files listed as off-limits in PROJECT.md.
CONTRACTS TOUCHED: none
TESTS EXPECTED: npm test; dotnet test VenueOps.slnx -c Release --filter "Category=Unit". Run them only to confirm the commands in PROJECT.md work; report a summary (pass/fail counts, failing names). Do not run integration or PostgreSQL tests.
ACCEPTANCE: (1) Every PROJECT.md section is marked in the report as VERIFIED, CHANGED or STILL UNVERIFIED, each with its evidence (command or path). (2) Each proposed PROJECT.md change is shown to the owner as a PROPOSAL and applied only after he confirms it; the VERIFIED AGAINST line is updated with today's date and the current commit. (3) The session file and one project-log row are written. (4) All communication with the owner is in Turkish.
STOP CONDITIONS: stop and ask before any write outside agentic/PROJECT.md and agentic/log/; stop if git status shows uncommitted changes, and report them before reading further.
CONTEXT: first session of plan-t_helper; no earlier log rows.
```

## Oturumdan sonra kontrol listesi (senin için)

Her maddeye evet/hayır de. "Hayır" çıkan maddeleri sağlayıcıya ilet; sistemin neresinin düzeltilmesi gerektiğini bunlar gösterir.

1. Ajan seninle baştan sona Türkçe konuştu mu?
2. Başta oturumu 5 satırda özetledi mi (hedef, dosyalar, kapsam dışı, nerede kaldık)?
3. Hiçbir uygulama dosyasına dokunmadı mı? (Kontrol: git status yalnızca agentic/ altını göstermeli.)
4. PROJECT.md değişikliklerini sana önce sordu, onaysız yazmadı mı?
5. Test çıktısını uzun uzun yapıştırmak yerine kısa özetledi mi?
6. agentic/log/sessions/ içinde yeni bir oturum dosyası ve agentic/log/PROJECT-LOG.md içinde yeni bir satır var mı?
7. Raporda NOT VERIFIED kısmı dolu mu (en azından "UI not visually checked")?
8. Kabaca: bu oturum kotanın ne kadarını yedi? (az / orta / çok)

# plan-t_helper

Plan-t projesi için araçtan bağımsız bir yapay zekâ yardımcı sistemi. Kod yazan ajanlara (Codex, Claude Code vb.) ve sohbet asistanlarına (ChatGPT, Claude, Gemini vb.) aynı kuralları, aynı proje bilgilerini ve aynı ortak günlüğü verir. Böylece hangi aracı kullanırsan kullan, iş kapsamda ve bağlamda kalır.

Sürüm: VERSION dosyasına bak. Sağlayıcı: Anıl Ediz. Proje sahibi: Tuğberk.

Sistemin dosyaları İngilizce yazılmıştır, çünkü bütün modeller onları aynı şekilde okusun. Ajanlar ve asistan seninle her zaman Türkçe konuşur.

## Bu repoda ne var

| Klasör | Plan-t reposunda nereye gider | Kim değiştirir |
|---|---|---|
| core/ (CORE.md, PLANNER.md, CORE-CHANGELOG.md) | agentic/ | Yalnızca sağlayıcı, yeni sürümlerle |
| adapters/ (AGENTS.md, CLAUDE.md) | repo kökü | Yalnızca sağlayıcı |
| project-template/ (PROJECT.md, log/) | agentic/ (yalnızca ilk kurulumda) | Proje sahibi |

## İlk kurulum

1. Plan-t reposunun kökünde agentic adında bir klasör aç.
2. core/ içindeki her şeyi agentic/ içine kopyala.
3. project-template/ içindeki her şeyi (PROJECT.md ve log klasörü) agentic/ içine kopyala.
4. adapters/ içindeki AGENTS.md ve CLAUDE.md dosyalarını repo köküne kopyala. Kökte aynı isimde bir dosya zaten varsa üzerine yazma: mevcut metni koru, adapter satırlarını en üste ekle.
5. agentic/PROJECT.md dosyasını aç ve UNVERIFIED yazan her satırı kendi repona göre kontrol et.
6. agentic/PLANNER.md metnini sohbet asistanının proje talimatlarına (custom instructions) yapıştır.
7. Commit et.

## Güncelleme (yeni sürüm)

1. agentic/ içinde core/'dan gelen dosyaları (CORE.md, PLANNER.md, CORE-CHANGELOG.md) yenileriyle değiştir.
2. AGENTS.md ve CLAUDE.md içindeki adapter satırlarını yenileriyle değiştir.
3. agentic/PROJECT.md ve agentic/log/ klasörünün üzerine asla yazma. Onlar senin projenin kendi bilgileri ve geçmişi.
4. PLANNER.md metnini sohbet asistanına yeniden yapıştır.
5. Neyin değiştiğini görmek için CORE-CHANGELOG.md'deki en yeni kayda bak.

## Bir çalışma oturumu nasıl ilerler

1. Sohbet asistanıyla planla. Projenin nerede olduğunu özetler, hedefi 1–6 oturuma böler ve her oturum için bir brief yazar.
2. Kod yazan ajana tek bir brief ver. Ajan oturumu kısaca tekrar eder, yalnızca o kapsamda çalışır, hedefli testleri çalıştırır, agentic/log/sessions/ içine bir rapor ve agentic/log/PROJECT-LOG.md içine tek bir satır yazar.
3. Arayüzü kendin tarayıcıda kontrol et.
4. Raporu sohbet asistanına geri yapıştır. ACCEPT (kabul), REVISE (düzelt) ya da BLOCKED (engelli) diye cevap verir.

Bir ajan sana bunun kritik bir CORE değişikliği olduğunu söylerse sağlayıcıyla iletişime geç. Projene özel her şey agentic/PROJECT.md içinde; onu kendin değiştirebilirsin.

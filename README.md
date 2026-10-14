# plan-t_helper

Plan-t için yapay zekâ yardımcısı. Hangi aracı kullanırsan kullan (Codex, Claude Code, ChatGPT…), hepsi aynı kurallarla, aynı proje bilgileriyle ve aynı ortak günlükle çalışır. İş kapsamda kalır, sen de nerede kaldığını kaybetmezsin.

Sağlayıcı: Anıl Ediz. Proje sahibi: Tuğberk.

## Kurulum

Kendin bir şey kopyalamana gerek yok. Codex'e (ya da VS Code'daki ajana) şunu yaz:

> plan-t_helper reposundaki INSTALL.md dosyasını oku ve bu repoya kur.

Ajan kurulumu yapar ve sana Türkçe olarak ne yaptığını söyler. Yeni bir sürüm geldiğinde aynı cümleyi tekrar yazman yeterli; senin proje bilgilerine ve geçmişine dokunmaz.

Son adım sende: agentic/PLANNER.md dosyasının içeriğini ChatGPT projenin talimatlarına (custom instructions) yapıştır.

## Nasıl kullanılır

Sistemde iki yardımcı var:

- **Planlayıcı (ChatGPT ya da başka bir sohbet asistanı):** Ne yapmak istediğini onunla konuşursun. İşi 1–6 küçük oturuma böler ve her oturum için bir "brief" yazar. Brief, kod ajanına verilecek kısa iş tanımıdır.
- **Kod ajanı (Codex ya da başka bir ajan):** Brief'i alır, sadece o işi yapar, testleri çalıştırır ve bir rapor yazar.

Bir çalışma döngüsü şöyle:

1. **Planla.** ChatGPT'ye ne istediğini anlat. Sana projenin nerede olduğunu kısaca özetler ve brief'leri hazırlar.
2. **Yaptır.** Bir brief'i kopyala, Codex'e yapıştır. Codex önce işi 5 satırda özetler; sonra yapar. Kritik bir şeye (veritabanı, giriş/yetki sistemi, yeni paket, dosya silme…) dokunması gerekirse durup sana sorar.
3. **Bak.** Uygulamayı tarayıcıda kendin dene, her zamanki gibi.
4. **Kontrol ettir.** Codex'in raporunu ChatGPT'ye yapıştır. Sana şu üç cevaptan birini verir:
   - **KABUL ET:** İş tamam, kanıtlarıyla.
   - **REVİZE ET:** Bir şey eksik ya da kanıtlanmamış; neyin olduğunu söyler.
   - **KARAR VER:** Senin karar vermen gereken bir konu var; ne olduğunu söyler.

Her oturum agentic/log/ klasörüne yazılır. Bir sonraki oturumda ajanlar oradan kaldığın yeri bulur; sana her şeyi baştan anlatmana gerek kalmaz.

Projene özel bilgiler (komutlar, portlar, dokunulmayacak dosyalar, ürün kuralların) agentic/PROJECT.md dosyasındadır. Onu sen değiştirebilirsin. Bir ajan sana "bu kritik bir CORE değişikliği" derse, sistemin kendisiyle ilgilidir; sağlayıcıya haber ver.

## İlk oturum

Kurulumdan sonra pilot/PILOT-01-verify-project-facts.md dosyasındaki adımları izle. Kodda hiçbir şey değişmez; sistemin çalıştığını ve proje bilgilerinin doğru olduğunu gösterir.

# OrçaFácil v3.0

Sistema de orçamentos profissional 100% offline. Desenvolvido por **Josimar Ferreira Soares** — JFSistemas © 2026.

---

## ⚙️ Como subir no GitHub e gerar APK/AAB

### 1. Clonar / subir o repositório
```bash
git init
git remote add origin https://github.com/SEU_USUARIO/orcafacil.git
git add .
git commit -m "feat: OrçaFácil v3.0"
git push -u origin main
```

### 2. Configurar Secrets para build assinado

No GitHub → Settings → Secrets and variables → Actions, adicione:

| Secret              | Valor                                           |
|---------------------|-------------------------------------------------|
| `KEYSTORE_BASE64`   | `base64 -w0 orcafacil-key.jks` (no terminal)   |
| `KEY_ALIAS`         | `orcafacil`                                     |
| `KEY_PASSWORD`      | Senha da chave (definida ao criar o keystore)   |
| `STORE_PASSWORD`    | Senha do keystore (mesma ou diferente)          |

### 3. Gerar o KEYSTORE_BASE64 (Windows PowerShell)
```powershell
[Convert]::ToBase64String([IO.File]::ReadAllBytes("C:\Orcamentos\orcafacil\orcafacil-key.jks")) | clip
# O valor já está na área de transferência — cole no secret
```

### 4. Disparar o build
- Faça um `git push` para a branch `main`, **ou**
- GitHub → Actions → Build OrçaFácil → **Run workflow**

### 5. Baixar os artefatos
Após o build: Actions → Selecionar a run → Artifacts
- `OrcaFacil-debug-apk` — APK para testes
- `OrcaFacil-release-aab` — AAB para Google Play Store ⭐
- `OrcaFacil-release-apk` — APK assinado para distribuição direta

---

## 💰 Monetização

| Plano       | PDFs/dia | Anúncios |
|-------------|----------|----------|
| Gratuito    | 1        | Sim (vídeo rewarded) |
| Premium R$9,99 | Ilimitado | Não |

Para integrar AdMob e Google Play Billing reais:
- Substitua os `// TODO` no `index.html` pelas chamadas reais dos plugins Capacitor.

---

## 🛠️ Instalação local
```bash
npm install
npx cap add android
npx cap sync android
# Abrir no Android Studio:
npx cap open android
```

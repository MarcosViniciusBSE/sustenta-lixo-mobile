# Sustenta Lixo - Aplicativo de Denúncia de Pontos de Lixo

Um aplicativo móvel desenvolvido com Expo e React Native que permite aos usuários denunciar pontos de acúmulo de lixo em suas cidades, contribuindo para a manutenção de espaços públicos limpos e saudáveis.

## 📱 Sobre o Projeto

Sustenta Lixo é um trabalho de universidade que implementa uma plataforma colaborativa para crowdsourcing de informações sobre poluição urbana. Através de um mapa interativo e georeferenciamento, usuários podem reportar áreas problemáticas, facilitando ações de limpeza e gestão ambiental por parte de autoridades públicas e comunidades.

### Funcionalidades Principais

- **Reportar Pontos de Lixo**: Capturar fotos e descrever áreas problemáticas com níveis de gravidade
- **Mapa Interativo**: Visualizar todos os pontos reportados em tempo real via Google Maps
- **Autenticação**: Sistema de login e registro seguro com Firebase
- **Histórico de Denúncias**: Listar e acompanhar reportes feitos
- **Perfil de Usuário**: Gerenciar dados pessoais e estatísticas de contribuição

---

## 🚀 Começar Rapidamente com Expo Go

A forma mais simples de executar este projeto é usando **Expo Go**, um aplicativo gratuito disponível no Android e iOS que permite testar apps Expo sem necessidade de compilação nativa.

### Pré-requisitos

- Node.js >= 18 instalado
- npm ou yarn
- Expo Go instalado no seu celular:
  - [Android](https://play.google.com/store/apps/details?id=host.exp.exponent)
  - [iOS](https://apps.apple.com/app/expo-go/id982107779)
- Credenciais Firebase e Google Maps (veja abaixo)

### Instalação e Execução

1. **Clone o repositório e instale dependências:**

   ```bash
   git clone https://github.com/MarcosViniciusBSE/sustenta-lixo-mobile.git
   cd sustenta-lixo-mobile
   npm install
   ```

2. **Configure as variáveis de ambiente:**

   ```bash
   npm run setup
   ```

   Isso criará um arquivo `.env.local`. Abra-o e preencha com suas credenciais:

   ```env
   EXPO_PUBLIC_FIREBASE_API_KEY=sua_api_key
   EXPO_PUBLIC_FIREBASE_AUTH_DOMAIN=seu_projeto.firebaseapp.com
   EXPO_PUBLIC_FIREBASE_PROJECT_ID=seu_project_id
   EXPO_PUBLIC_FIREBASE_STORAGE_BUCKET=seu_projeto.appspot.com
   EXPO_PUBLIC_FIREBASE_MESSAGING_SENDER_ID=seu_sender_id
   EXPO_PUBLIC_FIREBASE_APP_ID=seu_app_id
   EXPO_PUBLIC_GOOGLE_MAPS_API_KEY=sua_chave_google_maps
   ```

   Para obter essas credenciais, consulte o arquivo `SETUP.md` para instruções detalhadas.

3. **Inicie o servidor de desenvolvimento:**

   ```bash
   npm start
   ```

4. **Abra no Expo Go:**

   - Android: Escaneie o código QR que aparece no terminal com a câmera do seu celular
   - iOS: Abra o Expo Go e digitalize o código QR com sua câmera

Pronto! O app está rodando no seu celular em tempo real. Qualquer alteração no código será refletida instantaneamente (hot reload).

---

## ⚙️ Configuração Detalhada

Consulte o arquivo **`SETUP.md`** para instruções completas sobre:
- Obter credenciais Firebase
- Configurar Google Maps API
- Troubleshooting de problemas comuns
- Variáveis de ambiente disponíveis

---

## 📦 Scripts Disponíveis

```bash
npm start          # Inicia servidor Expo (recomendado para desenvolvimento)
npm run android    # Compila e instala em Android (requer Android SDK)
npm run ios        # Compila e instala em iOS (requer macOS/Xcode)
npm run web        # Abre em navegador
npm run setup      # Copia .env.example para .env.local
npm run lint       # Executa linter do projeto
```

---

## 🏗️ Tecnologias Utilizadas

- **Framework**: Expo com React Native e TypeScript
- **Navegação**: Expo Router (file-based routing)
- **Backend**: Firebase (Authentication, Firestore, Storage)
- **Mapas**: Google Maps API com react-native-maps
- **Persistência**: AsyncStorage para estado de autenticação
- **Câmera**: Expo Image Picker para captura de fotos
- **Localização**: Expo Location para GPS e geocoding

---

## 🔐 Segurança

Este projeto implementa boas práticas de segurança:

- Credenciais Firebase e Google Maps em variáveis de ambiente (nunca no código)
- Arquivo `.env.local` é ignorado pelo Git e nunca é commitado
- Autenticação via Firebase Auth (senhas não são armazenadas localmente)
- Validação de entrada e tratamento de erros

**Importante**: Nunca compartilhe o arquivo `.env.local` ou suas credenciais. Use `.env.example` como template para outras pessoas.

---

## 📁 Estrutura do Projeto

```
sustenta-lixo-mobile/
├── app/                    # Telas da aplicação (file-based routing)
│   ├── (auth)/            # Fluxo de autenticação (login, registro)
│   ├── (tabs)/            # Abas principais (reportar, mapa, denúncias, perfil)
│   ├── _layout.tsx        # Layout raiz
│   └── index.tsx          # Splash screen
├── services/              # Lógica de integração (Firebase, localização, imagens)
├── contexts/              # Context API (autenticação global)
├── types/                 # Definições TypeScript
├── components/            # Componentes reutilizáveis
├── constants/             # Constantes do app
├── assets/                # Imagens e ícones
├── .env.example          # Template de variáveis de ambiente
├── .env.local            # Credenciais reais (gitignored)
├── eas.json              # Configuração EAS (build na nuvem)
└── app.json              # Configuração Expo
```

---

## 🚀 Build e Deploy

### Opção 1: Expo Go (Recomendado para Desenvolvimento)

Execute `npm start` e escaneie o código QR com Expo Go. Perfeito para desenvolvimento e testes rápidos.

### Opção 2: Build Local

Para gerar um APK/AAB compilado para seu dispositivo:

```bash
# APK local (requer Android SDK)
eas build -p android --local --profile production

# APK na nuvem Expo
eas build -p android --profile production --wait
```

### Opção 3: Distribuição

Após gerar o APK, você pode:
- Compartilhar o link de download com testers
- Enviar para Firebase App Distribution
- Submeter ao Google Play Store

---

## 🐛 Troubleshooting

### "Variáveis de ambiente não configuradas"

Execute `npm run setup` e preencha o arquivo `.env.local` com suas credenciais.

### "Câmera/Localização não funciona"

Verifique se as permissões estão concedidas no seu dispositivo (Configurações > Aplicativos > Sustenta Lixo).

### Código QR não aparece

Tente limpar o cache e reiniciar:

```bash
npm start -- --clear
```

Para mais ajuda, consulte `SETUP.md`.

---

## 📚 Aprendizado e Referências

- [Documentação Expo](https://docs.expo.dev/)
- [React Native Documentation](https://reactnative.dev/)
- [Firebase Documentation](https://firebase.google.com/docs)
- [Expo Router Guide](https://docs.expo.dev/router/introduction/)

---

## 📄 Licença

Este projeto é fornecido como está para fins educacionais.

---

## 🤝 Contribuições

Sugestões e melhorias são bem-vindas! Se encontrar bugs ou tiver ideias, abra uma issue no repositório.

---

## ⚡ Dicas de Desenvolvimento

- Use Expo Go para desenvolvimento rápido (hot reload automático)
- Consulte `explicação.txt` para entender a arquitetura do projeto
- Leia `PROMPT_ENGINEERING_WEB_MIGRATION.md` para um plano de migração para web
- Execute `npm run lint` antes de fazer commit

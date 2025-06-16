# Sala Mineira - Gerenciador de Currículos

Uma aplicação web para gerenciamento de currículos desenvolvida para a Sala Mineira do Empreendedor. A aplicação permite cadastrar, editar, compartilhar e exportar currículos em PDF.

<!-- ![Screenshot do Aplicativo](https://placehold.co/600x400/e2e8f0/475569?text=Sala+Mineira+Screenshot) -->

## 📋 Índice

- [Tecnologias](#tecnologias)
- [Requisitos](#requisitos)
- [Configuração do Firebase](#configuração-do-firebase)
- [Como Executar](#como-executar)
- [Deploy](#deploy)
- [Funcionalidades](#funcionalidades)
- [Estrutura do Projeto](#estrutura-do-projeto)
- [Contribuição](#contribuição)
- [Licença](#licença)

## 🚀 Tecnologias

- HTML5, CSS3, JavaScript
- [Tailwind CSS](https://tailwindcss.com/)
- [Firebase](https://firebase.google.com/)
  - Authentication
  - Firestore Database
  - Hosting
- [jsPDF](https://github.com/parallax/jsPDF) & [html2canvas](https://html2canvas.hertzen.com/) para geração de PDFs
- [Font Awesome](https://fontawesome.com/) para ícones
- [GitHub Actions](https://github.com/features/actions) para CI/CD

## 📋 Requisitos

- Node.js (versão recomendada: 14.x ou superior)
- Conta no Firebase
- Firebase CLI (`npm install -g firebase-tools`)
- Navegador moderno (Chrome, Firefox, Edge, Safari)

## 🔥 Configuração do Firebase

1. Crie um projeto no [Firebase Console](https://console.firebase.google.com/)

2. Ative as seguintes funcionalidades:
   - Authentication (com método de email/senha)
   - Firestore Database
   - Hosting

3. Configure as regras do Firestore para garantir a segurança dos dados:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /resumes/{document=**} {
      allow read, write: if request.auth != null;
    }
    match /habilidades/{document=**} {
      allow read: if true;
      allow write: if request.auth != null;
    }
  }
}
```

4. Crie um usuário de teste no Authentication (Email/Password)

5. Atualize a configuração do Firebase no arquivo `public/index.html` com suas credenciais:

```javascript
const firebaseConfig = {
  apiKey: "SUA_API_KEY",
  authDomain: "SEU_PROJECT_ID.firebaseapp.com",
  projectId: "SEU_PROJECT_ID",
  storageBucket: "SEU_PROJECT_ID.appspot.com",
  messagingSenderId: "SEU_MESSAGING_SENDER_ID",
  appId: "SEU_APP_ID"
};
```

## 🚀 Como Executar

### Executar localmente

1. Clone o repositório:
```bash
git clone https://github.com/seu-usuario/smecv-gemini-v1.git
cd smecv-gemini-v1
```

2. Instale as dependências do Firebase CLI (caso ainda não tenha):
```bash
npm install -g firebase-tools
```

3. Faça login no Firebase:
```bash
firebase login
```

4. Inicie o servidor local:
```bash
firebase serve
```

5. Acesse a aplicação em: http://localhost:5000

### Ambiente de produção

Para ambientes de produção, você deverá utilizar um servidor web ou os serviços do Firebase Hosting.

## 🌐 Deploy

### Deploy com Firebase Hosting

1. Verifique se você está logado no Firebase CLI:
```bash
firebase login
```

2. Faça o deploy para o Firebase Hosting:
```bash
firebase deploy
```

3. Após o deploy, você receberá uma URL para acessar a aplicação (geralmente https://seu-projeto-id.web.app)

### Deploy Automatizado com GitHub Actions

O projeto já está configurado com GitHub Actions para fazer deploy automático quando houver:

- Push para a branch `main`
- Pull Requests para a branch `main` (preview)

Para configurar:

1. Adicione os segredos necessários nas configurações do seu repositório GitHub:
   - `FIREBASE_SERVICE_ACCOUNT_RESUME_APP_V1` (Obtenha este valor do console do Firebase)

2. Certifique-se de que os arquivos `.github/workflows` estão presentes no seu repositório.

## 🎯 Funcionalidades

- **Autenticação**: Sistema de login seguro
- **Cadastro de Currículos**: Formulário completo para inserção de dados
- **Gerenciamento de Habilidades**: Cadastro e associação de habilidades aos candidatos
- **Experiência e Formação**: Campos para histórico profissional e educacional
- **Compartilhamento**: Geração de links para compartilhar com empresas e candidatos
- **Exportação**: Geração de PDFs dos currículos
- **Filtros**: Pesquisa por nome, habilidades, CNH e PCD

## 📁 Estrutura do Projeto

```
smecv-gemini-v1/
├── .firebase/                  # Cache e arquivos de configuração do Firebase
├── .github/                    # Configurações do GitHub Actions
│   └── workflows/              # Workflows para CI/CD
├── public/                     # Arquivos públicos da aplicação
│   └── index.html              # Arquivo principal da aplicação
├── .firebaserc                 # Configuração do projeto Firebase
├── firebase.json               # Configuração do Firebase Hosting
├── .gitignore                  # Arquivos ignorados pelo Git
└── README.md                   # Este arquivo
```

## 👥 Contribuição

1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/nova-funcionalidade`)
3. Faça commit das suas alterações (`git commit -m 'Adiciona nova funcionalidade'`)
4. Faça push para a branch (`git push origin feature/nova-funcionalidade`)
5. Abra um Pull Request

<!-- ## 📄 Licença

Este projeto está licenciado sob a Licença MIT - veja o arquivo [LICENSE](LICENSE) para detalhes. -->

---

Desenvolvido com ❤️ 

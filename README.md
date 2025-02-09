# 🎨 Projeto Base com Design System

Bem-vindo ao nosso projeto base! Este é um template moderno e flexível para criar aplicações incríveis que funcionam tanto na web quanto em dispositivos móveis/nativo. 

## ✨ Destaques

- 🌓 Temas Claro e Escuro
- 📱 Design Responsivo
- 🎯 Componentes Reutilizáveis
- 🖌️ Design System Completo
- 🌐 Funciona na Web e Mobile

## 🚀 Começando

### 📋 Pré-requisitos

Antes de começar, você precisa ter instalado em sua máquina:

- [Git](https://git-scm.com) - Para clonar o projeto e controlar as versões
- [Node.js](https://nodejs.org/) - Recomendamos a versão LTS
- [npm](https://www.npmjs.com/) ou [yarn](https://yarnpkg.com/) - Para gerenciar os pacotes
- [Expo CLI](https://docs.expo.dev/workflow/expo-cli/) - Para rodar o projeto

> 💡 **Dica**: Não tem certeza se já tem algo instalado? Abra seu terminal e tente estes comandos:
> - `git --version`
> - `node --version`
> - `npm --version` ou `yarn --version`

### ⚙️ Configuração Inicial

1. **Clone o repositório**
```bash
git clone [url-do-repositório]
cd [nome-do-projeto]
```

2. **Instale as dependências**
```bash
# Com npm
npm install

# Com yarn
yarn install
```

3. **Instale o Expo CLI globalmente** (se ainda não tiver)
```bash
# Com npm
npm install -g expo-cli

# Com yarn
yarn global add expo-cli
```

## 🔐 Configuração do Supabase

Este projeto usa o Supabase como backend. Aqui está como configurar:

### 📋 Configuração Inicial

1. **Criar arquivo .env**
   - Primeiro, crie um novo arquivo chamado `.env` na raiz do projeto:
   ```bash
   touch .env
   ```
   > 💡 **Dica**: Se estiver no Windows, você pode criar o arquivo manualmente ou usar o comando `type nul > .env`

2. **Arquivo de Ambiente**
   - Copie o conteúdo do `.env.example` para seu novo arquivo `.env`:
   ```bash
   cp .env.example .env
   ```

3. **Configurando suas Credenciais**
   - Acesse [supabase.com](https://supabase.com)
   - Crie uma nova conta ou faça login
   - Crie um novo projeto
   - Vá em `Settings > API`
   - Copie as credenciais:
     - `Project URL` → Cole em `EXPO_PUBLIC_SUPABASE_URL`
     - `anon public` → Cole em `EXPO_PUBLIC_SUPABASE_ANON_KEY`

4. **Estrutura Atual**
   ```
   EXPO_PUBLIC_SUPABASE_URL=https://idnyppqhuctffszcdbwk.supabase.co
   EXPO_PUBLIC_SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
   ```
   > ⚠️ Estas são as chaves de desenvolvimento. Substitua com suas próprias chaves ao criar seu projeto!

### 🔒 Segurança

- O arquivo `.env` está no `.gitignore` e não será commitado para o GitHub
- As chaves "anon" do Supabase são públicas por natureza e podem ser vistas no navegador/console
  > ℹ️ **Importante**: Isso é normal e seguro! Estas chaves têm permissões limitadas e são feitas para serem públicas
- Para dados realmente sensíveis, use variáveis de ambiente sem o prefixo `EXPO_PUBLIC_`
- Nunca compartilhe suas chaves de produção em repositórios públicos
- Use o `.env.example` como template, mas sem credenciais reais

### 🚀 Deploy e Variáveis de Ambiente

#### 💡 Como Funciona?

1. **Em Desenvolvimento**
   ```typescript
   // Seu código já usa as variáveis assim:
   const supabaseUrl = process.env.EXPO_PUBLIC_SUPABASE_URL;
   // Em desenvolvimento, ele pega do seu arquivo .env local
   ```

2. **Em Produção**
   ```typescript
   // O MESMO código:
   const supabaseUrl = process.env.EXPO_PUBLIC_SUPABASE_URL;
   // Em produção, ele pega automaticamente das variáveis da Vercel!
   ```

> 🎯 **Incrível, né?** Você não precisa mudar NADA no seu código! 
> A Vercel cuida de tudo automaticamente.

#### 📦 Preparando para Produção

1. **Ambiente de Desenvolvimento**
   - Durante o desenvolvimento, mantenha o `.env` no `.gitignore`
   - Use o `.env.example` como template para outros desenvolvedores

2. **Deploy na Vercel**
   - NÃO remova o `.env` do `.gitignore`
   - Configure as variáveis de ambiente na Vercel em 4 passos simples:

   **Passo 1**: No Dashboard da Vercel, clique no seu projeto
   
   **Passo 2**: Clique em "Settings" na barra superior
   
   **Passo 3**: No menu lateral, clique em "Environment Variables"
   
   **Passo 4**: Adicione cada variável:
   - Nome: `EXPO_PUBLIC_SUPABASE_URL`
   - Valor: Cole sua URL do Supabase
   - Clique em "Add"
   - Repita para `EXPO_PUBLIC_SUPABASE_ANON_KEY`

   > 💡 **Dica**: Você pode copiar os valores direto do seu arquivo `.env` local!
   
   > 🎯 **Pronto!** A Vercel vai usar essas variáveis automaticamente em produção

3. **Múltiplos Ambientes (Desenvolvimento/Produção)**
   - Para desenvolvimento: use o `.env` local
   - Para produção: use as variáveis de ambiente da Vercel
   - Para staging/preview: configure variáveis específicas na Vercel para cada ambiente

#### ⚠️ Importante: Commits e Segurança

1. **NUNCA remova o `.env` do `.gitignore**
   - Mesmo em produção, mantenha o `.env` no `.gitignore`
   - Use a interface da Vercel para gerenciar variáveis de ambiente
   - Isso mantém suas credenciais seguras e fora do controle de versão

2. **Atualizando Credenciais**
   - Para atualizar credenciais em produção:
     1. Atualize localmente no seu `.env` para testes
     2. Se funcionar, atualize na interface da Vercel
     3. A Vercel fará automaticamente um novo deploy

3. **Commits Seguros**
   ```bash
   # Verifique se .env não está sendo commitado
   git status
   
   # Se aparecer .env na lista:
   git reset .env
   git add .
   git commit -m "sua mensagem"
   ```

> ⚠️ **ATENÇÃO**: 
> - NUNCA commite o arquivo `.env`
> - SEMPRE use a interface da Vercel para gerenciar variáveis de produção
> - Mantenha o `.env.example` atualizado, mas SEM credenciais reais

### 🔄 Mudando a Rota Home

Por padrão, o sistema tem duas rotas principais:

1. **Rota para Usuários Não Logados**:
   - Por padrão: `/(auth)/login`
   - Para mudar, edite o arquivo `app/index.tsx`:
   ```typescript
   export default function Index() {
     return <Redirect href="/(auth)/sua-nova-rota" />;
   }
   ```
   > 💡 **Dica**: Certifique-se de criar o arquivo correspondente em `app/(auth)/sua-nova-rota.tsx`

2. **Rota para Usuários Logados**:
   - Por padrão: `/(tabs)/dash`
   - Para mudar, edite em `contexts/auth.tsx`:
   ```typescript
   router.replace('/(tabs)/sua-nova-rota');
   ```
   > 💡 **Dica**: Certifique-se de criar o arquivo correspondente em `app/(tabs)/sua-nova-rota.tsx`

### 📱 Fluxo de Autenticação

1. **Login**: `/(auth)/login`
2. **Cadastro**: `/(auth)/signup`
3. **Home após login**: `/(tabs)/dash` (configurável)

> 💡 **Dica**: Para testar localmente, você pode usar as chaves de desenvolvimento fornecidas. Para produção, sempre use suas próprias chaves!

## 📱 Rodando o Projeto

Escolha como quer rodar o projeto:

### 🌐 Web
```bash
# Com npm
npm run web

# Com yarn
yarn web
```

### 📱 iOS
```bash
# Com npm
npm run ios

# Com yarn
yarn ios
```

### 🤖 Android
```bash
# Com npm
npm run android

# Com yarn
yarn android
```

## 🎯 Design System

Nosso Design System foi criado para tornar o desenvolvimento mais fácil e consistente. Você pode visualizar todos os elementos acessando a tela "Design System" no projeto.

### 📱 Layout Responsivo

O projeto se adapta automaticamente a três tipos de tela:

- 📱 Mobile (0-767px)
- 📟 Tablet (768-1023px)
- 🖥️ Desktop (1024px+)

> 💡 **Dica**: A barra de navegação (tabs) aparece apenas nas versões Mobile e Tablet, mas todo o conteúdo está disponível em todas as versões!

### 🎨 Elementos do Design System

Na tela de Design System você encontra:

- 🎨 Cores do Sistema
  - Cores Primárias
  - Cores Base (texto e fundo)
  - Cores de Interface (ícones e navegação)
  - Cores de Divisão (claro: #EBEBEB, escuro: #292929)
- 📝 Tipografia
- 📏 Breakpoints
- ⚡ Feedback Visual
- 📐 Sistema de Espaçamento
- 🔲 Sistema de Elevação (Sombras)
- 🧩 Biblioteca de Componentes
- 🎭 Sistema de Ícones (Lucide React)

### 🎯 Barra de Navegação (Tab Bar)

Nossa Tab Bar é adaptativa e oferece uma experiência consistente em todas as plataformas:

#### 🎨 Personalizando a Tab Bar:

1. **Trocando os Ícones**:
   ```typescript
   // Em app/(tabs)/_layout.tsx, importe os ícones que deseja usar:
   import { Home, Search, User, Palette } from 'lucide-react-native';
   
   // Use nas Tab Screens:
   <Tabs.Screen
     name="index"
     options={{
       title: 'Home',
       tabBarIcon: ({ color }) => (
         <Home 
           size={ICONS.sizes.md}
           color={color} 
           strokeWidth={1.5}
         />
       ),
     }}
   />
   ```

   > 💡 **Dica**: Veja todos os ícones disponíveis em [lucide.dev/icons](https://lucide.dev/icons)
   > - Para ícones de home: `Home`, `LayoutDashboard`, `LayoutGrid`
   > - Para explorar: `Compass`, `Search`, `Globe`
   > - Para perfil: `User`, `UserCircle`
   > - Para configurações: `Settings`, `Sliders`

2. **Cores dos Ícones**:
   - Edite em `constants/DesignSystem.ts`:
   ```typescript
   COLORS: {
     light: {
       primary: '#seu-hex', // Cor do item selecionado
       tabIconDefault: '#seu-hex', // Cor dos ícones não selecionados
     }
   }
   ```

3. **Background**:
   - **Web**: Em `app/(tabs)/_layout.tsx`, ajuste:
     ```typescript
     backgroundColor: currentTheme === 'dark' 
       ? 'rgba(0, 0, 0, 0.25)' // Opacidade do tema escuro
       : 'rgba(255, 255, 255, 0.25)' // Opacidade do tema claro
     ```
   - **iOS**: Em `components/ui/TabBarBackground.ios.tsx`, ajuste a `intensity` do blur
   - **Android**: Em `components/ui/TabBarBackground.tsx`, ajuste a opacidade do rgba

4. **Espaçamentos**:
   - Ajuste no StyleSheet em `app/(tabs)/_layout.tsx`:
     ```typescript
     tabBar: { height, paddingBottom },
     webTabBar: { height, paddingTop, paddingBottom },
     tabItem: { paddingTop, gap }
     ```

> 💡 **Dica**: O Lucide React oferece uma grande variedade de ícones modernos e consistentes. Consulte a documentação em [lucide.dev](https://lucide.dev) para ver todos os ícones disponíveis!

### 🛠️ Personalizando

Quer mudar as cores, tamanhos ou estilos? É super fácil!

1. Abra a pasta `constants`
2. Encontre o arquivo `DesignSystem.ts`
3. Modifique os valores conforme sua necessidade

> 🎯 Todas as alterações serão refletidas automaticamente em todo o projeto!

## 📁 Estrutura do Projeto

Nossa estrutura de arquivos foi cuidadosamente organizada para máxima produtividade:

### 📱 App
- `/app` - Contém todas as telas e rotas da aplicação
  - `_layout.tsx` - Layout principal da aplicação
  - `+not-found.tsx` - Página personalizada para rotas não encontradas (404)
  - `/(tabs)` - Páginas que aparecem na navegação por tabs
  - `/modal` - Telas que aparecem como modal

### 🎨 Design e UI
- `/assets` - Recursos estáticos como imagens, fontes e ícones
- `/components` - Componentes reutilizáveis
  - `/ui` - Componentes básicos de interface (botões, inputs, etc)
    - Arquivos com extensões `.ios.tsx`, `.android.tsx` e `.web.tsx` são específicos para cada plataforma
- `/constants` - Configurações do Design System, temas e constantes globais

### 🛠️ Lógica e Utilidades
- `/hooks` - Hooks personalizados do React para lógica reutilizável
- `/scripts` - Scripts de utilidade e automação
- `/types` - Definições de tipos TypeScript

### 📱 Navegação por Tabs
Nossa navegação mantém consistência visual em todas as plataformas (iOS, Android e Web), com adaptações nativas para garantir a melhor experiência em cada ambiente:
- Blur nativo no iOS
- Elevação material no Android
- Backdrop filter na Web

> 💡 **Dica**: A estrutura modular permite adicionar novas funcionalidades sem afetar o código existente!

## 📦 Componentes

### Toast

Sistema de notificações com diferentes tipos de feedback e posições na tela.

```typescript
import { useToast } from '@/hooks/useToast';

function MeuComponente() {
  const { showToast } = useToast();

  // Exemplo de uso
  const mostrarSucesso = () => {
    showToast({
      type: 'success', // 'success' | 'warning' | 'error' | 'info'
      message: 'Operação realizada!',
      description: 'Os dados foram salvos com sucesso.', // Opcional
      position: 'top', // Opcional - Padrão: 'top'
      duration: 5000, // Opcional - Padrão: 5000ms (5 segundos)
    });
  };
}
```

#### Posições disponíveis
- `top` (padrão)
- `bottom`
- `top-left`
- `top-right`
- `bottom-left`
- `bottom-right`

#### Tipos de Toast
- `success`: Para operações bem-sucedidas
- `warning`: Para alertas e avisos
- `error`: Para erros e falhas
- `info`: Para informações gerais

#### Características
- Design consistente com o Design System
- Animações suaves de entrada e saída
- Pausa automática ao passar o mouse (web)
- Pausa ao pressionar (mobile)
- Responsivo e adaptável a diferentes tamanhos de tela
- Ícones específicos para cada tipo de feedback
- Suporte a temas claro e escuro

### Sidebar

Menu lateral responsivo com suporte a navegação.

```typescript
import { Sidebar } from '@/components/Sidebar';

function App() {
  return (
    <Sidebar 
      onNavigate={(route) => {
        // Lógica de navegação
      }} 
    />
  );
}
```

### ThemeSelector

Componente para alternar entre temas claro, escuro e do sistema.

```typescript
import { ThemeSelector } from '@/components/ThemeSelector';

function App() {
  return <ThemeSelector />;
}
```

### 🎯 Componentes Principais

#### 📄 PageContainer
O PageContainer é um componente fundamental que padroniza o layout de todas as telas da aplicação. Ele garante uma experiência consistente, adaptando-se automaticamente à presença ou ausência da sidebar e diferentes breakpoints.

```typescript
import { PageContainer } from '@/components/PageContainer';

// Na sua tela:
export default function MinhaNovaScreen() {
  return (
    <PageContainer>
      {/* Seu conteúdo aqui */}
    </PageContainer>
  );
}
```

Características do PageContainer:
- 📱 Responsivo para mobile, tablet e desktop
- 📏 Largura máxima adaptativa (1200px desktop, 800px outros)
- 🎯 Padding responsivo baseado no breakpoint
- 🎨 Centralização automática do conteúdo
- 🔄 Compatível com sidebar (ajusta-se automaticamente)
- 🎭 Suporte total aos temas claro/escuro

> 💡 **Dica**: Use o PageContainer em todas as novas telas para manter a consistência do layout em toda a aplicação!

#### 🧭 Sidebar
A Sidebar é um componente opcional que pode ser adicionado a qualquer tela. Ela oferece navegação lateral e pode ser expandida ou recolhida:

```typescript
import { Sidebar } from '@/components/Sidebar';

// Na sua tela:
<Sidebar 
  onNavigate={handleNavigation} 
  currentPath="/sua-rota"
  onToggle={handleSidebarToggle}
/>
```

#### 🔝 Header
O Header é um componente opcional que pode ser adicionado a qualquer tela. Ele inclui:
- Título da página
- Barra de pesquisa
- Notificações
- Menu de perfil com seletor de tema

Para usar o Header:
```typescript
import { Header } from '@/components/Header';

// Na sua tela:
<Header 
  sidebarWidth={currentSidebarWidth} 
  onNavigate={handleNavigation}
/>
```

> 💡 **Dica**: Tanto a Sidebar quanto o Header são componentes opcionais. Você pode escolher usar um, ambos ou nenhum em cada tela da sua aplicação!

## 📤 GitHub

### Primeira vez enviando para o GitHub?

1. Crie um novo repositório no GitHub
2. Configure o repositório local e envie seu código:
```bash
git remote add origin [URL_DO_SEU_REPOSITÓRIO]
git branch -M main
git push -u origin main
```

### Enviando atualizações

Depois da configuração inicial, você pode enviar novas alterações com apenas três comandos:

```bash
git add .
git commit -m "Sua mensagem explicando o que mudou"
git push
```

> 💡 **Dica**: Use mensagens claras nos commits para manter um histórico organizado!

---

Feito com ❤️ pela [Aicrus Tech](https://www.aicrustech.com/) para tornar o desenvolvimento mais fácil e divertido!

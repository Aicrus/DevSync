# 🎨 Projeto Base com Design System

Bem-vindo ao nosso projeto base! Este é um template moderno e flexível para criar aplicações incríveis que funcionam tanto na web quanto em dispositivos móveis/nativo. 

## ✨ Destaques

- 🌓 Temas Claro e Escuro
- 📱 Design Responsivo
- 🎯 Componentes Reutilizáveis
- 🖌️ Design System Completo
- 🌐 Funciona na Web e Mobile

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

## 🎯 Estrutura do Projeto

```
projeto-base/
├── app/                    # Páginas e navegação
├── components/             # Componentes reutilizáveis
├── constants/             
│   └── DesignSystem.ts    # Configurações do Design System
├── hooks/                 
│   ├── ThemeContext.tsx   # Contexto de tema
│   └── useToast.tsx       # Hook do sistema de Toast
└── assets/                # Recursos estáticos
```

## 🚀 Começando

1. Clone o repositório
2. Instale as dependências:
```bash
npm install
```

3. Inicie o projeto:
```bash
npm start
```

## 📱 Plataformas Suportadas

- iOS
- Android
- Web

## 🛠️ Tecnologias

- React Native
- Expo
- TypeScript
- React Navigation
- Reanimated

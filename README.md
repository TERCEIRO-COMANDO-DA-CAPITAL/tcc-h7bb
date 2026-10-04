Vou estruturar como uma documentação de Git simples, focada em o que cada elemento faz + sintaxe + exemplo, sem transformar a página em um cadáver de 900 linhas. Afinal, é uma library de UI, não a Constituição.

# TechAnatomy — Avilon Library

Documentação rápida da estrutura da Avilon Library para Roblox.

## Inicialização

```lua
local Library = loadstring(game:HttpGet(
    "https://raw.githubusercontent.com/NIcoGabrielRealYtr/Avilon-Library/refs/heads/main/Source"
))()

Carrega a biblioteca diretamente do GitHub.


---

Window

Cria a janela principal.

local Window = Library:Window({
    Name = "Title",
    SubName = "SubTitle",
    Logo = "rbxassetid://114856413138528"
})

Propriedades

Propriedade	Tipo	Descrição

Name	string	Nome principal da janela
SubName	string	Texto secundário
Logo	string	Asset ID da logo



---

Page

Cria uma página dentro da Window.

local MainPage = Window:Page({
    Name = "Page",
    Icon = "rbxassetid://102973834692853"
})

Propriedades

Propriedade	Tipo	Descrição

Name	string	Nome da página
Icon	string	Asset ID do ícone



---

SubPage

Cria uma subpágina dentro de uma Page.

local SettingsSubPage = MainPage:SubPage({
    Name = "SubPage",
    Description = "All settings in one place",
    Icon = "rbxassetid://102973834692853"
})

Propriedades

Propriedade	Tipo	Descrição

Name	string	Nome da subpágina
Description	string	Descrição
Icon	string	Asset ID do ícone



---

Section

Cria uma seção dentro da SubPage.

local LeftSection = SettingsSubPage:Section({
    Name = "Title",
    Description = "Description",
    Side = 1
})

Side

Side = 1

Seção esquerda.

Side = 2

Seção direita.


---

Toggle

Cria um botão de ativar/desativar.

local Toggle = LeftSection:Toggle({
    Name = "Toggle",
    Flag = "AimbotEnabled",
    Default = false
})

Propriedades

Propriedade	Tipo	Descrição

Name	string	Nome exibido
Flag	string	Identificador da configuração
Default	boolean	Estado inicial



---

Label

Cria um texto.

local Label = LeftSection:Label({
    Name = "Label Title"
})


---

Keybind

Adiciona uma tecla a um Label.

Label:Keybind({
    Name = "Title",
    Flag = "AimbotKey",
    Default = Enum.KeyCode.RightAlt,
    Mode = "Hold",

    Callback = function(state)
        print("Key state:", state)
    end
})

Mode

Mode = "Toggle"

Ativa/desativa ao pressionar.

Mode = "Hold"

Ativo enquanto a tecla estiver pressionada.

Mode = "Always"

Sempre ativo.

Callback

Recebe o estado atual:

Callback = function(state)
    print(state)
end


---

Slider

Cria um controle numérico deslizante.

LeftSection:Slider({
    Name = "ESP Transparency",
    Flag = "ESPTransparency",
    Default = 0.5,
    Min = 0,
    Max = 1,
    Decimals = 0.01,
    Suffix = "",

    Callback = function(Value)
        print(Value)
    end
})

Propriedades

Propriedade	Tipo	Descrição

Name	string	Nome
Flag	string	Identificador
Default	number	Valor inicial
Min	number	Valor mínimo
Max	number	Valor máximo
Decimals	number	Precisão decimal
Suffix	string	Texto depois do valor
Callback	function	Executado quando o valor muda



---

Dropdown

Cria uma lista de opções.

LeftSection:Dropdown({
    Name = "Target Priority",
    Flag = "TargetPriority",
    Default = "Closest",

    Items = {
        "Closest",
        "Lowest HP",
        "Highest HP",
        "Random"
    }
})

Propriedades

Propriedade	Tipo	Descrição

Name	string	Nome
Flag	string	Identificador
Default	string	Opção inicial
Items	table	Lista de opções



---

Textbox

Cria uma caixa de texto.

LeftSection:Textbox({
    Name = "Username",
    Flag = "BoxName",
    Default = "Player",
    Placeholder = "Enter name...",
    Finished = true
})

Propriedades

Propriedade	Tipo	Descrição

Name	string	Nome
Flag	string	Identificador
Default	string	Texto inicial
Placeholder	string	Texto de exemplo
Finished	boolean	Define comportamento de finalização



---

Colorpicker

Cria um seletor de cor.

RightSection:Colorpicker({
    Name = "ESP Color",
    Flag = "ESPColor",
    Default = Color3.fromRGB(255, 0, 0),
    Alpha = 1
})

Propriedades

Propriedade	Tipo	Descrição

Name	string	Nome
Flag	string	Identificador
Default	Color3	Cor inicial
Alpha	number	Transparência


Exemplo:

Color3.fromRGB(255, 0, 0)

Representa vermelho.


---

Button

Cria um botão executável.

RightSection:Button({
    Name = "Teleport to Mouse",

    Callback = function()
        print("Button clicked")
    end
})

Propriedades

Propriedade	Tipo	Descrição

Name	string	Texto do botão
Callback	function	Código executado ao clicar



---

Alterando Label

Labels podem ser atualizados usando SetText.

StatusLabel:SetText("Status: Ready")

Exemplo:

Callback = function(Value)
    StatusLabel:SetText(
        "Status: Transparency " .. tostring(Value)
    )
end


---

Estrutura

A hierarquia básica da biblioteca é:

Library
└── Window
    └── Page
        └── SubPage
            ├── Section 1
            │   ├── Toggle
            │   ├── Label
            │   │   └── Keybind
            │   ├── Slider
            │   ├── Dropdown
            │   └── Textbox
            │
            └── Section 2
                ├── Colorpicker
                ├── Button
                └── Label


---

Exemplo completo

local Library = loadstring(game:HttpGet(
    "https://raw.githubusercontent.com/NIcoGabrielRealYtr/Avilon-Library/refs/heads/main/Source"
))()

local Window = Library:Window({
    Name = "Title",
    SubName = "SubTitle",
    Logo = "rbxassetid://114856413138528"
})

local MainPage = Window:Page({
    Name = "Page",
    Icon = "rbxassetid://102973834692853"
})

local SettingsSubPage = MainPage:SubPage({
    Name = "Settings",
    Description = "All settings in one place",
    Icon = "rbxassetid://102973834692853"
})

local LeftSection = SettingsSubPage:Section({
    Name = "General",
    Description = "General settings",
    Side = 1
})

local RightSection = SettingsSubPage:Section({
    Name = "Visual",
    Description = "Visual settings",
    Side = 2
})

local StatusLabel = RightSection:Label({
    Name = "Status: Ready"
})

LeftSection:Toggle({
    Name = "Enabled",
    Flag = "Enabled",
    Default = false
})

LeftSection:Slider({
    Name = "Transparency",
    Flag = "Transparency",
    Default = 0.5,
    Min = 0,
    Max = 1,
    Decimals = 0.01,
    Suffix = "",

    Callback = function(Value)
        StatusLabel:SetText(
            "Status: " .. tostring(Value)
        )
    end
})

LeftSection:Dropdown({
    Name = "Priority",
    Flag = "Priority",
    Default = "Closest",

    Items = {
        "Closest",
        "Lowest HP",
        "Highest HP",
        "Random"
    }
})

LeftSection:Textbox({
    Name = "Username",
    Flag = "Username",
    Default = "Player",
    Placeholder = "Enter name...",
    Finished = true
})

RightSection:Colorpicker({
    Name = "Color",
    Flag = "Color",
    Default = Color3.fromRGB(255, 0, 0),
    Alpha = 1
})

RightSection:Button({
    Name = "Execute",

    Callback = function()
        print("Executed")
    end
})


---

API Map

Library
│
└── Window()
    │
    └── Page()
        │
        └── SubPage()
            │
            └── Section()
                │
                ├── Toggle()
                ├── Label()
                │   └── Keybind()
                ├── Slider()
                ├── Dropdown()
                ├── Textbox()
                ├── Colorpicker()
                └── Button()

Resumo

Window      → Janela principal
Page        → Página
SubPage     → Subpágina
Section     → Seção
Toggle      → On / Off
Label       → Texto
Keybind     → Tecla
Slider      → Valor numérico
Dropdown    → Lista de opções
Textbox     → Entrada de texto
Colorpicker → Seleção de cor
Button      → Ação

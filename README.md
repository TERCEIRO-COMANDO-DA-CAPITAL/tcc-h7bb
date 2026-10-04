# T.C.C Lib

UI Library para Roblox.

## Loadstring

```lua
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/NIcoGabrielRealYtr/Avilon-Library/refs/heads/main/Source"))()
```

## Estrutura

```text
Library
└── Window
    └── Page
        └── SubPage
            └── Section
                ├── Toggle
                ├── Label
                │   └── Keybind
                ├── Slider
                ├── Dropdown
                ├── Textbox
                ├── Colorpicker
                └── Button
```

## Window

Cria a janela principal.

```lua
local Window = Library:Window({
    Name = "Title",
    SubName = "SubTitle",
    Logo = "rbxassetid://114856413138528"
})
```

## Page

```lua
local MainPage = Window:Page({
    Name = "Page",
    Icon = "rbxassetid://102973834692853"
})
```

## SubPage

```lua
local SubPage = MainPage:SubPage({
    Name = "SubPage",
    Description = "All settings in one place",
    Icon = "rbxassetid://102973834692853"
})
```

## Section

```lua
local Section = SubPage:Section({
    Name = "Title",
    Description = "Description",
    Side = 1
})
```

`Side = 1` = esquerda  
`Side = 2` = direita

## Toggle

```lua
Section:Toggle({
    Name = "Toggle",
    Flag = "ToggleEnabled",
    Default = false
})
```

## Label

```lua
local Label = Section:Label({
    Name = "Status: Ready"
})
```

### SetText

```lua
Label:SetText("Status: Enabled")
```

## Keybind

```lua
Label:Keybind({
    Name = "Toggle Key",
    Flag = "ToggleKey",
    Default = Enum.KeyCode.RightAlt,
    Mode = "Hold",
    Callback = function(state)
        print("Key state:", state)
    end
})
```

Modes disponíveis:

```text
Toggle
Hold
Always
```

## Slider

```lua
Section:Slider({
    Name = "Transparency",
    Flag = "Transparency",
    Default = 0.5,
    Min = 0,
    Max = 1,
    Decimals = 0.01,
    Suffix = "",
    Callback = function(Value)
        print(Value)
    end
})
```

## Dropdown

```lua
Section:Dropdown({
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
```

## Textbox

```lua
Section:Textbox({
    Name = "Username",
    Flag = "BoxName",
    Default = "Player",
    Placeholder = "Enter name...",
    Finished = true
})
```

## Colorpicker

```lua
Section:Colorpicker({
    Name = "ESP Color",
    Flag = "ESPColor",
    Default = Color3.fromRGB(255, 0, 0),
    Alpha = 1
})
```

## Button

```lua
Section:Button({
    Name = "Test",
    Callback = function()
        print("Button clicked")
    end
})
```

## API

```text
Library:Window()
Window:Page()
Page:SubPage()
SubPage:Section()

Section:Toggle()
Section:Label()
Section:Slider()
Section:Dropdown()
Section:Textbox()
Section:Colorpicker()
Section:Button()

Label:Keybind()
Label:SetText()
```

## Exemplo completo

```lua
local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/NIcoGabrielRealYtr/Avilon-Library/refs/heads/main/Source"))()

local Window = Library:Window({
    Name = "Avilon",
    SubName = "Example",
    Logo = "rbxassetid://114856413138528"
})

local MainPage = Window:Page({
    Name = "Main",
    Icon = "rbxassetid://102973834692853"
})

local SubPage = MainPage:SubPage({
    Name = "Settings",
    Description = "Library example",
    Icon = "rbxassetid://102973834692853"
})

local Section = SubPage:Section({
    Name = "Settings",
    Description = "Example controls",
    Side = 1
})

Section:Toggle({
    Name = "Enabled",
    Flag = "Enabled",
    Default = false
})

local Label = Section:Label({
    Name = "Status: Ready"
})

Label:Keybind({
    Name = "Toggle Key",
    Flag = "ToggleKey",
    Default = Enum.KeyCode.RightAlt,
    Mode = "Hold",
    Callback = function(state)
        print("Key state:", state)
    end
})

Section:Slider({
    Name = "Transparency",
    Flag = "Transparency",
    Default = 0.5,
    Min = 0,
    Max = 1,
    Decimals = 0.01,
    Suffix = "",
    Callback = function(Value)
        Label:SetText("Transparency: " .. tostring(Value))
    end
})

Section:Dropdown({
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

Section:Textbox({
    Name = "Username",
    Flag = "Username",
    Default = "Player",
    Placeholder = "Enter name...",
    Finished = true
})

Section:Colorpicker({
    Name = "Color",
    Flag = "Color",
    Default = Color3.fromRGB(255, 0, 0),
    Alpha = 1
})

Section:Button({
    Name = "Test",
    Callback = function()
        print("Avilon button clicked")
    end
})
```

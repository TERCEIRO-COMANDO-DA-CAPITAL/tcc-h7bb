# Avilon Library — TechAnatomy

UI Library para Roblox.

## Loadstring

local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/NIcoGabrielRealYtr/Avilon-Library/refs/heads/main/Source"))()

## Estrutura

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

## Window

local Window = Library:Window({
    Name = "Title",
    SubName = "Subtitle",
    Logo = "rbxassetid://ID"
})

## Page

local Page = Window:Page({
    Name = "Page",
    Icon = "rbxassetid://ID"
})

## SubPage

local SubPage = Page:SubPage({
    Name = "Settings",
    Description = "Description",
    Icon = "rbxassetid://ID"
})

## Section

local Section = SubPage:Section({
    Name = "Main",
    Description = "Description",
    Side = 1
})

Side = 1 -- Esquerda
Side = 2 -- Direita

## Toggle

Section:Toggle({
    Name = "Enabled",
    Flag = "Enabled",
    Default = false
})

## Label

local Label = Section:Label({
    Name = "Status"
})

Label:SetText("Running")

## Keybind

Label:Keybind({
    Name = "Key",
    Flag = "Key",
    Default = Enum.KeyCode.RightAlt,
    Mode = "Hold",

    Callback = function(State)
        print(State)
    end
})

Modes:
Toggle = Alternar
Hold = Segurar
Always = Sempre ativo

## Slider

Section:Slider({
    Name = "Speed",
    Flag = "Speed",
    Default = 16,
    Min = 1,
    Max = 100,
    Decimals = 1,
    Suffix = "",

    Callback = function(Value)
        print(Value)
    end
})

## Dropdown

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

## Textbox

Section:Textbox({
    Name = "Username",
    Flag = "Username",
    Default = "",
    Placeholder = "Enter name...",
    Finished = true
})

## Colorpicker

Section:Colorpicker({
    Name = "Color",
    Flag = "Color",
    Default = Color3.fromRGB(255, 0, 0),
    Alpha = 1
})

## Button

Section:Button({
    Name = "Execute",

    Callback = function()
        print("Executed")
    end
})

## API

Window()
Page()
SubPage()
Section()

Toggle()
Label()
Keybind()
Slider()
Dropdown()
Textbox()
Colorpicker()
Button()

Label:SetText()

## Exemplo completo

local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/NIcoGabrielRealYtr/Avilon-Library/refs/heads/main/Source"))()

local Window = Library:Window({
    Name = "Avilon",
    SubName = "Example",
    Logo = "rbxassetid://ID"
})

local Page = Window:Page({
    Name = "Main",
    Icon = "rbxassetid://ID"
})

local SubPage = Page:SubPage({
    Name = "Settings",
    Description = "Settings",
    Icon = "rbxassetid://ID"
})

local Section = SubPage:Section({
    Name = "Main",
    Description = "Settings",
    Side = 1
})

Section:Toggle({
    Name = "Enabled",
    Flag = "Enabled",
    Default = false
})

Section:Slider({
    Name = "Speed",
    Flag = "Speed",
    Default = 16,
    Min = 1,
    Max = 100
})

Section:Dropdown({
    Name = "Priority",
    Flag = "Priority",
    Default = "Closest",
    Items = {
        "Closest",
        "Lowest HP"
    }
})

Section:Button({
    Name = "Execute",
    Callback = function()
        print("Executed")
    end
})

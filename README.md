Avilon Library

UI Library para Roblox.

Loadstring

local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/NIcoGabrielRealYtr/Avilon-Library/refs/heads/main/Source"))()

Estrutura

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

Window

Cria a janela principal.

local Window = Library:Window({
    Name = "Title",
    SubName = "SubTitle",
    Logo = "rbxassetid://114856413138528"
})

Page

Cria uma página dentro da Window.

local MainPage = Window:Page({
    Name = "Page",
    Icon = "rbxassetid://102973834692853"
})

SubPage

Cria uma subpágina dentro da Page.

local SettingsSubPage = MainPage:SubPage({
    Name = "SubPage",
    Description = "All settings in one place",
    Icon = "rbxassetid://102973834692853"
})

Section

Cria uma seção dentro da SubPage.

Side = 1 para esquerda e Side = 2 para direita.

local Section = SettingsSubPage:Section({
    Name = "Title",
    Description = "Description",
    Side = 1
})

Toggle

Section:Toggle({
    Name = "Toggle",
    Flag = "AimbotEnabled",
    Default = false
})

Label

local Label = Section:Label({
    Name = "Status: Ready"
})

Para alterar o texto:

Label:SetText("Status: Running")

Keybind

Label:Keybind({
    Name = "Title",
    Flag = "AimbotKey",
    Default = Enum.KeyCode.RightAlt,
    Mode = "Hold",

    Callback = function(State)
        print("Key state:", State)
    end
})

Modos disponíveis:

Toggle

Hold

Always


Slider

Section:Slider({
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

Dropdown

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

Textbox

Section:Textbox({
    Name = "Username",
    Flag = "BoxName",
    Default = "Player",
    Placeholder = "Enter name...",
    Finished = true
})

Colorpicker

Section:Colorpicker({
    Name = "ESP Color",
    Flag = "ESPColor",
    Default = Color3.fromRGB(255, 0, 0),
    Alpha = 1
})

Button

Section:Button({
    Name = "Execute",

    Callback = function()
        print("Executed")
    end
})

API

Element	Método

Window	Library:Window()
Page	Window:Page()
SubPage	Page:SubPage()
Section	SubPage:Section()
Toggle	Section:Toggle()
Label	Section:Label()
Keybind	Label:Keybind()
Slider	Section:Slider()
Dropdown	Section:Dropdown()
Textbox	Section:Textbox()
Colorpicker	Section:Colorpicker()
Button	Section:Button()
SetText	Label:SetText()


Example

local Library = loadstring(game:HttpGet("https://raw.githubusercontent.com/NIcoGabrielRealYtr/Avilon-Library/refs/heads/main/Source"))()

local Window = Library:Window({
    Name = "Avilon",
    SubName = "Example",
    Logo = "rbxassetid://114856413138528"
})

local Page = Window:Page({
    Name = "Main",
    Icon = "rbxassetid://102973834692853"
})

local SubPage = Page:SubPage({
    Name = "Settings",
    Description = "Settings",
    Icon = "rbxassetid://102973834692853"
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

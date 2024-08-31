-- Carregar a biblioteca de interface de usuário
local library = loadstring(game:HttpGet("https://raw.githubusercontent.com/AikaV3rm/UiLib/master/Lib.lua"))()

-- Criar uma janela principal
local window = library:CreateWindow("Arsenal Script")

-- Criar uma aba principal
local mainTab = window:CreateFolder("Main")

-- Adicionar um botão para ativar o aimbot
mainTab:Button("Ativar Aimbot", function()
    loadstring(game:HttpGet("https://raw.githubusercontent.com/NougatBitz/ArsenalHaxx/master/Script"))()
    print("Aimbot ativado!")
end)

-- Adicionar um botão para ativar o chat spammer
mainTab:Button("Ativar Chat Spammer", function()
    loadstring(game:HttpGet("https://pastebin.com/raw/Ksw4PV2E"))()
    print("Chat Spammer ativado!")
end)

-- Adicionar um rótulo
mainTab:Label("Script simples para Arsenal", {
    TextSize = 15,
    TextColor = Color3.fromRGB(255, 255, 255),
    BgColor = Color3.fromRGB

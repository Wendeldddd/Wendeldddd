-- Verificando se a condição do PlaceId é satisfeita
if game.PlaceId == 15744137588 then

    -- Carregando a biblioteca OrionLib
    local OrionLib = loadstring(game:HttpGet('https://raw.githubusercontent.com/shlexware/Orion/main/source'))()
    if not OrionLib then
        error("Falha ao carregar a biblioteca OrionLib")
        return
    end

    -- Criando a janela principal
    local Window = OrionLib:MakeWindow({
        Name = "Wendel HUB",
        HidePremium = false,
        SaveConfig = true,
        ConfigFolder = "WendelCfg",
        IntroEnabled = false
    })

    -- Tabela para armazenar as variáveis globais
    local G = {}
    G.AutoAtk = false  -- Iniciando desativado
    G.AutoEggs = false  -- Iniciando desativado
    G.AutoRaid1 = false  -- Iniciando desativado
    G.AutoRaid2 = false  -- Iniciando desativado
    G.AutoRaid3 = false  -- Iniciando desativado
    G.AutoRaidAlmas = false  -- Iniciando desativado
    G.AutoMasmorra = false -- Iniciando desativado
    G.AutoRebirth = false
  
    -- Função para o auto-ataque
    local function AutoAtk()
        while G.AutoAtk do
            -- Chamar o evento de auto-ataque
            game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("PlayerClickAttack"):FireServer()
            local args = {
                [1] = {
                    ["harmIndex"] = 1,
                    ["skillId"] = 200254
                }
            }

            game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("RespirationSkillHarm"):FireServer(unpack(args))
            -- Adicione mais chamadas de habilidades aqui, se necessário

            game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 75
            wait(0.1)
        end
    end

    -- Função para comprar ovos automaticamente
    local function AutoEggs()
        while G.AutoEggs do
            -- Aqui você coloca o código para comprar ovos automaticamente
            wait(0.1)
        end
    end

    -- Função para iniciar ou parar o auto-raid 1
    local function AutoRaid1()
        local positions = {
            Vector3.new(-3, 206, -126),
            Vector3.new(-84, 204, -126),
            Vector3.new(73, 204, -128),
            Vector3.new(-2, 207, -10),
            Vector3.new(-90, 206, -0),
            Vector3.new(107, 206, 7),
            Vector3.new(64, 206, 104),
            Vector3.new(85, 205, 196),
            Vector3.new(34, 205, 166),
            Vector3.new(-46, 205, 176),
            Vector3.new(-99, 205, 201),
            Vector3.new(-73, 206, 100),
            Vector3.new(-2, 205, 175)
        }
        local index = 1
        while G.AutoRaid1 do
            -- Entrar na sala da raid
            local args = {
                [1] = "Room4"
            }
            game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("EnterRaidRoom"):FireServer(unpack(args))
            
            local args = {
                [1] = {
                    ["difficulty"] = 4,
                    ["roomName"] = "Room4",
                    ["selectMapId"] = 50103
                }
            }
            game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("SelectRaidsDifficulty"):FireServer(unpack(args))
            
            local args = {
                [1] = {
                    ["userIds"] = {
                        [1] = 3180945687
                    },
                    ["roomName"] = "Room4"
                }
            }
            game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("StartChallengeRaidMap"):InvokeServer(unpack(args))
            
            -- Função para teleportar para uma posição específica após 5 segundos
            local function TeleportToPosition(position)
                wait(2)  -- Aguarda 5 segundos antes de teleportar
                game.Players.LocalPlayer.Character:MoveTo(position)  -- Teleporta para a posição especificada
            end
            
            -- Teleportar para a posição específica após 5 segundos
            TeleportToPosition(positions[index])
            index = index % #positions + 1  -- Avança para a próxima posição
            wait(1)  -- Aguarda 2 segundos antes de teleportar novamente
        end
    end
  
    -- Função para iniciar ou parar o auto-raid 2
    local function AutoRaid2()
        while G.AutoRaid2 do
            local args = {[1] = "Room4"}
            game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("EnterRaidRoom"):FireServer(unpack(args))
            
            -- Iniciar o desafio de um mapa de raid
            local args = {
                [1] = {
                    ["userIds"] = {[1] = 3180945687},
                    ["roomName"] = "Room4"
                }
            }
            game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("StartChallengeRaidMap"):InvokeServer(unpack(args))
            
            -- Selecionar a dificuldade da raid
            local args = {
                [1] = {
                    ["difficulty"] = 4,
                    ["roomName"] = "Room4",
                    ["selectMapId"] = 50104
                }
            }
            game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("SelectRaidsDifficulty"):FireServer(unpack(args))
            
            -- Teleportar para a raid
            game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("LocalPlayerTeleportSuccess"):InvokeServer()
            wait(0.1)
        end
    end
  
    -- Função para iniciar ou parar o auto-raid 3
    local function AutoRaid3()
        while G.AutoRaid3 do
            local args = {[1] = "Room4"}
            game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("EnterRaidRoom"):FireServer(unpack(args))
            
            -- Iniciar o desafio de um mapa de raid
            local args = {
                [1] = {
                  ["userIds"] = {[1] = 3180945687},
                    ["roomName"] = "Room4"
                }
            }
            game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("StartChallengeRaidMap"):InvokeServer(unpack(args))
            
            -- Selecionar a dificuldade da raid
            local args = {
                [1] = {
                    ["difficulty"] = 4,
                    ["roomName"] = "Room4",
                    ["selectMapId"] = 50105
                }
            }
            game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("SelectRaidsDifficulty"):FireServer(unpack(args))
            
            -- Teleportar para a raid
            game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("LocalPlayerTeleportSuccess"):InvokeServer()
            wait(0.1)
        end
    end
  
    -- Função para iniciar ou parar o auto-raid de Almas
    local function AutoRaidAlmas()
        local positions = {
            Vector3.new(72, 197, -205),
            Vector3.new(82, 197, -232),
            Vector3.new(-32, 197, -176),
            Vector3.new(-84, 197, -225),
            Vector3.new(-161, 197, -202),
            Vector3.new(-169, 202, -4),
            Vector3.new(-199, 202, 12),
            Vector3.new(-115, 202, -92),
            Vector3.new(39, 202, -111),
            Vector3.new(82, 202, -114),
            Vector3.new(-0, 202, -14),
            Vector3.new(98, 202, 135),
            Vector3.new(161, 202, 125),
            Vector3.new(-120, 202, 126),
            Vector3.new(-170, 202, 119),
            Vector3.new(-1, 202, 120)
        }
        local index = 1
        while G.AutoRaidAlmas do
            local args = {[1] = "Room4"}
            game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("EnterRaidRoom"):FireServer(unpack(args))
            
            -- Iniciar o desafio de um mapa de raid
            local args = {
                [1] = {
                    ["userIds"] = {[1] = 3180945687},
                    ["roomName"] = "Room4"
                }
            }
            game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("StartChallengeRaidMap"):InvokeServer(unpack(args))
            
            -- Selecionar a dificuldade da raid
            local args = {
                [1] = {
                    ["difficulty"] = 4,
                    ["roomName"] = "Room4",
                    ["selectMapId"] = 50102
                }
            }
            game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("SelectRaidsDifficulty"):FireServer(unpack(args))
            
            -- Teleportar para a raid
            game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("LocalPlayerTeleportSuccess"):InvokeServer()
            
            -- Teleportar para a posição específica após 5 segundos
            local function TeleportToPosition(position)
                wait(2)  -- Aguarda 5 segundos antes de teleportar
                game.Players.LocalPlayer.Character:MoveTo(position)  -- Teleporta para a posição especificada
            end
            
            -- Teleportar para a posição específica
            TeleportToPosition(positions[index])
            index = (index % #positions) + 1  -- Avança para a próxima posição
            wait(1)  -- Aguarda 1 segundo antes de teleportar novamente
        end
    end

-- Função para iniciar ou parar o auto-masmorra
    local function AutoMasmorra()
        while G.AutoMasmorra do
            -- Obter o tempo atual
            local currentTime = os.time()
            
            -- Calcular o tempo para a próxima masmorra (15 segundos antes de cada 30 minutos)
            local nextMasmorraTime = math.floor(currentTime / (30 * 60)) * (30 * 60) + 30 * 60 - 15
            
            -- Calcular o tempo de espera até a próxima masmorra
            local waitTime = nextMasmorraTime - currentTime
            
            -- Aguardar até o tempo da próxima masmorra
            wait(waitTime)
            
            -- Executar a ação da masmorra
            -- Coloque aqui o código para entrar na masmorra e realizar as ações necessárias
            print("Próxima masmorra em breve!")
        end
    end
    -- Função para iniciar ou parar o auto-rebirth
    local function AutoRebirth()
        while G.AutoRebirth do
            game:GetService("ReplicatedStorage"):WaitForChild("Remotes"):WaitForChild("PlayerReborn"):FireServer()
            wait(0.1)
        end
    end
  -- Criando a aba Jogador
    local JogadorTab = Window:MakeTab({
        Name = "Jogador",
        Icon = "rbxassetid://4483345998",
        PremiumOnly = false
    })

    -- Adicionando uma seção para Auto-Farm na aba Jogador
    JogadorTab:AddSection({Name = "Auto-Farm"})

    -- Adicionando um toggle para iniciar ou parar o auto-ataque
    JogadorTab:AddToggle({
        Name = "Auto-Ataque",
        Default = false,
        Callback = function(Value)
            G.AutoAtk = Value
            if Value then
                AutoAtk()
            end
        end
    })

    -- Adicionando um toggle para iniciar ou parar a compra automática de ovos
    JogadorTab:AddToggle({
        Name = "Auto-Ovo",
        Default = false,
        Callback = function(Value)
            G.AutoEggs = Value
            if Value then
                AutoEggs()
            end
        end
    })

    -- Criando a aba Auto-Raid
    local AutoRaidTab = Window:MakeTab({
        Name = "Auto-Raid",
        Icon = "rbxassetid://4483345998",
        PremiumOnly = false
    })

    -- Adicionando uma seção para Auto-Raid na aba Auto-Raid
    AutoRaidTab:AddSection({Name = "Auto-Raid"})

    -- Adicionando um toggle para iniciar ou parar o auto-raid 1
    AutoRaidTab:AddToggle({
        Name = "Auto-Raid1",
        Default = false,
        Callback = function(Value)
            G.AutoRaid1 = Value
            if Value then
                AutoRaid1()
            end
        end
    })
  
   -- Adicionando um toggle para iniciar ou parar o auto-raid 2
    AutoRaidTab:AddToggle({
        Name = "Auto-Raid2",
        Default = false,
        Callback = function(Value)
            G.AutoRaid2 = Value
            if Value then
                AutoRaid2()
            end
        end
    })
  
  -- Adicionando um toggle para iniciar ou parar o auto-raid 3
    AutoRaidTab:AddToggle({
        Name = "Auto-Raid3",
        Default = false,
        Callback = function(Value)
            G.AutoRaid3 = Value
            if Value then
                AutoRaid3()
            end
        end
    })
    
  -- Adicionando um toggle para iniciar ou parar o auto-raid de Almas
    AutoRaidTab:AddToggle({
        Name = "Auto-RaidAlmas",
        Default = false,
        Callback = function(Value)
            G.AutoRaidAlmas = Value
            if Value then
                AutoRaidAlmas()
            end
        end
    })

    -- Adicionando uma seção para Auto-Masmorra na aba Auto-Raid
    AutoRaidTab:AddSection({Name = "Auto-Masmorra"})

    -- Adicionando um toggle para iniciar ou parar o auto-masmorra
    AutoRaidTab:AddToggle({
        Name = "Auto-Masmorra",
        Default = false,
        Callback = function(Value)
            G.AutoMasmorra = Value
            if Value then
                AutoMasmorra()
            end
        end
    })

    -- Adicionando uma seção para Auto-Rebirth na aba Auto-Raid
    AutoRaidTab:AddSection({Name = "Auto-Rebirth"})

    -- Adicionando um toggle para iniciar ou parar o auto-rebirth
    AutoRaidTab:AddToggle({
        Name = "Auto-Rebirth",
        Default = false,
        Callback = function(Value)
            G.AutoRebirth = Value
            if Value then
                AutoRebirth()
            end
        end
    })

end

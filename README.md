
     --[--------- Contains ---------]
    -- 眼位陷阱计时      Anti Ward v3.16 
	-- 自动解控         I Hate CC v2.0
    -- 敌方预警         Low Awareness : Created by Ryan, Ported by Manciuszz
    -- 塔范围显示       Enemy Tower Range : Created by SurfaceS
    -- 角色攻击范围     Champion Ranges : Created by heist, ported by Mistal 
    -- 完美插眼         Perfect Ward 1.7.3 : Created by Husky  
	-- 小地图计时       Minimap Timers v0.2c(),	
	-- 敌人消失红圈     Where Is He??? v1.2, 
	-- 敌人逃跑预测     Where did he go? v0.4,
	-- 本尊预测        Clone Revealer v1.1,  
	-- 自动惩戒        AutoSmite v3.1
	-- 无敌计时        Waiteee v0.2, 	
	-- 自动护盾        AutoShield,  
	-- 隐藏物件        Hidden Objects 3.14
	-- 自动 吃药/中亚/巫师帽     Auto Potion/Zhonyas/Wooglets	
	-- 自动点燃        Auto Ignite v1.2
	-- 闪现助手        Flash Assistant
	-- 补刀标记        Minion Bars v1.1
	-- 选择攻击英雄优化     Simple TS Priority Arranger
	-- 自动防止暂离    Surrender
	-- 自动升级加点    AutoLevel, 
	-- 平滑流畅移动    SafeMovement - by TheSource
	-- 显HP血量        ShowHP
	-- 显技能显CD      ProTrackerv2  v1.30
    -- 技能预判        ImAimingVPrediction   v0.15
    -- 屏蔽绿字       DISABLE BOL GREEN PRINT CHAT
  	-- ################################### DISABLE BOL GREEN PRINT CHAT ##################################
	function DisableGreenOnLoad()
		_G.PrintChat = function() end
	end
	-- Some green chat will not be disabled...
	-- ################################### DISABLE BOL GREEN PRINT CHAT ##################################  

	-- ############################################# ImAimingVPrediction ################################################
-- Globals ---------------------------------------------------------------------

require 'VPrediction'

--End Honda7 credit

_G.Champs = {
    ["Aatrox"] = {
        [_Q] = { speed = 450, delay = 0.27, range = 650, minionCollisionWidth = 280},
        [_E] = { speed = 1200, delay = 0.27, range = 1000, minionCollisionWidth = 80}
    },
        ["Ahri"] = {
        [_Q] = { speed = 1670, delay = 0.24, range = 895, minionCollisionWidth = 50},
        [_E] = { speed = 1550, delay = 0.24, range = 920, minionCollisionWidth = 80}
    },
        ["Amumu"] = {
        [_Q] = { speed = 2000, delay = 0.250, range = 1100, minionCollisionWidth = 80}
    },
        ["Anivia"] = {
        [_Q] = { speed = 860.05, delay = 0.250, range = 1100, minionCollisionWidth = 110},
        [_R] = { speed = math.huge, delay = 0.100, range = 615, minionCollisionWidth = 350}
    },
        ["Annie"] = {
        [_W] = { speed = math.huge, delay = 0.25, range = 625, minionCollisionWidth = 0},
        [_R] = { speed = math.huge, delay = 0.2, range = 600, minionCollisionWidth = 0}
    },
        ["Ashe"] = {
        [_W] = { speed = 2000, delay = 0.120, range = 1200, minionCollisionWidth = 85},
        [_R] = { speed = 1600, delay = 0.5, range = 1200, minionCollisionWidth = 0}
    },
        ["Blitzcrank"] = {
        [_Q] = { speed = 1800, delay = 0.250, range = 1050, minionCollisionWidth =  90}
    },
        ["Brand"] = {
        [_Q] = { speed = 1600, delay = 0.625, range = 1100, minionCollisionWidth = 90},
        [_W] = { speed = 900, delay = 0.25, range = 1100, minionCollisionWidth = 0},
        },
        ["Caitlyn"] = {
        [_Q] = { speed = 2200, delay = 0.625, range = 1300, minionCollisionWidth = 0},
        [_E] = { speed = 2000, delay = 0.400, range = 1000, minionCollisionWidth = 80},
    },
        ["Cassiopeia"] = {
        [_Q] = { speed = math.huge, delay = 0.535, range = 850, minionCollisionWidth = 0},
        [_W] = { speed = math.huge, delay = 0.350, range = 850, minionCollisionWidth = 80},
        [_R] = { speed = math.huge, delay = 0.535, range = 850, minionCollisionWidth = 350}
    },
        ["Chogath"] = {
        [_Q] = { speed = 950, delay = 0, range = 950, minionCollisionWidth = 0},
        [_W] = { speed = math.huge, delay = 0.25, range = 700, minionCollisionWidth = 0},
        },
        ["Corki"] = {
        [_Q] = { speed = 1500, delay = 0.350, range = 840, minionCollisionWidth = 0},
        [_R] = { speed = 2000, delay = 0.200, range = 1225, minionCollisionWidth = 60},
    },
        ["Darius"] = {
        [_E] = { speed = 1500, delay = 0.550, range = 530, minionCollisionWidth = 0}
    },
        ["Diana"] = {
        [_Q] = { speed = 2000, delay = 0.250, range = 830, minionCollisionWidth = 0}
    },
        ["DrMundo"] = {
        [_Q] = { speed = 2000, delay = 0.250, range = 1050, minionCollisionWidth = 80}
    },
        ["Draven"] = {
        [_E] = { speed = 1400, delay = 0.250, range = 1100, minionCollisionWidth = 0},
        [_R] = { speed = 2000, delay = 0.5, range = 2500, minionCollisionWidth = 0}
    },
        ["Elise"] = {
        [_E] = { speed = 1450, delay = 0.250, range = 975, minionCollisionWidth = 80}
    },
        ["Ezreal"] = {
        [_Q] = { speed = 2000, delay = 0.251, range = 1200, minionCollisionWidth = 80},
        [_W] = { speed = 1600, delay = 0.25, range = 1050, minionCollisionWidth = 0},
        [_R] = { speed = 2000, delay = 1, range = 20000, minionCollisionWidth = 150}
    },
        ["Fizz"] = {
        [_R] = { speed = 1350, delay = 0.250, range = 1150, minionCollisionWidth = 0}
    },
        ["Galio"] = {
        [_Q] = { speed = 850, delay = 0.25, range = 940, minionCollisionWidth = 0},
        --[_E] = { speed = 2000, delay = 0.400, range = 1180, minionCollisionWidth = 0},
    },
        ["Gragas"] = {
        [_Q] = { speed = 1000, delay = 0.250, range = 1100, minionCollisionWidth = 0}
    },
        ["Graves"] = {
        [_Q] = { speed = 1950, delay = 0.265, range = 950, minionCollisionWidth = 85},
        [_W] = { speed = 1650, delay = 0.300, range = 950, minionCollisionWidth = 0},
        [_R] = { speed = 2100, delay = 0.219, range = 1000, minionCollisionWidth = 30}
    },
        ["Heimerdinger"] = {
                [_W] = { speed = 1200, delay = 0.200, range = 1100, minionCollisionWidth = 70},
                [_E] = { speed = 1000, delay = 0.1, range = 925, minionCollisionWidth = 0},
        },
        ["Irelia"] = {
        [_R] = { speed = 1700, delay = 0.250, range = 1000, minionCollisionWidth = 0}
    },
        ["JarvanIV"] = {
                [_Q] = { speed = 1400, delay = 0.2, range = 800, minionCollisionWidth = 0},
                [_E] = { speed = 200, delay = 0.2, range = 850, minionCollisionWidth = 0},
        },
        ["Jinx"] = {
                [_W] = { speed = 3300, delay = 0.600, range = 1500, minionCollisionWidth = 70},
                [_E] = { speed = 887, delay = 0.500, range = 950, minionCollisionWidth = 0},
                [_R] = { speed = 2500, delay = 0.600, range = 2000 , minionCollisionWidth = 0}
        },
        ["Karma"] = {
        [_Q] = { speed = 1700, delay = 0.250, range = 1050, minionCollisionWidth = 80}
    },
        ["Karthus"] = {
        [_Q] = { speed = 1750, delay = 0.25, range = 875, minionCollisionWidth = 0},
    },
        ["Kennen"] = {
        [_Q] = { speed = 1700, delay = 0.180, range = 1050, minionCollisionWidth = 70}
    },
        ["Khazix"] = {
        [_W] = { speed = 828.5, delay = 0.225, range = 1000, minionCollisionWidth = 100}
    },
        ["KogMaw"] = {
        [_R] = { speed = 1050, delay = 0.250, range = 2200, minionCollisionWidth = 0}
    },
        ["Leblanc"] = {
        [_E] = { speed = 1600, delay = 0.250, range = 960, minionCollisionWidth = 0},
        [_R] = { speed = 1600, delay = 0.250, range = 960, minionCollisionWidth = 0},
    },
        ["LeeSin"] = {
        [_Q] = { speed = 1800, delay = 0.250, range = 1100, minionCollisionWidth = 100}
    },
        ["Leona"] = {
        [_E] = { speed = 2000, delay = 0.250, range = 900, minionCollisionWidth = 0},
        [_R] = { speed = 2000, delay = 0.250, range = 1200, minionCollisionWidth = 0},
    },
        ["Lucian"] = {
        [_W] = { speed = 1470, delay = 0.288, range = 1000, minionCollisionWidth = 25}
    },
        ["Lulu"] = {
        [_Q] = { speed = 1530, delay = 0.250, range = 945, minionCollisionWidth = 80}
    },
        ["Lux"] = {
        [_Q] = { speed = 1200, delay = 0.245, range = 1300, minionCollisionWidth = 50},
        [_E] = { speed = 1400, delay = 0.245, range = 1100, minionCollisionWidth = 0},
        [_R] = { speed = math.huge, delay = 0.245, range = 3500, minionCollisionWidth = 0}
    },
        ["Malzahar"] = {
        [_Q] = { speed = 1170, delay = 0.600, range = 900, minionCollisionWidth = 50}
    },
        ["Mordekaiser"] = {
        [_E] = { speed = math.huge, delay = 0.25, range = 700, minionCollisionWidth = 0},
        },
        ["Morgana"] = {
        [_Q] = { speed = 1200, delay = 0.250, range = 1300, minionCollisionWidth = 80}
    },
        ["Nami"] = {
        [_Q] = { speed = math.huge, delay = 0.8, range = 850, minionCollisionWidth = 0}
    },
        ["Nautilus"] = {
        [_Q] = { speed = 2000, delay = 0.250, range = 1080, minionCollisionWidth = 100}
    },
        ["Nidalee"] = {
        [_Q] = { speed = 1300, delay = 0.125, range = 1500, minionCollisionWidth = 60},
    },
        ["Nocturne"] = {
        [_Q] = { speed = 1600, delay = 0.250, range = 1200, minionCollisionWidth = 0}
    },
    ["Olaf"] = {
        [_Q] = { speed = 1600, delay = 0.25, range = 1000, minionCollisionWidth = 0}
    },
        ["Quinn"] = {
        [_Q] = { speed = 1600, delay = 0.25, range = 1050, minionCollisionWidth = 100}
    },
        ["Rumble"] = {
        [_E] = { speed = 2000, delay = 0.250, range = 950, minionCollisionWidth = 80}
    },
        ["Sejuani"] = {
        [_R] = { speed = 1300, delay = 0.200, range = 1175, minionCollisionWidth = 0}
    },
        ["Sivir"] = {
        [_Q] = { speed = 1330, delay = 0.250, range = 1075, minionCollisionWidth = 0}
    },
        ["Skarner"] = {
        [_E] = { speed = 1200, delay = 0.250, range = 760, minionCollisionWidth = 0}
    },
        ["Swain"] = {
        [_Q] = { speed = math.huge, delay = 0.500, range = 900, minionCollisionWidth = 0}
    },
        ["Syndra"] = {
        [_Q] = { speed = math.huge, delay = 0.400, range = 800, minionCollisionWidth = 0}
    },
        ["Thresh"] = {
        [_Q] = { speed = 1900, delay = 0.500, range = 1075, minionCollisionWidth = 80}
    },
        ["Twitch"] = {
        [_W] = {speed = 1750, delay = 0.283, range = 900, minionCollisionWidth = 0}
    },
        ["TwistedFate"] = {
        [_Q] = { speed = 1450, delay = 0.200, range = 1450, minionCollisionWidth = 0}
    },
        ["Urgot"] = {
        [_Q] = { speed = 1600, delay = 0.175, range = 1000, minionCollisionWidth = 100},
        [_E] = { speed = 1750, delay = 0.25, range = 900, minionCollisionWidth = 0}
    },
        ["Varus"] = {
       --[_Q] = { speed = 1850, delay = 0.1, range = 1475, minionCollisionWidth = 0},
        [_E] = { speed = 1500, delay = 0.245, range = 925, minionCollisionWidth = 0},
        [_R] = { speed = 1950, delay = 0.5, range = 1075, minionCollisionWidth = 0}
    },
        ["Veigar"] = {
        [_W] = { speed = 900, delay = 0.25, range = 900, minionCollisionWidth = 0}
    },
        ["Viktor"] = {
                [_W] = { speed = math.huge, delay = 0.25, range = 625, minionCollisionWidth = 0},
                [_E] = { speed = 1200, delay = 0.25, range = 1225, minionCollisionWidth = 0},
                [_R] = { speed = 1000, delay = 0.25, range = 700, minionCollisionWidth = 0},
    },
        ["Velkoz"] = {
                [_Q] = { speed = 1300, delay = 0.066, range = 1100, minionCollisionWidth = 50},
                [_W] = { speed = 1700, delay = 0.064, range = 1050, minionCollisionWidth = 0},
                [_E] = { speed = 1500, delay = 0.333, range = 1100, minionCollisionWidth = 0},
    },    
        ["Xerath"] = {
        [_Q] = { speed = 3000, delay = 0.6, range = 1100, minionCollisionWidth = 0},
        [_R] = { speed = 2000, delay = 0.25, range = 1100, minionCollisionWidth = 0}
    },
        ["Zed"] = {
        [_Q] = { speed = 1700, delay = 0.2, range = 925, minionCollisionWidth = 0},
    },
        ["Ziggs"] = {
        [_Q] = { speed = 1722, delay = 0.218, range = 850, minionCollisionWidth = 0},
                [_W] = { speed = 1727, delay = 0.249, range = 1000, minionCollisionWidth = 0},
                [_E] = { speed = 2694, delay = 0.125, range = 900, minionCollisionWidth = 0},
                [_R] = { speed = 1856, delay = 0.1014, range = 2500, minionCollisionWidth = 0},
    },
        ["Zyra"] = {
                 [_Q] = { speed = math.huge, delay = 0.7, range = 800, minionCollisionWidth = 0},
         [_E] = { speed = 1150, delay = 0.16, range = 1100, minionCollisionWidth = 0}
    }
}

-- put other declarations after this check
local data = Champs[myHero.charName]
local VP -- it is nil by default :D
local Target 
local ts2 = TargetSelector(TARGET_LOW_HP, 1500, DAMAGE_MAGIC, true) -- make these local
local Menu -- make these local
local predictions = {} -- make these local
local str = { [_Q] = "Q", [_W] = "W", [_E] = "E", [_R] = "R" }
local keybindings = { [_Q] = "Z", [_W] = "X", [_E] = "C", [_R] = "V" }
local ConfigType = SCRIPT_PARAM_ONKEYDOWN
local initDone = false
 -- Code ------------------------------------------------------------------------

function VPredictionOnLoad()
	if not Champs[myHero.charName] then
		TBConfig.VPrediction = false
		return 
	end
    VP = VPrediction()
	Config = scriptConfig("[多合一]技能预判设置", "ImAiming")
   -- if Champs[myHero.charName] ~= nil then -- this check is on line 297
	for i, spell in pairs(data) do
		Config:addParam(str[i], "使用预判 " .. str[i], ConfigType, false, GetKey(keybindings[i]))
		predictions[str[i]] = {spell.range, spell.speed, spell.delay, spell.minionCollisionWidth, i}
	end 
    Config:addParam("accuracy", "精准度设置", SCRIPT_PARAM_SLICE, 1, 0, 5, 0)
    Config:addParam("rangeoffset", "范围减少所抵销", SCRIPT_PARAM_SLICE, 0, 0, 200, 0)
    Config:addParam("autocast", "自动施法在100%命中", SCRIPT_PARAM_ONOFF, false)
    ts2.name = "我的目标"
    Config:addTS(ts2)
    initDone = true
	--PrintChat(" >> I'M Aiming by Klokje edited by Dienofail VPrediction v0.15 loaded") -- messages generally are at the end :D
end


function VPredictionOnTick()
	if not Champs[myHero.charName] then
		TBConfig.VPrediction = false
		return 
	end
	if initDone then
	    Target = GetCustomTarget() --Tmrees
	    if Target == nil then return end
	    for i, spell in pairs(data) do
            local collision = spell.minionCollisionWidth == 0 and false or true
            local CastPosition, HitChance, Position = VP:GetLineCastPosition(Target, spell.delay, spell.minionCollisionWidth, spell.range, spell.speed, myHero, collision)
	        if Config[str[i]] and myHero:CanUseSpell(i) and IsLeeThresh() then -- move spell ready check to top
	            if CastPosition and HitChance and HitChance >= Config.accuracy and GetDistance(CastPosition, myHero) < spell.range - Config.rangeoffset then CastSpell(i, CastPosition.x, CastPosition.z) end   
			elseif Config.autocast then
                if CastPosition and HitChance and HitChance > 2 and GetDistance(CastPosition, myHero) < spell.range - Config.rangeoffset then CastSpell(i, CastPosition.x, CastPosition.z) end
            end
		end 
	end
end 

--Credit Trees
function GetCustomTarget()
    if _G.MMA_Target and _G.MMA_Target.type == myHero.type then return _G.MMA_Target end
    if _G.AutoCarry and _G.AutoCarry.Crosshair and _G.AutoCarry.Attack_Crosshair and _G.AutoCarry.Attack_Crosshair.target and _G.AutoCarry.Attack_Crosshair.target.type == myHero.type then return _G.AutoCarry.Attack_Crosshair.target end
    ts2:update()
    --print('tstarget called')
    return ts2.target
end
--End Credit Trees

function IsLeeThresh()
	if myHero.charName == 'LeeSin' then
		if myHero:GetSpellData(_Q).name == 'BlindMonkQOne' then
			return true
		else
			return false
		end
	elseif myHero.charName == 'Thresh' then
		if myHero:GetSpellData(_Q).name == 'ThreshQ' then
			return true
		else
			return false
		end	
	else 
		return true
	end
end
    -- ############################################# ImAimingVPrediction ################################################
    
    -- ############################################# ProTrackerv2 ################################################
local version = 1.30
local AUTOUPDATE = false
local SCRIPT_NAME = "ProTracker"

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------

local SOURCELIB_URL = "https://raw.github.com/TheRealSource/public/master/common/SourceLib.lua"
local SOURCELIB_PATH = LIB_PATH.."SourceLib.lua"

if FileExist(SOURCELIB_PATH) then
	require("SourceLib")
else
	DOWNLOADING_SOURCELIB = true
	DownloadFile(SOURCELIB_URL, SOURCELIB_PATH, function() print("Required libraries downloaded successfully, please reload") end)
end

if DOWNLOADING_SOURCELIB then print("Downloading required libraries, please wait...") return end

if AUTOUPDATE then
	 SourceUpdater(SCRIPT_NAME, version, "raw.github.com", "/honda7/BoL/master/"..SCRIPT_NAME..".lua", SCRIPT_PATH .. GetCurrentEnv().FILE_NAME, "/honda7/BoL/master/VersionFiles/"..SCRIPT_NAME..".version"):CheckUpdate()
end

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------


local TrackSpells = {_Q, _W, _E, _R, SUMMONER_1, SUMMONER_2}
local SpellsData = {}
local TickLimit = 0
local FirstTick = false


local SSpells = {		{CName="-----------闪现", Name="SummonerFlash", Color={255, 255, 255, 0} },
						{CName="-----------鬼步", Name="SummonerHaste", Color={255, 0, 0, 255} },
						{CName="-----------引燃", Name="SummonerDot", Color={255, 255, 0, 0 }},
						{CName="-----------屏障", Name="SummonerBarrier", Color={255, 209, 143, 0}},
						{CName="-----------惩戒", Name="SummonerSmite", Color={255, 209, 143, 0}},
						{CName="-----------虚弱", Name="SummonerExhaust", Color={255, 209, 143, 0}},
						{CName="-----------治愈", Name="SummonerHeal", Color={255, 0, 255, 0}},
						{CName="-----------传送", Name="SummonerTeleport", Color={255, 192, 0, 209}},
						{CName="-----------净化", Name="SummonerBoost", Color={255, 255, 138, 181}},
						{CName="-----------清晰", Name="SummonerMana", Color={255, 0, 110, 255}},
						{CName="-----------洞察", Name="SummonerClairvoyance", Color={255, 0, 110, 255}},
						{CName="-----------重生", Name="SummonerRevive", Color={255, 0, 255, 0}},
						{CName="-----------卫戍部队", Name="SummonerOdinGarrison", Color={255, 0, 110, 255}},
						{CName="-----------其余的", Name="TheRest", Color={255, 255, 255, 255}},
						}
						
function ProTrackerOnLoad()
	Menu = scriptConfig("[多合一]显技能显CD", "ProTrackerv2")
	Menu:addParam("Enabled", "在敌人绘制指标", SCRIPT_PARAM_ONKEYTOGGLE, true, string.byte("M"))
	Menu:addParam("Enabled2", "在盟友绘制指标", SCRIPT_PARAM_ONKEYTOGGLE, false, string.byte("N"))
	
	Menu:addSubMenu("CD设置", "Drawing")
	Menu.Drawing:addParam("Always", "CD显示开关",  SCRIPT_PARAM_ONOFF, true)
	Menu.Drawing:addParam("DrawKey", "只有按住才显示", SCRIPT_PARAM_ONKEYDOWN, false, 16)
	
	--[[Appearance submenu]]
	Menu:addSubMenu("调节CD位置", "Appearance")
	Menu.Appearance:addParam("showh", "显示水平指标", SCRIPT_PARAM_ONOFF, true)
	Menu.Appearance:addParam("vposition", "水平的指示器垂直的位置", SCRIPT_PARAM_SLICE, 0, -25, 25)
	Menu.Appearance:addParam("width", "水平的指示器宽度", SCRIPT_PARAM_SLICE, 20, 1, 25)
	Menu.Appearance:addParam("height", "水平的指示器高度", SCRIPT_PARAM_SLICE, 5, 1, 20)
	Menu.Appearance:addParam("n", "水平指示器的数字", SCRIPT_PARAM_SLICE, 4, 1, 6)
	Menu.Appearance:addParam("showv", "显示垂直指标", SCRIPT_PARAM_ONOFF, true)
	Menu.Appearance:addParam("width2", "垂直的指示器宽度", SCRIPT_PARAM_SLICE, 9, 1, 25)
	Menu.Appearance:addParam("textsize", "本文大小", SCRIPT_PARAM_SLICE, 13, 10, 20)
	
	--[[Submenu to select the colors]]
	Menu:addSubMenu("调节CD颜色", "Colors")
	Menu.Colors:addParam("cdcolor", "没准备好的颜色", SCRIPT_PARAM_COLOR, {255, 214, 114, 0})--orange
	Menu.Colors:addParam("readycolor", "准备好的颜色", SCRIPT_PARAM_COLOR, {255, 54, 214, 0})--green
	Menu.Colors:addParam("textcolor", "文字颜色", SCRIPT_PARAM_COLOR, {255, 255, 255, 255})--white
	Menu.Colors:addParam("backgroundcolor", "背景颜色", SCRIPT_PARAM_COLOR, {255, 128, 128, 128})--grey
	
	Menu.Colors:addSubMenu("召唤师技能", "SSpells")
	for i, spell in ipairs(SSpells) do
		Menu.Colors.SSpells:addParam(spell.Name, spell.CName, SCRIPT_PARAM_COLOR, spell.Color)
	end

end

--[[Returns the healthbar position]]
function GetHPBarPos(enemy)
	enemy.barData = {PercentageOffset = {x = -0.05, y = 0}}--GetEnemyBarData()
	local barPos = GetUnitHPBarPos(enemy)
	local barPosOffset = GetUnitHPBarOffset(enemy)
	local barOffset = { x = enemy.barData.PercentageOffset.x, y = enemy.barData.PercentageOffset.y }
	local barPosPercentageOffset = { x = enemy.barData.PercentageOffset.x, y = enemy.barData.PercentageOffset.y }
	local BarPosOffsetX = 171
	local BarPosOffsetY = 46
	local CorrectionY = 39
	local StartHpPos = 31
	
	barPos.x = math.floor(barPos.x + (barPosOffset.x - 0.5 + barPosPercentageOffset.x) * BarPosOffsetX + StartHpPos)
	barPos.y = math.floor(barPos.y + (barPosOffset.y - 0.5 + barPosPercentageOffset.y) * BarPosOffsetY + CorrectionY)
						
	local StartPos = Vector(barPos.x , barPos.y, 0)
	local EndPos =  Vector(barPos.x + 108 , barPos.y , 0)
	return Vector(StartPos.x, StartPos.y, 0), Vector(EndPos.x, EndPos.y, 0)
end

function ProTrackerOnTick()
	if os.clock() - TickLimit > 0.3 then
		TickLimit = os.clock()
		for i=1, heroManager.iCount, 1 do
			local hero = heroManager:getHero(i)
			if ValidTarget(hero, math.huge, false) or ValidTarget(hero) then
				--[[	Update the current cooldowns]]
				hero = heroManager:getHero(i)
				for _, spell in pairs(TrackSpells) do
					if SpellsData[i] == nil then
						SpellsData[i] = {}
					end
					if SpellsData[i][spell] == nil then
						SpellsData[i][spell] = {currentCd=0, maxCd = 0, level=0}
					end
					--[[	Get the maximum cooldowns to make the progress  bar]]
					local thespell = hero:GetSpellData(spell)
					local currentcd
					if thespell and thespell.currentCd then
						currentcd = thespell.currentCd
					end
					if currentcd and thespell and thespell.currentCd then
						SpellsData[i][spell] = {
							currentCd = math.floor(currentcd),
							maxCd = math.floor(currentcd) > SpellsData[i][spell].maxCd and math.floor(currentcd) or SpellsData[i][spell].maxCd,
							level = thespell.level
						}
					end
				end
			end
		end
	end
	FirstTick = true
end

function DrawRectangleAL(x, y, w, h, color)
	local Points = {}
	Points[1] = D3DXVECTOR2(math.floor(x), math.floor(y))
	Points[2] = D3DXVECTOR2(math.floor(x + w), math.floor(y))
	DrawLines2(Points, math.floor(h), color)
end

function ProTrackerOnDraw()
	if (Menu.Enabled or Menu.Enabled2 or IsKeyDown(16)) and FirstTick and (Menu.Drawing.Always or Menu.Drawing.DrawKey) then
		for i=1, heroManager.iCount, 1 do
			local hero = heroManager:getHero(i)
			if ((ValidTarget(hero, math.huge,false)  and (Menu.Enabled2 or IsKeyDown(16))) or (ValidTarget(hero) and (Menu.Enabled or IsKeyDown(16)))) and not hero.isMe then
				local barpos = GetHPBarPos(hero)
				if OnScreen(barpos.x, barpos.y) and (SpellsData[i] ~= nil) then
					local pos = Vector(barpos.x, barpos.y, 0)
					local CDcolor = ARGB(Menu.Colors.cdcolor[1], Menu.Colors.cdcolor[2],Menu.Colors.cdcolor[3],Menu.Colors.cdcolor[4])
					local Readycolor = ARGB(Menu.Colors.readycolor[1],Menu.Colors.readycolor[2],Menu.Colors.readycolor[3],Menu.Colors.readycolor[4])
					local Textcolor = ARGB(Menu.Colors.textcolor[1],Menu.Colors.textcolor[2],Menu.Colors.textcolor[3],Menu.Colors.textcolor[4] )
					local Backgroundcolor = ARGB(Menu.Colors.backgroundcolor[1],Menu.Colors.backgroundcolor[2],Menu.Colors.backgroundcolor[3],Menu.Colors.backgroundcolor[4])
					local width = Menu.Appearance.width
					local height = Menu.Appearance.height
					local sep = 2
					--[[First 4 spells]]
					if Menu.Appearance.showh then
						pos.y =  pos.y + Menu.Appearance.vposition
						for j, Spells in ipairs (TrackSpells) do
							local currentcd = SpellsData[i][Spells].currentCd
							local maxcd = SpellsData[i][Spells].maxCd
							local level = SpellsData[i][Spells].level
							
							if j > 4 then
								CDcolor = ARGB(Menu.Colors.SSpells["TheRest"][1], Menu.Colors.SSpells["TheRest"][2], Menu.Colors.SSpells["TheRest"][3], Menu.Colors.SSpells["TheRest"][4])
								for _, spell in ipairs(SSpells) do
									if (Menu.Colors.SSpells[spell.Name] ~= nil) and (hero:GetSpellData(j == 5 and SUMMONER_1 or SUMMONER_2).name == spell.Name) then
										CDcolor = ARGB(Menu.Colors.SSpells[spell.Name][1], Menu.Colors.SSpells[spell.Name][2], Menu.Colors.SSpells[spell.Name][3], Menu.Colors.SSpells[spell.Name][4])
									end
								end
								Readycolor = CDcolor
							else
								CDcolor = ARGB(Menu.Colors.cdcolor[1], Menu.Colors.cdcolor[2],Menu.Colors.cdcolor[3],Menu.Colors.cdcolor[4])
								Readycolor = ARGB(Menu.Colors.readycolor[1],Menu.Colors.readycolor[2],Menu.Colors.readycolor[3],Menu.Colors.readycolor[4])
							end
						
							DrawRectangleAL(pos.x-1, pos.y-1, width + sep , height+4, Backgroundcolor)
						
							if (currentcd ~= 0) then
								DrawRectangleAL(pos.x, pos.y, width - math.floor(width * currentcd) / maxcd, height, CDcolor)
							else
								DrawRectangleAL(pos.x, pos.y, width, height, Readycolor)
							end
						
							if (currentcd ~= 0) and (currentcd < 100) then
								DrawText(tostring(currentcd),Menu.Appearance.textsize, pos.x+6, pos.y+4, ARGB(255, 0, 0, 0))
								DrawText(tostring(currentcd),Menu.Appearance.textsize, pos.x+8, pos.y+6, ARGB(255, 0, 0, 0))
								DrawText(tostring(currentcd),Menu.Appearance.textsize, pos.x+7, pos.y+5, Textcolor)
							elseif IsKeyDown(16) then
								DrawText(tostring(level),Menu.Appearance.textsize, pos.x+6, pos.y+4, ARGB(255, 0, 0, 0))
								DrawText(tostring(level),Menu.Appearance.textsize, pos.x+8, pos.y+6, ARGB(255, 0, 0, 0))
								DrawText(tostring(level),Menu.Appearance.textsize, pos.x+7, pos.y+5, Textcolor)
							end

							pos.x = pos.x + width + sep
							if j == Menu.Appearance.n then break end
						end
					end
					pos.x = barpos.x + 25*5+3 + 2*4
					pos.y = barpos.y - 8
					--[[Last 2 spells]]
					if Menu.Appearance.showv then
						for j, Spells in ipairs (TrackSpells) do
							local currentcd = SpellsData[i][Spells].currentCd
							local maxcd = SpellsData[i][Spells].maxCd
							local width2 = Menu.Appearance.width2
							if j > 4 then
								CDcolor = ARGB(Menu.Colors.SSpells["TheRest"][1], Menu.Colors.SSpells["TheRest"][2], Menu.Colors.SSpells["TheRest"][3], Menu.Colors.SSpells["TheRest"][4])
								for _, spell in ipairs(SSpells) do
									if (Menu.Colors.SSpells[spell.Name] ~= nil) and (hero:GetSpellData(j == 5 and SUMMONER_1 or SUMMONER_2).name == spell.Name) then
										CDcolor = ARGB(Menu.Colors.SSpells[spell.Name][1], Menu.Colors.SSpells[spell.Name][2], Menu.Colors.SSpells[spell.Name][3], Menu.Colors.SSpells[spell.Name][4])
									end
								end
								DrawRectangleAL(pos.x, pos.y,width2+2,11,Backgroundcolor)
								if currentcd ~= 0 then
									DrawRectangleAL(pos.x+1, pos.y+1, width2 - width2 * currentcd / maxcd,9,CDcolor)
								
								else
									DrawRectangleAL(pos.x+1, pos.y+1, width2, 9, CDcolor)
								end
								if (currentcd ~= 0) and (currentcd < 100) then
									DrawText(tostring(currentcd),Menu.Appearance.textsize, pos.x-1, pos.y-1, ARGB(255, 0, 0, 0))
									DrawText(tostring(currentcd),Menu.Appearance.textsize, pos.x+1, pos.y+1, ARGB(255, 0, 0, 0))
									DrawText(tostring(currentcd),Menu.Appearance.textsize, pos.x, pos.y, Textcolor)
								end
								Readycolor = CDcolor
								pos.y = pos.y - 12
							end
						end
					end
				end
			end
		end
	end
end
    
    -- ############################################# ProTrackerv2 ################################################
	-- ############################################# ShowHP ################################################
local enemyTable = {}

function ShowHPOnTick()
	if enemyTable ~= nil then
		if #enemyTable <= 0 then
			updateTable()	
		else
			doDraw(getFirst())
		end
	end
end

function getFirst()
	local enemy
	for i, champ in ipairs(enemyTable) do
		enemy = champ
		break
	end
	return enemy
end

function updateTable()
	for i=1, heroManager.iCount do
		local hero = heroManager:GetHero(i)
		if  hero.team ~= myHero.team and not enemyTable[hero] then
			table.insert(enemyTable,hero)
		end
	end
end

function doDraw(enemy)
	local health = tostring(math.floor((enemy.health)+0.5))
	PrintFloatText(enemy,0,health)
	table.remove(enemyTable,1)
end	
	
	-- ############################################# ShowHP ################################################		
	
	-- ############################################# SafeMovement ################################################		
-- Change autoUpdate to false if you wish to not receive auto updates.
-- Change silentUpdate to true if you wish not to receive any message regarding updates
local autoUpdate   = false
local silentUpdate = false

local version = 0.008

local scriptName = "SafeMovement"

--[[
.____    ._____.     ________                      .__                    .___            
|    |   |__\_ |__   \______ \   ______  _  ______ |  |   _________     __| _/___________ 
|    |   |  || __ \   |    |  \ /  _ \ \/ \/ /    \|  |  /  _ \__  \   / __ |/ __ \_  __ \
|    |___|  || \_\ \  |    `   (  <_> )     /   |  \  |_(  <_> ) __ \_/ /_/ \  ___/|  | \/
|_______ \__||___  / /_______  /\____/ \/\_/|___|  /____/\____(____  /\____ |\___  >__|   
        \/       \/          \/                  \/                \/      \/    \/       
]]

-- SourceLib auto download
local sourceLibFound = true
if FileExist(LIB_PATH .. "SourceLib.lua") then
    require "SourceLib"
else
    sourceLibFound = false
    DownloadFile("https://raw.github.com/TheRealSource/public/master/common/SourceLib.lua", LIB_PATH .. "SourceLib.lua", function() print("<font color=\"#6699ff\"><b>" .. scriptName .. ":</b></font> <font color=\"#FFFFFF\">SourceLib downloaded! Please reload!</font>") end)
end
-- Return if SourceLib has to be downloaded
if not sourceLibFound then 
printchat()
return 
end

-- Updater
if autoUpdate then
    SourceUpdater(scriptName, version, "raw.github.com", "/TheRealSource/public/master/SafeMovement.lua", SCRIPT_PATH .. GetCurrentEnv().FILE_NAME, "/TheRealSource/public/master/SafeMovement.version"):SetSilent(silentUpdate):CheckUpdate()
end


--[[
_________            .___      
\_   ___ \  ____   __| _/____  
/    \  \/ /  _ \ / __ |/ __ \ 
\     \___(  <_> ) /_/ \  ___/ 
 \______  /\____/\____ |\___  >
        \/            \/    \/ 
]]

local menu = nil
local lastSend = 0
local menuText = nil

function SafeMoveOnLoad()
	
    menu = scriptConfig("[多合一]平滑流畅移动", "SafeMovement")

    menu:addParam("enabled",  "启用",                        SCRIPT_PARAM_ONOFF, false)
    menu:addParam("sep",      "",                               SCRIPT_PARAM_INFO,  "")
    menu:addParam("interval", "移动间隔(X 毫秒)",  SCRIPT_PARAM_SLICE, 50, 0, 100, 0)
    menu:addParam("text",     "",                               SCRIPT_PARAM_INFO,  "")

    menuText = menu._param[#menu._param]

    PacketHandler:HookOutgoingPacket(Packet.headers.S_MOVE, OnMovePacket)

end

function SafeMoveOnTick()

    -- Update menu text
    local clicksPerSecond = menu.interval > 0 and math.round(1000 / menu.interval) or "不受限"
    menuText.text = " = " .. clicksPerSecond .. " 点击/秒"

end

function OnMovePacket(p)

    local packet = Packet(p)
    if packet:get("type") == 2 then
        if os.clock() * 1000 - lastSend < menu.interval and not _G.Evadeee_evading then
            p:Block()
        else
            lastSend = os.clock() * 1000
        end
    else
        -- Reset on AA
        lastSend = 0
    end

end
	-- ############################################# SafeMovement ################################################	
	-- ############################################# Surrender ################################################

local delay = 0
local Mdelay = 0
local Mtdelay = (Mdelay + 0)
local p50 = (myHero.x + 150)
local m50 = (myHero.x - 150)
local pz50 = (myHero.z + 150)
local mz50 = (myHero.z - 150)

function SurrenderOnLoad()
	Surrender = scriptConfig("[多合一]暂离投降设置", "Surrender")
	Surrender:addParam("FF", "自动投降", SCRIPT_PARAM_ONOFF, false)
	Surrender:addParam("AAFK", "防止暂离", SCRIPT_PARAM_ONOFF, true)
	Surrender:addParam("FFT", "自动投降时间-分", SCRIPT_PARAM_SLICE, 1, 1, 20, 0)
	Surrender:addParam("AAFKT", "防止暂离时间-秒", SCRIPT_PARAM_SLICE, 1, 1, 60, 0)
end

function SurrenderOnTick()
	TimesDelay = (Surrender.FFT * 60000)
	MoveDelay1 = (Surrender.AAFKT * 1000)
	MoveDelay2 = (Surrender.AAFKT * 2000)
	if GetTickCount() > Mdelay + MoveDelay1 then
		if Surrender.AAFK then
			myHero:MoveTo(p50, pz50)
		end
	Mdelay = GetTickCount()
end
	if GetTickCount() > Mtdelay + MoveDelay2 then
		if Surrender.AAFK then
			myHero:MoveTo(m50, mz50)
	end
		Mtdelay = GetTickCount()
	end
	if GetTickCount() > delay + TimesDelay then
		if Surrender.FF then
			SendChat("/ff")
		end
		delay = GetTickCount()
	end
end

-- ############################################# Surrender ################################################
	-- ############################################# 择攻击英雄优化 Simple TS Priority Arranger ################################################

local priorityTable = {

	AP = {
		"Ahri", "Akali", "Anivia", "Annie", "Brand", "Cassiopeia", "Diana", "Evelynn", "FiddleSticks", "Fizz", "Gragas", "Heimerdinger", "Karthus",
		"Kassadin", "Katarina", "Kayle", "Kennen", "Leblanc", "Lissandra", "Lux", "Malzahar", "Mordekaiser", "Morgana", "Nidalee", "Orianna",
		"Rumble", "Ryze", "Sion", "Swain", "Syndra", "Teemo", "TwistedFate", "Veigar", "Viktor", "Vladimir", "Xerath", "Ziggs", "Zyra", "MasterYi",
	},
	Support = {
		"Blitzcrank", "Janna", "Karma", "Leona", "Lulu", "Nami", "Sona", "Soraka", "Thresh", "Zilean",
	},

	Tank = {
		"Amumu", "Chogath", "DrMundo", "Galio", "Hecarim", "Malphite", "Maokai", "Nasus", "Rammus", "Sejuani", "Shen", "Singed", "Skarner", "Volibear",
		"Warwick", "Yorick", "Zac", "Nunu", "Taric", "Alistar",
	},

	AD_Carry = {
		"Ashe", "Caitlyn", "Corki", "Draven", "Ezreal", "Graves", "Jayce", "KogMaw", "MissFortune", "Pantheon", "Quinn", "Shaco", "Sivir",
		"Talon", "Tristana", "Twitch", "Urgot", "Varus", "Vayne", "Zed", "Jinx"

	},

	Bruiser = {
		"Darius", "Elise", "Fiora", "Gangplank", "Garen", "Irelia", "JarvanIV", "Jax", "Khazix", "LeeSin", "Nautilus", "Nocturne", "Olaf", "Poppy",
		"Renekton", "Rengar", "Riven", "Shyvana", "Trundle", "Tryndamere", "Udyr", "Vi", "MonkeyKing", "XinZhao", "Aatrox"
	},

}

function SetPriority(table, hero, priority)
	for i=1, #table, 1 do
		if hero.charName:find(table[i]) ~= nil then
			TS_SetHeroPriority(priority, hero.charName)
		end
	end
end

function arrangePrioritys(enemies)
	local priorityOrder = {
		[2] = {1,1,2,2,2},
		[3] = {1,1,2,3,3},
		[4] = {1,2,3,4,4},
		[5] = {1,2,3,4,5},
	}
	for i, enemy in ipairs(GetEnemyHeroes()) do
		SetPriority(priorityTable.AD_Carry, enemy, priorityOrder[enemies][1])
		SetPriority(priorityTable.AP,       enemy, priorityOrder[enemies][2])
		SetPriority(priorityTable.Support,  enemy, priorityOrder[enemies][3])
		SetPriority(priorityTable.Bruiser,  enemy, priorityOrder[enemies][4])
		SetPriority(priorityTable.Tank,     enemy, priorityOrder[enemies][5])
	end
end

function STSPAOnLoad()
	if #GetEnemyHeroes() <= 1 then
		PrintChat(" >> 娌℃湁瓒冲鐨勬晫浜猴紝鏃犻渶璁剧疆浼樺厛绾э紒")
	else
		TargetSelector(TARGET_LESS_CAST_PRIORITY, 0) -- Create a dummy target selector
		arrangePrioritys(#GetEnemyHeroes())
		PrintChat(" >> 浼樺厛瀹夋帓鐨勶紒")
	end
end

-- ############################################# 择攻击英雄优化 Simple TS Priority Arranger ################################################
	-- ############################################# 补刀标记 Minion Bars v1.1 ################################################
local smiteDamage = 0

function MinionBarsOnLoad()

	MinionBars = scriptConfig("[多合一]补刀标记设置", "MinionBars")
	MinionBars:addSubMenu("显示设置", "Drawing")
	MinionBars.Drawing:addParam("drawBars", "显示计量格数",  SCRIPT_PARAM_ONOFF, true)
	MinionBars.Drawing:addParam("drawLarge", "显示大小龙血量",  SCRIPT_PARAM_ONOFF, true)
	MinionBars.Drawing:addParam("drawMinions", "显示小兵补刀标记",  SCRIPT_PARAM_ONOFF, true)
	MinionBars.Drawing:addParam("drawJungle", "显示野怪补刀标记",  SCRIPT_PARAM_ONOFF, true)
	MinionBars.Drawing:addParam("drawKill", "显示补刀血量位置",  SCRIPT_PARAM_ONOFF, true)
	MinionBars.Drawing:addParam("drawKillOutline", "显示补刀血条变色",  SCRIPT_PARAM_ONOFF, true)
	MinionBars.Drawing:addParam("drawSmite", "显示当前惩戒数值", SCRIPT_PARAM_ONOFF, true)
	MinionBars.Drawing:addParam("drawSmiteOutline", "显示惩戒血条变色", SCRIPT_PARAM_ONOFF, true)

	MinionBars:addSubMenu("颜色设置", "Color")
	MinionBars.Color:addParam("lineColor", "线条颜色", SCRIPT_PARAM_COLOR, {255, 0, 0, 0})
	MinionBars.Color:addParam("killColor", "补刀颜色", SCRIPT_PARAM_COLOR, {255, 0, 255, 0})
	MinionBars.Color:addParam("smiteColor", "惩戒颜色", SCRIPT_PARAM_COLOR, {255, 0, 252, 255})

	MinionBars:addSubMenu("天赋设置", "Masteries")
	MinionBars.Masteries:addParam("butcherMastery", "屠夫",  SCRIPT_PARAM_ONOFF, false)
	MinionBars.Masteries:addParam("doubleEdgedSwordMastery", "双刃剑",  SCRIPT_PARAM_ONOFF, false)
	MinionBars.Masteries:addParam("arcaneBladeMastery", "奥术之刃",  SCRIPT_PARAM_ONOFF, false)
	--MinionBars.Masteries:addParam("devastatingStrikesMastery", "Devastating Strikes", SCRIPT_PARAM_SLICE, 0, 0, 3)
	-- Can't figure out how to factor in the armor/magic pen using CalcDamage.
end

function DrawRectangleAL(x, y, w, h, color) -- thanks to honda7's protracker script for this
	local Points = {}
	Points[1] = D3DXVECTOR2(math.floor(x), math.floor(y))
	Points[2] = D3DXVECTOR2(math.floor(x + w), math.floor(y))
	DrawLines2(Points, math.floor(h), color)
end

function OutLineBar(x, y, color)
	DrawRectangleAL(x, y - 3, 64, 1, color) -- Top
	DrawRectangleAL(x, y + 2, 64, 1, color) -- Bottom

	DrawRectangleAL(x, y, 1, 5, color) -- Left
	DrawRectangleAL(x + 63, y, 1, 5, color) -- Right
end

function OutLineBarLarge(x, y, color)
	DrawRectangleAL(x, y - 3, 125, 1, color) -- Top
	DrawRectangleAL(x, y + 2, 125, 1, color) -- Bottom

	DrawRectangleAL(x, y, 1, 5, color) -- Left
	DrawRectangleAL(x + 124, y, 1, 5, color) -- Right
end

function drawDetails(minion, lineColor, killColor, smiteColor, isJungle)
	if minion.charName == "TestCubeRender" or minion.charName == "TT_Buffplat_R" or minion.charName == "TT_Buffplat_L" then return end
	local barPos = GetUnitHPBarPos(minion)
	local myDamageToMinion = 0

	-- Calculate the damage we deal to a minion
	local myPhysicalDamage = myHero.addDamage + myHero.damage
	local myMagicDamage = 0
	if MinionBars.Masteries.arcaneBladeMastery == true then
		myMagicDamage = myHero.ap * 0.05
	end
	if MinionBars.Masteries.doubleEdgedSwordMastery == true then -- Does this apply to Arcane Blade damage?
		if myHero.range < 400 then
			myPhyscialDamage = myPhysicalDamage * 1.02
		else
			myPhyscialDamage = myPhysicalDamage * 1.015
		end
	end
	--if MinionBars.Masteries.devastatingStrikesMastery > 0 then
		--myHero.armorPenPercent = 0.06
		--minion.armor = minion.armor * (1.00 - (MinionBars.Masteries.devastatingStrikesMastery * 0.02))
		--minion.magicArmor = minion.magicArmor * (1.00 - (MinionBars.Masteries.devastatingStrikesMastery * 0.02))
	--end
	myDamageToMinion = myHero:CalcDamage(minion, myPhysicalDamage) + myHero:CalcMagicDamage(minion, myMagicDamage)
	if MinionBars.Masteries.butcherMastery == true then
		myDamageToMinion = myDamageToMinion + 2
	end
	-- Calculate some vars for drawing
	local hitsToKill = math.ceil(minion.maxHealth / myDamageToMinion)
	local barsToDraw = math.floor(minion.maxHealth / 100.0)
	local barDistance = 100.0 / (minion.maxHealth / 62.0)
	local myDamageDistance = myDamageToMinion / (minion.maxHealth / 62.0)
	local barsDrawn = 0
	local heightOffset = 3
	local barSize = 4
	local barWidth = 1
	barPos.x = barPos.x - 32
	barPos.y = barPos.y + heightOffset
	--DrawRectangleAL(barPos.x, barPos.y, barWidth, barSize, lineColor) -- Left
	--DrawRectangleAL(barPos.x + 62, barPos.y, barWidth, barSize, lineColor) -- Right
	local text = false
	-- Minions to ignore smite on = LesserWraith, YoungLizard, SmallGolem, Wolf
	--PrintChat(minion.charName)
	-- Draw the required bars at 100 hp per
	if isJungle == true and (minion.charName == "Dragon" or minion.charName == "Worm" or minion.charName == "TT_Spiderboss") then -- Dragon and baron have different sized hp bars.
		local healthDraw = 500.0
		if minion.charName == "Dragon" then
			barPos.x = barPos.x - 31
			barPos.y = barPos.y - 7
		elseif minion.charName == "Worm" then
			barPos.x = barPos.x - 31
			healthDraw = 1000.0
		elseif minion.charName == "TT_Spiderboss" then
			barPos.x = barPos.x - 31
		end
		barsToDraw = math.floor(minion.maxHealth / healthDraw)
		barDistance = healthDraw / (minion.maxHealth / 124.0)
		local mySmiteDistance = smiteDamage / (minion.maxHealth / 124.0)
		--PrintChat("Dragon/Baron")
		--DrawRectangleAL(barPos.x, barPos.y, barWidth, barSize, ARGB(255,252,252,252)) -- Left
		--DrawRectangleAL(barPos.x + 124, barPos.y, barWidth, barSize, ARGB(255,252,252,252)) -- Left

		-- Draw some crap for my own testing
		if text == true then
			DrawText(tostring(mySmiteDistance), 12, barPos.x + 60, barPos.y - 45, ARGB(255, 255, 0, 0))
			DrawText(tostring(myDamageDistance), 12, barPos.x + 60, barPos.y - 30, ARGB(255, 255, 0, 0))
			DrawText(tostring(barDistance), 12, barPos.x + 60, barPos.y - 15, ARGB(255, 255, 0, 0))
			DrawText(tostring(math.ceil(smiteDamage)), 12, barPos.x + 25, barPos.y - 45, ARGB(255, 255, 100, 100))
			DrawText(tostring(math.ceil(myDamageToMinion)), 12, barPos.x + 25, barPos.y - 30, ARGB(255, 255, 0, 255))
			DrawText(tostring(math.floor(minion.health)), 12, barPos.x + 25, barPos.y - 15, ARGB(255, 255, 255, 255))
			DrawText(tostring(hitsToKill), 12, barPos.x, barPos.y - 30, ARGB(255, 0, 255, 255))
			DrawText(tostring(barsToDraw), 12, barPos.x, barPos.y - 15, ARGB(255, 0, 255, 255))
		end
		local drawDistance = 0
		-- Draw the bars for jungle creeps.
		while barsDrawn ~= barsToDraw and barsToDraw ~= 0  and barsToDraw < 200 and MinionBars.Drawing.drawBars == true do -- If there are 32 bars, there reall is no reason to draw this, perhaps make a method for it
			drawDistance = drawDistance + barDistance
			if barsDrawn % 2 == 1 then
				DrawRectangleAL(barPos.x + drawDistance, barPos.y, barWidth + 1, barSize, lineColor)
				if minion.charName == "Worm" then
					DrawText(tostring(math.ceil(barsDrawn + 1)).."k", 10, barPos.x + drawDistance - 2, barPos.y + 2, ARGB(252,252,252,252))
				elseif minion.charName == "Dragon" or minion.charName == "TT_Spiderboss" then
					DrawText(tostring(math.ceil(barsDrawn / 2.0)).."k", 10, barPos.x + drawDistance - 2, barPos.y + 2, ARGB(252,252,252,252))

				end
			else
				DrawRectangleAL(barPos.x + drawDistance, barPos.y, barWidth, barSize, lineColor)
			end
			barsDrawn = barsDrawn + 1
		end
		if MinionBars.Drawing.drawSmite == true then
			DrawRectangleAL(barPos.x + mySmiteDistance, barPos.y, barWidth, barSize, smiteColor)
			-- Draw a backdrop and the damage the smite will do
			DrawRectangleAL(barPos.x + mySmiteDistance - 5, barPos.y - 8, barWidth + 19, barSize + 6, ARGB(255,0,0,0))
			DrawText(tostring(smiteDamage), 11, barPos.x + mySmiteDistance - 3, barPos.y - 13, smiteColor)
			if MinionBars.Drawing.drawSmiteOutline == true and smiteDamage >= minion.health then
				OutLineBarLarge(barPos.x, barPos.y, smiteColor)
			end
		end
		if MinionBars.Drawing.drawLarge == true then
			DrawRectangleAL(barPos.x + 57, barPos.y - 8, 35, 10, ARGB(255, 0, 0, 0))
			DrawText(tostring(math.floor(minion.health)), 12, barPos.x + 60, barPos.y - 14, ARGB(255, 255, 255, 255))
		end
	else
		-- Draw some crap for my own testing
		if text == true then
			DrawText(tostring(barDistance), 12, barPos.x + 40, barPos.y - 15, ARGB(255, 0, 255, 255))
			DrawText(tostring(myDamageDistance), 12, barPos.x + 40, barPos.y - 30, ARGB(255, 255, 0, 0))
			DrawText(tostring(math.ceil(myDamageToMinion)), 12, barPos.x + 20, barPos.y - 30, ARGB(255, 255, 0, 255))
			DrawText(tostring(math.floor(minion.health)), 12, barPos.x + 20, barPos.y - 15, ARGB(255, 255, 255, 255))
			DrawText(tostring(hitsToKill), 12, barPos.x, barPos.y - 30, ARGB(255, 0, 255, 255))
			DrawText(tostring(barsToDraw), 12, barPos.x, barPos.y - 15, ARGB(255, 0, 255, 255))
		end
		--=================================================
		local drawDistance = 0
		while barsDrawn ~= barsToDraw and barsToDraw ~= 0  and barsToDraw < 50 and MinionBars.Drawing.drawBars == true do -- If there are 32 bars, there reall is no reason to draw this, perhaps make a method for it
			drawDistance = drawDistance + barDistance
			if barsToDraw > 20 then -- If the minion HP is higher than 2000, draw lines at 500 and 1000
				if barsDrawn % 5 == 4 then
					if barsDrawn % 10 == 9 then
						DrawRectangleAL(barPos.x + drawDistance, barPos.y, barWidth + 1, barSize, lineColor)
					else
						DrawRectangleAL(barPos.x + drawDistance, barPos.y, barWidth, barSize, lineColor)
					end
				end
			else
				DrawRectangleAL(barPos.x + drawDistance, barPos.y, barWidth, barSize, lineColor)
			end
			barsDrawn = barsDrawn + 1
		end
		-- Draw smite here so the outline of kill damage overlays smite overlay if on.
		-- LesserWraith, YoungLizard, SmallGolem, Wolf
		if isJungle == true and MinionBars.Drawing.drawSmite == true and (minion.charName ~= "LesserWraith" and minion.charName ~= "YoungLizard" and minion.charName ~= "SmallGolem" and minion.charName ~= "Wolf" and minion.charName ~= "TT_NWraith2" and minion.charName ~= "TT_NWolf2" and minion.charName ~= "TT_NGolem2")then
			local mySmiteDistance = smiteDamage / (minion.maxHealth / 62.0)
			DrawRectangleAL(barPos.x + mySmiteDistance, barPos.y, barWidth, barSize, smiteColor)
			DrawRectangleAL(barPos.x + mySmiteDistance - 5, barPos.y - 8, barWidth + 19, barSize + 6, ARGB(255,0,0,0))
			DrawText(tostring(smiteDamage), 11, barPos.x + mySmiteDistance - 3, barPos.y - 13, smiteColor)
			if MinionBars.Drawing.drawSmiteOutline == true and smiteDamage >= minion.health then
				OutLineBar(barPos.x, barPos.y, smiteColor)
			end
		end
		-- Finish by drawing hero damage
		if MinionBars.Drawing.drawKill == true then
			DrawRectangleAL(barPos.x + myDamageDistance, barPos.y, barWidth, barSize, killColor)
		end
		if myDamageToMinion > minion.health and MinionBars.Drawing.drawKillOutline == true then
			OutLineBar(barPos.x, barPos.y, killColor)
		end
	end
end


function MinionBarsOnDraw()
	local color = ARGB(MinionBars.Color.lineColor[1], MinionBars.Color.lineColor[2],MinionBars.Color.lineColor[3],MinionBars.Color.lineColor[4])
	local colorKill = ARGB(MinionBars.Color.killColor[1], MinionBars.Color.killColor[2],MinionBars.Color.killColor[3],MinionBars.Color.killColor[4])
	local colorSmite = ARGB(MinionBars.Color.smiteColor[1], MinionBars.Color.smiteColor[2],MinionBars.Color.smiteColor[3],MinionBars.Color.smiteColor[4])
	if MinionBars.Drawing.drawMinions == true then
		local enemyMinions = minionManager(MINION_ENEMY, 2000, myHero, MINION_SORT_HEALTH_ASC).objects
		for i,minion in pairs(enemyMinions) do
			drawDetails(minion, color, colorKill, colorSmite, false)
		end
	end
	if MinionBars.Drawing.drawJungle == true then
		if MinionBars.Drawing.drawSmite == true then
			smiteDamage = math.max(20 * myHero.level + 370, 30 * myHero.level + 330, 40 * myHero.level + 240, 50 * myHero.level + 100)
		end
		local jungleMinions = minionManager(MINION_JUNGLE, 2000, myHero, MINION_SORT_HEALTH_ASC).objects
		for i,creep in pairs(jungleMinions) do
			drawDetails(creep, color, colorKill, colorSmite, true)
		end
	end
end

-- ############################################# 补刀标记 Minion Bars v1.1 ################################################
-- ############################################# 闪现助手 Flash Assistant ################################################

local timeStamp=GetTickCount()
local Recall = false

function FlashCheck()
	if not(myHero:GetSpellData(SUMMONER_1).name:find("SummonerFlash") or myHero:GetSpellData(SUMMONER_2).name:find("SummonerFlash") or myHero.charName=="Ezreal") then 
		return false 
	end
end
function getWardSlot()
    local JumpingSlot = nil
    if GetInventorySlotItem(2045) ~= nil and myHero:CanUseSpell(GetInventorySlotItem(2045)) == READY then
        JumpingSlot = GetInventorySlotItem(2045)
    elseif GetInventorySlotItem(2049) ~= nil and myHero:CanUseSpell(GetInventorySlotItem(2049)) == READY then
        JumpingSlot = GetInventorySlotItem(2049)
    elseif myHero:CanUseSpell(ITEM_7) == READY and myHero:getItem(ITEM_7).id == 3340 or myHero:CanUseSpell(ITEM_7) == READY and myHero:getItem(ITEM_7).id == 3350 or myHero:CanUseSpell(ITEM_7) == READY and myHero:getItem(ITEM_7).id == 3361 or myHero:CanUseSpell(ITEM_7) == READY and myHero:getItem(ITEM_7).id == 3362 then
        JumpingSlot = ITEM_7
    elseif GetInventorySlotItem(2044) ~= nil and myHero:CanUseSpell(GetInventorySlotItem(2044)) == READY then
        JumpingSlot = GetInventorySlotItem(2044)
    elseif GetInventorySlotItem(2043) ~= nil and myHero:CanUseSpell(GetInventorySlotItem(2043)) == READY then
        JumpingSlot = GetInventorySlotItem(2043)
		end
	return JumpingSlot
end

function doTheFlash()
	if GetSpecialHeroReady()==true then
		CastSpell(GetSpecialHeroSpell(), flashFinalSpot.x, flashFinalSpot.z)
	else 
		if not(IsWallOfGrass(myHero.pos)) and timeStamp<GetTickCount()-50 then
			CastSpell(flashSlot, flashFinalSpot.x, flashFinalSpot.z)
		end
	end
	if FlashConfig.doRecall then
		CastSpell(RECALL)
	end
	myHero:StopPosition()
end
function FlashOnDraw()
	if not FlashCheck() then return end
	for i, flashSpot in pairs(Spots) do
		if GetDistance(flashSpot) < 2000 then
		DrawCircle3D(flashSpot.x, flashSpot.y, flashSpot.z, 50, 5, 0xFFFF0000, 50)
			if myHero:CanUseSpell(flashSlot)==READY or (GetSpecialHeroReady()==true) then
				flashFinalSpot=SpotsFinal[i]
				DrawLine3D(flashSpot.x, flashSpot.y, flashSpot.z, flashFinalSpot.x, flashFinalSpot.y, flashFinalSpot.z, 3, 0xFFFF0000)
			end
		end
	end
end
function GetSpecialHeroSpell()
	if myHero.charName=="Ezreal" then
		return _E
	elseif myHero.charName=="Shaco" then
		return _Q
	else
		return
	end
end

function GetSpecialHeroReady()
	if myHero.charName=="Ezreal" and myHero:CanUseSpell(_E)==READY and myHero:GetSpellData(_E).mana <= myHero.mana then
		return true
	elseif myHero.charName=="Shaco" and myHero:CanUseSpell(_Q)==READY and myHero:GetSpellData(_Q).mana <= myHero.mana then
		return true
	else
		return false
	end
end

function FlashOnTick()
	if not FlashCheck() then return end
    if FlashConfig.flashkey and (myHero:CanUseSpell(flashSlot) == READY or GetSpecialHeroReady()==true) then
        for j, flashSpot in pairs(Spots) do
          if GetDistance(flashSpot) < 50 then
						flashFinalSpot=SpotsFinal[j]
						if FlashConfig.ward then
							wardSlot=getWardSlot()
							if wardSlot and not(getVision(flashFinalSpot.x,flashFinalSpot.z)) then
								CastSpell(wardSlot,flashFinalSpot.x,flashFinalSpot.z)
							end
						end
						if getValidity(flashFinalSpot.x,flashFinalSpot.z) then
							doTheFlash()  
							timeStamp=GetTickCount()
						end
					else
					end				
				end
end --
	modifier=700
	if not(FlashConfig.recall) then
		modifier=5000
	end
	if FlashConfig.flashkey and GetTickCount()>timeStamp+modifier and Recall==false then
		myHero:MoveTo(mousePos.x, mousePos.z)
	end
			end
function FlashOnCreateObj(obj)
	if not FlashCheck() then return end
	if obj.name:find("TeleportHome.troy") then
		if GetDistance(obj, myHero) <= 70 then
			Recall = true
		end
	end
end

function FlashOnDeleteObj(obj)
	if not FlashCheck() then return end
	if obj.name:find("TeleportHome.troy") then
		if GetDistance(obj, myHero) <= 70 then
			Recall = false
		end
	end
end

function getValidity(x,z)
    for i = 1, heroManager.iCount, 1 do
        local hero = heroManager:getHero(i)
        if hero and hero.team~=myHero.team then
          if IsWallOfGrass(hero.pos) and GetDistance(Vector(x,0,z),hero)<680 then
                return false
            end
        end
    end
    return true
end

function getVision(x, z)
    for i = 1, objManager.maxObjects, 1 do
        local object = objManager:getObject(i)
				mypoint = Vector(x,0,z)
        if object and (GetDistance(mypoint,object) < 680) then
            if IsWallOfGrass(object.pos) and object.type=="obj_AI_Minion" then
                return true
            end
        end
    end
    return false
end

function Initialize()
	Spots = {
				{ x = 5976, y = 40, z = 12584},
				{ x = 8145, y = 54, z = 1915},
				{ x = 5815, y = 53, z = 11397},
				{ x = 8135, y = 57, z = 3058},
        { x = 11530, y = 53, z = 4733},
        { x = 2485, y = 53, z = 9683},
        { x = 9963, y = 55, z = 6435},
        { x = 4123, y = 52, z = 7979},
		{ x = 3935, y = 53, z = 7214},
		{ x = 8926, y = 64, z = 2402},
		{ x = 5718, y = 53, z = 3502},
		{ x = 7052, y = 55, z = 3223},
		{ x = 7059, y = 55, z = 3081},
		{ x = 5054, y = 41, z = 11998},
		{ x = 6966, y = 53, z = 11282},
		{ x = 6959, y = 53, z = 11416},
		{ x = 8265, y = 50, z = 11103},
		{ x = 9949, y = 55, z = 7249},
		{ x = 11361, y = -62, z = 4257},
		{ x = 5240, y = -65, z = 9233},
		{ x = 5405, y = 55, z = 9926},
		{ x = 8655, y = -64, z = 5195},
        { x = 8583, y = 55, z = 4408},
		{ x = 2788, y = -65, z = 10204},
				{ x = 3513, y = 55, z = 7555}, 
				{ x = 10595, y = 54, z = 6915}, 
				{ x = 5924, y = 51, z = 4975}, 
				{ x = 8042, y = 53, z = 9542}, 
	}
	SpotsFinal = {
					{ x = 5571, y = 40, z = 12561},
					{ x = 8537, y = 55, z = 1963},
					{ x = 6109, y = 54, z = 11204},
					{ x = 7867, y = 56, z = 3293},
          { x = 11885, y = 45, z = 4933},
          { x = 2171, y = 53, z = 9569},
					{ x = 9614, y = 51, z = 6339},
          { x = 4446, y = 34, z = 8148},
		{ x = 4273, y = 54, z = 7017},
		{ x = 8875, y = 55, z = 2061},
		{ x = 5375, y = 54, z = 3293},
		{ x = 7391, y = 55, z = 3297},
		{ x = 6729, y = 55, z = 2911},
		{ x = 5082, y = 40, z = 12374},
		{ x = 6619, y = 54, z = 11165},
		{ x = 7303, y = 52, z = 11525},
		{ x = 8604, y = 54, z = 11161},
		{ x = 9665, y = 54, z = 7497},
		{ x = 11435, y = -55, z = 3881},
		{ x = 4942, y = -63, z = 8970},
		{ x = 5772, y = 54, z = 10033},
		{ x = 8935, y = -64, z = 5417},
					{ x = 8267, y = 55, z = 4415},
		{ x = 2685, y = -64, z = 10567},
					{ x = 3153, y = 56, z = 7534}, 
					{ x = 10936, y = 54, z = 6865}, 
					{ x = 6101, y = 51, z = 4621}, 
					{ x = 7917, y = 53, z = 9885}, 
	}
end

function FlashOnLoad()
	if not FlashCheck() then return end
	myHero = GetMyHero()
	FlashConfig = scriptConfig("[多合一]神奇闪现助手", "Flash Assistant")
	FlashConfig:addParam("flashkey", "闪现助手按键", SCRIPT_PARAM_ONKEYDOWN, false, GetKey("T"))
	FlashConfig:addParam("recall", "闪现后回城", SCRIPT_PARAM_ONOFF, true)
    FlashConfig:addParam("ward", "闪现前先在草丛插眼", SCRIPT_PARAM_ONOFF, true)
	if myHero:GetSpellData(SUMMONER_1).name:find("SummonerFlash") then
		flashSlot = SUMMONER_1
	elseif myHero:GetSpellData(SUMMONER_2).name:find("SummonerFlash") then
		flashSlot = SUMMONER_2
	else
		flashSlot = nil
	end
	Initialize()
end
-- ############################################# 闪现助手 Flash Assistant ################################################
-- ############################################# I Hate CC v2.0 ################################################

function IHateCCOnLoad()
	--PrintChat(">> I Hate CC v2.0")
	QssConfig = scriptConfig("[多合一]解除控制设置 - Free", "IHateCC")
	QssConfig:addParam("igniteqss", "点燃效果", SCRIPT_PARAM_ONOFF, false)
	QssConfig:addParam("exhaustqss", "虚弱效果", SCRIPT_PARAM_ONOFF, false)
	QssConfig:addParam("Silenceqss", "沉默效果", SCRIPT_PARAM_ONOFF, false)
	QssConfig:addParam("stunqss", "眩晕效果", SCRIPT_PARAM_ONOFF, false)
	QssConfig:addParam("fearqss", "恐惧效果", SCRIPT_PARAM_ONOFF, false)
	QssConfig:addParam("tauntqss", "嘲讽效果", SCRIPT_PARAM_ONOFF, false)
	QssConfig:addParam("grievousqss", "重伤效果", SCRIPT_PARAM_ONOFF, false)
	QssConfig:addParam("luxqss", "光辉女郎 Q", SCRIPT_PARAM_ONOFF, false)
	QssConfig:addParam("teemoqss", "迅捷斥候 Q", SCRIPT_PARAM_ONOFF, false)
	QssConfig:addParam("morganaqss", "堕落天使 Q", SCRIPT_PARAM_ONOFF, false)
	QssConfig:addParam("ryzeqss", "流浪法师 W", SCRIPT_PARAM_ONOFF, false)
	QssConfig:addParam("witherqss", "沙漠死神 W", SCRIPT_PARAM_ONOFF, false)
	QssConfig:addParam("caitqss", "皮城女警 W", SCRIPT_PARAM_ONOFF, false)
	QssConfig:addParam("luluqss", "仙灵女巫 W", SCRIPT_PARAM_ONOFF, false)
	QssConfig:addParam("nunuqss", "雪人骑士 E", SCRIPT_PARAM_ONOFF, false)
	QssConfig:addParam("sonaqss", "琴瑟仙女 R", SCRIPT_PARAM_ONOFF, false)
	QssConfig:addParam("asheqss", "寒冰射手 R", SCRIPT_PARAM_ONOFF, false)
	QssConfig:addParam("fizzqss", "潮汐海灵 R", SCRIPT_PARAM_ONOFF, false)
	QssConfig:addParam("mordeqss", "金属大师 R", SCRIPT_PARAM_ONOFF, false)
	QssConfig:addParam("skarnerqss", "水晶先锋 R", SCRIPT_PARAM_ONOFF, false)
	QssConfig:addParam("zileanqss", "时光守护者 E", SCRIPT_PARAM_ONOFF, false)
	QssConfig:addParam("amumuqss", "殇之木乃伊 R", SCRIPT_PARAM_ONOFF, false)
	QssConfig:addParam("suppressionqss", "嗜血猎手/虚空先知 R", SCRIPT_PARAM_ONOFF, false)
	cleanseslot2 = nil
	if player:GetSpellData(SUMMONER_1).name == "SummonerBoost" then
		cleanseslotS = SUMMONER_1
	elseif player:GetSpellData(SUMMONER_2).name == "SummonerBoost" then
		cleanseslotS = SUMMONER_2
	else
		cleanseslotS = nil
	end
	if player.charName == "Gangplank" then
		cleanseslotS2 = SPELL_2
	elseif player.charName == "Olaf" then
		cleanseslotS2 = SPELL_4
	elseif player.charName == "Alistar" then
		cleanseslotS2 = SPELL_4
	else
		cleanseslotS2 = nil
	end
end

function IHateCCOnTick()
	if TBConfig.IHateCC == false then return end
	if GetInventorySlotItem(3140) ~= nil then
		cleanseslot2 = GetInventorySlotItem(3140)
	elseif GetInventorySlotItem(3139) ~= nil then
		cleanseslot2 = GetInventorySlotItem(3139)
	elseif GetInventorySlotItem(3222) ~= nil then
		cleanseslot2 = GetInventorySlotItem(3222)
	else
		cleanseslot2 = nil
	end
	if cleanseslotS2 and GetMyHero():CanUseSpell(cleanseslotS2) == READY then
		cleanseslot = cleanseslotS2
	elseif cleanseslot2 and GetMyHero():CanUseSpell(cleanseslot2) == READY then
		cleanseslot = cleanseslot2
	elseif cleanseslotS and GetMyHero():CanUseSpell(cleanseslotS) == READY then
		cleanseslot = cleanseslotS
	end
	if cleanseslot == nil then return end
	for i = 1, player.buffCount, 1 do
		local buff = player:getBuff(i)
		if buff.valid then
			if buff.name == "SummonerDot" and QssConfig.igniteqss then
				CastSpell(cleanseslot)
			end
			if buff.name == "SummonerExhaust" and QssConfig.exhaustqss then
				CastSpell(cleanseslot)
			end
			if buff.name == "MordekaiserChildrenOfTheGrave" and QssConfig.mordeqss then
				CastSpell(cleanseslot)
			end
			if buff.name == "SkarnerImpale" and QssConfig.skarnerqss then
				CastSpell(cleanseslot)
			end
			if buff.name == "suppression" and QssConfig.suppressionqss then
				CastSpell(cleanseslot)
			end
			if buff.name == "Silence" and  QssConfig.Silenceqss then
				CastSpell(cleanseslot)
			end
			if (buff.name == "stun" or buff.name == "Stun") and QssConfig.stunqss then
				CastSpell(cleanseslot)
			end
			if buff.name == "Fear" and QssConfig.fearqss then
				CastSpell(cleanseslot)
			end
			if buff.name == "taunt" and QssConfig.tauntqss then
				CastSpell(cleanseslot)
			end
			if buff.name == "LuxLightBindingMis" and QssConfig.luxqss then
				CastSpell(cleanseslot)
			end
			if buff.name == "Wither" and QssConfig.witherqss then
				CastSpell(cleanseslot)
			end
			if buff.name == "SonaCrescendo" and QssConfig.sonaqss then
				CastSpell(cleanseslot)
			end
			if buff.name == "RunePrison" and QssConfig.ryzeqss then
				CastSpell(cleanseslot)
			end
			if buff.name == "DarkBindingMissile" and QssConfig.morganaqss then
				CastSpell(cleanseslot)
			end
			if buff.name == "IceBlast" and QssConfig.nunuqss then
				CastSpell(cleanseslot)
			end
			if buff.name == "timewarpslow" and QssConfig.zileanqss then
				CastSpell(cleanseslot)
			end
			if buff.name == "caitlynyordletrapdebuff" and QssConfig.caitqss then
				CastSpell(cleanseslot)
			end
			if buff.name == "CurseoftheSadMummy" and QssConfig.amumuqss then
				CastSpell(cleanseslot)
			end
			if buff.name == "EnchantedCrystalArrow" and QssConfig.asheqss then
				CastSpell(cleanseslot)
			end
			if buff.name == "BlindingDart" and QssConfig.teemoqss then
				CastSpell(cleanseslot)
			end
			if buff.name == "grievouswounds" and QssConfig.grievousqss then
				CastSpell(cleanseslot)
			end
			if buff.name == "LuluWTwo" and QssConfig.luluqss then
				CastSpell(cleanseslot)
			end
			if buff.name == "fizzmarinerdoombomb" and QssConfig.fizzqss then
				CastSpell(cleanseslot)
			end
		end
	end
end

-- ############################################# I Hate CC v2.0 ################################################
	-- ############################################# Anti Ward v3.16 ################################################

local blackColor  = 4278190080
local purpleColor = 4294902015
local greenColor  = 4278255360
local aquaColor = ARGB(255,102, 205, 170)
local whiteColor = ARGB(255,255, 255, 255)
local grayColor = ARGB(255, 200, 200, 200)

function AntiWardOnLoad()
	placedWards = {}
	AntiWard = scriptConfig("[多合一]眼位陷阱计时", "AntiWard")
	AntiWard:addParam("OwnTeam", "显示友方标记", SCRIPT_PARAM_ONOFF, false)
	AntiWard:addParam("ShowPinks", "显示真眼计时", SCRIPT_PARAM_ONOFF, true)
	AntiWard:addParam("ShowTraps", "显示陷阱计时", SCRIPT_PARAM_ONOFF, true)
	AntiWard:addParam("sep", "", SCRIPT_PARAM_INFO,"" )
	AntiWard:addParam("Manual", "手动放置/删除标记", SCRIPT_PARAM_ONOFF, false)
	AntiWard:addParam("DeleteWard", "删除标记", SCRIPT_PARAM_ONKEYDOWN, false, 115)
	AntiWard:addParam("PutWard1", "放置1分钟的标记", SCRIPT_PARAM_ONKEYDOWN, false, 97)
	AntiWard:addParam("PutWard2", "放置2分钟的标记", SCRIPT_PARAM_ONKEYDOWN, false, 98)
	AntiWard:addParam("PutWard3", "放置3分钟的标记", SCRIPT_PARAM_ONKEYDOWN, false, 99)
	TriggerTrap()
end

local _allyHeroes

function GetAllyHeroes()
	if _allyHeroes then return _allyHeroes end
	_allyHeroes = {}
	for i = 1, heroManager.iCount do
		local hero = heroManager:GetHero(i)
		if hero.team == myHero.team then
			table.insert(_allyHeroes, hero)
		end
	end
	return setmetatable(_allyHeroes,{
		__newindex = function(self, key, value)
			error("Adding to AllyHeroes is not granted. Use table.copy.")
		end,
	})
end

function TriggerTrap()
  for ID, ward in pairs(placedWards) do
	for i = 1, heroManager.iCount do
	  local hero = heroManager:GetHero(i)
	  if ward.trap and ward.team ~= hero.team and GetDistance(ward, hero) <= ward.triggerRange then
		placedWards[ID] = nil
	  end
	end
  end
  DelayAction(TriggerTrap, 0.2)
end

function AntiWardOnTick()
  if AntiWard.Manual then
	if AntiWard.DeleteWard then DeleteWard(mousePos.x, mousePos.y, mousePos.z) end
	if AntiWard.PutWard1 then PutWard(mousePos.x, mousePos.y, mousePos.z, 1 * 60) end
	if AntiWard.PutWard2 then PutWard(mousePos.x, mousePos.y, mousePos.z, 2 * 60) end
	if AntiWard.PutWard3 then PutWard(mousePos.x, mousePos.y, mousePos.z, 3 * 60) end
  end
end

function AntiWardOnDraw()
	for ID, ward in pairs(placedWards) do
		if (GetTickCount() - ward.spawnTime) > ward.duration + 5000 or (ward.object and ward.object.health == 0) then
			placedWards[ID] = nil
		elseif (ward.team == TEAM_ENEMY or AntiWard.OwnTeam) and (ward.duration < math.huge or AntiWard.ShowPinks) and (not ward.trap or AntiWard.ShowTraps) then
			local minimapPosition = GetMinimap(ward)
			DrawTextWithBorder('.', 60, minimapPosition.x - 6.5, minimapPosition.y - 45.5, ward.color, blackColor)
			local x, y, onScreen = get2DFrom3D(ward.x, ward.y, ward.z)
			DrawTextWithBorder(TimerText((ward.duration - (GetTickCount() - ward.spawnTime)) / 1000), 20, x - 15, y - 11, ward.color, blackColor)
	  if ward["creator"] then DrawTextWithBorder(ward["creator"].charName, 16, x - 20, y + 10, whiteColor, blackColor) end
			DrawCircle2(ward.x, ward.y, ward.z, 90, ward.color)
			if IsKeyDown(16) then
				DrawCircle2(ward.x, ward.y, ward.z, ward.visionRange, ward.color)
			end
		end
	end
end

function DrawTextWithBorder(textToDraw, textSize, x, y, textColor, backgroundColor)
	DrawText(textToDraw, textSize, x + 1, y, backgroundColor)
	DrawText(textToDraw, textSize, x - 1, y, backgroundColor)
	DrawText(textToDraw, textSize, x, y - 1, backgroundColor)
	DrawText(textToDraw, textSize, x, y + 1, backgroundColor)
	DrawText(textToDraw, textSize, x , y, textColor)
end

function DrawCircleNextLvl(x, y, z, radius, width, color, chordlength)
	radius = radius or 300
	quality = math.max(8,math.floor(180/math.deg((math.asin((chordlength/(2*radius)))))))
	quality = 2 * math.pi / quality
	radius = radius*.92
	local points = {}
	for theta = 0, 2 * math.pi + quality, quality do
		local c = WorldToScreen(D3DXVECTOR3(x + radius * math.cos(theta), y, z - radius * math.sin(theta)))
		points[#points + 1] = D3DXVECTOR2(c.x, c.y)
	end
	DrawLines2(points, width or 1, color or 4294967295)
end

function DrawCircle2(x, y, z, radius, color)
	local vPos1 = Vector(x, y, z)
	local vPos2 = Vector(cameraPos.x, cameraPos.y, cameraPos.z)
	local tPos = vPos1 - (vPos1 - vPos2):normalized() * radius
	local sPos = WorldToScreen(D3DXVECTOR3(tPos.x, tPos.y, tPos.z))
	if OnScreen({ x = sPos.x, y = sPos.y }, { x = sPos.x, y = sPos.y })  then
		DrawCircleNextLvl(x, y, z, radius, 1, color, 75)
	end
end

function get2DFrom3D(x, y, z)
	local pos = WorldToScreen(D3DXVECTOR3(x, y, z))
	return pos.x, pos.y, OnScreen(pos.x, pos.y)
end

function FindObjAt(x, y, z, distance, timediff, timestart)
  if not distance then distance = 1 end
  if not timediff then timediff = math.huge end
  if not timestart then timestart = GetTickCount() end
  for networkID, ward in pairs(placedWards) do
	if GetDistance(ward, Vector(x, y, z)) < distance and timestart - ward.spawnTime < timediff then return networkID end
  end
  return nil
end

function GetLandingPos(CastPoint)
	local wall = IsWall(D3DXVECTOR3(CastPoint.x, CastPoint.y, CastPoint.z))
	local Point = Vector(CastPoint)
	local StartPoint = Vector(Point)
		if not wall then return Point end
	for i = 0, 700, 10--[[Decrease for better precision, increase for less fps drops:]] do
		for theta = 0, 2 * math.pi + 0.2, 0.2 --[[Same :)]] do
			local c = Vector(StartPoint.x + i * math.cos(theta), StartPoint.y, StartPoint.z + i * math.sin(theta))
			if not IsWall(D3DXVECTOR3(c.x, c.y, c.z)) then
				return c
			end
		end
	end
	return Point
end

local types = {
  { duration=60 * 1000, sightRange=1350, triggerRange=70, charName="SightWard", name="YellowTrinket", spellName="RelicSmallLantern", color = aquaColor }, -- 1 minute trinket
  { duration=120 * 1000, sightRange=1350, triggerRange=70, charName="SightWard", name="YellowTrinketUpgrade", spellName="RelicLantern", color = aquaColor }, -- 2 minute trinket
  { duration=180 * 1000, sightRange=1350, triggerRange=70, charName="SightWard", name="SightWard", spellName="SightWard", color = greenColor }, -- 3 minute green ward
  { duration=180 * 1000, sightRange=1350, triggerRange=70, charName="SightWard", name="SightWard", spellName="wrigglelantern", color = greenColor }, -- 3 minute lantern ward
  { duration=180 * 1000, sightRange=1350, triggerRange=70, charName="VisionWard", name="SightWard", spellName="ItemGhostWard", color = greenColor }, -- 3 minute item ward
  { duration=math.huge, sightRange=1350, triggerRange=70, charName="VisionWard", name="VisionWard", spellName="VisionWard", color = purpleColor }, -- pink ward
  { duration=600 * 1000, sightRange=405, triggerRange=115, charName="Noxious Trap", name="TeemoMushroom", spellName="BantamTrap", color = whiteColor, trap = true }, -- teemo mushroom
  { duration=60 * 1000, sightRange=690, triggerRange=300, charName="Jack In The Box", name="ShacoBox", spellName="JackInTheBox", color = whiteColor, trap = true }, -- shaco trap
  { duration=240 * 1000, sightRange=150, triggerRange=150, charName="Cupcake Trap", name="CaitlynTrap", spellName="CaitlynYordleTrap", color = whiteColor, trap = true }, -- caitlyn trap
  { duration=240 * 1000, sightRange=0, triggerRange=150, charName="Noxious Trap", name="Nidalee_Spear", spellName="Bushwhack", color = whiteColor, trap = true } -- nidalee trap
}

function AntiWardOnDeleteObj(object)
	if object and object.name and object.valid and object.type == "obj_AI_Minion" then
	for _,type in ipairs(types) do
	  if object.name == type.charName and object.charName == type.name then
		local ID = FindObjAt(object.x, object.y, object.z)
		if ID and object.health == 0 then
		  placedWards[ID] = nil
		end
	  end
	end
  end
end

COOLDOWN = GetGameTimer()

function PutWard(x, y, z, time)
  if GetGameTimer() - COOLDOWN < 1 then return end
  local ID = FindObjAt(x, y, z, 150)
  if ID == nil then
	placedWards["user:" .. GetTickCount()] = { x = x, y = y, z = z, visionRange = 1350, color = grayColor, spawnTime = GetTickCount(), duration = time*1000, creator = nil, team = nil }
  end
  COOLDOWN = GetGameTimer()
end

function DeleteWard(x, y, z)
  if GetGameTimer() - COOLDOWN < 1 then return end
  local ID = FindObjAt(x, y, z, 100)
  if ID then placedWards[ID] = nil end
  COOLDOWN = GetGameTimer()
end

function AntiWardOnCreateObj(object)
	if object and object.name and object.valid and object.type == "obj_AI_Minion" then
	DelayAction(function(object, timer, gtimer)
	  for _,type in ipairs(types) do
		if object.name == type.charName and object.charName == type.name then
		  local ID = FindObjAt(object.x, object.y, object.z, 1100, 500, timer)
		  if object.health > 0 then
			if ID == nil then
			  placedWards["create:" .. GetTickCount()] = { x = object.x, y = object.y, z = object.z, visionRange = type.sightRange, color = type.color, object = object,
				triggerRange = type.triggerRange, spawnTime = timer, duration = type.duration, creator = nil, team = object.team, trap = type.trap }
			else
			  placedWards[ID].x = object.x
			  placedWards[ID].y = object.y
			  placedWards[ID].z = object.z
			end
		  end
		end
	  end
	end, 1, { object, GetTickCount(), GetGameTimer() } )
  end
end

function AntiWardOnProcessSpell(unit, spell)
  if unit.type == "obj_AI_Hero" then
		for _,type in ipairs(types) do
			if type.spellName == spell.name then
		local wardPos = GetLandingPos(spell.endPos)
		if FindObjAt(wardPos.x, wardPos.y, wardPos.z) == nil then
				placedWards["spell:" .. GetTickCount()] = { x = wardPos.x, y = wardPos.y, z = wardPos.z, visionRange = type.sightRange, color = type.color, triggerRange = type.triggerRange, spawnTime = GetTickCount(), duration = type.duration, creator = unit, team = unit.team, trap = type.trap }
		end
			end
		end
  end
end


-- ############################################# Anti Ward v3.16 ################################################
-- ############################################# Auto Ignite v1.2 ################################################

local iSlot = nil

function AutoIgniteOnLoad()
	AIConfig = scriptConfig("[多合一]自动点燃设置", "AutoIgnite")
	AIConfig:addParam("useIgnite", "自动点燃击杀", SCRIPT_PARAM_ONOFF, true)
	AIConfig:addParam("doubleI", "禁止重复点燃", SCRIPT_PARAM_ONOFF, true)
	AIConfig:permaShow("useIgnite")
	if myHero:GetSpellData(SUMMONER_1).name:find("SummonerDot") then iSlot = SUMMONER_1
		elseif myHero:GetSpellData(SUMMONER_2).name:find("SummonerDot") then iSlot = SUMMONER_2
			else iSlot = nil
	end
end

function AutoIgniteOnTick()
	if AIConfig.useIgnite then
		local iDmg = 0
		if iSlot ~= nil and myHero:CanUseSpell(iSlot) == READY then
			for i = 1, heroManager.iCount, 1 do
				local target = heroManager:getHero(i)
				if ValidTarget(target) then
					iDmg = 50 + 20 * myHero.level
					if target ~= nil and target.team ~= myHero.team and not target.dead and target.visible and (GetDistance(target) > 450 and GetDistance(target) < 600) and target.health < iDmg then
						if AIConfig.doubleI and not TargetHaveBuff("SummonerDot", target) then
							CastSpell(iSlot, target)
						elseif not AIConfig.doubleI then
							CastSpell(iSlot, target)
						end
					end
				end
			end
		end
	end
end

-- ############################################# Auto Ignite v1.2 ################################################


    -- ############################################# LOW AWARENESS ##############################################
     
    local alertActive = true
    local championTable = {}
    local playerTimer = {}
    local playerDrawer = {}
    local player = GetMyHero()
    --showErrorsInChat = false
    --showErrorTraceInChat = false
     
    nextTick = 0 
function LowAwarenessOnTick()   
		if nextTick > GetTickCount() then 
		return 
		end   
		nextTick = GetTickCount() + 250 --(100 is the delay)      
		
        local tick = GetTickCount()
        if alertActive == true then
            for i = 1, heroManager.iCount, 1 do
            local object = heroManager:getHero(i)
                if object.team ~= player.team and object.dead == false then
                    if object.visible == true and player:GetDistance(object) < 2500 then
                        if playerTimer[i] == nil then
                            PrintChat(string.format("<font color='#FF0000'> >> !!!璀﹀憡: %s</font>", object.charName))
                            PingSignal(PING_FALLBACK,object.x,object.y,object.z,2)
                            PingSignal(PING_FALLBACK,object.x,object.y,object.z,2)
                            PingSignal(PING_FALLBACK,object.x,object.y,object.z,2)
                            table.insert(championTable, object )
                            playerDrawer[i] = tick
                        end
                        playerTimer[ i ] = tick
                        if (tick - playerDrawer[i]) > 5000 then
                            for ii, tableObject in ipairs(championTable) do
                                if tableObject.charName == object.charName then
                                    table.remove(championTable, ii)
                                end
                            end
                        end
                    else
                        if playerTimer[i] ~= nil and (tick - playerTimer[i]) > 10000 then
                            playerTimer[i] = nil
                            for ii, tableObject in ipairs(championTable) do
                                if tableObject.charName == object.charName then
                                    table.remove(championTable, ii)
                                end
                            end
                        end
                    end
                end
            end
        end
    end
     
     
     
    function LowAwarenessOnDraw()
        for i,tableObject in ipairs(championTable) do
           if tableObject.visible and tableObject.dead == false and tableObject.team ~= player.team then
                            for t = 0, 1 do
                                    DrawCircle(tableObject.x, tableObject.y, tableObject.z, 1250 + t*0.25, 0xFFFF0000)
                            end
           end
        end
    end
     
 -- ############################################# LOW AWARENESS ##############################################
 -- ############################################ CloneRevealer ############################################
--[[
    Displays the original enemy with a circle for enemies who can clone
    v1.1 BoL version
    Modified by Mistal, based on Zynox's AttackRange
]]

function CloneRevOnLoad()
--[[        Globals     ]]
    --if player == nil then player = GetMyHero() end

    --[[             Code            ]]
    do
        local cloneRevealer = {
            heros = {},
            charNameToShow = {"Shaco", "LeBlanc", "MonkeyKing", "Yorick"}
        }
        
        for index,charName in pairs(cloneRevealer.charNameToShow) do
            for i = 1, heroManager.iCount do
                local hero = heroManager:getHero(i)
                if hero ~= nil and hero.team ~= myHero.team and hero.charName == charName then
                    table.insert(cloneRevealer.heros, hero)
                end
            end
        end
        
        if #cloneRevealer.heros > 0 then
            --PrintChat(" >> Clones Revealer by Mistal Loaded!")
            function OnDraw()
                for index,hero in pairs(cloneRevealer.heros) do
                    if hero.dead == false and hero.visible then 
                        DrawCircle(hero.x, hero.y, hero.z, 100, 0x3232FF00) 
                    end
                end
            end
        else
            cloneRevealer = nil
        end
    end
end  





-- ############################################# ENEMY RANGE ################################################

-- Simple Player and Enemy Range Circles
-- by heist
-- v1.0
-- Initial release
-- v1.0.1
-- Adjusted AA range to be more accurate
-- Adopted to studio by Mistal

champAux = {}
champ = {
	Ahri = { 880, 975 },
	Akali = { 800, 0 },
	Alistar = { 650, 0 },
	Amumu = { 0, 600 },
	Anivia = { 650, 1100 },
	Annie = { 625, 0 },
	Ashe = { 1200, 0 },
	Blitzcrank = { 1000, 0 },
	Brand = { 900, 0 },
	Caitlyn = { 1300, 0 },
	Cassiopeia = { 700, 850 },
	Chogath = { 950, 700 },
	Corki = { 1200, 0 },
	Darius = {550, 475}, -- his E and R
	Diana = {830, 900}, -- Q and R
	Draven = {550, 0 }, -- his Ulti is global, his normal range is 550
	DrMundo = { 1000, 0 },
	Evelynn = { 325, 0 },
	Ezreal = { 1000, 0 },
	Fiddlesticks = { 475, 575 },
	Fiora = { 600, 400 },
	Fizz = { 550, 1275 },
	Galio = { 1000, 550 },
	Gangplank = { 625, 0 },
	Garen = { 400, 0 },
	Gragas = { 1150, 1050 },
	Graves = { 750, 0 },
	Hecarim = { 325, 0 }, -- Placeholder
	Heimerdinger = { 1000, 0 },
	Irelia = { 650, 425 },
	Janna = { 800, 1700 },
	JarvanIV = { 770, 650 },
	Jax = { 700, 0 },
	Jayce = { 500, 1050 }, -- normal range attack and ulti
	Karma = { 800, 0 },
	Karthus = { 850, 1000 },
	Kassadin = { 700, 650 },
	Katarina = { 700, 0 },
	Kayle = { 650, 0 },
	Kennen = { 1050, 0 },
	KogMaw = { 1000, 0 },
	Leblanc = { 1300, 600 },
	LeeSin = { 1100, 0 },
	Leona = { 1200, 0 },
	Lulu = { 925, 650 },
	Lux = { 1000, 0 },
	Malphite = { 1000, 0 },
	Malzahar = { 700, 0 },
	Maokai = { 650, 0 },
	MasterYi = { 600, 0 },
	MissFortune = { 625, 1400 },
	MonkeyKing = { 625, 325 },
	Mordekaiser = { 700, 1125 },
	Morgana = { 1300, 600 },
	Nasus = { 700, 0 },
	Nautilus = { 950, 850 },
	Nidalee = { 1500, 0 },
	Nocturne = { 1200, 465 },
	Nunu = { 550, 0 },
	Olaf = { 1000, 0 },
	Orianna = { 825, 0 },
	Pantheon = { 0, 600 },
	Poppy = { 525, 0 },
	Rammus = { 0, 325 },
	Renekton = { 550, 0 },
	Riven = { 0, 250 },
	Rumble = { 600, 1000 },
	Ryze = { 675, 625 },
	Sejuani = { 700, 1150 },
	Shaco = { 625, 0 },
	Shen = { 0, 600 },
	Shyvana = { 1000, 0 },
	Singed = { 0, 125 },
	Sion = { 550, 0 },
	Sivir = { 1100, 0 },
	Skarner = { 600, 350 },
	Sona = { 0, 1000 },
	Soraka = { 0, 725 },
	Swain = { 900, 0 },
	Syndra = { 550, 0 },
	Talon = { 700, 0 },
	Taric = { 0, 625 },
	Teemo = { 680, 0 },
	Tristana = { 900, 700 },
	Trundle = { 0, 1000 },
	Tryndamere = { 660, 0 },
	TwistedFate = { 1700, 0 },
	Twitch = { 1200, 0 },
	Udyr = { 625, 0 },
	Urgot = { 1000, 0 },
	Varus = { 925, 1075 },
	Vayne = { 0, 450 },
	Veigar = { 650, 0 },
	Viktor = { 600, 0 },
	Vladimir = { 600, 700 },
	Volibear = { 425, 0 },
	Warwick = { 0, 700 },
	Xerath = { 1300, 900 },
	XinZhao = { 650, 0 },
	Yorick = { 600, 0 },
	Ziggs = { 1000, 850 },
	Zilean = { 700, 0 },
	Zyra = { 825, 1100 },
}
champAux = champ
player = GetMyHero()
heroindex, c = {}, 0
for i = 1, heroManager.iCount do
local h = heroManager:getHero(i)
if h.name == player.name or h.team ~= player.team then
heroindex[c+1] = i
c = c+1
end
end

function ERangesOnDraw()
for _,v in ipairs(heroindex) do
local h = heroManager:getHero(v)
local t = champAux[h.charName]

if h.visible and not h.dead then
         if h.range > 400 and (t == nil or (h.range + 100 ~= t[1] and h.range + 100 ~= t[2])) then
         DrawCircle(h.x, h.y, h.z,h.range + 100, 0x992D3D)
         end
         if t ~= nil then
         if t[1] > 0 then
                 DrawCircle(h.x, h.y, h.z,t[1], 0x992D3D)
         end
         if t[2] > 0 then
                 DrawCircle(h.x, h.y, h.z,t[2], 0xFF0000)
         end
         end
end
end
end

function PRangesOnDraw()
local h = GetMyHero()
local t = champAux[h.charName]

if h.visible and not h.dead then
         if h.range > 400 and (t == nil or (h.range + 100 ~= t[1] and h.range + 100 ~= t[2])) then
         DrawCircle(h.x, h.y, h.z,h.range + 100, 0x992D3D)
         end
         if t ~= nil then
         if t[1] > 0 then
                 DrawCircle(h.x, h.y, h.z,t[1], 0x992D3D)
         end
         if t[2] > 0 then
                 DrawCircle(h.x, h.y, h.z,t[2], 0xFF0000)
         end
         end
end
end

-- ############################################# ENEMY RANGE ################################################

-- ############################################# PERFECT WARD ################################################
--[[
    Perfect Ward 1.7.3 by Husky. Updated by Ballsdeep
    ========================================================================

    Makes warding a no-brainer by suggesting good ward places, that give you
    the maximum field of view for most of the important ward spots where
    ward positioning is crucial (in brushes + at dragon/nashor).

    Magnetic ward spots make it nearly impossible to misplace a ward - even
    in stressfull situations. This maximizes your vision and helps you gank
    and counter jungle.

    Changelog
    ~~~~~~~~~

    1.0    - Magnetic ward spots makes wards "snap" to the perfect position

    1.1    - Added "safe wards" that can be placed over walls
            (thx to Dottie for coordinates)
           - Smartcasting wards is now supported through packet modification
            (thx to TRUS for initial code snippet)
           - Added configurable hotkeys, for people having slot items bound
             to non-default keys
           - Added an intelligent anti-gank system, that automatically pings
             roaming enemies
           - Added Possibility, to easily dump ward coordinates for script
             customization (click on a placed ward and hover the ward with
             your mouse to see the coordinates)

    1.2    - Removed the anti-gank system, since it has to be improved to send
             reasonable pings. It will be part of a separate Script (Perfect
             Ping).
           - Simplified the placement of "safe wards" by automating the movement
             and moving the magnetic spots closer to the place from where the wards
             are put.
           - Improved the visuals to make it easier to distinguish warding spots
             between "safe wards" and "perfect wards".
           - Fixed FPS issues for users with not so powerfull computers.

    1.3   - Added new ward items of season 3 patch

    1.4   - Fixed a problem that occured when using other scripts that utilize
            the packet api as well

    1.5   - Removed AllClass since its included by default
          - Made it work with new Version of Bot of Legends

    1.6   - Added compatability for BoL Mods hotkeys
          - Added new ward spots to reflect season 3 map changes
          - Fixed a bug showing c stack overflows when casting inside a circle

    1.7   - Added full support for free users (except smart cast items)

    1.7.1 - Fixed a small bug with smartcasted wards not being magnetic after latest changes
          - Reduced the amount of ward spots drawn, by showing only the visible spots (increases fps)

    1.7.2 - script uses the Packet library now, to faster address packet changes in the future

    1.7.3 - Updated Season 4 warding spots nd items, and added few extra warding spots

    Hotkeys
    ~~~~~~~

    Just press the number associated to the inventory slot containing your
    ward, or define your own Hotkeys in the script
]]

-- Config ----------------------------------------------------------------------

local HK_1 = HK_1 and string.byte(HK_1) or 49 -- hotkey for first itemslot (default "1")
local HK_2 = HK_2 and string.byte(HK_2) or 50 -- hotkey for first itemslot (default "2")
local HK_3 = HK_3 and string.byte(HK_3) or 51 -- hotkey for first itemslot (default "3")
local HK_4 = HK_4 and string.byte(HK_4) or 52 -- hotkey for first itemslot (default "4")
local HK_5 = HK_5 and string.byte(HK_5) or 53 -- hotkey for first itemslot (default "5")
local HK_6 = HK_6 and string.byte(HK_6) or 54 -- hotkey for first itemslot (default "6")
local HK_7 = HK_7 and string.byte(HK_7) or 55 -- hotkey for first itemslot (default "7")

local wardSpots = {
    -- Perfect Wards
    { x = 2823.37,    y = 55.03,  z = 7617.03},     -- BLUE GOLEM
    { x = 7422,    y = 46.53,  z = 3282},     -- BLUE LIZARD
    { x = 10148,   y = 44.41,  z = 2839},     -- BLUE TRI BUSH
    { x = 6269,    y = 42.51,  z = 4445},     -- BLUE PASS BUSH
    { x = 7151.64,    y = 51.67,  z = 4719.66},     -- BLUE RIVER ENTRANCE
    { x = 4354.54,    y = 53.67,  z = 7079.51},  -- BLUE ROUND BUSH
    { x = 4728,    y = -51.29, z = 8336},     -- BLUE RIVER ROUND BUSH
    { x = 6762.52,    y = 55.68,  z = 2918.75},     -- BLUE SPLIT PUSH BUSH

    { x = 11217.39,   y = 54.87,  z = 6841.89},     -- PURPLE GOLEM
    { x = 6610.35,    y = 54.45,  z = 11064.61},    -- PURPLE LIZARD
    { x = 3883,    y = 39.87,  z = 11577},    -- PURPLE TRI BUSH
    { x = 7775,    y = 43.14,  z = 10046.49}, -- PURPLE PASS BUSH
    { x = 6867.68, y = 57.01,  z = 9567.63},     -- PURPLE RIVER ENTRANCE
    { x = 9720.86,    y = 54.85,  z = 7501.50},     -- PURPLE ROUND BUSH
    { x = 9233.13,    y = -44.63, z = 6094.48},     -- PURPLE RIVER ROUND BUSH
    { x = 7282.69,    y = 52.59,     z = 11482.53},    -- PURPLE SPLIT PUSH BUSH

    { x = 10180.18,   y = -62.32,    z = 4969.32},      -- DRAGON
    { x = 8875.13,  y = -64.07,  z = 5390.57}, -- DRAGON BUSH
    { x = 3920.88,   y = -60.42,    z = 9477.78},      -- BARON
    { x = 5017.27,  y = -62.70,  z = 8954.09}, -- BARON BUSH

    { x = 12731.25,  y = 50.32,  z = 9132.66}, -- PURPLE BOT T2
    { x = 8036.52,  y = 45.19,  z = 12882.94}, -- PURPLE TOP T2
    { x = 9260.02,  y = 54.62,  z = 8582.67}, -- PURPLE MID T1

    { x = 4749.79,  y = 53.59,  z = 5890.76}, -- BLUE MID T1
    { x = 5983.58,  y = 52.99,  z = 1547.98}, -- BLUE BOT T2
    { x = 1213.70,  y = 58.77,  z = 5324.73}, -- BLUE TOP T2

}

local safeWardSpots = {
    {    -- DRAGON -> TRI BUSH
        magneticSpot =  {x = 9695,    y = 43.02, z = 3465},
        clickPosition = {x = 9843.38, y = 43.02, z = 3125.16},
        wardPosition =  {x = 9946.10, y = 43.02, z = 3064.81},
        movePosition  = {x = 9595,    y = 43.02, z = 3665}
    },
    {    -- NASHOR -> TRI BUSH
        magneticSpot =  {x = 4346.10, y = 36.62, z = 10964.81},
        clickPosition = {x = 4214.93, y = 36.62, z = 11202.01},
        wardPosition =  {x = 4146.10, y = 36.62, z = 11314.81},
        movePosition  = {x = 4384.36, y = 36.62, z = 10680.41}
    },
    {    -- BLUE TOP -> SOLO BUSH
        magneticSpot  = {x = 2349,    y = 44.20, z = 10387},
        clickPosition = {x = 2267.97, y = 44.20, z = 10783.37},
        wardPosition  = {x = 2446.10, y = 44.20, z = 10914.81},
        movePosition  = {x = 2311,    y = 44.20, z = 10185}
    },
    { -- BLUE MID -> ROUND BUSH // Inconsistent Placement
        magneticSpot  = {x = 4946.52, y = 54.71, z = 6474.56},
        clickPosition = {x = 4891.98, y = 53.62, z = 6639.05},
        wardPosition  = {x = 4546.10, y = 53.78, z = 6864.81},
        movePosition  = {x = 5217,    y = 54.95, z = 6263}
    },
    { -- BLUE MID -> RIVER LANE BUSH
        magneticSpot  = {x = 5528.96, y = 45.64, z = 7615.20},
        clickPosition = {x = 5688.96, y = 45.64, z = 7825.20},
        wardPosition  = {x = 5796.10, y = 45.64, z = 7914.81},
        movePosition  = {x = 5460.13, y = 45.64, z = 7469.77}
    },
    { -- BLUE LIZARD -> DRAGON PASS BUSH
        magneticSpot  = {x = 7745,    y = 47.71, z = 4065},
        clickPosition = {x = 7927.65, y = 47.71, z = 4239.77},
        wardPosition  = {x = 8146.10, y = 47.71, z = 4414.81},
        movePosition  = {x = 7645,    y = 47.71, z = 4015}
    },
    { -- PURPLE MID -> ROUND BUSH // Inconsistent Placement
        magneticSpot  = {x = 9057,    y = 45.73, z = 8245},
        clickPosition = {x = 9230.77, y = 66.39, z = 7897.22},
        wardPosition  = {x = 9446.10, y = 54.66, z = 7814.81},
        movePosition  = {x = 8895,    y = 54.89, z = 8313}
    },
    { -- PURPLE MID -> RIVER ROUND BUSH // Inconsistent Placement
        magneticSpot  = {x = 9025.78, y = 46.27, z = 6591.64},
        clickPosition = {x = 9200.08, y = 43.21, z = 6425.05},
        wardPosition  = {x = 9396.10, y = 23.72, z = 6264.81},
        movePosition  = {x = 8795, y = 56.11, z = 6815}
    },
    { -- PURPLE MID -> RIVER LANE BUSH
        magneticSpot  = {x = 8530.27, y = 46.98, z = 6637.38},
        clickPosition = {x = 8539.27, y = 46.98, z = 6637.38},
        wardPosition  = {x = 8396.10, y = 46.98, z = 6464.81},
        movePosition  = {x = 8779.17, y = 46.98, z = 6804.70}
    },
    { -- PURPLE BOTTOM -> SOLO BUSH
        magneticSpot  = {x = 11889,    y = 42.84, z = 4205},
        clickPosition = {x = 11974.23, y = 42.84, z = 3807.21},
        wardPosition  = {x = 11646.10, y = 42.84, z = 3464.81},
        movePosition  = {x = 11939,    y = 42.84, z = 4255}
    },
    { -- PURPLE LIZARD -> NASHOR PASS BUSH // Inconsistent Placement
        magneticSpot  = {x = 6299,    y = 45.47, z = 10377.75},
        clickPosition = {x = 6030.24, y = 54.29, z = 10292.37},
        wardPosition  = {x = 5846.10, y = 53.94, z = 10164.81},
        movePosition  = {x = 6447,    y = 54.63, z = 10463}
    }
}

local wardItems = {
    { id = 2043, spellName = "VisionWard",     range = 1450, duration = 180000},
    { id = 2044, spellName = "SightWard",      range = 1450, duration = 180000},
    { id = 3154, spellName = "WriggleLantern", range = 1450, duration = 180000},
    { id = 2045, spellName = "ItemGhostWard",  range = 1450, duration = 180000},
    { id = 2049, spellName = "ItemGhostWard",  range = 1450, duration = 180000},
    { id = 2050, spellName = "ItemMiniWard",   range = 1450, duration = 60000}
}

-- Globals ---------------------------------------------------------------------

local drawWardSpots      = false
local wardSlot           = nil
local putSafeWard        = nil
local wardCorrected      = false
local packetApiAvailable = false

-- Code ------------------------------------------------------------------------

function PerfectWardOnLoad()
    --PrintChat(" >> Perfect Ward 1.7.3")
end

function PerfectWardOnTick()
    if putSafeWard ~= nil then
        if GetDistance(safeWardSpots[putSafeWard].clickPosition, myHero) <= 650 then
            CastSpell(wardSlot, safeWardSpots[putSafeWard].clickPosition.x, safeWardSpots[putSafeWard].clickPosition.z)
            putSafeWard = nil
        end
    end
end

function PerfectWardOnWndMsg(msg,key)
    if msg == KEY_DOWN then
        wardSlot = nil
        if key == HK_1 then
            wardSlot = ITEM_1
        elseif key == HK_2 then
            wardSlot = ITEM_2
        elseif key == HK_3 then
            wardSlot = ITEM_3
        elseif key == HK_4 then
            wardSlot = ITEM_7
        elseif key == HK_5 then
            wardSlot = ITEM_4
        elseif key == HK_6 then
            wardSlot = ITEM_5
        elseif key == HK_7 then
            wardSlot = ITEM_6
        end

        if wardSlot ~= nil then
            if wardSlot == ITEM_7 then
                drawWardSpots = true
                return
            else
                local item = myHero:getInventorySlot(wardSlot)
                for i,wardItem in pairs(wardItems) do
                    if item == wardItem.id and myHero:CanUseSpell(wardSlot) == READY then
                        drawWardSpots = true
                        return
                    end
                end
            end
        end
    elseif msg == WM_LBUTTONUP and drawWardSpots then
        drawWardSpots = false
    elseif msg == WM_LBUTTONDOWN and drawWardSpots and not packetApiAvailable then
        drawWardSpots = false
        for i,wardSpot in pairs(wardSpots) do
            if GetDistance(wardSpot, mousePos) <= 250 and not wardCorrected then
                CastSpell(wardSlot, wardSpot.x, wardSpot.z)
                return
            end
        end

        for i,wardSpot in pairs(safeWardSpots) do
            if GetDistance(wardSpot.magneticSpot, mousePos) <= 100 and not wardCorrected then
                CastSpell(wardSlot, wardSpot.clickPosition.x, wardSpot.clickPosition.z)
                myHero:MoveTo(wardSpot.movePosition.x, wardSpot.movePosition.z)
                putSafeWard = i
                return
            end
        end
    elseif msg == WM_RBUTTONDOWN and drawWardSpots then
        drawWardSpots = false
    elseif msg == WM_RBUTTONDOWN then
        putSafeWard = nil
    end
end

function OnSendPacket(p)
    packetApiAvailable = true

    local packet = Packet(p)
    if packet:get('name') == 'S_CAST' then
        if wardSlot == packet:get('spellId') or (wardSlot == ITEM_7 and packet:get('spellId') == 138) then
            drawWardSpots = false
            for i,wardSpot in pairs(wardSpots) do
                if GetDistance(wardSpot, {x = packet:get('fromX'), y = myHero.y, z = packet:get('fromY')}) <= 250 and not wardCorrected then
                    packet:block()
                    wardCorrected = true
                    Packet('S_CAST', {spellId = packet:get('spellId'), fromX = wardSpot.x, fromY = wardSpot.z, toX = wardSpot.x, toY = wardSpot.z}):send()
                    wardCorrected = false
                    return
                end
            end

            for i,wardSpot in pairs(safeWardSpots) do
                if GetDistance(wardSpot.magneticSpot, {x = packet:get('fromX'), y = myHero.y, z = packet:get('fromY')}) <= 100 and not wardCorrected then
                    packet:block()
                    myHero:MoveTo(wardSpot.movePosition.x, wardSpot.movePosition.z)
                    putSafeWard = i
                    return
                end
            end
        end
    end
end

function PerfectWardOnDraw()
    if drawWardSpots then
        for i, wardSpot in pairs(wardSpots) do
            local wardColor = (GetDistance(wardSpot, mousePos) <= 250) and 0x00FF00 or 0xFFFFFF

            local x, y, onScreen = get2DFrom3D(wardSpot.x, wardSpot.y, wardSpot.z)
            if onScreen then
                DrawCircle(wardSpot.x, wardSpot.y, wardSpot.z, 31, wardColor)
                DrawCircle(wardSpot.x, wardSpot.y, wardSpot.z, 32, wardColor)
                DrawCircle(wardSpot.x, wardSpot.y, wardSpot.z, 250, wardColor)
            end
        end

        for i,wardSpot in pairs(safeWardSpots) do
            local wardColor  = (GetDistance(wardSpot.magneticSpot, mousePos) <= 100) and 0x00FF00 or 0xFFFFFF
            local arrowColor = (GetDistance(wardSpot.magneticSpot, mousePos) <= 100) and RGBA(0,255,0,0) or RGBA(255,255,255,0)

            local x, y, onScreen = get2DFrom3D(wardSpot.magneticSpot.x, wardSpot.magneticSpot.y, wardSpot.magneticSpot.z)
            if onScreen then
                DrawCircle(wardSpot.wardPosition.x, wardSpot.wardPosition.y, wardSpot.wardPosition.z, 31, wardColor)
                DrawCircle(wardSpot.wardPosition.x, wardSpot.wardPosition.y, wardSpot.wardPosition.z, 32, wardColor)

                DrawCircle(wardSpot.magneticSpot.x, wardSpot.magneticSpot.y, wardSpot.magneticSpot.z, 99, wardColor)
                DrawCircle(wardSpot.magneticSpot.x, wardSpot.magneticSpot.y, wardSpot.magneticSpot.z, 100, wardColor)

                local magneticWardSpotVector = Vector(wardSpot.magneticSpot.x, wardSpot.magneticSpot.y, wardSpot.magneticSpot.z)
                local wardPositionVector = Vector(wardSpot.wardPosition.x, wardSpot.wardPosition.y, wardSpot.wardPosition.z)
                local directionVector = (wardPositionVector-magneticWardSpotVector):normalized()
                local magneticWardSpotLineVector = magneticWardSpotVector + directionVector * 90

                DrawArrow(D3DXVECTOR3(magneticWardSpotLineVector.x, magneticWardSpotLineVector.y, magneticWardSpotLineVector.z), D3DXVECTOR3(directionVector.x, directionVector.y, directionVector.z), GetDistance(magneticWardSpotVector, wardPositionVector) + 85, 20, -10000000000000000000000, arrowColor)
            end
        end
    end

    local target = GetTarget()
    for i,wardItem in pairs(wardItems) do
        if target ~= nil and target.name == wardItem.spellName then
            DrawCircle(target.x, target.y, target.z, 68, 0x00FF00)
            DrawCircle(target.x, target.y, target.z, 69, 0x00FF00)
            DrawCircle(target.x, target.y, target.z, 70, 0x00FF00)
            if GetDistanceFromMouse(target) <= 70 then
                local cursor = GetCursorPos()

                DrawText("X = " .. string.format("%.2f", target.x),16, cursor.x, cursor.y + 50, 0xFF00FF00)
                DrawText("Y = " .. string.format("%.2f", target.y),16, cursor.x, cursor.y + 65, 0xFF00FF00)
                DrawText("Z = " .. string.format("%.2f", target.z),16, cursor.x, cursor.y + 80, 0xFF00FF00)
            end
        end
    end
end
-- ############################################# PERFECT WARD ################################################    
	 
-- ################################################## Minimap Timers v0.3c #######################################################
--[[
Script: minimapTimers v0.3  (3.14 LoL patch)
 
Author: SurfaceS
Updated by TEAM DEKLAND
]]
do
        --[[      GLOBAL      ]]
        monsters = {
                summonerRift = {
                        {       -- baron
                                name = "baron",
                                spawn = 900,
                                respawn = 420,
                                advise = true,
                                camps = {
                                        {
                                                pos = { x = 4600, y = 60, z = 10250 },
                                                name = "monsterCamp_12",
                                                creeps = { { { name = "Worm12.1.1" }, }, },
                                                team = TEAM_NEUTRAL,
                                        },
                                },
                        },
                        {       -- dragon
                                name = "dragon",
                                spawn = 150,
                                respawn = 360,
                                advise = true,
                                camps = {
                                        {
                                                pos = { x = 9459, y = 60, z = 4193 },
                                                name = "monsterCamp_6",
                                                creeps = { { { name = "Dragon6.1.1" }, }, },
                                                team = TEAM_NEUTRAL,
                                        },
                                },
                        },
                        {       -- blue
                                name = "blue",
                                spawn = 115,
                                respawn = 300,--蓝BUFF
                                advise = true,
                                camps = {
                                        {
                                                pos = { x = 3632, y = 60, z = 7600 },
                                                name = "monsterCamp_1",
                                                creeps = { { { name = "AncientGolem1.1.1" }, { name = "YoungLizard1.1.2" }, { name = "YoungLizard1.1.3" }, }, },
                                                team = TEAM_BLUE,
                                        },
                                        {
                                                pos = { x = 10386, y = 60, z = 6811 },
                                                name = "monsterCamp_7",
                                                creeps = { { { name = "AncientGolem7.1.1" }, { name = "YoungLizard7.1.2" }, { name = "YoungLizard7.1.3" }, }, },
                                                team = TEAM_RED,
                                        },
                                },
                        },
                        {       -- red
                                name = "red",
                                spawn = 115,
                                respawn = 300,--红BUFF
                                advise = true,
                                camps = {
                                        {
                                                pos = { x = 7455, y = 60, z = 3890 },
                                                name = "monsterCamp_4",
                                                creeps = { { { name = "LizardElder4.1.1" }, { name = "YoungLizard4.1.2" }, { name = "YoungLizard4.1.3" }, }, },
                                                team = TEAM_BLUE,
                                        },
                                        {
                                                pos = { x = 6504, y = 60, z = 10584 },
                                                name = "monsterCamp_10",
                                                creeps = { { { name = "LizardElder10.1.1" }, { name = "YoungLizard10.1.2" }, { name = "YoungLizard10.1.3" }, }, },
                                                team = TEAM_RED,
                                        },
                                },
                        },
                        {       -- wolves
                                name = "wolves",
                spawn = 125,
                                respawn = 50,
                                advise = false,
                                camps = {
                                        {
                        pos = { x = 3370, y = 60, z = 6220 },
                                                name = "monsterCamp_2",
                                                creeps = { { { name = "GiantWolf2.1.3" }, { name = "wolf2.1.1" }, { name = "wolf2.1.2" }, }, },
                                                team = TEAM_BLUE,
                                        },
                                        {
                        pos = { x = 10650, y = 60, z = 8120 },
                                                name = "monsterCamp_8",
                                                creeps = { { { name = "GiantWolf8.1.3" }, { name = "wolf8.1.1" }, { name = "wolf8.1.2" }, }, },
                                                team = TEAM_RED,
                                        },
                                },
                        },
                        {       -- wraiths
                                name = "wraiths",
                spawn = 125,
                                respawn = 50,
                                advise = false,
                                camps = {
                                        {
                        pos = { x = 6450, y = 60, z = 5220 },
                                                name = "monsterCamp_3",
                                                creeps = { { { name = "Wraith3.1.3" }, { name = "LesserWraith3.1.1" }, { name = "LesserWraith3.1.2" }, { name = "LesserWraith3.1.4" }, }, },
                                                team = TEAM_BLUE,
                                        },
                                        {
                        pos = { x = 7600, y = 60, z = 9250 },
                                                name = "monsterCamp_9",
                                                creeps = { { { name = "Wraith9.1.3" }, { name = "LesserWraith9.1.1" }, { name = "LesserWraith9.1.2" }, { name = "LesserWraith9.1.4" }, }, },
                                                team = TEAM_RED,
                                        },
                                },
                        },
                        {       -- GreatWraiths
                                name = "GreatWraiths",
                spawn = 125,
                                respawn = 50,
                                advise = false,
                                camps = {
                                        {
                        pos = { x = 1655, y = 60, z = 8200 },
                                                name = "monsterCamp_13",
                                                creeps = { { { name = "GreatWraith13.1.1" }, }, },
                                                team = TEAM_BLUE,
                                        },
                                        {
                        pos = { x = 12330, y = 60, z = 6300 },
                                                name = "monsterCamp_14",
                                                creeps = { { { name = "GreatWraith14.1.1" }, }, },
                                                team = TEAM_RED,
                                        },
                                },
                        },
                        {       -- Golems
                                name = "Golems",
                spawn = 125,
                                respawn = 50,
                                advise = false,
                                camps = {
                                        {
                        pos = { x = 8100, y = 60, z = 2550 },
                                                name = "monsterCamp_5",
                                                creeps = { { { name = "Golem5.1.2" }, { name = "SmallGolem5.1.1" }, }, },
                                                team = TEAM_BLUE,
                                        },
                                        {
                        pos = { x = 6110, y = 60, z = 11970 },
                                                name = "monsterCamp_11",
                                                creeps = { { { name = "Golem11.1.2" }, { name = "SmallGolem11.1.1" }, }, },
                                                team = TEAM_RED,
                                        },
                                },
                        },
                },
                twistedTreeline = {
                        {       -- Wraith
                                name = "Wraith",
                                spawn = 100,
                                respawn = 50,
                                advise = false,
                                camps = {
                                        {
                                                --pos = { x = 4414, y = 60, z = 5774 },
                                                name = "monsterCamp_1",
                                                creeps = {
                                                        { { name = "TT_NWraith1.1.1" }, { name = "TT_NWraith21.1.2" }, { name = "TT_NWraith21.1.3" }, },
                                                },
                                                team = TEAM_BLUE,
                                        },
                                        {
                                                --pos = { x = 11008, y = 60, z = 5775 },
                                                name = "monsterCamp_4",
                                                creeps = {
                                                        { { name = "TT_NWraith4.1.1" }, { name = "TT_NWraith24.1.2" }, { name = "TT_NWraith24.1.3" }, },
                                                },
                                                team = TEAM_RED,
                                        },
                                },
                        },
                        {       -- Golems
                                name = "Golems",
                                respawn = 50,
                                spawn = 100,
                                advise = false,
                                camps = {
                                        {
                                                --pos = { x = 5088, y = 60, z = 8065 },
                                                name = "monsterCamp_2",
                                                creeps = {
                                                        { { name = "TT_NGolem2.1.1" }, { name = "TT_NGolem22.1.2" } },
                                                },
                                                team = TEAM_BLUE,
                                        },
                                        {
                                                --pos = { x = 10341, y = 60, z = 8084 },
                                                name = "monsterCamp_5",
                                                creeps = {
                                                        { { name = "TT_NGolem5.1.1" }, { name = "TT_NGolem25.1.2" } },
                                                },
                                                team = TEAM_RED,
                                        },
                                },
                        },
                        {       -- Wolves
                                name = "Wolves",
                                respawn = 50,
                                spawn = 100,
                                advise = false,
                                camps = {
                                        {
                                                --pos = { x = 6148, y = 60, z = 5993 },
                                                name = "monsterCamp_3",
                                                creeps = { { { name = "TT_NWolf3.1.1" }, { name = "TT_NWolf23.1.2" }, { name = "TT_NWolf23.1.3" } }, },
                                                team = TEAM_BLUE,
                                        },
                                        {
                                                --pos = { x = 9239, y = 60, z = 6022 },
                                                name = "monsterCamp_6",
                                                creeps = { { { name = "TT_NWolf6.1.1" }, { name = "TT_NWolf26.1.2" }, { name = "TT_NWolf26.1.3" } }, },
                                                team = TEAM_RED,
                                        },
                                },
                        },
                        {       -- Heal
                                name = "Heal",
                                spawn = 115,
                                respawn = 90,
                                advise = true,
                                camps = {
                                        {
                                                pos = { x = 7711, y = 60, z = 6722 },
                                                name = "monsterCamp_7",
                                                creeps = { { { name = "TT_Relic7.1.1" }, }, },
                                                team = TEAM_NEUTRAL,
                                        },
                                },
                        },
                        {       -- Vilemaw
                                name = "Vilemaw",
                                spawn = 600,
                respawn = 300,
                                advise = true,
                                camps = {
                                        {
                                                pos = { x = 7711, y = 60, z = 10080 },
                                                name = "monsterCamp_8",
                                                creeps = { { { name = "TT_Spiderboss8.1.1" }, }, },
                                                team = TEAM_NEUTRAL,
                                        },
                                },
                        },
                },
                crystalScar = {},
                provingGrounds = {
                        {       -- Heal
                                name = "Heal",
                                spawn = 190,
                                respawn = 40,
                                advise = false,
                                camps = {
                                        {
                                                pos = { x = 8922, y = 60, z = 7868 },
                                                name = "monsterCamp_1",
                                                creeps = { { { name = "OdinShieldRelic1.1.1" }, }, },
                                                team = TEAM_NEUTRAL,
                                        },
                                        {
                                                pos = { x = 7473, y = 60, z = 6617 },
                                                name = "monsterCamp_2",
                                                creeps = { { { name = "OdinShieldRelic2.1.1" }, }, },
                                                team = TEAM_NEUTRAL,
                                        },
                                        {
                                                pos = { x = 5929, y = 60, z = 5190 },
                                                name = "monsterCamp_3",
                                                creeps = { { { name = "OdinShieldRelic3.1.1" }, }, },
                                                team = TEAM_NEUTRAL,
                                        },
                                        {
                                                pos = { x = 4751, y = 60, z = 3901 },
                                                name = "monsterCamp_4",
                                                creeps = { { { name = "OdinShieldRelic4.1.1" }, }, },
                                                team = TEAM_NEUTRAL,
                                        },
                                },
                        },
                },
                howlingAbyss = {
                        {       -- Heal
                                name = "Heal",
                                spawn = 190,
                                respawn = 40,
                                advise = false,
                                camps = {
                                        {
                                                pos = { x = 8922, y = 60, z = 7868 },
                                                name = "monsterCamp_1",
                                                creeps = { { { name = "HA_AP_HealthRelic1.1.1" }, }, },
                                                team = TEAM_NEUTRAL,
                                        },
                                        {
                                                pos = { x = 7473, y = 60, z = 6617 },
                                                name = "monsterCamp_2",
                                                creeps = { { { name = "HA_AP_HealthRelic2.1.1" }, }, },
                                                team = TEAM_NEUTRAL,
                                        },
                                        {
                                                pos = { x = 5929, y = 60, z = 5190 },
                                                name = "monsterCamp_3",
                                                creeps = { { { name = "HA_AP_HealthRelic3.1.1" }, }, },
                                                team = TEAM_NEUTRAL,
                                        },
                                        {
                                                pos = { x = 4751, y = 60, z = 3901 },
                                                name = "monsterCamp_4",
                                                creeps = { { { name = "HA_AP_HealthRelic4.1.1" }, }, },
                                                team = TEAM_NEUTRAL,
                                        },
                                },
                        },
                },
        }
 
        altars = {
                summonerRift = {},
                twistedTreeline = {
                        {
                                name = "Left Altar",
                                spawn = 180,
                                respawn = 85,
                                advise = true,
                                objectName = "TT_Buffplat_L",
                                locked = false,
                                lockNames = {"TT_Lock_Blue_L.troy", "TT_Lock_Purple_L.troy", "TT_Lock_Neutral_L.troy", },
                                unlockNames = {"TT_Unlock_Blue_L.troy", "TT_Unlock_purple_L.troy", "TT_Unlock_Neutral_L.troy", },
                        },
                        {
                                name = "Right Altar",
                                spawn = 180,
                                respawn = 85,
                                advise = true,
                                objectName = "TT_Buffplat_R",
                                locked = false,
                                lockNames = {"TT_Lock_Blue_R.troy", "TT_Lock_Purple_R.troy", "TT_Lock_Neutral_R.troy", },
                                unlockNames = {"TT_Unlock_Blue_R.troy", "TT_Unlock_purple_R.troy", "TT_Unlock_Neutral_R.troy", },
                        },
                },
                crystalScar = {},
                provingGrounds = {},
                howlingAbyss = {},
        }
 
        relics = {
                summonerRift = {},
                twistedTreeline = {},
                crystalScar = {
                        {
                                pos = { x = 5500, y = 60, z = 6500 },
                                name = "Relic",
                                team = TEAM_BLUE,
                                spawn = 180,
                                respawn = 180,
                                advise = true,
                                locked = false,
                                precenceObject = (player.team == TEAM_BLUE and "Odin_Prism_Green.troy" or "Odin_Prism_Red.troy"),
                        },
                        {
                                pos = { x = 7550, y = 60, z = 6500 },
                                name = "Relic",
                                team = TEAM_RED,
                                spawn = 180,
                                respawn = 180,
                                advise = true,
                                locked = false,
                                precenceObject = (player.team == TEAM_RED and "Odin_Prism_Green.troy" or "Odin_Prism_Red.troy"),
                        },
                },
                provingGrounds = {},
                howlingAbyss = {},
        }
 
        heals = {
                summonerRift = {},
                twistedTreeline = {},
                provingGrounds = {},
                crystalScar = {
                        {
                                name = "Heal",
                                objectName = "OdinShieldRelic",
                                respawn = 30,
                                objects = {},
                        },
                },
                howlingAbyss = {},
        }
 
        inhibitors = {}
 
        function addCampCreepAltar(object)
                if object ~= nil and object.name ~= nil then
                        if object.name == "Order_Inhibit_Gem.troy" or object.name == "Chaos_Inhibit_Gem.troy" then
                                table.insert(inhibitors, { object = object, destroyed = false, lefttime = 0, x = object.x, y = object.y, z = object.z, minimap = GetMinimap(object), textTick = 0 })
                                return
                        elseif object.name == "Order_Inhibit_Crystal_Shatter.troy" or object.name == "Chaos_Inhibit_Crystal_Shatter.troy" then
                                for i,inhibitor in pairs(inhibitors) do
                                        if GetDistance(inhibitor, object) < 200 then
                                                local tick = GetTickCount()
                                                inhibitor.dtime = tick
                                                inhibitor.rtime = tick + 240000
                                                inhibitor.ltime = 240000
                                                inhibitor.destroyed = true
                                        end
                                end
                                return
                        end
                        for i,monster in pairs(monsters[mapName]) do
                                for j,camp in pairs(monster.camps) do
                                        if camp.name == object.name then
                                                camp.object = object
                                                return
                                        end
                                        if object.type == "obj_AI_Minion" then
                                                for k,creepPack in ipairs(camp.creeps) do
                                                        for l,creep in ipairs(creepPack) do
                                                                if object.name == creep.name then
                                                                        creep.object = object
                                                                        return
                                                                end
                                                        end
                                                end
                                        end
                                end
                        end
                        for i,altar in pairs(altars[mapName]) do
                                if altar.objectName == object.name then
                                        altar.object = object
                                        altar.textTick = 0
                                        altar.minimap = GetMinimap(object)
                                end
                                if altar.locked then
                                        for j,lockName in pairs(altar.unlockNames) do
                                                if lockName == object.name then
                                                        altar.locked = false
                                                        return
                                                end
                                        end
                                else
                                        for j,lockName in pairs(altar.lockNames) do
                                                if lockName == object.name then
                                                        altar.drawColor = 0
                                                        altar.drawText = ""
                                                        altar.locked = true
                                                        altar.advised = false
                                                        altar.advisedBefore = false
                                                        return
                                                end
                                        end
                                end
                        end
                        for i,relic in pairs(relics[mapName]) do
                                if relic.precenceObject == object.name then
                                        relic.object = object
                                        relic.textTick = 0
                                        relic.locked = false
                                        return
                                end
                        end
                        for i,heal in pairs(heals[mapName]) do
                                if heal.objectName == object.name then
                                        for j,healObject in pairs(heal.objects) do
                                                if (GetDistance(healObject, object) < 50) then
                                                        healObject.object = object
                                                        healObject.found = true
                                                        healObject.locked = false
                                                        return
                                                end
                                        end
                                        local k = #heal.objects + 1
                                        heals[mapName][i].objects[k] = {found = true, locked = false, object = object, x = object.x, y = object.y, z = object.z, minimap = GetMinimap(object), textTick = 0,}
                                        return
                                end
                        end
                end
        end
 
        function removeCreep(object)
                if object ~= nil and object.type == "obj_AI_Minion" and object.name ~= nil then
                        for i,monster in pairs(monsters[mapName]) do
                                for j,camp in pairs(monster.camps) do
                                        for k,creepPack in ipairs(camp.creeps) do
                                                for l,creep in ipairs(creepPack) do
                                                        if object.name == creep.name then
                                                                creep.object = nil
                                                                return
                                                        end
                                                end
                                        end
                                end
                        end
                end
        end
 
    function MiniMapTimersOnLoad()
                mapName = GetGame().map.shortName
                if monsters[mapName] == nil then
                        mapName = nil
                        monsters = nil
                        addCampCreepAltar = nil
                        removeCreep = nil
                        addAltarObject = nil
                        return
                else
                        startTick = GetGame().tick
                        -- CONFIG
            MMTConfig = scriptConfig("[多合一]小地图计时 0.3", "minimapTimers")
            MMTConfig:addParam("pingOnRespawn", "复活时声音提示", SCRIPT_PARAM_ONOFF, false) -- ping location on respawn
            MMTConfig:addParam("pingOnRespawnBefore", "复活前声音预报", SCRIPT_PARAM_ONOFF, false) -- ping location before respawn
            MMTConfig:addParam("textOnRespawn", "复活时聊天提示", SCRIPT_PARAM_ONOFF, true) -- print chat text on respawn
            MMTConfig:addParam("textOnRespawnBefore", "复活前聊天预报", SCRIPT_PARAM_ONOFF, true) -- print chat text before respawn
            MMTConfig:addParam("adviceEnemyMonsters", "敌方野怪提醒", SCRIPT_PARAM_ONOFF, true) -- advice enemy monster, or just our monsters
            MMTConfig:addParam("adviceBefore", "预报野怪时间", SCRIPT_PARAM_SLICE, 20, 1, 40, 0) -- time in second to advice before monster respawn
            MMTConfig:addParam("textOnMap", "地图文本", SCRIPT_PARAM_ONOFF, true) -- time in second on map
                        for i,monster in pairs(monsters[mapName]) do
                                monster.isSeen = false
                                for j,camp in pairs(monster.camps) do
                                        camp.enemyTeam = (camp.team == TEAM_ENEMY)
                                        camp.textTick = 0
                                        camp.status = 0
                                        camp.drawText = ""
                                        camp.drawColor = 0xFF00FF00
                                end
                        end
                        for i = 1, objManager.maxObjects do
                                local object = objManager:getObject(i)
                                if object ~= nil then
                                        addCampCreepAltar(object)
                                end
                        end
                        AddCreateObjCallback(addCampCreepAltar)
                        AddDeleteObjCallback(removeCreep)
                end
        end
    function MiniMapTimersOnTick()
                if GetGame().isOver then return end
                local GameTime = (GetTickCount()-startTick) / 1000
                local monsterCount = 0
                for i,monster in pairs(monsters[mapName]) do
                        for j,camp in pairs(monster.camps) do
                                local campStatus = 0
                                for k,creepPack in ipairs(camp.creeps) do
                                        for l,creep in ipairs(creepPack) do
                                                if creep.object ~= nil and creep.object.valid and creep.object.dead == false then
                                                        if l == 1 then
                                                                campStatus = 1
                                                        elseif campStatus ~= 1 then
                                                                campStatus = 2
                                                        end
                                                end
                                        end
                                end
                                --[[  Not used until camp.showOnMinimap work
                                if (camp.object and camp.object.showOnMinimap == 1) then
                                -- camp is here
                                if campStatus == 0 then campStatus = 3 end
                                elseif camp.status == 3 then                                            -- empty not seen when killed
                                campStatus = 5
                                elseif campStatus == 0 and (camp.status == 1 or camp.status == 2) then
                                campStatus = 4
                                camp.deathTick = tick
                                end
                                ]]
                                -- temp fix until camp.showOnMinimap work
                                -- not so good
                                if camp.object ~= nil and camp.object.valid then
                                        camp.minimap = GetMinimap(camp.object)
                                        if campStatus == 0 then
                                                if (camp.status == 1 or camp.status == 2) then
                                                        campStatus = 4
                                                        camp.advisedBefore = false
                                                        camp.advised = false
                            camp.respawnTime = math.ceil(GameTime) + monster.respawn
                            camp.respawnText = (camp.enemyTeam and "敌人的 " or "我们的 ")..monster.name.." 复活于 "..TimerText(camp.respawnTime)
                                                elseif (camp.status == 4) then
                                                        campStatus = 4
                                                else
                                                        campStatus = 3
                                                end
                                        end
                                elseif camp.pos ~= nil then
                                        camp.minimap = GetMinimap(camp.pos)
                                        if (GameTime < monster.spawn) then
                                                campStatus = 4
                                                camp.advisedBefore = true
                                                camp.advised = true
                                                camp.respawnTime = monster.spawn
						camp.respawnText = (camp.enemyTeam and "敌人的 " or "我们的 ")..monster.name.." 将于 "..TimerText(camp.respawnTime).." 复活"
                                        end
                                end
                                if camp.status ~= campStatus or campStatus == 4 then
                                        if campStatus ~= 0 then
                                                if monster.isSeen == false then monster.isSeen = true end
                                                camp.status = campStatus
                                        end
                                        if camp.status == 1 then                                -- ready
                        camp.drawText = "准备"
                                                camp.drawColor = 0xFF00FF00
                                        elseif camp.status == 2 then                    -- ready, master creeps dead
                        camp.drawText = "偷掉"
                                                camp.drawColor = 0xFFFF0000
                                        elseif camp.status == 3 then                    -- ready, not creeps shown
                                                camp.drawText = "   ?"
                                                camp.drawColor = 0xFF00FF00
                                        elseif camp.status == 4 then                    -- empty from creeps kill
                                                local secondLeft = math.ceil(math.max(0, camp.respawnTime - GameTime))
                        if monster.advise == true and (MMTConfig.adviceEnemyMonsters == true or camp.enemyTeam == false) then
                                                        if secondLeft == 0 and camp.advised == false then
                                                                camp.advised = true
                                if MMTConfig.textOnRespawn then PrintChat("<font color='#00FFCC'>"..(camp.enemyTeam and "鏁屼汉鐨? " or "鎴戜滑鐨? ")..monster.name.."</font><font color='#FFAA00'> 宸茬粡澶嶆椿</font>") end
                                                                if MMTConfig.pingOnRespawn then PingSignal(PING_FALLBACK,camp.object.x,camp.object.y,camp.object.z,2) end
                                                        elseif secondLeft <= MMTConfig.adviceBefore and camp.advisedBefore == false then
                                                                camp.advisedBefore = true
                                if MMTConfig.textOnRespawnBefore then PrintChat("<font color='#00FFCC'>"..(camp.enemyTeam and "鏁屼汉鐨? " or "鎴戜滑鐨? ")..monster.name.."</font><font color='#FFAA00'>灏嗗湪</font><font color='#00FFCC'>"..secondLeft.." 绉?</font>".."澶嶆椿") end
                                                                if MMTConfig.pingOnRespawnBefore then PingSignal(PING_FALLBACK,camp.object.x,camp.object.y,camp.object.z,2) end
                                                        end
                                                end
                                                -- temp fix until camp.showOnMinimap work
                                                if secondLeft == 0 then
                                                        camp.status = 0
                                                end
                                                camp.drawText = " "..TimerText(secondLeft)
                                                camp.drawColor = 0xFFFFFF00
                                        elseif camp.status == 5 then                    -- camp found empty (not using yet)
                                                camp.drawText = "   -"
                                                camp.drawColor = 0xFFFF0000
                                        end
                                end
                                -- shift click
                                if IsKeyDown(16) and camp.status == 4 then
                                        camp.drawText = " "..(camp.respawnTime ~= nil and TimerText(camp.respawnTime) or "")
                                        camp.textUnder = (CursorIsUnder(camp.minimap.x - 9, camp.minimap.y - 5, 20, 8))
                                else
                                        camp.textUnder = false
                                end
                                if MMTConfig.textOnMap and camp.status == 4 and camp.object and camp.object.valid and camp.textTick < GetTickCount() and camp.floatText ~= camp.drawText then
                                        camp.floatText = camp.drawText
                                        camp.textTick = GetTickCount() + 1000
                                        PrintFloatText(camp.object,6,camp.floatText)
                                end
                        end
                end
 
                -- altars
                for i,altar in pairs(altars[mapName]) do
                        if altar.object and altar.object.valid then
                                if altar.locked then
                                        if GameTime < altar.spawn then
                                                altar.secondLeft = math.ceil(math.max(0, altar.spawn - GameTime))
                                        else
                                                local tmpTime = ((altar.object.mana > 39600) and (altar.object.mana - 39900) / 20100 or (39600 - altar.object.mana) / 20100)
                                                altar.secondLeft = math.ceil(math.max(0, tmpTime * altar.respawn))
                                        end
                                        altar.unlockTime = math.ceil(GameTime + altar.secondLeft)
                    altar.unlockText = altar.name.." 将于 "..TimerText(altar.unlockTime).." 解锁 "
                                        altar.drawColor = 0xFFFFFF00
                                        if altar.advise == true then
                                                if altar.secondLeft == 0 and altar.advised == false then
                                                        altar.advised = true
                            if MMTConfig.textOnRespawn then PrintChat("<font color='#00FFCC'>"..altar.name.."</font><font color='#FFAA00'> 宸茬粡瑙ｉ攣</font>") end
                                                        if MMTConfig.pingOnRespawn then PingSignal(PING_FALLBACK,altar.object.x,altar.object.y,altar.object.z,2) end
                                                elseif altar.secondLeft <= MMTConfig.adviceBefore and altar.advisedBefore == false then
                                                        altar.advisedBefore = true
                            if MMTConfig.textOnRespawnBefore then PrintChat("<font color='#00FFCC'>"..altar.name.."</font><font color='#FFAA00'> 灏嗕簬 </font><font color='#00FFCC'>"..altar.secondLeft.." 绉掑唴瑙ｉ攣</font>") end
                                                        if MMTConfig.pingOnRespawnBefore then PingSignal(PING_FALLBACK,altar.object.x,altar.object.y,altar.object.z,2) end
                                                end
                                        end
                                        -- shift click
                                        if IsKeyDown(16) then
                                                altar.drawText = " "..(altar.unlockTime ~= nil and TimerText(altar.unlockTime) or "")
                                                altar.textUnder = (CursorIsUnder(altar.minimap.x - 9, altar.minimap.y - 5, 20, 8))
                                        else
                                                altar.drawText = " "..(altar.secondLeft ~= nil and TimerText(altar.secondLeft) or "")
                                                altar.textUnder = false
                                        end
                                        if MMTConfig.textOnMap and altar.object and altar.object.valid and altar.textTick < GetTickCount() and altar.floatText ~= altar.drawText then
                                                altar.floatText = altar.drawText
                                                altar.textTick = GetTickCount() + 1000
                                                PrintFloatText(altar.object,6,altar.floatText)
                                        end
                                end
                        end
                end
 
                -- relics
                for i,relic in pairs(relics[mapName]) do
                        if (not relic.locked and (not relic.object or not relic.object.valid or relic.dead)) then
                                if GameTime < relic.spawn then
                                        relic.unlockTime = relic.spawn - GameTime
                                else
                                        relic.unlockTime = math.ceil(GameTime + relic.respawn)
                                end
                                relic.advised = false
                                relic.advisedBefore = false
                                relic.drawText = ""
                relic.unlockText = relic.name.." 将于 "..TimerText(relic.unlockTime).." 复活 "
                                relic.drawColor = 4288610048
                                --FF9EFF00
                                relic.minimap = GetMinimap(relic.pos)
                                relic.locked = true
                        end
                        if relic.locked then
                                relic.secondLeft = math.ceil(math.max(0, relic.unlockTime - GameTime))
                                if relic.advise == true then
                                        if relic.secondLeft == 0 and relic.advised == false then
                                                relic.advised = true
                        if MMTConfig.textOnRespawn then PrintChat("<font color='#00FFCC'>"..relic.name.."</font><font color='#FFAA00'> 宸茬粡澶嶆椿</font>") end
                                                if MMTConfig.pingOnRespawn then PingSignal(PING_FALLBACK,relic.pos.x,relic.pos.y,relic.pos.z,2) end
                                        elseif relic.secondLeft <= MMTConfig.adviceBefore and relic.advisedBefore == false then
                                                relic.advisedBefore = true
                        if MMTConfig.textOnRespawnBefore then PrintChat("<font color='#00FFCC'>"..relic.name.."</font><font color='#FFAA00'> 灏嗕簬 </font><font color='#00FFCC'>"..relic.secondLeft.." 绉掑唴澶嶆椿</font>") end
                                                if MMTConfig.pingOnRespawnBefore then PingSignal(PING_FALLBACK,relic.pos.x,relic.pos.y,relic.pos.z,2) end
                                        end
                                end
                                -- shift click
                                if IsKeyDown(16) then
                                        relic.drawText = " "..(relic.unlockTime ~= nil and TimerText(relic.unlockTime) or "")
                                        relic.textUnder = (CursorIsUnder(relic.minimap.x - 9, relic.minimap.y - 5, 20, 8))
                                else
                                        relic.drawText = " "..(relic.secondLeft ~= nil and TimerText(relic.secondLeft) or "")
                                        relic.textUnder = false
                                end
                        end
                end
 
                for i,heal in pairs(heals[mapName]) do
                        for j,healObject in pairs(heal.objects) do
                                if (not healObject.locked and healObject.found and (not healObject.object or not healObject.object.valid or healObject.object.dead)) then
                                        healObject.drawColor = 0xFF00FF04
                                        healObject.unlockTime = math.ceil(GameTime + heal.respawn)
                                        healObject.drawText = ""
                                        healObject.found = false
                                        healObject.locked = true
                                end
                                if healObject.locked then
                                        -- shift click
                                        local secondLeft = math.ceil(math.max(0, healObject.unlockTime - GameTime))
                                        if IsKeyDown(16) then
                                                healObject.drawText = " "..(healObject.unlockTime ~= nil and TimerText(healObject.unlockTime) or "")
                                                healObject.textUnder = (CursorIsUnder(healObject.minimap.x - 9, healObject.minimap.y - 5, 20, 8))
                                        else
                                                healObject.drawText = " "..(secondLeft ~= nil and TimerText(secondLeft) or "")
                                                healObject.textUnder = false
                                        end
                                        if secondLeft == 0 then healObject.locked = false end
                                end
                        end
                end
                -- inhib
                for i,inhibitor in pairs(inhibitors) do
                        if inhibitor.destroyed then
                                local tick = GetTickCount()
                                if inhibitor.rtime < tick then
                                        inhibitor.destroyed = false
                                else
                                        inhibitor.ltime = (inhibitor.rtime - GetTickCount()) / 1000;
                                        inhibitor.drawText = TimerText(inhibitor.ltime)
                                        --inhibitor.drawText = (IsKeyDown(16) and TimerText(inhibitor.rtime) or TimerText(inhibitor.rtime))
                                        if MMTConfig.textOnMap and inhibitor.textTick < tick then
                                                inhibitor.textTick = tick + 1000
                                                PrintFloatText(inhibitor.object,6,inhibitor.drawText)
                                        end
                                end
                        end
                end
        end
 
    function MiniMapTimersOnDraw()
                if GetGame().isOver then return end
                for i,monster in pairs(monsters[mapName]) do
                        if monster.isSeen == true then
                                for j,camp in pairs(monster.camps) do
                                        if camp.status == 2 then
                                                DrawText("X",16,camp.minimap.x - 4, camp.minimap.y - 5, camp.drawColor)
                                        elseif camp.status == 4 then
                                                DrawText(camp.drawText,16,camp.minimap.x - 9, camp.minimap.y - 5, camp.drawColor)
                                        end
                                end
                        end
                end
                for i,altar in pairs(altars[mapName]) do
                        if altar.locked then
                                DrawText(altar.drawText,16,altar.minimap.x - 9, altar.minimap.y - 5, altar.drawColor)
                        end
                end
                for i,relic in pairs(relics[mapName]) do
                        if relic.locked then
                                DrawText(relic.drawText,16,relic.minimap.x - 9, relic.minimap.y - 5, relic.drawColor)
                        end
                end
                for i,heal in pairs(heals[mapName]) do
                        for j,healObject in pairs(heal.objects) do
                                if healObject.locked then
                                        DrawText(healObject.drawText,16,healObject.minimap.x - 9, healObject.minimap.y - 5, healObject.drawColor)
                                end
                        end
                end
                for i,inhibitor in pairs(inhibitors) do
                        if inhibitor.destroyed == true then
                                DrawText(inhibitor.drawText,16,inhibitor.minimap.x - 9, inhibitor.minimap.y - 5, 0xFFFFFF00)
                        end
                end
        end
 
    function MiniMapTimersOnWndMsg(msg,key)
                if msg == WM_LBUTTONDOWN and IsKeyDown(16) then
                        for i,monster in pairs(monsters[mapName]) do
                                if monster.isSeen == true then
                                        if monster.iconUnder then
                                                monster.advise = not monster.advise
                                                break
                                        else
                                                for j,camp in pairs(monster.camps) do
                                                        if camp.textUnder then
                                                                if camp.respawnText ~= nil then SendChat(""..camp.respawnText) end
                                                                break
                                                        end
                                                end
                                        end
                                end
                        end
                        for i,altar in pairs(altars[mapName]) do
                                if altar.locked and altar.textUnder then
                                        if altar.unlockText ~= nil then SendChat(""..altar.unlockText) end
                                        break
                                end
                        end
                end
        end
end
-- ################################################## Minimap Timers v0.3c #######################################################
-- ######################################  Where Is He ??? ###############################################
--[[
    WhereIsHe v1.2 by eXtragoZ
        
    -Simple script that shows where the enemy can be
    -Thinner is the line is means that the enemy can be closer
    -Calculates the moving speed multiplied by the time that the enemy is miss
    -Circles have a minimum radius and maximum radius
]]

--[[        Code        ]]
local player = GetMyHero()
local unittraveled = 0
local MissTimer = {}
local MissSec = {}
local tick_heros = {}

function WhereIsHeOnTick()
    for i=1, heroManager.iCount do
        local heros = heroManager:GetHero(i)
        if heros.visible == false and heros.dead == false and heros.team ~= player.team then
            if tick_heros[i] == nil then
                tick_heros[i] = GetTickCount()
            end
            MissTimer[i] = GetTickCount() - tick_heros[i]           
            MissSec[i] =  MissTimer[i]/1000
        else
            tick_heros[i] = nil
            MissTimer[i] = nil
            MissSec[i] = 0
        end
    end
end
function WhereIsHeOnDraw()
    for i = 1, heroManager.iCount, 1 do
        local enemy = heroManager:getHero(i)
        if enemy ~= nil and enemy.team ~= player.team and enemy.dead == false and enemy.visible == false then
                if MissSec[i] == nil then
                    MissSec[i] = 0
                end
            unittraveled = enemy.ms*MissSec[i]
            if unittraveled > 50 and unittraveled < 10000 then
                DrawCircle(enemy.x, enemy.y, enemy.z, unittraveled, 0xFF0000)
            end
        end
    end
end
--PrintChat(" >> WhereIsHe 1.2 loaded!")
-- #############################################################################

-- ############################################# 敌人逃跑预测v0.4 ################################################

local blink = {} --Blink Ability Array
local vayneUltEndTick = 0
local shacoIndex = 0

function FindNearestNonWall(x0, y0, z0, maxRadius, precision) --returns the nearest non-wall-position of the given position(Credits to gReY)
	local vec = D3DXVECTOR3(x0, y0, z0)
	if not IsWall(vec) then return vec end
	precision = precision or 50
	maxRadius = maxRadius and math.floor(maxRadius / precision) or math.huge
	x0, z0 = math.round(x0 / precision) * precision, math.round(z0 / precision) * precision
	local radius = 1
	local function checkP(x, y)
		vec.x, vec.z = x0 + x * precision, z0 + y * precision
		return not IsWall(vec)
	end
	while radius <= maxRadius do
		if checkP(0, radius) or checkP(radius, 0) or checkP(0, -radius) or checkP(-radius, 0) then
			return vec
		end
		local f, x, y = 1 - radius, 0, radius
		while x < y - 1 do
			x = x + 1
			if f < 0 then
				f = f + 1 + 2 * x
			else
				y, f = y - 1, f + 1 + 2 * (x - y)
			end
			if checkP(x, y) or checkP(-x, y) or checkP(x, -y) or checkP(-x, -y) or
			   checkP(y, x) or checkP(-y, x) or checkP(y, -x) or checkP(-y, -x) then
				return vec
			end
		end
		radius = radius + 1
	end
end

function WhereGoOnLoad() --Called one time on load
	for i, heroObj in pairs(GetEnemyHeroes()) do
		if heroObj and heroObj.valid then
			if heroObj:GetSpellData(SUMMONER_1).name:find("Flash") or heroObj:GetSpellData(SUMMONER_2).name:find("Flash") then
				table.insert(blink,{name = "SummonerFlash"..heroObj.charName, maxRange = 400, delay = 0, casted = false, timeCasted = 0, startPos = {}, endPos = {}, castingHero = heroObj, shortName = "Flash"})
			end
			if heroObj.charName == "Ezreal" then
				table.insert(blink,{name = "EzrealArcaneShift", maxRange = 475, delay = 0, casted = false, timeCasted = 0, startPos = {}, endPos = {}, castingHero = heroObj, shortName = "E"})
			elseif heroObj.charName == "Fiora" then
				table.insert(blink,{name = "FioraDance", maxRange = 700, delay = 1, casted = false, timeCasted = 0, startPos = {}, endPos = {}, castingHero = heroObj, shortName = "R", target = {}, targetDead = false})
			elseif heroObj.charName == "Kassadin" then
				table.insert(blink,{name = "RiftWalk", maxRange = 700, delay = 0, casted = false, timeCasted = 0, startPos = {}, endPos = {}, castingHero = heroObj, shortName = "R"})
			elseif heroObj.charName == "Katarina" then
				table.insert(blink,{name = "KatarinaE", maxRange = 700, delay = 0, casted = false, timeCasted = 0, startPos = {}, endPos = {}, castingHero = heroObj, shortName = "E"})
			elseif heroObj.charName == "Leblanc" then
				table.insert(blink,{name = "LeblancSlide", maxRange = 600, delay = 0.5, casted = false, timeCasted = 0, startPos = {}, endPos = {}, castingHero = heroObj, shortName = "W"})
				table.insert(blink,{name = "leblancslidereturn", delay = 0, casted = false, timeCasted = 0, startPos = {}, endPos = {}, castingHero = heroObj, shortName = "W"})
				table.insert(blink,{name = "LeblancSlideM", maxRange = 600, delay = 0.5, casted = false, timeCasted = 0, startPos = {}, endPos = {}, castingHero = heroObj, shortName = "W"})
				table.insert(blink,{name = "leblancslidereturnm", delay = 0, casted = false, timeCasted = 0, startPos = {}, endPos = {}, castingHero = heroObj, shortName = "W"})
			elseif heroObj.charName == "MasterYi" then
				table.insert(blink,{name = "AlphaStrike", maxRange = 600, delay = 0.9, casted = false, timeCasted = 0, startPos = {}, endPos = {}, castingHero = heroObj, shortName = "Q", target = {}, targetDead = false})
			elseif heroObj.charName == "Shaco" then
				table.insert(blink,{name = "Deceive", maxRange = 400, delay = 0, casted = false, timeCasted = 0, startPos = {}, endPos = {}, castingHero = heroObj, shortName = "Q", outOfBush = false})
				shacoIndex = #blink --Save the position of shacos Q
			elseif heroObj.charName == "Talon" then
				table.insert(blink,{name = "TalonCutthroat", maxRange = 700, delay = 0, casted = false, timeCasted = 0, startPos = {}, endPos = {}, castingHero = heroObj, shortName = "E"})
			elseif heroObj.charName == "Vayne" then
				table.insert(blink,{name = "VayneTumble", maxRange = 250, delay = 0, casted = false, timeCasted = 0, startPos = {}, endPos = {}, castingHero = heroObj, shortName = "Q"})
				vayneUltEndTick = 1 --Start to check for Vayne's ult
			end
		end
	end
	if #blink > 0 then
		WDHGConfig = scriptConfig("[多合一]敌人逃跑预测","WhereDidHeGo")
		WDHGConfig:addParam("wallPrediction",     "使用障碍预测",      SCRIPT_PARAM_ONOFF, false)
		WDHGConfig:addParam("sep", "", SCRIPT_PARAM_INFO,"" )
		WDHGConfig:addParam("displayTime",        "显示时间 (无视野)", SCRIPT_PARAM_SLICE, 3, 1, 5, 0)
		WDHGConfig:addParam("displayTimeVisible", "显示时间 (视野中)", SCRIPT_PARAM_SLICE, 1, 0.5, 3, 1)
		WDHGConfig:addParam("sep", "", SCRIPT_PARAM_INFO,"" )
		WDHGConfig:addParam("lineColor",          "线条颜色",          SCRIPT_PARAM_COLOR, {255,255,255,0})
		WDHGConfig:addParam("lineWidth",          "线条宽度",          SCRIPT_PARAM_SLICE, 3, 1, 5, 0)
		WDHGConfig:addParam("sep", "", SCRIPT_PARAM_INFO,"" )
		WDHGConfig:addParam("circleColor",        "圆圈颜色",          SCRIPT_PARAM_COLOR, {255,255,25,0})
		WDHGConfig:addParam("circleSize",         "圆圈大小",          SCRIPT_PARAM_SLICE, 100, 50, 300, 0)
		if #blink > 1 then
			print('<font color="#A0FF00">閫冭窇棰勬祴 v0.4 宸插姞杞斤紝鎵惧埌 '..#blink..' 涓灛绉绘妧鑳斤紒</font>')
		else
			print('<font color="#A0FF00">閫冭窇棰勬祴 v0.4 宸插姞杞斤紝鎵惧埌 1 涓灛绉绘妧鑳斤紒</font>')
		end
	else
		print('<font color="#FFFF55">閫冭窇棰勬祴 v0.4 宸插姞杞斤紝娌℃湁鎵惧埌鐬Щ鎶€鑳斤紒</font>')
	end
end

function WhereGoOnProcessSpell(unit, spell)--When a spell is casted
	if unit and unit.valid and unit.team == TEAM_ENEMY and unit.type == "obj_AI_Hero" then
		if vayneUltEndTick > 0 and spell.name == "vayneinquisition" then
			vayneUltEndTick = os.clock() + 6 + 2*spell.level
			return --skip the array
		end
		for i=1, #blink, 1 do
			if spell.name == blink[i].name or spell.name..unit.charName == blink[i].name then
				local function SetNormalEndPosition(i, spell)
					if GetDistance(spell.startPos, spell.endPos) <= blink[i].maxRange then
						blink[i].endPos = { x = spell.endPos.x, y = spell.endPos.y, z = spell.endPos.z }
					else
						local vStartPos = Vector(spell.startPos.x, spell.startPos.y, spell.startPos.z)
						local vEndPos = Vector(spell.endPos.x, spell.endPos.y, spell.endPos.z)
						local tEndPos = vStartPos - (vStartPos - vEndPos):normalized() * blink[i].maxRange
						if WDHGConfig.wallPrediction then
							tEndPos = FindNearestNonWall(tEndPos.x, tEndPos.y, tEndPos.z, 1000)
						end
						blink[i].endPos = { x = tEndPos.x, y = tEndPos.y, z = tEndPos.z }
					end
				end
				if blink[i].name == "VayneTumble" and os.clock() >= vayneUltEndTick then return end
				if blink[i].name == "Deceive" then
					blink[i].outOfBush = false
				end
				if blink[i].name == "LeblancSlideM" then
					blink[i-2].casted = false
					blink[i].startPos = { x = blink[i-2].startPos.x, y = blink[i-2].startPos.y, z = blink[i-2].startPos.z }
					SetNormalEndPosition(i, spell)
				elseif blink[i].name == "leblancslidereturn" or blink[i].name == "leblancslidereturnm" then
					if blink[i].name == "leblancslidereturn" then
						blink[i-1].casted = false
						blink[i+1].casted = false
						blink[i+2].casted = false
					else
						blink[i-3].casted = false
						blink[i-2].casted = false
						blink[i-1].casted = false
					end
					blink[i].startPos = { x = spell.startPos.x, y = spell.startPos.y, z = spell.startPos.z }
					blink[i].endPos = { x = blink[i-1].startPos.x, y = blink[i-1].startPos.y, z = blink[i-1].startPos.z }
				elseif blink[i].name == "FioraDance" or blink[i].name == "AlphaStrike" then
					blink[i].target = spell.target
					blink[i].targetDead = false
					blink[i].startPos = { x = spell.startPos.x, y = spell.startPos.y, z = spell.startPos.z }
					blink[i].endPos = { x = blink[i].target.x, y = blink[i].target.y, z = blink[i].target.z }
				else
					blink[i].startPos = { x = spell.startPos.x, y = spell.startPos.y, z = spell.startPos.z }
					SetNormalEndPosition(i, spell)

				end
				blink[i].casted = true
				blink[i].timeCasted = os.clock()
				break
			end
		end
	end
end

function WhereGoOnCreateObj(obj)
	if shacoIndex ~= 0 and obj and obj.valid and obj.name == "JackintheboxPoof2.troy" and not blink[shacoIndex].casted then
		blink[shacoIndex].startPos = { x = obj.x, y = obj.y, z = obj.z }
		blink[shacoIndex].endPos = { x = obj.x, y = obj.y, z = obj.z }
		blink[shacoIndex].casted = true
		blink[shacoIndex].timeCasted = os.clock()
		blink[shacoIndex].outOfBush = true
	end
end

function WhereGoOnTick()
	for i=1, #blink, 1 do
		if blink[i].casted then
			if blink[i].name == "FioraDance" or blink[i].name == "AlphaStrike" and not blink[i].targetDead then
				if os.clock() > (blink[i].timeCasted + blink[i].delay + 0.2) then
					blink[i].casted = false
				elseif blink[i].target.dead then
					local tempPos = { x = blink[i].endPos.x, y = blink[i].endPos.y, z = blink[i].endPos.z }
					blink[i].endPos = { x = blink[i].startPos.x, y = blink[i].startPos.y, z = blink[i].startPos.z }
					blink[i].startPos = { x = tempPos.x, y = tempPos.y, z = tempPos.z }
					blink[i].targetDead = true
				else
					blink[i].endPos = { x = blink[i].target.x, y = blink[i].target.y, z = blink[i].target.z }
				end
			elseif blink[i].castingHero.dead or (not blink[i].castingHero.visible and os.clock() > (blink[i].timeCasted + WDHGConfig.displayTime + blink[i].delay)) or (blink[i].castingHero.visible and os.clock() > (blink[i].timeCasted + WDHGConfig.displayTimeVisible + blink[i].delay)) then
				blink[i].casted = false
			elseif not blink[i].outOfBush and blink[i].castingHero.visible and os.clock() > blink[i].timeCasted + blink[i].delay then
				blink[i].endPos = { x = blink[i].castingHero.x, y = blink[i].castingHero.y, z = blink[i].castingHero.z }
			end
		end
	end
end

function WhereGoOnDraw()
	for i=1, #blink, 1 do
		if blink[i].casted then
			local lineStartPos = WorldToScreen(D3DXVECTOR3(blink[i].startPos.x, blink[i].startPos.y, blink[i].startPos.z))
			local lineEndPos = WorldToScreen(D3DXVECTOR3(blink[i].endPos.x, blink[i].endPos.y, blink[i].endPos.z))
			if blink[i].outOfBush then
				for j=0, 3, 1 do
					DrawCircle(blink[i].endPos.x , blink[i].endPos.y , blink[i].endPos.z, blink[i].maxRange+j*2, ARGB(255, 255, 25, 0))
				end
			else
				for j=0, 3, 1 do
					DrawCircle(blink[i].endPos.x , blink[i].endPos.y , blink[i].endPos.z , WDHGConfig.circleSize+j*2, RGB(WDHGConfig.circleColor[2],WDHGConfig.circleColor[3],WDHGConfig.circleColor[4]))
				end
				DrawLine(lineStartPos.x, lineStartPos.y, lineEndPos.x, lineEndPos.y, WDHGConfig.lineWidth, RGB(WDHGConfig.lineColor[2],WDHGConfig.lineColor[3],WDHGConfig.lineColor[4]))
			end
			local offset = 30
			local infoText = blink[i].castingHero.charName .. " " .. blink[i].shortName
			DrawLine(lineEndPos.x, lineEndPos.y, lineEndPos.x + offset, lineEndPos.y - offset, 1, ARGB(255,255,255,255))
			DrawLine(lineEndPos.x + offset, lineEndPos.y - offset, lineEndPos.x + offset + 6 * infoText:len(), lineEndPos.y - offset, 1, ARGB(255,255,255,255))
			DrawTextA(infoText, 12, lineEndPos.x + offset + 1, lineEndPos.y - offset, ARGB(255,255,255,255), "left", "bottom")
		end
	end
end

-- ############################################# 敌人逃跑预测v0.4 ################################################
-- ############################################ AUTOSHIELD ###############################################
--[[
	Auto Shield 1.9
		by eXtragoZ
		
	Features:
		- Supports:
			- Shields: Lulu, Janna, Karma, LeeSin, Orianna, Lux, Thresh, JarvanIV, Nautilus, Rumble, Sion, Shen, Skarner, Urgot, Diana, Riven, Morgana, Sivir and Nocturne
			- Items: Locket of the Iron Solari, Seraph's Embrace, Face of the Mountain
			- Summoner Spells: Heal, Barrier
			- Heals: Alistar E, Kayle W, Nami W, Nidalee E, Sona W, Soraka W, Taric Q ,Gangplank W
			- Ultimates: Zilean R, Tryndamere R, Kayle R, Shen R, Lulu R, Soraka R
			- Yasuo Wall
		- If the skill has immediate damage, the script does not reached to activate the shield/heal/invulnerability
		- In the case that the enemy ability hits multiple allies the script looks for the highest percentage of damage unless it is a skillshot that only hits the first target in that case looks for the closest one from the enemy
		- Press shift to configure	
]]
local typeshield
local spellslot
local typeheal
local healslot
local typeult
local ultslot
local wallslot
local range = 0
local healrange = 0
local ultrange = 0
local shealrange = 300
local lisrange = 600
local FotMrange = 700
if myHero.charName == "Lulu" then
	typeshield = 1
	spellslot = _E
	range = 650
	typeult = 1
	ultslot = _R
	ultrange = 900
elseif myHero.charName == "Janna" then
        typeshield = 1
        spellslot = _E
        range = 800
elseif myHero.charName == "Karma" then
        typeshield = 1
        spellslot = _E
        range = 800
elseif myHero.charName == "LeeSin" then
        typeshield = 1
        spellslot = _W
        range = 700
elseif myHero.charName == "Orianna" then
	typeshield = 1
	spellslot = _E
	range = 1120 -- 1095
elseif myHero.charName == "Lux" then
        typeshield = 2
        spellslot = _W
        range = 1075
elseif myHero.charName == "Thresh" then
	typeshield = 2
	spellslot = _W
	range = 950 + 300
elseif myHero.charName == "JarvanIV" then
	typeshield = 3
	spellslot = _W
elseif myHero.charName == "Nautilus" then
	typeshield = 3
	spellslot = _W
elseif myHero.charName == "Rumble" then
	typeshield = 3
	spellslot = _W
elseif myHero.charName == "Sion" then
	typeshield = 3
	spellslot = _W
elseif myHero.charName == "Shen" then
	typeshield = 3
	spellslot = _W
	typeult = 3
	ultslot = _R
	ultrange = 25000
elseif myHero.charName == "Skarner" then
	typeshield = 3
	spellslot = _W
elseif myHero.charName == "Urgot" then
	typeshield = 3
	spellslot = _W
elseif myHero.charName == "Diana" then
	typeshield = 3
	spellslot = _W
-- elseif myHero.charName == "Udyr" then
	-- typeshield = 3
	-- spellslot = _W
elseif myHero.charName == "Riven" then
	typeshield = 4
	spellslot = _E
elseif myHero.charName == "Morgana" then
        typeshield = 5
        spellslot = _E
        range = 750
elseif myHero.charName == "Sivir" then
	typeshield = 6
	spellslot = _E
elseif myHero.charName == "Nocturne" then
	typeshield = 6
	spellslot = _W
elseif myHero.charName == "Alistar" then
	typeheal = 2
	healslot = _E
	healrange = 575
elseif myHero.charName == "Kayle" then
	typeheal = 1
	healslot = _W
	healrange = 900
	typeult = 1
	ultslot = _R
	ultrange = 900
elseif myHero.charName == "Nami" then
	typeheal = 1
	healslot = _W
	healrange = 725
elseif myHero.charName == "Nidalee" then
	typeheal = 1
	healslot = _E
	healrange = 600
elseif myHero.charName == "Sona" then
	typeheal = 2
	healslot = _W
	healrange = 1000
elseif myHero.charName == "Soraka" then
	typeheal = 1
	healslot = _W
	healrange = 750
	typeult = 2
	ultslot = _R
	ultrange = 25000
elseif myHero.charName == "Taric" then
	typeheal = 1
	healslot = _Q
	healrange = 750
elseif myHero.charName == "Gangplank" then
	typeheal = 3
	healslot = _W
elseif myHero.charName == "Zilean" then
        typeult = 1
        ultslot = _R
        ultrange = 900
elseif myHero.charName == "Tryndamere" then
	typeult = 4
	ultslot = _R
elseif myHero.charName == "Yasuo" then
	wallslot = _W
end

local sbarrier = nil
local sheal = nil
local useitems = true
local spelltype = nil
local casttype = nil
local BShield,SShield,Shield,CC = false,false,false,false
local shottype,radius,maxdistance = 0,0,0
local hitchampion = false
--[[        Code        ]]

function AutoShieldOnLoad()
    if myHero:GetSpellData(SUMMONER_1).name:find("SummonerBarrier") then sbarrier = SUMMONER_1
    elseif myHero:GetSpellData(SUMMONER_2).name:find("SummonerBarrier") then sbarrier = SUMMONER_2 end
    if myHero:GetSpellData(SUMMONER_1).name:find("SummonerHeal") then sheal = SUMMONER_1
    elseif myHero:GetSpellData(SUMMONER_2).name:find("SummonerHeal") then sheal = SUMMONER_2 end
    if typeshield ~= nil then
        ASConfig = scriptConfig("[多合一]自动护盾", "AutoShield")
        for i=1, heroManager.iCount do
            local teammate = heroManager:GetHero(i)
            if teammate.team == myHero.team then ASConfig:addParam("teammateshield"..i, "加护盾给 "..teammate.charName, SCRIPT_PARAM_ONOFF, true) end
        end
        ASConfig:addParam("maxhppercent", "生命值百分比", SCRIPT_PARAM_SLICE, 100, 0, 100, 0)  
        ASConfig:addParam("mindmgpercent", "最小攻击百分比", SCRIPT_PARAM_SLICE, 20, 0, 100, 0)
        ASConfig:addParam("mindmg", "最小攻击近似值", SCRIPT_PARAM_INFO, 0)
        ASConfig:addParam("skillshots", "自动给被集火目标加护盾", SCRIPT_PARAM_ONOFF, true)
        ASConfig:addParam("shieldcc", "自动给肉盾加护盾", SCRIPT_PARAM_ONOFF, true)
        ASConfig:addParam("shieldslow", "自动给减速者加护盾", SCRIPT_PARAM_ONOFF, true)
        ASConfig:addParam("drawcircles", "绘制范围", SCRIPT_PARAM_ONOFF, true)
        ASConfig:permaShow("mindmg")
    end
    if typeheal ~= nil then
        AHConfig = scriptConfig("[多合一]自动治疗", "AutoHeal")
        for i=1, heroManager.iCount do
            local teammate = heroManager:GetHero(i)
            if teammate.team == myHero.team then AHConfig:addParam("teammateheal"..i, "治疗 "..teammate.charName, SCRIPT_PARAM_ONOFF, true) end
        end
        AHConfig:addParam("maxhppercent", "生命值百分比", SCRIPT_PARAM_SLICE, 100, 0, 100, 0)  
        AHConfig:addParam("mindmgpercent", "最小攻击百分比", SCRIPT_PARAM_SLICE, 35, 0, 100, 0)
        AHConfig:addParam("mindmg", "最小攻击近似值", SCRIPT_PARAM_INFO, 0)
        AHConfig:addParam("skillshots", "治疗被集火目标", SCRIPT_PARAM_ONOFF, true)
        AHConfig:addParam("drawcircles", "绘制范围", SCRIPT_PARAM_ONOFF, true)
        AHConfig:permaShow("mindmg")
    end
    if typeult ~= nil then
        AUConfig = scriptConfig("[多合一]自动大招", "AutoUlt")
        for i=1, heroManager.iCount do
            local teammate = heroManager:GetHero(i)
            if teammate.team == myHero.team then AUConfig:addParam("teammateult"..i, "大招给 "..teammate.charName, SCRIPT_PARAM_ONOFF, false) end
        end
        AUConfig:addParam("maxhppercent", "生命值百分比", SCRIPT_PARAM_SLICE, 100, 0, 100, 0)  
        AUConfig:addParam("mindmgpercent", "最小攻击百分比", SCRIPT_PARAM_SLICE, 100, 0, 100, 0)
        AUConfig:addParam("mindmg", "最小攻击近似值", SCRIPT_PARAM_INFO, 0)
        AUConfig:addParam("skillshots", "大招给被集火目标", SCRIPT_PARAM_ONOFF, true)
        AUConfig:addParam("drawcircles", "绘制范围", SCRIPT_PARAM_ONOFF, true)
        AUConfig:permaShow("mindmg")
    end
	if wallslot ~= nil then
		WConfig = scriptConfig("[多合一]自动 墙", "AutoWall")
		WConfig:addParam("wallon", "自动放墙(Yasuo)", SCRIPT_PARAM_ONOFF, false)
		WConfig:addParam("maxhppercent", "生命值百分比", SCRIPT_PARAM_SLICE, 100, 0, 100, 0)	
		WConfig:addParam("mindmgpercent", "最小攻击百分比", SCRIPT_PARAM_SLICE, 20, 0, 100, 0)
		WConfig:addParam("mindmg", "最小攻击近似值", SCRIPT_PARAM_INFO, 0)
		WConfig:addParam("skillshots", "自动保护被集火目标", SCRIPT_PARAM_ONOFF, true)
		WConfig:addParam("shieldcc", "自动保护肉盾", SCRIPT_PARAM_ONOFF, true)
		WConfig:addParam("shieldslow", "自动保护减速者", SCRIPT_PARAM_ONOFF, true)
		WConfig:permaShow("mindmg")
	end
    if sbarrier ~= nil then
        ASBConfig = scriptConfig("[多合一]自动召唤师技能:屏障", "AutoSummonerBarrier")
        ASBConfig:addParam("barrieron", "屏障", SCRIPT_PARAM_ONOFF, false)
        ASBConfig:addParam("maxhppercent", "生命值百分比", SCRIPT_PARAM_SLICE, 100, 0, 100, 0)
        ASBConfig:addParam("mindmgpercent", "最小攻击百分比", SCRIPT_PARAM_SLICE, 95, 0, 100, 0)
        ASBConfig:addParam("mindmg", "最小攻击近似值", SCRIPT_PARAM_INFO, 0)
        ASBConfig:addParam("skillshots", "被集火时释放屏障", SCRIPT_PARAM_ONOFF, true)
    end
    if sheal ~= nil then
        ASHConfig = scriptConfig("[多合一]自动召唤师技能:治疗", "AutoSummonerHeal")
        for i=1, heroManager.iCount do
            local teammate = heroManager:GetHero(i)
            if teammate.team == myHero.team then ASHConfig:addParam("teammatesheal"..i, "治疗 "..teammate.charName, SCRIPT_PARAM_ONOFF, false) end
        end
        ASHConfig:addParam("maxhppercent", "生命值百分比", SCRIPT_PARAM_SLICE, 100, 0, 100, 0)
        ASHConfig:addParam("mindmgpercent", "最小攻击百分比", SCRIPT_PARAM_SLICE, 95, 0, 100, 0)
        ASHConfig:addParam("mindmg", "最小攻击近似值", SCRIPT_PARAM_INFO, 0)
        ASHConfig:addParam("skillshots", "治疗被集火者", SCRIPT_PARAM_ONOFF, true)
    end
    if useitems then
        ASIConfig = scriptConfig("[多合一]自动使用护盾道具", "AutoShieldItems")
        for i=1, heroManager.iCount do
            local teammate = heroManager:GetHero(i)
            if teammate.team == myHero.team then ASIConfig:addParam("teammateshieldi"..i, "加护盾(道具)给 "..teammate.charName, SCRIPT_PARAM_ONOFF, false) end
        end
        ASIConfig:addParam("maxhppercent", "生命值百分比", SCRIPT_PARAM_SLICE, 100, 0, 100, 0)
        ASIConfig:addParam("mindmgpercent", "最小攻击百分比", SCRIPT_PARAM_SLICE, 50, 0, 100, 0)
        ASIConfig:addParam("mindmg", "最小攻击近似值", SCRIPT_PARAM_INFO, 0)
        ASIConfig:addParam("skillshots", "自动给被集火目标加护盾", SCRIPT_PARAM_ONOFF, true)
    end
	--PrintChat(" >> Auto Shield 1.9 loaded!")
end

function AutoShieldOnProcessSpell(object,spell)
    if object.team ~= myHero.team and not myHero.dead and not (object.name:find("Minion_") or object.name:find("Odin")) then
		--if typeshield ~= nil then
			--if myHero.charName == "Lux" then range = 1075
			--else range = myHero:GetSpellData(spellslot).range end
		--end
		--if typeheal ~= nil then healrange = myHero:GetSpellData(healslot).range end
		--if typeult ~= nil then ultrange = myHero:GetSpellData(ultslot).range end
        local leesinW = myHero.charName ~= "LeeSin" or myHero:GetSpellData(_W).name == "BlindMonkWOne"
        local nidaleeE = myHero.charName ~= "Nidalee" or myHero:GetSpellData(_E).name == "PrimalSurge"
        local shieldREADY = typeshield ~= nil and myHero:CanUseSpell(spellslot) == READY and leesinW
        local healREADY = typeheal ~= nil and myHero:CanUseSpell(healslot) == READY and nidaleeE
        local ultREADY = typeult ~= nil and myHero:CanUseSpell(ultslot) == READY
		local wallREADY = wallslot ~= nil and myHero:CanUseSpell(wallslot) == READY
        local sbarrierREADY = sbarrier ~= nil and myHero:CanUseSpell(sbarrier) == READY
        local shealREADY = sheal ~= nil and myHero:CanUseSpell(sheal) == READY
        local lisslot = GetInventorySlotItem(3190)
        local seslot = GetInventorySlotItem(3040)
		local FotMslot = GetInventorySlotItem(3401)
        local lisREADY = lisslot ~= nil and myHero:CanUseSpell(lisslot) == READY
        local seREADY = seslot ~= nil and myHero:CanUseSpell(seslot) == READY
		local FotMREADY = FotMslot ~= nil and myHero:CanUseSpell(FotMslot) == READY
        local HitFirst = false
        local shieldtarget,SLastDistance,SLastDmgPercent = nil,nil,nil
        local healtarget,HLastDistance,HLastDmgPercent = nil,nil,nil
        local ulttarget,ULastDistance,ULastDmgPercent = nil,nil,nil
		YWall,BShield,SShield,Shield,CC = false,false,false,false,false
        shottype,radius,maxdistance = 0,0,0
        if object.type == "obj_AI_Hero" then
            spelltype, casttype = getSpellType(object, spell.name)
			if casttype == 4 or casttype == 5 or casttype == 6 then return end
			if spelltype == "BAttack" or spelltype == "CAttack" then
                Shield = true
				YWall = true
			elseif spell.name:find("SummonerDot") then
				Shield = true
            elseif spelltype == "Q" or spelltype == "W" or spelltype == "E" or spelltype == "R" or spelltype == "P" or spelltype == "QM" or spelltype == "WM" or spelltype == "EM" then
                HitFirst = skillShield[object.charName][spelltype]["HitFirst"]
				YWall = skillShield[object.charName][spelltype]["YWall"]
                BShield = skillShield[object.charName][spelltype]["BShield"]
                SShield = skillShield[object.charName][spelltype]["SShield"]
                Shield = skillShield[object.charName][spelltype]["Shield"]
                CC = skillShield[object.charName][spelltype]["CC"]
                shottype = skillData[object.charName][spelltype]["type"]
                radius = skillData[object.charName][spelltype]["radius"]
                maxdistance = skillData[object.charName][spelltype]["maxdistance"]
            end
        else
            Shield = true
        end
        for i=1, heroManager.iCount do
            local allytarget = heroManager:GetHero(i)
            if allytarget.team == myHero.team and not allytarget.dead and allytarget.health > 0 then
                hitchampion = false
                local allyHitBox = getHitBox(allytarget)
                if shottype == 0 then hitchampion = spell.target and spell.target.networkID == allytarget.networkID
                elseif shottype == 1 then hitchampion = checkhitlinepass(object, spell.endPos, radius, maxdistance, allytarget, allyHitBox)
                elseif shottype == 2 then hitchampion = checkhitlinepoint(object, spell.endPos, radius, maxdistance, allytarget, allyHitBox)
                elseif shottype == 3 then hitchampion = checkhitaoe(object, spell.endPos, radius, maxdistance, allytarget, allyHitBox)
                elseif shottype == 4 then hitchampion = checkhitcone(object, spell.endPos, radius, maxdistance, allytarget, allyHitBox)
                elseif shottype == 5 then hitchampion = checkhitwall(object, spell.endPos, radius, maxdistance, allytarget, allyHitBox)
                elseif shottype == 6 then hitchampion = checkhitlinepass(object, spell.endPos, radius, maxdistance, allytarget, allyHitBox) or checkhitlinepass(object, Vector(object)*2-spell.endPos, radius, maxdistance, allytarget, allyHitBox)
                elseif shottype == 7 then hitchampion = checkhitcone(spell.endPos, object, radius, maxdistance, allytarget, allyHitBox)
                end
                if hitchampion then
                    if shieldREADY and ASConfig["teammateshield"..i] and ((typeshield<=4 and Shield) or (typeshield==5 and BShield) or (typeshield==6 and SShield)) then
                        if (((typeshield==1 or typeshield==2 or typeshield==5) and GetDistance(allytarget)<=range) or allytarget.isMe) then
                            local shieldflag, dmgpercent = shieldCheck(object,spell,allytarget,"shields")
                            if shieldflag then
                                if HitFirst and (SLastDistance == nil or GetDistance(allytarget,object) <= SLastDistance) then
                                    shieldtarget,SLastDistance = allytarget,GetDistance(allytarget,object)
                                elseif not HitFirst and (SLastDmgPercent == nil or dmgpercent >= SLastDmgPercent) then
                                    shieldtarget,SLastDmgPercent = allytarget,dmgpercent
                                end
                            end
                        end
                    end
                    if healREADY and AHConfig["teammateheal"..i] and Shield then
                        if ((typeheal==1 or typeheal==2) and GetDistance(allytarget)<=healrange) or allytarget.isMe then
                            local healflag, dmgpercent = shieldCheck(object,spell,allytarget,"heals")
                            if healflag then
                                if HitFirst and (HLastDistance == nil or GetDistance(allytarget,object) <= HLastDistance) then
                                    healtarget,HLastDistance = allytarget,GetDistance(allytarget,object)
                                elseif not HitFirst and (HLastDmgPercent == nil or dmgpercent >= HLastDmgPercent) then
                                    healtarget,HLastDmgPercent = allytarget,dmgpercent
                                end
                            end     
                        end
                    end
                    if ultREADY and AUConfig["teammateult"..i] and Shield then
                        if typeult==2 or (typeult==1 and GetDistance(allytarget)<=ultrange) or (typeult==4 and allytarget.isMe) or (typeult==3 and not allytarget.isMe) then
                            local ultflag, dmgpercent = shieldCheck(object,spell,allytarget,"ult")
                            if ultflag then
                                if HitFirst and (ULastDistance == nil or GetDistance(allytarget,object) <= ULastDistance) then
                                    ulttarget,ULastDistance = allytarget,GetDistance(allytarget,object)
                                elseif not HitFirst and (ULastDmgPercent == nil or dmgpercent >= ULastDmgPercent) then
                                    ulttarget,ULastDmgPercent = allytarget,dmgpercent
                                end
                            end
                        end
                    end
					if wallREADY and WConfig.wallon and allytarget.isMe and YWall then
						local wallflag, dmgpercent = shieldCheck(object,spell,allytarget,"wall")
						if wallflag then
							CastSpell(wallslot,spell.startPos.x,spell.startPos.z)
						end
					end
                    if sbarrierREADY and ASBConfig.barrieron and allytarget.isMe and Shield then
                        local barrierflag, dmgpercent = shieldCheck(object,spell,allytarget,"barrier")
                        if barrierflag then
                            CastSpell(sbarrier)
                        end
                    end
                    if shealREADY and ASHConfig["teammatesheal"..i] and Shield then
                        if GetDistance(allytarget)<=shealrange then
                            local shealflag, dmgpercent = shieldCheck(object,spell,allytarget,"sheals")
                            if shealflag then
                                CastSpell(sheal)
                            end
                        end
                    end
                    if lisREADY and ASIConfig["teammateshieldi"..i] and Shield then
                        if GetDistance(allytarget)<=lisrange then
                            local lisflag, dmgpercent = shieldCheck(object,spell,allytarget,"items")
                            if lisflag then
                                CastSpell(lisslot)
							end
						end
					end
					if FotMREADY and ASIConfig["teammateshieldi"..i] and Shield then
						if GetDistance(allytarget)<=FotMrange then
							local FotMflag, dmgpercent = shieldCheck(object,spell,allytarget,"items")
							if FotMflag then
								CastSpell(FotMslot, allytarget)
                            end
                        end
                    end
                    if seREADY and ASIConfig["teammateshieldi"..i] and allytarget.isMe and Shield then
                        local seflag, dmgpercent = shieldCheck(object,spell,allytarget,"items")
                        if seflag then
                            CastSpell(seslot)
                        end
                    end
                end
            end
        end
        if shieldtarget ~= nil then
            if typeshield==1 or typeshield==5 then CastSpell(spellslot,shieldtarget)
            elseif typeshield==2 or typeshield==4 then CastSpell(spellslot,shieldtarget.x,shieldtarget.z)
            elseif typeshield==3 or typeshield==6 then CastSpell(spellslot) end
        end
        if healtarget ~= nil then
            if typeheal==1 then CastSpell(healslot,healtarget)
            elseif typeheal==2 or typeheal==3 then CastSpell(healslot) end
        end
        if ulttarget ~= nil then
            if typeult==1 or typeult==3 then CastSpell(ultslot,ulttarget)
            elseif typeult==2 or typeult==4 then CastSpell(ultslot) end     
        end
    end 
end

function shieldCheck(object,spell,target,typeused)
	local configused
	if typeused == "shields" then configused = ASConfig
	elseif typeused == "heals" then configused = AHConfig
	elseif typeused == "ult" then configused = AUConfig
	elseif typeused == "wall" then configused = WConfig
	elseif typeused == "barrier" then configused = ASBConfig 
	elseif typeused == "sheals" then configused = ASHConfig
	elseif typeused == "items" then configused = ASIConfig end
	local shieldflag = false
	if (not configused.skillshots and shottype ~= 0) then return false, 0 end
	local adamage = object:CalcDamage(target,object.totalDamage)
	local InfinityEdge,onhitdmg,onhittdmg,onhitspelldmg,onhitspelltdmg,muramanadmg,skilldamage,skillTypeDmg = 0,0,0,0,0,0,0,0

    if object.type ~= "obj_AI_Hero" then
        if spell.name:find("BasicAttack") then skilldamage = adamage
        elseif spell.name:find("CritAttack") then skilldamage = adamage*2 end
    else
        if GetInventoryHaveItem(3186,object) then onhitdmg = getDmg("KITAES",target,object) end
        if GetInventoryHaveItem(3114,object) then onhitdmg = onhitdmg+getDmg("MALADY",target,object) end
        if GetInventoryHaveItem(3091,object) then onhitdmg = onhitdmg+getDmg("WITSEND",target,object) end
        if GetInventoryHaveItem(3057,object) then onhitdmg = onhitdmg+getDmg("SHEEN",target,object) end
        if GetInventoryHaveItem(3078,object) then onhitdmg = onhitdmg+getDmg("TRINITY",target,object) end
        if GetInventoryHaveItem(3100,object) then onhitdmg = onhitdmg+getDmg("LICHBANE",target,object) end
        if GetInventoryHaveItem(3025,object) then onhitdmg = onhitdmg+getDmg("ICEBORN",target,object) end
        if GetInventoryHaveItem(3087,object) then onhitdmg = onhitdmg+getDmg("STATIKK",target,object) end
        if GetInventoryHaveItem(3153,object) then onhitdmg = onhitdmg+getDmg("RUINEDKING",target,object) end
        if GetInventoryHaveItem(3209,object) then onhittdmg = getDmg("SPIRITLIZARD",target,object) end
        if GetInventoryHaveItem(3184,object) then onhittdmg = onhittdmg+80 end
        if GetInventoryHaveItem(3042,object) then muramanadmg = getDmg("MURAMANA",target,object) end
        if spelltype == "BAttack" then
            skilldamage = (adamage+onhitdmg+muramanadmg)*1.07+onhittdmg
        elseif spelltype == "CAttack" then
            if GetInventoryHaveItem(3031,object) then InfinityEdge = .5 end
            skilldamage = (adamage*(2.1+InfinityEdge)+onhitdmg+muramanadmg)*1.07+onhittdmg --fix Lethality
        elseif spelltype == "Q" or spelltype == "W" or spelltype == "E" or spelltype == "R" or spelltype == "P" or spelltype == "QM" or spelltype == "WM" or spelltype == "EM" then
            if GetInventoryHaveItem(3151,object) then onhitspelldmg = getDmg("LIANDRYS",target,object) end
            if GetInventoryHaveItem(3188,object) then onhitspelldmg = getDmg("BLACKFIRE",target,object) end
            if GetInventoryHaveItem(3209,object) then onhitspelltdmg = getDmg("SPIRITLIZARD",target,object) end
            muramanadmg = skillShield[object.charName][spelltype]["Muramana"] and muramanadmg or 0
            if casttype == 1 then
                skilldamage, skillTypeDmg = getDmg(spelltype,target,object,1,spell.level)
            elseif casttype == 2 then
                skilldamage, skillTypeDmg = getDmg(spelltype,target,object,2,spell.level)
            elseif casttype == 3 then
                skilldamage, skillTypeDmg = getDmg(spelltype,target,object,3,spell.level)
            end
            if skillTypeDmg == 2 then
                skilldamage = (skilldamage+adamage+onhitspelldmg+onhitdmg+muramanadmg)*1.07+onhittdmg+onhitspelltdmg
            else
                if skilldamage > 0 then skilldamage = (skilldamage+onhitspelldmg+muramanadmg)*1.07+onhitspelltdmg end
            end
        elseif spell.name:find("SummonerDot") then
            skilldamage = getDmg("IGNITE",target,object)
        end
    end
    local dmgpercent = skilldamage*100/target.health
    local dmgneeded = dmgpercent >= configused.mindmgpercent
    local hpneeded = configused.maxhppercent >= (target.health-skilldamage)*100/target.maxHealth
    
    if dmgneeded and hpneeded then
        shieldflag = true
	elseif (typeused == "shields" or typeused == "wall") and ((CC == 2 and configused.shieldcc) or (CC == 1 and configused.shieldslow)) then
        shieldflag = true
    end
    return shieldflag, dmgpercent
end
function getHitBox(hero)
    local hitboxTable = { ['HeimerTGreen'] = 50.0, ['Darius'] = 80.0, ['ZyraGraspingPlant'] = 20.0, ['HeimerTRed'] = 50.0, ['ZyraThornPlant'] = 20.0, ['Nasus'] = 80.0, ['HeimerTBlue'] = 50.0, ['SightWard'] = 1, ['HeimerTYellow'] = 50.0, ['Kennen'] = 55.0, ['VisionWard'] = 1, ['ShacoBox'] = 10, ['HA_AP_Poro'] = 0, ['TempMovableChar'] = 48.0, ['TeemoMushroom'] = 50.0, ['OlafAxe'] = 50.0, ['OdinCenterRelic'] = 48.0, ['Blue_Minion_Healer'] = 48.0, ['AncientGolem'] = 100.0, ['AnnieTibbers'] = 80.0, ['OdinMinionGraveyardPortal'] = 1.0, ['OriannaBall'] = 48.0, ['LizardElder'] = 65.0, ['YoungLizard'] = 50.0, ['OdinMinionSpawnPortal'] = 1.0, ['MaokaiSproutling'] = 48.0, ['FizzShark'] = 0, ['Sejuani'] = 80.0, ['Sion'] = 80.0, ['OdinQuestIndicator'] = 1.0, ['Zac'] = 80.0, ['Red_Minion_Wizard'] = 48.0, ['DrMundo'] = 80.0, ['Blue_Minion_Wizard'] = 48.0, ['ShyvanaDragon'] = 80.0, ['HA_AP_OrderShrineTurret'] = 88.4, ['Heimerdinger'] = 55.0, ['Rumble'] = 80.0, ['Ziggs'] = 55.0, ['HA_AP_OrderTurret3'] = 88.4, ['HA_AP_OrderTurret2'] = 88.4, ['TT_Relic'] = 0, ['Veigar'] = 55.0, ['HA_AP_HealthRelic'] = 0, ['Teemo'] = 55.0, ['Amumu'] = 55.0, ['HA_AP_ChaosTurretShrine'] = 88.4, ['HA_AP_ChaosTurret'] = 88.4, ['HA_AP_ChaosTurretRubble'] = 88.4, ['Poppy'] = 55.0, ['Tristana'] = 55.0, ['HA_AP_PoroSpawner'] = 50.0, ['TT_NGolem'] = 80.0, ['HA_AP_ChaosTurretTutorial'] = 88.4, ['Volibear'] = 80.0, ['HA_AP_OrderTurretTutorial'] = 88.4, ['TT_NGolem2'] = 80.0, ['HA_AP_ChaosTurret3'] = 88.4, ['HA_AP_ChaosTurret2'] = 88.4, ['Shyvana'] = 50.0, ['HA_AP_OrderTurret'] = 88.4, ['Nautilus'] = 80.0, ['ARAMOrderTurretNexus'] = 88.4, ['TT_ChaosTurret2'] = 88.4, ['TT_ChaosTurret3'] = 88.4, ['TT_ChaosTurret1'] = 88.4, ['ChaosTurretGiant'] = 88.4, ['ARAMOrderTurretFront'] = 88.4, ['ChaosTurretWorm'] = 88.4, ['OdinChaosTurretShrine'] = 88.4, ['ChaosTurretNormal'] = 88.4, ['OrderTurretNormal2'] = 88.4, ['OdinOrderTurretShrine'] = 88.4, ['OrderTurretDragon'] = 88.4, ['OrderTurretNormal'] = 88.4, ['ARAMChaosTurretFront'] = 88.4, ['ARAMOrderTurretInhib'] = 88.4, ['ChaosTurretWorm2'] = 88.4, ['TT_OrderTurret1'] = 88.4, ['TT_OrderTurret2'] = 88.4, ['ARAMChaosTurretInhib'] = 88.4, ['TT_OrderTurret3'] = 88.4, ['ARAMChaosTurretNexus'] = 88.4, ['OrderTurretAngel'] = 88.4, ['Mordekaiser'] = 80.0, ['TT_Buffplat_R'] = 0, ['Lizard'] = 50.0, ['GolemOdin'] = 80.0, ['Renekton'] = 80.0, ['Maokai'] = 80.0, ['LuluLadybug'] = 50.0, ['Alistar'] = 80.0, ['Urgot'] = 80.0, ['LuluCupcake'] = 50.0, ['Gragas'] = 80.0, ['Skarner'] = 80.0, ['Yorick'] = 80.0, ['MalzaharVoidling'] = 10.0, ['LuluPig'] = 50.0, ['Blitzcrank'] = 80.0, ['Chogath'] = 80.0, ['Vi'] = 50, ['FizzBait'] = 0, ['Malphite'] = 80.0, ['EliseSpiderling'] = 1.0, ['Dragon'] = 100.0, ['LuluSquill'] = 50.0, ['Worm'] = 100.0, ['redDragon'] = 100.0, ['LuluKitty'] = 50.0, ['Galio'] = 80.0, ['Annie'] = 55.0, ['EliseSpider'] = 50.0, ['SyndraSphere'] = 48.0, ['LuluDragon'] = 50.0, ['Hecarim'] = 80.0, ['TT_Spiderboss'] = 200.0, ['Thresh'] = 55.0, ['ARAMChaosTurretShrine'] = 88.4, ['ARAMOrderTurretShrine'] = 88.4, ['Blue_Minion_MechMelee'] = 65.0, ['TT_NWolf'] = 65.0, ['Tutorial_Red_Minion_Wizard'] = 48.0, ['YorickRavenousGhoul'] = 1.0, ['SmallGolem'] = 80.0, ['OdinRedSuperminion'] = 55.0, ['Wraith'] = 50.0, ['Red_Minion_MechCannon'] = 65.0, ['Red_Minion_Melee'] = 48.0, ['OdinBlueSuperminion'] = 55.0, ['TT_NWolf2'] = 50.0, ['Tutorial_Red_Minion_Basic'] = 48.0, ['YorickSpectralGhoul'] = 1.0, ['Wolf'] = 50.0, ['Blue_Minion_MechCannon'] = 65.0, ['Golem'] = 80.0, ['Blue_Minion_Basic'] = 48.0, ['Blue_Minion_Melee'] = 48.0, ['Odin_Blue_Minion_caster'] = 48.0, ['TT_NWraith2'] = 50.0, ['Tutorial_Blue_Minion_Wizard'] = 48.0, ['GiantWolf'] = 65.0, ['Odin_Red_Minion_Caster'] = 48.0, ['Red_Minion_MechMelee'] = 65.0, ['LesserWraith'] = 50.0, ['Red_Minion_Basic'] = 48.0, ['Tutorial_Blue_Minion_Basic'] = 48.0, ['GhostWard'] = 1, ['TT_NWraith'] = 50.0, ['Red_Minion_MechRange'] = 65.0, ['YorickDecayedGhoul'] = 1.0, ['TT_Buffplat_L'] = 0, ['TT_ChaosTurret4'] = 88.4, ['TT_Buffplat_Chain'] = 0, ['TT_OrderTurret4'] = 88.4, ['OrderTurretShrine'] = 88.4, ['ChaosTurretShrine'] = 88.4, ['WriggleLantern'] = 1, ['ChaosTurretTutorial'] = 88.4, ['TwistedLizardElder'] = 65.0, ['RabidWolf'] = 65.0, ['OrderTurretTutorial'] = 88.4, ['OdinShieldRelic'] = 0, ['TwistedGolem'] = 80.0, ['TwistedSmallWolf'] = 50.0, ['TwistedGiantWolf'] = 65.0, ['TwistedTinyWraith'] = 50.0, ['TwistedBlueWraith'] = 50.0, ['TwistedYoungLizard'] = 50.0, ['Summoner_Rider_Order'] = 65.0, ['Summoner_Rider_Chaos'] = 65.0, ['Ghast'] = 60.0, ['blueDragon'] = 100.0, }
    return (hitboxTable[hero.charName] ~= nil and hitboxTable[hero.charName] ~= 0) and hitboxTable[hero.charName] or 65
end
function AutoShieldOnDraw()
    if typeshield ~= nil then
        if ASConfig.drawcircles and not myHero.dead and (typeshield == 1 or typeshield == 2 or typeshield == 5) then
            DrawCircle(myHero.x, myHero.y, myHero.z, range, 0x19A712)
        end
        ASConfig.mindmg = math.floor(myHero.health*ASConfig.mindmgpercent/100)
    end
    if typeheal ~= nil then
        if AHConfig.drawcircles and not myHero.dead and (typeheal == 1 or typeheal == 2) then
            DrawCircle(myHero.x, myHero.y, myHero.z, healrange, 0x19A712)
        end
        AHConfig.mindmg = math.floor(myHero.health*AHConfig.mindmgpercent/100)
    end
    if typeult ~= nil then
        if AUConfig.drawcircles and not myHero.dead and typeult == 1 then
            DrawCircle(myHero.x, myHero.y, myHero.z, ultrange, 0x19A712)
        end
        AUConfig.mindmg = math.floor(myHero.health*AUConfig.mindmgpercent/100)
    end
	if wallslot ~= nil then WConfig.mindmg = math.floor(myHero.health*WConfig.mindmgpercent/100) end
    if sbarrier ~= nil then ASBConfig.mindmg = math.floor(myHero.health*ASBConfig.mindmgpercent/100) end
    if sheal ~= nil then ASHConfig.mindmg = math.floor(myHero.health*ASHConfig.mindmgpercent/100) end
    if useitems then ASIConfig.mindmg = math.floor(myHero.health*ASIConfig.mindmgpercent/100) end
end
-- ############################################ AUTOSHIELD ###############################################

-- ############################################# AutoLevel ##############################################

--[[ 		Globals		]]
local abilitySequence
local qOff, wOff, eOff, rOff = 0,0,0,0

--[[ 		Functions	]]
function AutoLevelOnTick()
    local qL, wL, eL, rL = player:GetSpellData(_Q).level + qOff, player:GetSpellData(_W).level + wOff, player:GetSpellData(_E).level + eOff, player:GetSpellData(_R).level + rOff
    if qL + wL + eL + rL < player.level then
        local spellSlot = { SPELL_1, SPELL_2, SPELL_3, SPELL_4, }
        local level = { 0, 0, 0, 0 }
        for i = 1, player.level, 1 do
            level[abilitySequence[i]] = level[abilitySequence[i]] + 1
        end
        for i, v in ipairs({ qL, wL, eL, rL }) do
            if v < level[i] then LevelSpell(spellSlot[i]) end
        end
    end
end

function AutoLevelOnLoad()
    local champ = player.charName
    --[[
     In this section you can adjust the ability sequence of champions.

     To turn off the script for a particular champion,
     you have to comment out this line with two dashes.
     ]]
    if champ == "Aatrox" then           abilitySequence = { 1, 2, 3, 2, 2, 4, 2, 3, 2, 3, 4, 3, 3, 1, 1, 4, 1, 1, }
    elseif champ == "Jinx" then         abilitySequence = { 1, 2, 3, 1, 1, 4, 1, 2, 1, 2, 4, 2, 2, 3, 3, 4, 2, 2, }
    elseif champ == "Ahri" then         abilitySequence = { 1, 3, 1, 2, 1, 4, 1, 2, 1, 2, 4, 2, 2, 3, 3, 4, 2, 2, }
    elseif champ == "Akali" then        abilitySequence = { 1, 2, 1, 3, 1, 4, 1, 3, 1, 3, 4, 3, 3, 2, 2, 4, 2, 2, }
    elseif champ == "Alistar" then      abilitySequence = { 1, 3, 2, 1, 3, 4, 1, 3, 1, 3, 4, 1, 3, 2, 2, 4, 2, 2, }
    elseif champ == "Amumu" then        abilitySequence = { 2, 3, 3, 1, 3, 4, 3, 1, 3, 1, 4, 1, 1, 2, 2, 4, 2, 2, }
    elseif champ == "Anivia" then       abilitySequence = { 1, 3, 1, 3, 3, 4, 3, 2, 3, 2, 4, 1, 1, 1, 2, 4, 2, 2, }
    elseif champ == "Annie" then        abilitySequence = { 2, 1, 1, 3, 1, 4, 1, 2, 1, 2, 4, 2, 2, 3, 3, 4, 3, 3, }
    elseif champ == "Ashe" then         abilitySequence = { 2, 3, 2, 1, 2, 4, 2, 1, 2, 1, 4, 1, 1, 3, 3, 4, 3, 3, }
    elseif champ == "Blitzcrank" then   abilitySequence = { 1, 3, 2, 3, 2, 4, 3, 2, 3, 2, 4, 3, 2, 1, 1, 4, 1, 1, }
    elseif champ == "Brand" then        abilitySequence = { 2, 3, 2, 1, 2, 4, 2, 3, 2, 3, 4, 3, 3, 1, 1, 4, 1, 1, }
    elseif champ == "Caitlyn" then      abilitySequence = { 2, 1, 1, 3, 1, 4, 1, 3, 1, 3, 4, 3, 3, 2, 2, 4, 2, 2, }
    elseif champ == "Cassiopeia" then   abilitySequence = { 1, 3, 3, 2, 1, 4, 3, 3, 3, 1, 4, 1, 1, 2, 2, 4, 2, 2, }
    elseif champ == "Chogath" then      abilitySequence = { 1, 3, 2, 2, 2, 4, 2, 3, 2, 3, 4, 3, 3, 1, 1, 4, 1, 1, }
    elseif champ == "Corki" then        abilitySequence = { 1, 2, 1, 3, 1, 4, 1, 3, 1, 3, 4, 3, 2, 3, 2, 4, 2, 2, }
    elseif champ == "Darius" then       abilitySequence = { 1, 3, 1, 2, 1, 4, 1, 2, 1, 2, 4, 2, 3, 2, 3, 4, 3, 3, }
    elseif champ == "Diana" then        abilitySequence = { 2, 1, 2, 3, 1, 4, 1, 1, 1, 2, 4, 2, 2, 3, 3, 4, 3, 3, }
    elseif champ == "DrMundo" then      abilitySequence = { 2, 1, 3, 2, 2, 4, 2, 3, 2, 3, 4, 3, 3, 1, 1, 4, 1, 1, }
    elseif champ == "Draven" then       abilitySequence = { 1, 3, 2, 1, 1, 4, 1, 2, 1, 2, 4, 2, 2, 3, 3, 4, 3, 3, }
    elseif champ == "Elise" then        abilitySequence = { 2, 1, 3, 1, 1, 4, 1, 2, 1, 2, 4, 2, 2, 3, 3, 4, 3, 3, } rOff = -1
    elseif champ == "Evelynn" then      abilitySequence = { 1, 3, 1, 2, 1, 4, 1, 3, 1, 3, 4, 3, 3, 2, 2, 4, 2, 2, }
    elseif champ == "Ezreal" then       abilitySequence = { 1, 3, 2, 1, 1, 4, 1, 3, 1, 2, 4, 3, 2, 3, 2, 4, 3, 2, }
    elseif champ == "FiddleSticks" then abilitySequence = { 3, 2, 2, 1, 2, 4, 2, 1, 2, 1, 4, 1, 1, 3, 3, 4, 3, 3, }
    elseif champ == "Fiora" then        abilitySequence = { 2, 1, 3, 2, 2, 4, 2, 3, 2, 3, 4, 3, 3, 1, 1, 4, 1, 1, }
    elseif champ == "Fizz" then         abilitySequence = { 3, 1, 2, 1, 2, 4, 1, 1, 1, 2, 4, 2, 2, 3, 3, 4, 3, 3, }
    elseif champ == "Galio" then        abilitySequence = { 1, 2, 1, 3, 1, 4, 1, 2, 1, 2, 4, 3, 3, 2, 2, 4, 3, 3, }
    elseif champ == "Gangplank" then    abilitySequence = { 1, 2, 1, 3, 1, 4, 1, 2, 1, 2, 4, 2, 2, 3, 3, 4, 3, 3, }
    elseif champ == "Garen" then        abilitySequence = { 1, 2, 3, 3, 3, 4, 3, 1, 3, 1, 4, 1, 1, 2, 2, 4, 2, 2, }
    elseif champ == "Gragas" then       abilitySequence = { 1, 3, 2, 1, 1, 4, 1, 2, 1, 2, 4, 2, 3, 2, 3, 4, 3, 3, }
    elseif champ == "Graves" then       abilitySequence = { 1, 3, 1, 2, 1, 4, 1, 2, 1, 3, 4, 3, 3, 3, 2, 4, 2, 2, }
    elseif champ == "Hecarim" then      abilitySequence = { 1, 2, 1, 3, 1, 4, 1, 2, 1, 2, 4, 2, 2, 3, 3, 4, 3, 3, }
    elseif champ == "Heimerdinger" then abilitySequence = { 1, 2, 2, 1, 1, 4, 3, 2, 2, 2, 4, 1, 1, 3, 3, 4, 1, 1, }
    elseif champ == "Irelia" then       abilitySequence = { 3, 1, 2, 2, 2, 4, 2, 3, 2, 3, 4, 1, 1, 3, 1, 4, 3, 1, }
    elseif champ == "Janna" then        abilitySequence = { 3, 1, 3, 2, 3, 4, 3, 2, 3, 2, 1, 2, 2, 1, 1, 1, 4, 4, }
    elseif champ == "JarvanIV" then     abilitySequence = { 1, 3, 1, 2, 1, 4, 1, 3, 2, 1, 4, 3, 3, 3, 2, 4, 2, 2, }
    elseif champ == "Jax" then          abilitySequence = { 3, 2, 1, 2, 2, 4, 2, 3, 2, 3, 4, 1, 3, 1, 1, 4, 3, 1, }
    elseif champ == "Jayce" then        abilitySequence = { 1, 3, 1, 2, 1, 4, 1, 3, 1, 3, 4, 3, 3, 2, 2, 4, 2, 2, } rOff = -1
    elseif champ == "Karma" then        abilitySequence = { 1, 3, 1, 2, 3, 1, 3, 1, 3, 1, 3, 1, 3, 2, 2, 2, 2, 2, }
    elseif champ == "Karthus" then      abilitySequence = { 1, 3, 2, 1, 1, 4, 1, 1, 3, 3, 4, 3, 3, 2, 2, 4, 2, 2, }
    elseif champ == "Kassadin" then     abilitySequence = { 1, 2, 1, 3, 1, 4, 1, 3, 1, 3, 4, 3, 3, 2, 2, 4, 2, 2, }
    elseif champ == "Katarina" then     abilitySequence = { 1, 3, 2, 2, 2, 4, 2, 3, 2, 1, 4, 1, 1, 1, 3, 4, 3, 3, }
    elseif champ == "Kayle" then        abilitySequence = { 3, 1, 2, 1, 1, 4, 1, 3, 1, 3, 4, 3, 3, 2, 2, 4, 2, 2, }
    elseif champ == "Kennen" then       abilitySequence = { 1, 3, 2, 2, 2, 4, 2, 1, 2, 1, 4, 1, 1, 3, 3, 4, 3, 3, }
    elseif champ == "Khazix" then       abilitySequence = { 1, 3, 1, 2 ,1, 4, 1, 2, 1, 2, 4, 2, 2, 3, 3, 4, 3, 3, }
    elseif champ == "KogMaw" then       abilitySequence = { 2, 3, 2, 1, 2, 4, 2, 1, 2, 1, 4, 1, 1, 3, 3, 4, 3, 3, }
    elseif champ == "Leblanc" then      abilitySequence = { 1, 2, 3, 1, 1, 4, 1, 2, 1, 2, 4, 2, 3, 2, 3, 4, 3, 3, }
    elseif champ == "LeeSin" then       abilitySequence = { 3, 1, 2, 1, 1, 4, 1, 2, 1, 2, 4, 2, 2, 3, 3, 4, 3, 3, }
    elseif champ == "Leona" then        abilitySequence = { 1, 3, 2, 2, 2, 4, 2, 3, 2, 3, 4, 3, 3, 1, 1, 4, 1, 1, }
    elseif champ == "Lissandra" then    abilitySequence = { 1, 3, 1, 2, 1, 4, 1, 2, 1, 2, 4, 2, 2, 3, 3, 4, 3, 3, }
    elseif champ == "Lucian" then       abilitySequence = { 1, 3, 2, 1, 1, 4, 1, 2, 1, 2, 4, 2, 2, 3, 3, 4, 3, 3, }
    elseif champ == "Lulu" then         abilitySequence = { 3, 2, 1, 3, 3, 4, 3, 2, 3, 2, 4, 2, 2, 1, 1, 4, 1, 1, }
    elseif champ == "Lux" then          abilitySequence = { 3, 1, 3, 2, 3, 4, 3, 1, 3, 1, 4, 1, 1, 2, 2, 4, 2, 2, }
    elseif champ == "Malphite" then     abilitySequence = { 1, 3, 1, 2, 1, 4, 1, 3, 1, 3, 4, 3, 2, 3, 2, 4, 2, 2, }
    elseif champ == "Malzahar" then     abilitySequence = { 1, 3, 3, 2, 3, 4, 1, 3, 1, 3, 4, 2, 1, 2, 1, 4, 2, 2, }
    elseif champ == "Maokai" then       abilitySequence = { 3, 1, 2, 3, 3, 4, 3, 2, 3, 2, 4, 2, 2, 1, 1, 4, 1, 1, }
    elseif champ == "MasterYi" then     abilitySequence = { 3, 1, 3, 1, 3, 4, 3, 1, 3, 1, 4, 1, 2, 2, 2, 4, 2, 2, }
    elseif champ == "MissFortune" then  abilitySequence = { 1, 3, 1, 2, 1, 4, 1, 2, 1, 2, 4, 2, 2, 3, 3, 4, 3, 3, }
    elseif champ == "MonkeyKing" then   abilitySequence = { 3, 1, 2, 1, 1, 4, 3, 1, 3, 1, 4, 3, 3, 2, 2, 4, 2, 2, }
    elseif champ == "Mordekaiser" then  abilitySequence = { 3, 1, 3, 2, 3, 4, 3, 1, 3, 1, 4, 1, 1, 2, 2, 4, 2, 2, }
    elseif champ == "Morgana" then      abilitySequence = { 1, 2, 2, 3, 2, 4, 2, 1, 2, 1, 4, 1, 1, 3, 3, 4, 3, 3, }
    elseif champ == "Nami" then         abilitySequence = { 1, 2, 3, 2, 2, 4, 2, 2, 3, 3, 4, 3, 3, 1, 1, 4, 1, 1, }
    elseif champ == "Nasus" then        abilitySequence = { 1, 2, 1, 3, 1, 4, 1, 2, 1, 2, 4, 2, 3, 2, 3, 4, 3, 3, }
    elseif champ == "Nautilus" then     abilitySequence = { 2, 3, 2, 1, 2, 4, 2, 3, 2, 3, 4, 3, 3, 2, 2, 4, 2, 2, }
    elseif champ == "Nidalee" then      abilitySequence = { 1, 3, 1, 2, 1, 4, 1, 3, 1, 3, 4, 3, 3, 2, 2, 4, 2, 2, }
    elseif champ == "Nocturne" then     abilitySequence = { 1, 2, 1, 3, 1, 4, 1, 3, 1, 3, 4, 3, 3, 2, 2, 4, 2, 2, }
    elseif champ == "Nunu" then         abilitySequence = { 1, 3, 1, 2, 1, 4, 3, 1, 3, 1, 4, 3, 3, 2, 2, 4, 2, 2, }
    elseif champ == "Olaf" then         abilitySequence = { 1, 3, 1, 2, 1, 4, 1, 3, 1, 3, 4, 3, 3, 2, 2, 4, 2, 2, }
    elseif champ == "Orianna" then      abilitySequence = { 1, 3, 2, 1, 1, 4, 1, 2, 1, 2, 4, 2, 2, 3, 3, 4, 3, 3, }
    elseif champ == "Pantheon" then     abilitySequence = { 1, 2, 3, 1, 1, 4, 1, 3, 1, 3, 4, 3, 2, 3, 2, 4, 2, 2, }
    elseif champ == "Poppy" then        abilitySequence = { 3, 2, 1, 1, 1, 4, 1, 2, 1, 2, 2, 2, 3, 3, 3, 3, 4, 4, }
    elseif champ == "Quinn" then        abilitySequence = { 3, 1, 1, 2, 1, 4, 1, 3, 1, 3, 4, 3, 3, 2, 2, 4, 2, 2, }
    elseif champ == "Rammus" then       abilitySequence = { 1, 2, 3, 3, 3, 4, 3, 2, 3, 2, 4, 2, 2, 1, 1, 4, 1, 1, }
    elseif champ == "Renekton" then     abilitySequence = { 2, 1, 3, 1, 1, 4, 1, 2, 1, 2, 4, 2, 2, 3, 3, 4, 3, 3, }
    elseif champ == "Rengar" then       abilitySequence = { 1, 3, 2, 1, 1, 4, 2, 1, 1, 2, 4, 2, 2, 3, 3, 4, 3, 3, }
    elseif champ == "Riven" then        abilitySequence = { 1, 2, 3, 2, 2, 4, 2, 3, 2, 3, 4, 3, 3, 1, 1, 4, 1, 1, }
    elseif champ == "Rumble" then       abilitySequence = { 3, 1, 1, 2, 1, 4, 1, 3, 1, 3, 4, 3, 3, 2, 2, 4, 2, 2, }
    elseif champ == "Ryze" then         abilitySequence = { 1, 2, 1, 3, 1, 4, 1, 2, 1, 2, 4, 2, 2, 3, 3, 4, 3, 3, }
    elseif champ == "Sejuani" then      abilitySequence = { 2, 1, 3, 3, 2, 4, 3, 2, 3, 3, 4, 2, 1, 2, 1, 4, 1, 1, }
    elseif champ == "Shaco" then        abilitySequence = { 2, 3, 1, 3, 3, 4, 3, 2, 3, 2, 4, 2, 2, 1, 1, 4, 1, 1, }
    elseif champ == "Shen" then         abilitySequence = { 1, 2, 3, 1, 1, 4, 1, 2, 1, 2, 4, 2, 2, 3, 3, 4, 3, 3, }
    elseif champ == "Shyvana" then      abilitySequence = { 2, 1, 2, 3, 2, 4, 2, 3, 2, 3, 4, 3, 1, 3, 1, 4, 1, 1, }
    elseif champ == "Singed" then       abilitySequence = { 1, 3, 1, 3, 1, 4, 1, 2, 1, 2, 4, 3, 2, 3, 2, 4, 2, 3, }
    elseif champ == "Sion" then         abilitySequence = { 1, 3, 3, 2, 3, 4, 3, 1, 3, 1, 4, 1, 1, 2, 2, 4, 2, 2, }
    elseif champ == "Sivir" then        abilitySequence = { 1, 3, 1, 2, 1, 4, 1, 2, 1, 2, 4, 2, 3, 2, 3, 4, 3, 3, }
    elseif champ == "Skarner" then      abilitySequence = { 1, 2, 1, 2, 1, 4, 1, 2, 1, 2, 4, 2, 3, 3, 3, 4, 3, 3, }
    elseif champ == "Sona" then         abilitySequence = { 1, 2, 3, 1, 1, 4, 1, 2, 1, 2, 4, 2, 2, 3, 3, 4, 3, 3, }
    elseif champ == "Soraka" then       abilitySequence = { 1, 3, 1, 2, 1, 4, 1, 2, 1, 3, 4, 2, 3, 2, 3, 4, 2, 3, }
    elseif champ == "Swain" then        abilitySequence = { 2, 3, 3, 1, 3, 4, 3, 1, 3, 1, 4, 1, 1, 2, 2, 4, 2, 2, }
    elseif champ == "Syndra" then       abilitySequence = { 1, 3, 1, 2, 1, 4, 1, 3, 1, 3, 4, 3, 3, 2, 2, 4, 2, 2, }
    elseif champ == "Talon" then        abilitySequence = { 2, 3, 1, 2, 2, 4, 2, 1, 2, 1, 4, 1, 1, 3, 3, 4, 3, 3, }
    elseif champ == "Taric" then        abilitySequence = { 3, 2, 1, 2, 2, 4, 1, 2, 2, 1, 4, 1, 1, 3, 3, 4, 3, 3, }
    elseif champ == "Teemo" then        abilitySequence = { 1, 3, 2, 3, 3, 4, 1, 3, 1, 3, 4, 1, 1, 2, 2, 4, 2, 2, }
    elseif champ == "Thresh" then       abilitySequence = { 1, 3, 2, 2, 2, 4, 2, 3, 2, 3, 4, 3, 3, 1, 1, 4, 1, 1, }
    elseif champ == "Tristana" then     abilitySequence = { 3, 2, 2, 3, 2, 4, 2, 1, 2, 1, 4, 1, 1, 1, 3, 4, 3, 3, }
    elseif champ == "Trundle" then      abilitySequence = { 1, 2, 1, 3, 1, 4, 1, 2, 1, 3, 4, 2, 3, 2, 3, 4, 2, 3, }
    elseif champ == "Tryndamere" then   abilitySequence = { 3, 1, 2, 1, 1, 4, 1, 2, 1, 2, 4, 2, 2, 3, 3, 4, 3, 3, }
    elseif champ == "TwistedFate" then  abilitySequence = { 2, 1, 1, 3, 1, 4, 1, 2, 1, 2, 4, 2, 2, 3, 3, 4, 3, 3, }
    elseif champ == "Twitch" then       abilitySequence = { 1, 3, 3, 2, 3, 4, 3, 1, 3, 1, 4, 1, 1, 2, 2, 1, 2, 2, }
    elseif champ == "Udyr" then         abilitySequence = { 4, 2, 3, 4, 4, 2, 4, 2, 4, 2, 2, 1, 3, 3, 3, 3, 1, 1, }
    elseif champ == "Urgot" then        abilitySequence = { 3, 1, 1, 2, 1, 4, 1, 2, 1, 3, 4, 2, 3, 2, 3, 4, 2, 3, }
    elseif champ == "Varus" then        abilitySequence = { 1, 2, 3, 1, 1, 4, 1, 2, 1, 2, 4, 2, 2, 3, 3, 4, 3, 3, }
    elseif champ == "Vayne" then        abilitySequence = { 1, 3, 2, 1, 1, 4, 1, 3, 1, 3, 4, 3, 3, 2, 2, 4, 2, 2, }
    elseif champ == "Veigar" then       abilitySequence = { 1, 3, 1, 2, 1, 4, 2, 2, 2, 2, 4, 3, 1, 1, 3, 4, 3, 3, }
    elseif champ == "Vi" then           abilitySequence = { 3, 1, 2, 3, 3, 4, 3, 1, 3, 1, 4, 1, 1, 2, 2, 4, 2, 2, }
    elseif champ == "Viktor" then       abilitySequence = { 3, 2, 3, 1, 3, 4, 3, 1, 3, 1, 4, 1, 2, 1, 2, 4, 2, 2, }
    elseif champ == "Vladimir" then     abilitySequence = { 1, 2, 1, 3, 1, 4, 1, 3, 1, 3, 4, 3, 3, 2, 2, 4, 2, 2, }
    elseif champ == "Volibear" then     abilitySequence = { 2, 3, 2, 1, 2, 4, 3, 2, 1, 2, 4, 3, 1, 3, 1, 4, 3, 1, }
    elseif champ == "Warwick" then      abilitySequence = { 2, 1, 1, 2, 1, 4, 1, 3, 1, 3, 4, 3, 3, 3, 2, 4, 2, 2, }
    elseif champ == "Xerath" then       abilitySequence = { 1, 3, 1, 2, 1, 4, 1, 2, 1, 2, 4, 2, 2, 3, 3, 4, 3, 3, }
    elseif champ == "XinZhao" then      abilitySequence = { 1, 3, 1, 2, 1, 4, 1, 2, 1, 2, 4, 2, 2, 3, 3, 4, 3, 3, }
    elseif champ == "Yorick" then       abilitySequence = { 2, 3, 1, 3, 3, 4, 3, 2, 3, 1, 4, 2, 1, 2, 1, 4, 2, 1, }
    elseif champ == "Zac" then          abilitySequence = { 1, 2, 3, 1, 1, 4, 1, 3, 1, 3, 4, 3, 3, 2, 2, 4, 2, 2, }
    elseif champ == "Zed" then          abilitySequence = { 1, 2, 3, 1, 1, 4, 1, 3, 1, 3, 4, 3, 3, 2, 2, 4, 2, 2, }
    elseif champ == "Ziggs" then        abilitySequence = { 1, 2, 3, 1, 1, 4, 1, 3, 1, 3, 4, 3, 3, 2, 2, 4, 2, 2, }
    elseif champ == "Zilean" then       abilitySequence = { 1, 2, 1, 3, 1, 4, 1, 2, 1, 2, 4, 2, 2, 3, 3, 4, 3, 3, }
    elseif champ == "Zyra" then         abilitySequence = { 3, 2, 1, 1, 1, 4, 1, 3, 1, 3, 4, 3, 3, 2, 2, 4, 2, 2, }
    else PrintChat(string.format(" >> 鑷姩鍗囩骇鍔犵偣鏃犳硶搴旂敤浜?  %s", champ))
    end
    if abilitySequence and #abilitySequence == 18 then
        --PrintChat(" >> AutoLevelSpell Script loaded!")
    else
        PrintChat(" >> 鑷姩鍗囩骇鍔犵偣鎶€鑳介『搴忛敊璇紝璇峰弽棣?")
        AutoLevelExhOnTick = function() end
        return
    end
end
-- #############################################  AutoLevel ##############################################

-- ######################################  AUTO SMITE  ###################################################
--[[
	AutoSmite 3.1
		by eXtragoZ

		Features:
			- Hotkey for switching AutoSmite On/Off (default: N)
			- Hold-Hotkey for using AutoSmite (default: CTRL)
			- Range indicator of smite
			- A bar that indicates at what life can be smited in the hp bar
			- The damage that smite will do to the monster using smite in the hp bar
			- Supports Nunu Q and Chogath R

2.0 : Smiteable targets will now be highlighted if you are in range
	: Different colors for the highlighting when smite is on cooldown
	: Added Nashor smite spot
2.1	: Added Range indicator of smite
	: Added options on the menu Nashor spot, Draw Circles and Draw Text
	: Now says the percentage of life remaining will be left after use smite , Q and R in case of Nunu or Chogath
	: Added Vilemaw of Twisted Treeline
	: Removed Blue Dragon and Lizard Elder of Twisted Treeline
2.5	: Smite damage increased to 490-1000
	: Added new method to go to Nashor spot, right click on the circle next to the wall of Nashor
	: Added option to always smite Nashor
	: Added option to draw smite range (separated from the option to draw circles)
	: Now the range of smite and the circles in the camps disappear when AutoSmite is off
	: Now the circles in the camps disappear when AutoSmite is on CD, if you are Nunu or Chogath the respective skills must be on CD
	: New function of the circles in the camps:
		The green circle indicates the percentage of current life
		The purple circle indicates the percentage of life necessary to use smite
		If you are Nunu or Chogath the respective skills have a circle ((Q + Smite) or Q for Nunu or (Smite + R) or R for ChoGath) depending if Smite is in CD
2.6	: Now Says the percentage of current life you will do to the monster using smite
2.7 : Removed option to go to Nashor spot, does not work anymore
	: AutoSmite will start on by default if you have Smite
3.0 : Removed
		Circles in the camps
		The percentage of current life you will do to the monster using smite
	: Re did part of the code, now it uses minionManager
	: Added Smite and Draw options for every camp / monster
	: Now shows information in the hp bar
		A bar that indicates at what life can be smited
		The damage that smite will do to the monster using smite
		It highlight the hp bar and the damage when its at the right health
		The bar and the damage gets transparency when smite is on CD, its out of range or disabled
]]
--[[            Config          ]]
local range = 780		-- Range of smite (~800)
local turnoff = false	--true/false
--[[            Globals         ]]
local smiteSlot = nil
local jungleMonsters = {}

local smiteDamage, qDamage, mixDamage, rDamage, mixdDamage = 0, 0, 0, 0, 0
local canuseQ,canuseR,canusesmite = false,false,false
local Smiteison = false
local GameMap = 0

--[[            Code            ]]
function OnLoad()
	if myHero:GetSpellData(SUMMONER_1).name:find("Smite") then smiteSlot = SUMMONER_1
    elseif myHero:GetSpellData(SUMMONER_2).name:find("Smite") then smiteSlot = SUMMONER_2 end
	if myHero.charName == "Nunu" or myHero.charName == "Chogath" or smiteSlot or not turnoff then
		SmiteConfig = scriptConfig("[多合一]自动惩戒 3.1", "autosmite")
		SmiteConfig:addParam("switcher", "切换热键", SCRIPT_PARAM_ONKEYTOGGLE, (smiteSlot ~= nil), 78)
		SmiteConfig:addParam("hold", "按住热键", SCRIPT_PARAM_ONKEYDOWN, false, 17)
		SmiteConfig:addParam("active", "自动惩戒", SCRIPT_PARAM_INFO, false)
		SmiteConfig:addParam("smitenashor", "自动惩戒 男爵", SCRIPT_PARAM_ONOFF, true)
		SmiteConfig:addParam("drawrange", "显示惩戒范围", SCRIPT_PARAM_ONOFF, true)
		SmiteConfig:addParam("drawcircles", "显示圆圈", SCRIPT_PARAM_ONOFF, true)
		SmiteConfig:addParam("drawtext", "显示文本", SCRIPT_PARAM_ONOFF, true)
		SmiteConfig:addSubMenu("惩戒设置", "smiteat")
		SmiteConfig.smiteat:addParam("Worm", "大龙", SCRIPT_PARAM_ONOFF, true)
		SmiteConfig.smiteat:addParam("Dragon", "小龙", SCRIPT_PARAM_ONOFF, true)
		SmiteConfig.smiteat:addParam("AncientGolem", "远古魔像", SCRIPT_PARAM_ONOFF, true)
		SmiteConfig.smiteat:addParam("LizardElder", "蜥蜴长老", SCRIPT_PARAM_ONOFF, true)
		SmiteConfig.smiteat:addParam("GiantWolf", "巨狼", SCRIPT_PARAM_ONOFF, false)
		SmiteConfig.smiteat:addParam("GreatWraith", "鬼魂", SCRIPT_PARAM_ONOFF, false)
		SmiteConfig.smiteat:addParam("Wraith", "幽灵", SCRIPT_PARAM_ONOFF, false)
		SmiteConfig.smiteat:addParam("Golem", "魔像", SCRIPT_PARAM_ONOFF, false)
		SmiteConfig.smiteat:addParam("TTSpiderboss", "TT蜘蛛BOSS", SCRIPT_PARAM_ONOFF, true)
		SmiteConfig.smiteat:addParam("TTNGolem", "TT魔像", SCRIPT_PARAM_ONOFF, true)
		SmiteConfig.smiteat:addParam("TTNWolf", "TT狼", SCRIPT_PARAM_ONOFF, true)
		SmiteConfig.smiteat:addParam("TTNWraith", "TT幽灵", SCRIPT_PARAM_ONOFF, true)
		SmiteConfig:addSubMenu("范围信息", "drawinfo")
		SmiteConfig.drawinfo:addParam("Worm", "大龙", SCRIPT_PARAM_ONOFF, true)
		SmiteConfig.drawinfo:addParam("Dragon", "小龙", SCRIPT_PARAM_ONOFF, true)
		SmiteConfig.drawinfo:addParam("AncientGolem", "远古魔像", SCRIPT_PARAM_ONOFF, true)
		SmiteConfig.drawinfo:addParam("LizardElder", "蜥蜴长老", SCRIPT_PARAM_ONOFF, true)
		SmiteConfig.drawinfo:addParam("GiantWolf", "巨狼", SCRIPT_PARAM_ONOFF, true)
		SmiteConfig.drawinfo:addParam("GreatWraith", "鬼魂", SCRIPT_PARAM_ONOFF, true)
		SmiteConfig.drawinfo:addParam("Wraith", "小幽灵", SCRIPT_PARAM_ONOFF, true)
		SmiteConfig.drawinfo:addParam("Golem", "魔像", SCRIPT_PARAM_ONOFF, true)
		SmiteConfig.drawinfo:addParam("YoungLizard", "小蜥蜴", SCRIPT_PARAM_ONOFF, false)
		SmiteConfig.drawinfo:addParam("Wolf", "狼", SCRIPT_PARAM_ONOFF, false)
		SmiteConfig.drawinfo:addParam("LesserWraith", "小幽灵", SCRIPT_PARAM_ONOFF, false)
		SmiteConfig.drawinfo:addParam("SmallGolem", "小魔像", SCRIPT_PARAM_ONOFF, false)
		SmiteConfig.drawinfo:addParam("TTSpiderboss", "TT蜘蛛BOSS", SCRIPT_PARAM_ONOFF, true)
		SmiteConfig.drawinfo:addParam("TTNGolem", "TT魔像", SCRIPT_PARAM_ONOFF, true)
		SmiteConfig.drawinfo:addParam("TTNWolf", "TT巨狼", SCRIPT_PARAM_ONOFF, true)
		SmiteConfig.drawinfo:addParam("TTNWraith", "TT幽灵", SCRIPT_PARAM_ONOFF, true)
		SmiteConfig.drawinfo:addParam("TTNGolem2", "TT小魔像", SCRIPT_PARAM_ONOFF, false)
		SmiteConfig.drawinfo:addParam("TTNWraith2", "TT小幽灵", SCRIPT_PARAM_ONOFF, false)
		SmiteConfig.drawinfo:addParam("TTNWolf2", "TT小狼", SCRIPT_PARAM_ONOFF, false)
		SmiteConfig:permaShow("active")
		jungleMonsters = minionManager(MINION_JUNGLE, 1000000)
		GameMap = GetGame().map.index
		Smiteison = true
		--PrintChat(" >> 鑷姩鎯╂垝 3.1 loaded!")
	end
end

function OnTick()
	if not Smiteison then return end
	jungleMonsters:update()
	SmiteConfig.active = ((SmiteConfig.hold and not SmiteConfig.switcher) or (not SmiteConfig.hold and SmiteConfig.switcher))
	if not SmiteConfig.active and SmiteConfig.smitenashor then
		if GameMap == 1 and GetDistance({x=4543,y=0,z=10234}) <= 850 then
			SmiteConfig.active = true
		elseif GameMap == 10 and GetDistance({x=7687,y=0,z=9921}) <= 1000 then
			SmiteConfig.active = true
		end
	end
	smiteDamage = math.max(20*myHero.level+370,30*myHero.level+330,40*myHero.level+240,50*myHero.level+100)
	qDamage = 250+150*myHero:GetSpellData(_Q).level
	mixDamage = qDamage+smiteDamage
	rDamage = 1000+.7*myHero.ap
	mixdDamage = rDamage+smiteDamage
	canuseQ = (myHero.charName == "Nunu" and myHero:CanUseSpell(_Q) == READY)
	canuseR = (myHero.charName == "Chogath" and myHero:CanUseSpell(_R) == READY)
	if smiteSlot ~= nil then canusesmite = (myHero:CanUseSpell(smiteSlot) == READY) end
	if SmiteConfig.active and not myHero.dead and (canusesmite or canuseQ or canuseR) then
		for i,monster in pairs(jungleMonsters.objects) do
			if monster ~= nil and monster.valid and not monster.dead and monster.visible and monster.x ~= nil and monster.health > 0 and monster.charName ~= "HA_AP_Poro" and monster.charName ~= "TestCubeRender" and monster.charName ~= "TT_Buffplat_R" and monster.charName ~= "TT_Buffplat_L" then
				if SmiteConfig.smiteat[monster.charName:gsub("_", "")] then
					checkMonster(monster)
				end
			end
		end	
	end
end
function checkMonster(object)
	local DistanceMonster = GetDistance(object)
	if canusesmite and DistanceMonster <= range and object.health <= smiteDamage then
		CastSpell(smiteSlot, object)
	elseif canuseQ and DistanceMonster <= 125+200 then
		if canusesmite and object.health <= mixDamage then
			CastSpell(_Q, object)
		elseif object.health <= qDamage then
			CastSpell(_Q, object)
		end
	elseif canuseR and DistanceMonster <= 150+200 then
		if canusesmite and object.health <= mixdDamage then
			CastSpell(_R, object)
		elseif object.health <= rDamage then
			CastSpell(_R, object)
		end
	end
end
function OnDraw()
	if not Smiteison then return end
	if smiteSlot ~= nil and SmiteConfig.active and SmiteConfig.drawrange and not myHero.dead then
		DrawCircle(myHero.x, myHero.y, myHero.z, range, 0x992D3D)
	end
	if not myHero.dead and (SmiteConfig.drawtext or SmiteConfig.drawcircles) then
		for i,monster in pairs(jungleMonsters.objects) do
			if monster ~= nil and monster.valid and not monster.dead and monster.visible and monster.x ~= nil and monster.health > 0 and monster.charName ~= "HA_AP_Poro" and monster.charName ~= "TestCubeRender" and monster.charName ~= "TT_Buffplat_R" and monster.charName ~= "TT_Buffplat_L" then
				if SmiteConfig.drawinfo[monster.charName:gsub("_", "")] then
					MonsterDraw(monster)
				end
			end
		end
	end
end
function MonsterDraw(minion)
	local isEpicMonster = minion.charName == "Dragon" or minion.charName == "Worm" or minion.charName == "TT_Spiderboss"
	local barPos = GetUnitHPBarPos(minion)
	barPos.x = math.floor(barPos.x - 32)
	barPos.y = math.floor(barPos.y - 3)
	local maxDistance = 62
	if minion.charName == "Dragon" then
		barPos.x = barPos.x - 31
		barPos.y = barPos.y - 7
		maxDistance = 124
	elseif minion.charName == "Worm" then
		barPos.x = barPos.x - 31
		maxDistance = 124
	elseif minion.charName == "TT_Spiderboss" then
		barPos.x = barPos.x - 31
		maxDistance = 124
	end
	if isEpicMonster then
		DrawRectangle(barPos.x + 57, barPos.y - 10, 35, 10, ARGB(255,0,0,0))
		DrawText(tostring(math.floor(minion.health)), 12, barPos.x + 60, barPos.y - 12, ARGB(255, 255, 255, 255))
	end
	local SmiteDistance = smiteDamage / minion.maxHealth * maxDistance
	local alphaSmite = (canusesmite and SmiteConfig.active and GetDistance(minion) <= range) and 255 or 100
	DrawLine(barPos.x + SmiteDistance, barPos.y + 1, barPos.x + SmiteDistance, barPos.y + 5, 1, ARGB(alphaSmite,0,252,255))
	DrawRectangle(barPos.x + SmiteDistance - 8, barPos.y - 10, 20, 10, ARGB(alphaSmite,0,0,0))
	DrawText(tostring(smiteDamage), 11, barPos.x + SmiteDistance - 6, barPos.y - 11, ARGB(alphaSmite,0,252,255))
	if smiteDamage >= minion.health then
		DrawOutline(barPos.x-1, barPos.y-1, maxDistance+3, 7, ARGB(150,0,252,255))
		DrawOutline(barPos.x + SmiteDistance - 8, barPos.y - 10, 20, 9, ARGB(150,0,252,255))
	end
	if myHero.charName == "Nunu" and myHero:GetSpellData(_Q).level > 0 then
		local QDistance = qDamage / minion.maxHealth * maxDistance
		local alphaQ = (canuseQ and SmiteConfig.active and GetDistance(minion) <= range) and 255 or 100
		local alphaQSmite = (canusesmite and canuseQ and SmiteConfig.active and GetDistance(minion) <= range) and 255 or 100
		DrawLine(barPos.x + QDistance, barPos.y + 1, barPos.x + QDistance, barPos.y + 5, 1, ARGB(alphaQ,0,252,255))
		DrawRectangle(barPos.x + QDistance - 16, barPos.y + 7, 20, 10, ARGB(alphaQ,0,0,0))
		DrawText(tostring(qDamage), 11, barPos.x + QDistance - 14, barPos.y + 7, ARGB(alphaQ,0,252,255))
		DrawLine(barPos.x + QDistance + SmiteDistance, barPos.y + 1, barPos.x + QDistance + SmiteDistance, barPos.y + 5, 1, ARGB(alphaQSmite,0,252,255))
		DrawRectangle(barPos.x + QDistance + SmiteDistance, barPos.y + 7, 20, 10, ARGB(alphaQSmite,0,0,0))
		DrawText(tostring(mixDamage), 11, barPos.x + QDistance + SmiteDistance + 2, barPos.y + 7, ARGB(alphaQSmite,0,252,255))
		if mixDamage >= minion.health then
			local alphaBorder = qDamage >= minion.health and 255 or 150
			DrawOutline(barPos.x-1, barPos.y-1, maxDistance+2, 7, ARGB(alphaBorder,0,252,255))
			DrawOutline(barPos.x + QDistance + SmiteDistance, barPos.y + 7, 20, 10, ARGB(150,0,252,255))
			if qDamage >= minion.health then
				DrawOutline(barPos.x + QDistance - 16, barPos.y + 7, 20, 10, ARGB(150,0,252,255))
			end
		end
	end
	if myHero.charName == "Chogath" and myHero:GetSpellData(_R).level > 0 then
		local RDistance = rDamage / minion.maxHealth * maxDistance
		local alphaR = (canuseR and SmiteConfig.active and GetDistance(minion) <= range) and 255 or 100
		local alphaRSmite = (canusesmite and canuseR and SmiteConfig.active and GetDistance(minion) <= range) and 255 or 100
		DrawLine(barPos.x + RDistance, barPos.y + 1, barPos.x + RDistance, barPos.y + 5, 1, ARGB(alphaR,0,252,255))
		DrawRectangle(barPos.x + RDistance - 16, barPos.y + 7, 20, 10, ARGB(alphaR,0,0,0))
		DrawText(tostring(rDamage), 11, barPos.x + RDistance - 14, barPos.y + 7, ARGB(alphaR,0,252,255))
		DrawLine(barPos.x + RDistance + SmiteDistance, barPos.y + 1, barPos.x + RDistance + SmiteDistance, barPos.y + 5, 1, ARGB(alphaRSmite,0,252,255))
		DrawRectangle(barPos.x + RDistance + SmiteDistance, barPos.y + 7, 20, 10, ARGB(alphaRSmite,0,0,0))
		DrawText(tostring(mixdDamage), 11, barPos.x + RDistance + SmiteDistance + 2, barPos.y + 7, ARGB(alphaRSmite,0,252,255))
		if mixdDamage >= minion.health then
			local alphaBorder = rDamage >= minion.health and 255 or 150
			DrawOutline(barPos.x-1, barPos.y-1, maxDistance+2, 7, ARGB(alphaBorder,0,252,255))
			DrawOutline(barPos.x + RDistance + SmiteDistance, barPos.y + 7, 20, 10, ARGB(150,0,252,255))
			if rDamage >= minion.health then
				DrawOutline(barPos.x + RDistance - 16, barPos.y + 7, 20, 10, ARGB(150,0,252,255))
			end
		end
	end
end
function DrawOutline(x, y, width, height, color)
	DrawLine(x, 		y, 			x + width + 1, y, 1, color)
	DrawLine(x, 		y, 			x, 				y + height, 1, color)
	DrawLine(x + width, y, 			x + width, 		y + height, 1, color)
	DrawLine(x, 		y + height, x + width + 1, y + height, 1, color)
end
-- ######################################  AUTO SMITE  ###################################################

-- ######################################  WAITEEE  ######################################################
--[[
    Waiteee aka Wait For It! v0.2
        by Weee

    Shows the countdowns of stuff like zilean's ultimate, tryndamere's ultimate, GA, zhonya, aatrox's passive and so on.
    Full list:
        - Zilean's Ultimate (before death)
        - Zilean's Ultimate (after death, same as GA)
        - Guardian Angel
        - Zhonya's Hourglass
        - Aatrox's Passive
        - Kayle's Ultimate
        - Tryndamere's Ultimate
        - Anivia's Egg
]]

immuneTable = {
    { "zhonyas_ring_activate.troy", 2.5 },              -- Zhonya
    { "Aatrox_Passive_Death_Activate.troy", 3 },        -- Aatrox Passive
    { "LifeAura.troy", 4 },                             -- GA and Zil Ulti after death
    { "nickoftime_tar.troy", 7 },                       -- Zil Ulti before death
    { "eyeforaneye_self.troy", 2 },                     -- Kayle Ulti (self?)
    { "UndyingRage_buf.troy", 5 },                      -- Tryn Ulti
    { "EggTimer.troy", 6 },                             -- Anivia Egg
}

function WaiteeeOnLoad()
    startTick = GetGame().tick
    
    WConfig = scriptConfig("[多合一]无敌计时", "waiteee")
    WConfig:addParam("ShowAlly", "显示盟友无敌时间", SCRIPT_PARAM_ONOFF, true)
    WConfig:addParam("ShowEnemy", "显示敌方无敌时间", SCRIPT_PARAM_ONOFF, true)
    WConfig:addParam("UseTimerText", "计时显示方式: 0:02 (开启); 2 (关闭)", SCRIPT_PARAM_ONOFF, false)
    
    heroTable = {}
    for i = 1, heroManager.iCount do
        local hero = heroManager:GetHero(i)
        hero.immune = { endTime = 0, floatSec = 0, text = "" }
        table.insert(heroTable, hero)
    end
    --PrintChat("Waiteee aka Wait For It! v0.2 loaded.")
end

function WaiteeeOnCreateObj(object)
    for i, hero in pairs(heroTable) do
        for j, immune in pairs(immuneTable) do
            if object and object.valid and GetDistance(object,hero) <= 80 and object.name == immune[1] then
                hero.immune.endTime = GameTime + immune[2]
                hero.immune.floatSec = immune[2]
            end
        end
    end
end

function WaiteeeOnTick()
    GameTime = GetInGameTimer()

    for i, hero in pairs(heroTable) do
        if ((WConfig.ShowAlly and hero.team == player.team) or (WConfig.ShowEnemy and hero.team ~= player.team)) and hero.immune.endTime+0.1 >= GameTime then
            local secondsLeft = math.ceil(math.max(0, hero.immune.endTime - GameTime))
            if hero.immune.floatSec >= secondsLeft and hero.immune.text ~= TimerText(secondsLeft) then
                hero.immune.floatSec = secondsLeft - 1
                hero.immune.text = "" .. ((WConfig.UseTimerText and TimerText(secondsLeft)) or secondsLeft)
                PrintFloatText(hero, 10, hero.immune.text)
            end
        end
    end
end
-- ######################################  WAITEEE  ######################################################

-- ############################################# TOWER RANGE ################################################

--[[
	Script: Tower Range v0.4
	Author: SurfaceS

	v0.1 	initial release -- thanks Shoot for idea
	V0.1b	added mode 4 -- thanks hellspan
	v0.1c	added gameOver to stop script at end
	v0.2	BoL Studio version
	v0.3	use the scriptConfig
	v0.4    Tower ranges now show ally and enemy tower range when you are in range
    v0.4a   Tower range changed in S3
]]

local towerRange = {
	turrets = {},
	typeText = {"OFF", "ON (enemy close)", "ON (enemy)", "ON (all)", "ON (all close)"},
	--[[         Config         ]]
	turretRange = 975,	 				-- 950-S3 updates to 975
	fountainRange = 1050,	 			-- 1050
	allyTurretColor = 0x003300, 		-- Green color
	enemyTurretColor = 0xFF0000, 		-- Red color
--	activeType = 4,						-- 0 Off, 1 Close enemy towers, 2 All enemy towers, 3 Show all, 4 Show all close
	tickUpdate = 1000,
	nextUpdate = 0,
}

function	TowerRangeMenu()
		TRConfig = scriptConfig("[多合一]塔攻击范围", "TowerRange")
		TRConfig:addParam("ActiveType", "显示方式", SCRIPT_PARAM_SLICE, 4 , 0 , 4 , 0)
		TRConfig:addParam("desc", "-----说明-------------", SCRIPT_PARAM_INFO,"" )			
		TRConfig:addParam("desc", "方式0：关闭显示", SCRIPT_PARAM_INFO,"" )		
		TRConfig:addParam("desc", "方式1：附近的敌方塔", SCRIPT_PARAM_INFO,"" )
		TRConfig:addParam("desc", "方式2：所有敌方塔", SCRIPT_PARAM_INFO,"" )
		TRConfig:addParam("desc", "方式3：所有的塔", SCRIPT_PARAM_INFO,"" )
		TRConfig:addParam("desc", "方式4：附近的塔", SCRIPT_PARAM_INFO,"" )
end

function towerRange.checkTurretState()
	if TRConfig.ActiveType > 0 then
		for name, turret in pairs(towerRange.turrets) do
			turret.active = false
		end
		for i = 1, objManager.maxObjects do
			local object = objManager:getObject(i)
			if object ~= nil and object.type == "obj_AI_Turret" then
				local name = object.name
				if towerRange.turrets[name] ~= nil then towerRange.turrets[name].active = true end
			end
		end
		for name, turret in pairs(towerRange.turrets) do
			if turret.active == false then towerRange.turrets[name] = nil end
		end
	end
end

function TowerRangeOnDraw()
	if GetGame().isOver then return end
	if TRConfig.ActiveType > 0 then
		for name, turret in pairs(towerRange.turrets) do
			if turret ~= nil then
				if (TRConfig.ActiveType == 1 and turret.team ~= player.team and player.dead == false and GetDistance(turret) < 2000)
				or (TRConfig.ActiveType == 2 and turret.team ~= player.team)
				or (TRConfig.ActiveType == 3)
				or (TRConfig.ActiveType == 4 and player.dead == false and GetDistance(turret) < 2000) then
					DrawCircle(turret.x, turret.y, turret.z, turret.range, turret.color)
				end
			end
		end
	end
end
function TowerRangeOnTick()
end
function TowerRangeOnDeleteObj(object)
	if object ~= nil and object.type == "obj_AI_Turret" then
		for name, turret in pairs(towerRange.turrets) do
			if name == object.name then
				towerRange.turrets[name] = nil
				return
			end
		end
	end
end
function TowerRangeOnLoad()
	gameState = GetGame()
	TowerRangeMenu()
	
	for i = 1, objManager.maxObjects do
		local object = objManager:getObject(i)
		if object ~= nil and object.type == "obj_AI_Turret" then
			local turretName = object.name
			towerRange.turrets[turretName] = {
				object = object,
				team = object.team,
				color = (object.team == player.team and towerRange.allyTurretColor or towerRange.enemyTurretColor),
				range = towerRange.turretRange,
				x = object.x,
				y = object.y,
				z = object.z,
				active = false,
			}
			if turretName == "Turret_OrderTurretShrine_A" or turretName == "Turret_ChaosTurretShrine_A" then
				towerRange.turrets[turretName].range = towerRange.fountainRange
				for j = 1, objManager.maxObjects do
					local object2 = objManager:getObject(j)
					if object2 ~= nil and object2.type == "obj_SpawnPoint" and GetDistance(object, object2) < 1000 then
						towerRange.turrets[turretName].x = object2.x
						towerRange.turrets[turretName].z = object2.z
					elseif object2 ~= nil and object2.type == "obj_HQ" and object2.team == object.team then
						towerRange.turrets[turretName].y = object2.y
					end
				end
			end
		end
	end
end

-- ############################################# TOWER RANGE ################################################



-- ############################################# Auto Potion/Zhonyas/Wooglets ################################################

function AutoHMZWOnLoad()
        AHMZWConfig = scriptConfig("[多合一]自动 吃药/中亚/巫师帽", "AutoHMZW") 
		AHMZWConfig:addParam("ZWItems", "自动 中亚/巫师帽", SCRIPT_PARAM_ONOFF, true)
        AHMZWConfig:addParam("ZWHealth", "中亚/巫师帽 血量<%", SCRIPT_PARAM_SLICE, 25, 0, 100, 0)
        AHMZWConfig:addParam("ZWEnemys", "中亚/巫师帽 附近敌人>?", SCRIPT_PARAM_SLICE, 1, 0, 5, 0)
		AHMZWConfig:addParam("s1", "", SCRIPT_PARAM_INFO,"" )			
        AHMZWConfig:addParam("aHP", "自动生命药水", SCRIPT_PARAM_ONOFF, true)
        AHMZWConfig:addParam("aHPHealth", "生命药水 血量<%", SCRIPT_PARAM_SLICE, 50, 0, 100, 0)
		AHMZWConfig:addParam("s2", "", SCRIPT_PARAM_INFO,"" )		
        AHMZWConfig:addParam("aMP", "自动法力药水", SCRIPT_PARAM_ONOFF, true)
        AHMZWConfig:addParam("aMPMana", "法力药水 蓝量<%", SCRIPT_PARAM_SLICE, 50, 0, 100, 0)
		AHMZWConfig:addParam("s3", "提示:当红,蓝药不足时,自动水晶瓶/饼干", SCRIPT_PARAM_INFO,"" )		
end

function AutoZWOnTick()
	BuffCheck()
	if aRecall or InFountain() then return end
	znaSlot, wgtSlot = GetInventorySlotItem(3157),GetInventorySlotItem(3090)
    hpSlot, mpSlot, fskSlot, biscuitSlot = GetInventorySlotItem(2003),GetInventorySlotItem(2004),GetInventorySlotItem(2041),GetInventorySlotItem(2010)
	
    ZNAREADY = (znaSlot ~= nil and myHero:CanUseSpell(znaSlot) == READY)
    WGTREADY = (wgtSlot ~= nil and myHero:CanUseSpell(wgtSlot) == READY)
    HPREADY = (hpSlot ~= nil and myHero:CanUseSpell(hpSlot) == READY)
    MPREADY =(mpSlot ~= nil and myHero:CanUseSpell(mpSlot) == READY)
    FSKREADY = (fskSlot ~= nil and myHero:CanUseSpell(fskSlot) == READY)
    BISREADY = (biscuitSlot ~= nil and myHero:CanUseSpell(biscuitSlot) == READY)	
		
    if AHMZWConfig.ZWItems and IsZWHealthLow() and (countNearbyAlies()>=AHMZWConfig.ZWEnemys) and (ZNAREADY or WGTREADY) then CastSpell((wgtSlot or znaSlot)) end
    if AHMZWConfig.aHP and IsHPHealthLow() and not (UsingHPot or UsingBiscuit or UsingFlask) and (HPREADY or BISREADY or FSKREADY ) then CastSpell((hpSlot or  biscuitSlot or fskSlot)) end
    if AHMZWConfig.aMP and IsMPManaLow() and not (UsingMPot or UsingFlask) and(MPREADY  or FSKREADY ) then CastSpell((mpSlot  or fskSlot)) end	
end

function BuffCheck()
	if 	TargetHaveBuff({"Recall","SummonerTeleport","RecallImproved"}) then 
	     aRecall = true
	else
	     aRecall = false	
	end
	
	if 	TargetHaveBuff({"ItemCrystalFlask"}) then 
	     UsingFlask = true
	else
	     UsingFlask = false	
	end
	
	if 	TargetHaveBuff({"RegenerationPotion"}) then 
	     UsingHPot = true
	else
	     UsingHPot = false	
	end	

	if 	TargetHaveBuff({"FlaskOfCrystalWater"}) then 
	     UsingMPot = true
	else
	     UsingMPot = false	
	end		

	if 	TargetHaveBuff({"ItemMiniRegenPotion"}) then 
	     UsingBiscuit = true
	else
	     UsingBiscuit = false	
	end		
end

function countNearbyAlies()
        local nearbyHeroes = 0
        for i = 1, heroManager.iCount, 1 do
                local hero = heroManager:getHero(i)
                if hero ~= nil and hero.team ~= TEAM_ENEMY and hero.dead == false then
                        if math.sqrt((hero.x - player.x) ^ 2 + (hero.z - player.z) ^ 2) < 585 then
                                nearbyHeroes = nearbyHeroes + 1
                        end    
                end
        end
        return nearbyHeroes
end

function IsZWHealthLow()
        if myHero.health < (myHero.maxHealth * ( AHMZWConfig.ZWHealth / 100)) then
                return true
        else
                return false
        end
end

function IsHPHealthLow()
        if myHero.health < (myHero.maxHealth * ( AHMZWConfig.aHPHealth / 100)) then
                return true
        else
                return false
        end
end

function IsMPManaLow()
        if myHero.mana < (myHero.maxMana * ( AHMZWConfig.aMPMana / 100)) then
                return true
        else
                return false
        end
end

-- ############################################# Auto Potion/Zhonyas/Wooglets ################################################	
	
	
-- ############################################# Hidden Objects ##############################################	

--[[
        Script: Hidden Objects Display v0.4
        Author: SurfaceS (up to v0.3)
        Updated by: Fabolous1 (v0.4 for patch 3.14)
       
        required libs :                
        required sprites :              Hidden Objects Sprites (if used)
        exposed variables :     hiddenObjects
       
        UPDATES :
        v0.1                            initial release
        v0.1b                           change spells names for 3 champs (thx TRUS)
        v0.1c                           change spells names for teemo
        v0.1d                           fix the perma show
        v0.2                            BoL Studio Version
        v0.3                            Reworked
        v0.4                            Updated for patch 3.14
       
        USAGE :
        Hold shift key to see the hidden object's range.
]]
 
do
                --[[      CONFIG      ]]
                showOnMiniMap = true                    -- show objects on minimap
                useSprites = true                               -- show sprite on minimap
                --[[      GLOBAL      ]]
                objectsToAdd = {
                        { name = "VisionWard", objectType = "wards", spellName = "visionward", charName = "VisionWard", color = 0x00FF00FF, range = 1450, duration = 180000, sprite = "yellowPoint"},
                        { name = "SightWard", objectType = "wards", spellName = "sightward", charName = "SightWard", color = 0x0000FF00, range = 1450, duration = 180000, sprite = "greenPoint"},
                        { name = "VisionWard", objectType = "wards", spellName = "itemghostward", charName = "SightWard", color = 0x0000FF00, range = 1450, duration = 180000, sprite = "greenPoint"},
                        { name = "VisionWard", objectType = "wards", spellName = "itemminiward", charName = "SightWard", color = 0x00FF00FF, range = 1450, duration = 60000, sprite = "greenPoint"},
                        { name = "SightWard", objectType = "wards", spellName = "wrigglelantern", charName = "SightWard", color = 0x0000FF00, range = 1450, duration = 180000, sprite = "greenPoint"},
                        { name = "Jack In The Box", objectType = "boxes", spellName = "jackinthebox", charName = "ShacoBox", color = 0x00FF0000, range = 300, duration = 60000, sprite = "redPoint"},
                        { name = "Cupcake Trap", objectType = "traps", spellName = "caitlynyordletrap", charName = "CaitlynTrap", color = 0x00FF0000, range = 300, duration = 240000, sprite = "cyanPoint"},
                        { name = "Noxious Trap", objectType = "traps", spellName = "bushwhack", charName = "Nidalee_Spear", color = 0x00FF0000, range = 300, duration = 240000, sprite = "cyanPoint"},
                        { name = "Noxious Trap", objectType = "traps", spellName = "bantamtrap", charName = "TeemoMushroom", color = 0x00FF0000, range = 300, duration = 600000, sprite = "cyanPoint"},
                        { name = "Seed", objectType = "traps", spellName = "zyraseed", charName = "ZyraSeed", color = 0x00FF0000, range = 300, duration = 30000, sprite = "cyanPoint"},
                        -- to confirm spell
                        { name = "DoABarrelRoll", objectType = "boxes", spellName = "maokaisapling2", charName = "MaokaiSproutling", color = 0x00FF0000, range = 300, duration = 35000, sprite = "redPoint"},
                }
                --
                tmpObjects = {}
                sprites = {
                        cyanPoint = { spriteFile = "PingMarkerCyan_8", },
                        redPoint = { spriteFile = "PingMarkerRed_8", },
                        greenPoint = { spriteFile = "PingMarkerGreen_8", },
                        yellowPoint = { spriteFile = "PingMarkerYellow_8", },
                        greyPoint = { spriteFile = "PingMarkerGrey_8", },
                }
                objects = {}
 
        --[[      CODE      ]]
        function objectExist(charName, pos, tick)
                for i,obj in pairs(objects) do
                        if obj.object == nil and obj.charName == charName and GetDistance(obj.pos, pos) < 200 and tick < obj.seenTick then
                                return i
                        end
                end    
                return nil
        end
 
        function addObject(objectToAdd, pos, object)
                -- add the object
                local tick = GetTickCount()
                local objId = objectToAdd.charName..(math.floor(pos.x) + math.floor(pos.z))
                --check if exist
                local objectExist = objectExist(objectToAdd.charName, {x = pos.x, z = pos.z,}, tick - 2000)
                if objectExist ~= nil then
                        objId = objectExist
                end
                if objects[objId] == nil then
                        objects[objId] = {
                                object = object,
                                color = objectToAdd.color,
                                range = objectToAdd.range,
                                sprite = objectToAdd.sprite,
                                charName = objectToAdd.charName,
                                seenTick = tick,
                                endTick = tick + objectToAdd.duration,
                                visible = (object == nil),
                                objectFound = (object ~= nil),
                                display = { visible = false, text = ""},
                        }
                elseif objects[objId].object == nil and object ~= nil and object.valid then
                        objects[objId].object = object
                        objects[objId].objectFound = true
                end
                if (object ~= nil and object.valid and object.maxMana > 0) then endTick = tick + object.mana end
                objects[objId].pos = {x = pos.x, y = pos.y, z = pos.z, }
                if showOnMiniMap == true then objects[objId].minimap = GetMinimap(pos) end
        end
 
        function HiddenObjectsOnCreateObj(object)
                if object ~= nil and object.valid and object.type == "obj_AI_Minion" then
                        for i,objectToAdd in pairs(objectsToAdd) do
                                if object.name == objectToAdd.name then
                                        local tick = GetTickCount()
                                        table.insert(tmpObjects, {tick = tick, object = object})
                                end
                        end
                end
        end
 
        function HiddenObjectsOnProcessSpell(object,spell)
                if object ~= nil and object.valid and object.team == TEAM_ENEMY and object.type == "obj_AI_Hero" then
                        for i,objectToAdd in pairs(objectsToAdd) do
                                if spell.name:lower() == objectToAdd.spellName then
                                        ticked = GetTickCount()
                                        addObject(objectToAdd, spell.endPos)
                                end
                        end
                end
        end
 
        function HiddenObjectsOnDeleteObj(object)
                if object ~= nil and object.valid and object.name ~= nil and object.type == "obj_AI_Minion" then
                        for i,objectToAdd in pairs(objectsToAdd) do
                                if object.charName == objectToAdd.charName then
                                        -- remove the object
                                        for j,obj in pairs(objects) do
                                                if obj.object ~= nil and obj.object.valid and obj.object.networkID ~= nil and obj.object.networkID == object.networkID then
                                                        objects[j] = nil
                                                        return
                                                end
                                        end
                                end
                        end
                end
        end

 
        function HiddenObjectsOnDraw()
                if GetGame().isOver then return end
                local shiftKeyPressed = IsKeyDown(16)
                for i,obj in pairs(objects) do
                        if obj.visible == true then
                                if obj.object ~= nil and obj.object.valid then
                                        DrawCircle(obj.pos.x, obj.pos.y, obj.pos.z, 100, 0x00FFFFFF)
                                else
                                        DrawCircle(obj.pos.x, obj.pos.y, obj.pos.z, 100, obj.color)
                                end
                                DrawCircle(obj.pos.x, obj.pos.y, obj.pos.z, (shiftKeyPressed and obj.range or 200), obj.color)
                                --minimap
                                if showOnMiniMap == true then
                                        if useSprites then
                                                sprites[obj.sprite].sprite:Draw(obj.minimap.x, obj.minimap.y, 0xFF)
                                        else
                                                DrawText("o",31,obj.minimap.x-7,obj.minimap.y-13,obj.color)
                                        end
                                        if obj.display.visible then
                                                DrawText(obj.display.text,14,obj.display.x,obj.display.y,obj.display.color)
                                        end
                                end
                        end
                end
        end
 
        function HiddenObjectsOnTick()
                if GetGame().isOver then return end
                local tick = GetTickCount()
                for i,obj in pairs(tmpObjects) do
                        if tick > obj.tick + 1000 or obj.object == nil or not obj.object.valid or obj.object.team == player.team then
                                tmpObjects[i] = nil
                        else
                                for j,objectToAdd in pairs(objectsToAdd) do
                                        if obj.object.charName == objectToAdd.charName and obj.object.team == TEAM_ENEMY then
                                                addObject(objectToAdd, obj.object, obj.object)
                                                tmpObjects[i] = nil
                                                break
                                        end
                                end
                        end
                end
                for i,obj in pairs(objects) do
                        if tick > obj.endTick
                        or (obj.objectFound and obj.object.valid and obj.object.team == player.team)
                        or (obj.objectFound and (not obj.object.valid or obj.object.dead or (obj.object.maxHealth > 0 and obj.object.health == 0))) then
                                objects[i] = nil
                        else
                        --objectType = "wards"
                                if obj.object == nil or (obj.objectFound and obj.object.valid and not obj.object.dead) then
                                        obj.visible = true
                                else
                                        obj.visible = false
                                end
                                -- cursor pos
                                if obj.visible and GetDistanceFromMouse(obj.pos) < 150 then
                                        local cursor = GetCursorPos()
                                        obj.display.color = (obj.objectFound and 0xFFFF0000 or 0xFF00FF00)
                                        obj.display.text = TimerText((obj.endTick-tick)/1000)
                                        obj.display.x = cursor.x - 50
                                        obj.display.y = cursor.y - 50
                                        obj.display.visible = true
                                else
                                        obj.display.visible = false
                                end
                        end
                end
        end
 
        function HiddenObjectsOnLoad()
                gameState = GetGame()
                if showOnMiniMap and useSprites then
                        for i,sprite in pairs(sprites) do sprites[i].sprite = GetSprite("hiddenObjects/"..sprite.spriteFile..".dds") end
                end
                for i = 1, objManager.maxObjects do
                        local object = objManager:getObject(i)
                        if object ~= nil then OnCreateObj(object) end
                end
        end
end


-- ############################################# Hidden Objects ##############################################	



	-- XT002 --
     
    function OnLoad()
        TBConfig = scriptConfig("===多合一功能菜单===", "xt002hud")
		TBConfig:addParam("AutoHMZW", "自动 吃药/中亚/巫师帽", SCRIPT_PARAM_ONOFF, true)
		TBConfig:addParam("AutoIgnite", "自动点燃", SCRIPT_PARAM_ONOFF, true)
		TBConfig:addParam("IHateCC", "自动解控", SCRIPT_PARAM_ONOFF, true)
	    TBConfig:addParam("HiddenObjects", "隐形单位侦测", SCRIPT_PARAM_ONOFF, true)		
		TBConfig:addParam("TowerRange", "显示塔攻击范围", SCRIPT_PARAM_ONOFF, true)
		TBConfig:addParam("PerfectWard", "开启完美插眼", SCRIPT_PARAM_ONOFF, true)            
        TBConfig:addParam("LowAwareness", "敌方预警提示", SCRIPT_PARAM_ONOFF, false)        
		TBConfig:addParam("PlayerRange", "显示玩家范围", SCRIPT_PARAM_ONOFF, false)
		TBConfig:addParam("EnemyRanges", "显示敌方范围", SCRIPT_PARAM_ONOFF, false)		          
		TBConfig:addParam("WhereIsHe", "敌人消失红圈", SCRIPT_PARAM_ONOFF, true)		
	    TBConfig:addParam("WhereDidHeGo", "逃跑预测", SCRIPT_PARAM_ONOFF, true)		
		TBConfig:addParam("AutoSmite", "自动惩戒 v3.1", SCRIPT_PARAM_ONOFF, true)
		TBConfig:addParam("WaiteEe", "无敌计时 v0.2", SCRIPT_PARAM_ONOFF, false)		
	    TBConfig:addParam("AntiWard", "眼位陷阱", SCRIPT_PARAM_ONOFF, true)
		TBConfig:addParam("FlashAssistant", "闪现助手", SCRIPT_PARAM_ONOFF, true)
		TBConfig:addParam("MinionBars", "补刀标记", SCRIPT_PARAM_ONOFF, true)
		TBConfig:addParam("useLvl", "自动升级加点", SCRIPT_PARAM_ONOFF, false)
		TBConfig:addParam("ShowHP", "显示血量", SCRIPT_PARAM_ONOFF, true)
		TBConfig:addParam("MiniMapTimers", "小地图计时 (需重新载入(F9))", SCRIPT_PARAM_ONOFF, true) 
		TBConfig:addParam("CloneR", "本尊预测(需重新载入(F9))", SCRIPT_PARAM_ONOFF, false)	
		TBConfig:addParam("AutoShield", "自动护盾(需重新载入(F9))", SCRIPT_PARAM_ONOFF, true)
		TBConfig:addParam("ProTrackerv", "显技能显CD(需重新载入(F9))", SCRIPT_PARAM_ONOFF, true)
		TBConfig:addParam("VPrediction", "技能预判(需重新载入(F9))", SCRIPT_PARAM_ONOFF, true)
		if VIP_USER then
			TBConfig:addParam("SafeMove", "平滑流畅移动", SCRIPT_PARAM_ONOFF, true)
		end
		TBConfig:addParam("DisableGreen", "屏蔽绿字(需重新载入(F9))", SCRIPT_PARAM_ONOFF, false)

	if TBConfig.DisableGreen then
		DisableGreenOnLoad()
	end	   
	if TBConfig.VPrediction then
		VPredictionOnLoad()
	end 				
	if TBConfig.ProTrackerv then
		ProTrackerOnLoad()
	end  
	if TBConfig.SafeMove and VIP_USER then
		SafeMoveOnLoad()
	end	
	if TBConfig.Surrender then
		SurrenderOnLoad()
	end
	if TBConfig.SimpleTS then
		STSPAOnLoad()
	end	
	if TBConfig.MinionBars then
		MinionBarsOnLoad()
	end	
	if TBConfig.FlashAssistant then
		FlashOnLoad()
	end
	if TBConfig.WhereDidHeGo then
		WhereGoOnLoad()
	end
	if TBConfig.IHateCC then
	    IHateCCOnLoad()
	end
	if TBConfig.AntiWard then
	    AntiWardOnLoad()
	end
    if TBConfig.CloneR then
		CloneRevOnLoad()
	end		
	if TBConfig.AutoShield then
		AutoShieldOnLoad()
	end	
	if TBConfig.AutoSmite then
		AutoSmiteOnLoad()
	end
	if TBConfig.WaiteEe then
		WaiteeeOnLoad()
	end
	if TBConfig.MiniMapTimers then
		MiniMapTimersOnLoad()
	end	
	if TBConfig.HiddenObjects then
		HiddenObjectsOnLoad()	
	end	
	if TBConfig.AutoHMZW then
		AutoHMZWOnLoad()
	end	
	if TBConfig.TowerRange then
		TowerRangeOnLoad()			
	end		
	if TBConfig.useLvl then
		AutoLevelOnLoad()
	end	
	if TBConfig.AutoIgnite then
		AutoIgniteOnLoad()
	end	
		PrintChat("寰风帥瑗夸簹鎴樹簤瀛﹂櫌QQ缇?68830534>>鍏嶈垂鍙戝竷:寰风帥瑗夸簹鎴樹簤瀛﹂櫌>>缂栬緫:鈶犻噸妤间竴鍙垛憽楠ㄥご")
	end
	  
function OnTick()	
	if TBConfig.VPrediction then
		VPredictionOnTick()
	end		
	if TBConfig.ProTrackerv then
		ProTrackerOnTick()
	end	
	if TBConfig.ShowHP then
		ShowHPOnTick()
	end	
	if TBConfig.SafeMove and VIP_USER then
		SafeMoveOnTick()
	end	
	if TBConfig.useLvl then
		AutoLevelOnTick()
	end	
	if TBConfig.Surrender then
		SurrenderOnTick()
	end
	if TBConfig.FlashAssistant then
		FlashOnTick()
	end
	if TBConfig.WhereDidHeGo then
		WhereGoOnTick()
	end
	if TBConfig.AntiWard then
		AntiWardOnTick()
	end
	if TBConfig.AutoIgnite then
		AutoIgniteOnTick()
	end
	if TBConfig.PerfectWard then
	    PerfectWardOnTick()
	end
	if TBConfig.WaiteEe then
		WaiteeeOnTick()
	end
	if TBConfig.AutoSmite then
		AutoSmiteOnTick()
	end 	
	if TBConfig.WhereIsHe then
		WhereIsHeOnTick()
	end		
	if TBConfig.MiniMapTimers then
		MiniMapTimersOnTick()
	end		
    if TBConfig.LowAwareness then
        LowAwarenessOnTick()
    end	
	if TBConfig.TowerRange then
		TowerRangeOnTick()
	end
	if TBConfig.AutoHMZW then
		AutoZWOnTick()
	end
	if TBConfig.HiddenObjects then
		HiddenObjectsOnTick()
	end		
end

function OnDraw()
	if TBConfig.ProTrackerv then
		ProTrackerOnDraw()
	end	
	if TBConfig.MinionBars then
		MinionBarsOnDraw()
	end 
	if TBConfig.FlashAssistant then
		FlashOnDraw()
	end
	if TBConfig.WhereDidHeGo then
		WhereGoOnDraw()
	end
	if TBConfig.AntiWard then
		AntiWardOnDraw()
	end
	if TBConfig.PerfectWard then
		PerfectWardOnDraw()
	end
	if TBConfig.WhereIsHe then
		WhereIsHeOnDraw()
	end
    if TBConfig.LowAwareness then
        LowAwarenessOnDraw()
    end
	if TBConfig.EnemyRanges then
		ERangesOnDraw()
	end
	if TBConfig.PlayerRange then
		PRangesOnDraw()
	end
	if TBConfig.MiniMapTimers then
		MiniMapTimersOnDraw()
	end
	if TBConfig.AutoSmite then
		AutoSmiteOnDraw()
	end
	if TBConfig.AutoShield then
		AutoShieldOnDraw()
	end
	if TBConfig.TowerRange then
		TowerRangeOnDraw()
	end	
	if TBConfig.HiddenObjects then
		HiddenObjectsOnDraw()
	end		
end
     
function OnCreateObj(obj)
	if TBConfig.WhereDidHeGo then
		WhereGoOnCreateObj(obj)
	end
	if TBConfig.AntiWard then
		AntiWardOnCreateObj(obj)
	end
    if TBConfig.WaiteEe then
	    WaiteeeOnCreateObj(obj)
	end	
	if TBConfig.HiddenObjects then
		HiddenObjectsOnCreateObj(obj)
	end
	if TBConfig.FlashAssistant then
		FlashOnCreateObj(obj)
	end
end
     
function OnDeleteObj(obj)
	if TBConfig.AntiWard then
		AntiWardOnDeleteObj(obj)
	end
    if TBConfig.HiddenObjects then
		HiddenObjectsOnDeleteObj(obj)
	end
	if TBConfig.TowerRange then
		TowerRangeOnDeleteObj(obj)
	end
	if TBConfig.FlashAssistant then
		FlashOnDeleteObj(obj)
	end
end
	
function OnProcessSpell(obj,spell)
	if TBConfig.WhereDidHeGo then
		WhereGoOnProcessSpell(obj, spell)
	end
	if TBConfig.AntiWard then
		AntiWardOnProcessSpell(obj, spell)
	end
	if TBConfig.AutoShield then
		AutoShieldOnProcessSpell(obj,spell)
	end	
	if TBConfig.HiddenObjects then
		HiddenObjectsOnProcessSpell(obj,spell)
	end	
end  
     
function OnWndMsg(msg,key)
	if TBConfig.PerfectWard then
		PerfectWardOnWndMsg(msg, key)
	end
	if TBConfig.MiniMapTimers then
		MiniMapTimersOnWndMsg(msg, key)
	end   
end
     

---
title: KeyBinding-Element | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3b5e35738f04dd4a05a753a58e91ca385ecd56bd
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639323"
---
# <a name="keybinding-element"></a>KeyBinding-element
KeyBinding-Element gibt die Tastenkombinationen für die Befehle an.  
  
 Befehle können sowohl bei Einzel- oder dualcontrollern tastenzuordnungen zugeordnet haben. Ist ein Beispiel für eine einzelne tastenzuordnung **STRG**+**S** für die **speichern** Befehl. Duale tastenzuordnungen erfordern zwei aufeinander folgenden Tastenkombinationen einen Befehl ausgelöst. Ist ein Beispiel für eine duale tastenzuordnung **STRG * +** K **,** STRG**+** K ** ein, um das Setzen eines Lesezeichens.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|guid|Erforderlich.|  
|ID|Erforderlich.|  
|Editor|Erforderlich. Der Editor GUID gibt an, der Bearbeitungskontext für den diese Tastenkombination aktiv sein werden. Der globale Bindung Bereichswert ist "guidVSStd97".|  
|key1|Erforderlich. Gültige Werte sind alle eingegeben alphanumerische Zeichen sowie zweistelligen Hexadezimalwerten, 0 X vorangestellt und [VK_constants](https://msdn.microsoft.com/library/windows/desktop/dd375731.aspx).|  
|MOD1|Dies ist optional. Eine beliebige Kombination von **STRG**, **Alt**, und **UMSCHALT** durch Leerzeichen getrennt sind.|  
|key2|Dies ist optional. Gültige Werte sind alle eingegeben alphanumerische Zeichen sowie zweistelligen Hexadezimalwerten, 0 X vorangestellt und [VK_constants](https://msdn.microsoft.com/library/windows/desktop/dd375731.aspx).|  
|MOD2|Dies ist optional. Eine beliebige Kombination von **STRG**, **Alt**, und **UMSCHALT** durch Leerzeichen getrennt sind.|  
|Emulator|Dies ist optional.|  
|Bedingung|Dies ist optional. Finden Sie unter [bedingte Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|Übergeordnetes Element||  
|Anmerkung||  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[KeyBindings-element](../extensibility/keybindings-element.md)|Gruppen KeyBinding-Elementen und anderen KeyBindings Gruppierungen.|  
  
## <a name="example"></a>Beispiel  
  
```  
<KeyBindings>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"   
    editor="guidWidgetEditor" key1="VK_F5"/>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"   
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>  
</KeyBindings>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [KeyBindings-element](../extensibility/keybindings-element.md)   
 [Visual Studio-Befehlstabellen (VSCT)-Befehlsdateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

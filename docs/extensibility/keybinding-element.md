---
title: KeyBinding Element | Microsoft Docs
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
ms.openlocfilehash: 226a5913cbaa151689a886dc88986f7de8cc29f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="keybinding-element"></a>KeyBinding-Element
Das KeyBinding-Element gibt die Tastenkombinationen für Befehle.  
  
 Befehle können mit einem Subnetz und zwei tastenbindungen zugeordnet haben. Ein Beispiel für eine einzelnes schlüsselbindung wird STRG + S, für die **speichern** Befehl. Wichtige dualbindungen erfordern zwei aufeinander folgenden Tastenkombinationen einen Befehl auslösen. Ein Beispiel für eine wichtige dualbindung ist STRG + K, STRG + K, um ein Lesezeichen festzulegen.  
  
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
|Editor|Erforderlich. Der Editor GUID gibt an, der Bearbeitungskontext, der für den diese Tastenkombination aktiv sein. Der globale Bindung Bereichswert ist "guidVSStd97".|  
|key1|Erforderlich. Gültige Werte sind alle eingegeben alphanumerische Zeichen sowie zweistelligen Hexadezimalwerten, 0 X vorangestellt und [VK_constants](https://msdn.microsoft.com/en-us/library/windows/desktop/dd375731.aspx).|  
|MOD1|Dies ist optional. Eine beliebige Kombination aus STRG, ALT und UMSCHALT durch Leerzeichen getrennt sind.|  
|key2|Dies ist optional. Gültige Werte sind alle eingegeben alphanumerische Zeichen sowie zweistelligen Hexadezimalwerten, 0 X vorangestellt und [VK_constants](https://msdn.microsoft.com/en-us/library/windows/desktop/dd375731.aspx).|  
|MOD2|Dies ist optional. Eine beliebige Kombination aus STRG, ALT und UMSCHALT durch Leerzeichen getrennt sind.|  
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
|[KeyBindings-Element](../extensibility/keybindings-element.md)|Gruppen KeyBinding Elementen und anderen Schlüsselbindungen Gruppierungen.|  
  
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
 [Schlüsselbindungen-Element](../extensibility/keybindings-element.md)   
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

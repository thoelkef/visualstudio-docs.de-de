---
title: "KeyBinding-Element | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT XML-Schemaelemente, KeyBindings"
  - "KeyBinding-Element (VSCT-XML-Schema)"
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# KeyBinding-Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das KeyBinding\-Element gibt Tastenkombinationen für Befehle.  
  
 Befehle können einem oder zwei tastaturzuordnungen zugeordnet sind. Ist ein Beispiel für eine einzelne Tastenkombination STRG \+ S, für die **Speichern** Befehl. Wichtige dualbindungen erfordern zwei aufeinander folgenden Tastenkombinationen einen Befehl ausgelöst. Ist ein Beispiel für eine duale Tastenkombination STRG \+ K,STRG \+ K, um ein Lesezeichen festzulegen.  
  
## Syntax  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|GUID|Erforderlich.|  
|ID|Erforderlich.|  
|Editor|Erforderlich. Der Editor GUID gibt an, der Bearbeitungskontext, für den diese Tastenkombination aktiv sein. Der globale Bindung Bereichswert ist "guidVSStd97".|  
|Key1|Erforderlich. Gültige Werte sind alle eingegeben alphanumerische Zeichen sowie zweistelligen Hexadezimalwerten, 0 X und VK\_constants vorangestellt.|  
|MOD1|Optional. Eine beliebige Kombination aus STRG, ALT und UMSCHALT durch Leerzeichen getrennt sind.|  
|Key2|Optional. Gültige Werte sind alle eingegeben alphanumerische Zeichen sowie zweistelligen Hexadezimalwerten, 0 X und VK\_constants vorangestellt.|  
|MOD2|Optional. Eine beliebige Kombination aus STRG, ALT und UMSCHALT durch Leerzeichen getrennt sind.|  
|Emulator|Optional.|  
|Bedingung|Optional. Siehe [Bedingten Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|Übergeordnetes Element||  
|Anmerkung||  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[KeyBindings\-Element](../extensibility/keybindings-element.md)|Gruppen KeyBinding Elementen und anderen KeyBindings Gruppierungen.|  
  
## Beispiel  
  
```  
<KeyBindings> <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget" editor="guidWidgetEditor" key1="VK_F5"/> <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget" editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/> </KeyBindings>  
```  
  
## Siehe auch  
 [KeyBindings\-Element](../extensibility/keybindings-element.md)   
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
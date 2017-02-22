---
title: "Tastenk&#252;rzel-Element | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Tastenkürzel-Element (VSCT-XML-Schema)"
  - "VSCT XML-Schemaelemente, Tastenkürzel"
ms.assetid: ef48d2d2-0c47-4f93-8cfe-52026b6c463e
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# Tastenk&#252;rzel-Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gruppiert [Kombinationsfeld\-Element](../extensibility/combo-element.md)\-Elemente.  
  
## Syntax  
  
```  
<Combos>  
  <Combo>... </Combo>  
  <Combo>... </Combo>  
</Combos>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|Bedingung|Optional. Siehe [Bedingten Attribute](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Combos Element](../extensibility/combos-element.md)|Gruppiert Elemente Kombinationsfeld.|  
|[Kombinationsfeld\-Element](../extensibility/combo-element.md)|Definiert die Befehle, die in einem Kombinationsfeld angezeigt werden.|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Commands\-Element](../extensibility/commands-element.md)|Stellt die Auflistung von Befehlen auf der Symbolleiste des VSPackage.|  
  
## Beispiel  
  
```  
<Combos> <Combo guid="guidWidgetPackage" id="cmdidInsertOptions" defaultWidth="100" idCommandList="cmdidGetInsertOptionsList"> <CommandFlag>DynamicVisibility</CommandFlag> <Strings> <ButtonText>Select Insert Options</ButtonText> </Strings> </Combo> <Combo guid="guidWidgetPackage" id="cmdidInsertOptions" priority="0x0500" type="DropDownCombo" defaultWidth="100" idCommandList="cmdidGetInsertOptionsList"> <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"> <CommandFlag>DynamicVisibility</CommandFlag> <Strings> <ButtonText>Select Insert Options</ButtonText> </Strings> </Combo> </Combos>  
```  
  
## Siehe auch  
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
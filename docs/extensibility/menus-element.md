---
title: "Men&#252;s-Element | Microsoft Docs"
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
  - "VSCT XML-Schemaelemente, Menüs"
  - "Menüs-Element (VSCT-XML-Schema)"
ms.assetid: d825a99b-e05c-4dd9-8933-a180216d667a
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Men&#252;s-Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Definiert alle Menüs und Symbolleisten, die ein VSPackage implementiert.  
  
## Syntax  
  
```  
<Menus>  
  <Menu>... </Menu>  
  <Menu>... </Menu>  
</Menus>  
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
|[Menus Element](../extensibility/menus-element.md)|Definiert alle Menüs und Symbolleisten, die ein VSPackage implementiert.|  
|[Menu\-Element](../extensibility/menu-element.md)|Stellt ein Menü oder eine Symbolleiste.|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Commands\-Element](../extensibility/commands-element.md)|Stellt die Auflistung von Befehlen in das VSPackage.|  
  
## Beispiel  
  
```  
<Commands package="guidMyPackage"> <Menus> <Menu Condition="'%(DEBUG)' != 'true'" guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu" priority="0x0000" type="Menu"> <Annotation> <Documentation>this is an annotation</Documentation> <AppInfo> <CustomData> <CustomSubElement>Some data</CustomSubElement> </CustomData> </AppInfo> </Annotation> <CommandFlag>AlwaysCreate</CommandFlag> <Strings> <ButtonText>MainMenu</ButtonText> </Strings> </Menu> </Menus> <Commands>  
```  
  
## Siehe auch  
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
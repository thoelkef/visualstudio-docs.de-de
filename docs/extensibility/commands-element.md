---
title: "Commands-Element | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Commands"
helpviewer_keywords: 
  - "Commands-Element (VSCT-XML-Schema)"
  - "VSCT XML-Schemaelemente, Befehle"
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Commands-Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Stellt die Auflistung von Befehlen auf der Symbolleiste des VSPackage. Die Auflistung kann bis zu fünf Unterabschnitte haben, wie folgt: Gruppen, Menüs, Schaltflächen, Kombinationen und Bitmaps.  
  
 Jeder Unterabschnitt untergeordnetes Element, z. B. \< Menü \> wird durch eine eindeutige Befehls\-ID identifiziert, die einen GUID auch einen numerischen Bezeichner ist. Die GUID identifiziert die "Befehl" und wird verwendet, um eine Gruppe von logisch verknüpften Befehlen. Das VSPackage sollte eine eigene\-Befehlssatz zum Vermeiden von Konflikten mit der Befehls\-IDs, die von anderen VSPackages definiert sind definieren.  
  
## Syntax  
  
```  
<Commands package="GuidMyPackage" >  
  <Menus>... </Menus>  
  <Groups>... </Groups>  
  <Buttons>... </Buttons>  
  <Combos>... </Combos>  
  <Bitmaps>... </Bitmaps>  
</Commands>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|package|Eine GUID, die VSPackages identifiziert, die die Befehle bereitstellt.<br /><br /> Z. B. Verpacken \= "guidVsPackage1Pkg".|  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Menüs\-Element](../extensibility/menus-element.md)|Definiert alle Menüs, die ein VSPackage implementiert.|  
|[Groups\-Element](../extensibility/groups-element.md)|Enthält Einträge, die die Befehlsgruppen in ein VSPackage definieren.|  
|[Schaltflächen\-Element](../extensibility/buttons-element.md)|Gruppen\-Button\-Elemente.|  
|[Bitmaps\-Element](../extensibility/bitmaps-element.md)|Gruppen\-Bitmap\-Elemente.|  
|[Tastenkürzel\-Element](../extensibility/combos-element.md)|Gruppiert Elemente Kombinationsfeld.|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[CommandTable\-Element](../extensibility/commandtable-element.md)|Definiert die Elemente aus, die die Befehle darstellen, die einem VSPackage in der IDE bietet. Mögliche Elemente sind Elemente, Menüs, Symbolleisten und Kombinationsfelder.|  
  
## Beispiel  
 Das folgende Beispiel zeigt, wie Sie eine [Commands Element](../extensibility/commands-element.md).  
  
```  
<Commands package="guidMyPackage"> <Menus> <Menu Condition="'%(DEBUG)' != 'true'" guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu" priority="0x0000" type="Menu"> <Annotation> <Documentation>this is an annotation</Documentation> <AppInfo> <CustomData> <CustomSubElement>Some data</CustomSubElement> </CustomData> </AppInfo> </Annotation> <CommandFlag>AlwaysCreate</CommandFlag> <Strings> <ButtonText>MainMenu</ButtonText> </Strings> </Menu> </Menus> <Commands>  
```  
  
## Siehe auch  
 [Wie VSPackages Benutzeroberflächenelemente hinzufügen](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Befehle, Menüs und Symbolleisten](../extensibility/internals/commands-menus-and-toolbars.md)
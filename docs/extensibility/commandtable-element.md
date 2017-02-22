---
title: "CommandTable-Element | Microsoft Docs"
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
  - "CommandTable"
helpviewer_keywords: 
  - "CommandTable-Element (VSCT-XML-Schema)"
  - "VSCT XML-Schemaelemente, CommandTable"
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# CommandTable-Element
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

CommandTable ist das Stammelement der .vsct\-Datei. Dies ist die Datei, die definiert das tatsächliche Layout und die Art der Befehle, die einem VSPackage in der IDE bietet. Befehle zählen Menüelemente, Menüs, Symbolleisten und Kombinationsfelder. Weitere Informationen finden Sie unter [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## Syntax  
  
```  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema" >  
  <Extern>... </Extern>  
  <Include>... </Include>  
  <Define>... </Define>  
  <Commands>... </Commands>  
  <CommandPlacements>... </CommandPlacements>  
  <VisibilityConstraints>... </VisibilityConstraints>  
  <KeyBindings>... </KeyBindings>  
  <UsedCommands... </UsedCommands>  
  <Symbols>... </Symbols>  
</CommandTable>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|xmlns|Erforderlich. XML\-Namespaces:<br /><br /> Xmlns \= "http:\/\/schemas.microsoft.com\/VisualStudio\/2005\-10\-18\/CommandTable"<br /><br /> xmlns: xs \= "http:\/\/www.w3.org\/2001\/XMLSchema"|  
|language|Optional. Das Language\-Attribut kann verwendet werden, um die Standardsprache für alle \< Zeichenfolgen \>\-Elemente in der Befehlstabelle anzugeben.  Wenn die Sprache nicht angegeben ist, wird die Sprache des aktuellen Prozesses verwendet werden:<br /><br /> Language \= "En\-us"|  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Extern\-Element](../extensibility/extern-element.md)|Optional. Enthält die Präprozessordirektiven für den Compiler.|  
|[Include\-Element](../extensibility/include-element.md)|Optional. Enthält die Pfade zu Dateien in die Kompilierung eingeschlossen werden.|  
|[Definieren von Element](../extensibility/define-element.md)|Optional. Definiert ein Symbol mit dem angegebenen Namen und Wert.|  
|[Commands\-Element](../extensibility/commands-element.md)|Optional. Das übergeordnete Element, definieren alle Befehle für das VSPackage, das alle anderen Elemente enthält.|  
|[CommandPlacements\-Element](../extensibility/commandplacements-element.md)|Optional. Definiert, wo auf der Befehlsleiste die Befehle platziert werden.|  
|[VisibilityConstraints\-Element](../extensibility/visibilityconstraints-element.md)|Optional. Bestimmt die Sichtbarkeit statische, Befehle und Symbolleisten.|  
|[KeyBindings\-Element](../extensibility/keybindings-element.md)|Optional. Gibt die Tastenkombinationen für die Befehle an.|  
|[UsedCommands\-Element](../extensibility/usedcommands-element.md)|Optional. Ermöglicht es einem VSPackage optional eine eigene Version der ursprünglich von anderen VSPackages unterstützten Funktionen zu implementieren.|  
|[Symbols Element](http://msdn.microsoft.com/de-de/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|Optional. Enthält alle Symboldaten\-\-GUIDs, IDs und So weiter – für den Compiler.|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|Keine||  
  
## Siehe auch  
 [Visual Studio\-Befehl\-Tabelle \(. VSCT\) Dateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
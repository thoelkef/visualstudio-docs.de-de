---
title: CommandTable Element | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d4f1a906f545dcdbaefca7f5a38824a1f3259c97
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="commandtable-element"></a>CommandTable-Element
CommandTable ist das Stammelement der VSCT-Datei. Dies ist die Datei, die das tatsächliche Layout und den Typ der Befehle, die eine VSPackage für der IDE bietet definiert. Menüelemente, Menüs, Symbolleisten und Kombinationsfeldern folgende Befehle zählen. Weitere Informationen finden Sie unter [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="syntax"></a>Syntax  
  
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
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|xmlns|Erforderlich. XML-Namespaces:<br /><br /> Xmlns = "http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"<br /><br /> xmlns: xs = "http://www.w3.org/2001/XMLSchema"|  
|language|Dies ist optional. Language-Attribut kann verwendet werden, an die Standardsprache für alle \<Zeichenfolgen > Elemente in der Befehlstabelle.  Wenn die Sprache nicht angegeben ist, wird die Sprache des aktuellen Prozesses verwendet werden:<br /><br /> Language = "En-us"|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Extern-Element](../extensibility/extern-element.md)|Dies ist optional. Enthält die Präprozessordirektiven für den Compiler.|  
|[Include-Element](../extensibility/include-element.md)|Dies ist optional. Enthält die Pfade für alle Dateien in die Kompilierung eingeschlossen werden sollen.|  
|[Define-Element](../extensibility/define-element.md)|Dies ist optional. Definiert ein Symbol mit dem angegebenen Namen und Wert.|  
|[Commands-Element](../extensibility/commands-element.md)|Dies ist optional. Das übergeordnete Element aller Befehle definieren, die für das VSPackage, das alle anderen Elemente enthält.|  
|[CommandPlacements-Element](../extensibility/commandplacements-element.md)|Dies ist optional. Definiert, in dem in der Befehlszeile die Befehle sind abgelegt werden soll.|  
|[VisibilityConstraints-Element](../extensibility/visibilityconstraints-element.md)|Dies ist optional. Bestimmt die Sichtbarkeit statische, Befehle und Symbolleisten.|  
|[KeyBindings-Element](../extensibility/keybindings-element.md)|Dies ist optional. Gibt die Tastenkombinationen an, sofern vorhanden, für die Befehle.|  
|[UsedCommands-Element](../extensibility/usedcommands-element.md)|Dies ist optional. Ermöglicht eine VSPackage, um optional eine eigene Version der ursprünglich von anderen VSPackages unterstützten Funktionen zu implementieren.|  
|[Symbols-Element](http://msdn.microsoft.com/en-us/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|Dies ist optional. Enthält alle Symboldaten--GUIDs, IDs usw. – für den Compiler.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|Keine||  
  
## <a name="see-also"></a>Siehe auch  
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
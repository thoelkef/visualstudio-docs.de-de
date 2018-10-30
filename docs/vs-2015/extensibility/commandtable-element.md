---
title: CommandTable-Element | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ce1d7b431e7918c172947c508ae06e5770877ea6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49863502"
---
# <a name="commandtable-element"></a>CommandTable-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

CommandTable ist das Stammelement der VSCT-Datei. Dies ist die Datei, die definiert, die tatsächliche Layout und den Typ der Befehle, die eine VSPackage für der IDE bietet. Menüelemente, Menüs, Symbolleisten und Kombinationsfeldern folgende Befehle zählen. Weitere Informationen finden Sie unter [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
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
  
| Attribut |                                                                                                                   Beschreibung                                                                                                                   |
|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   xmlns   |                                   Erforderlich. XML-Namespaces:<br /><br /> Xmlns = "<http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable>"<br /><br /> xmlns: xs = "<http://www.w3.org/2001/XMLSchema>"                                   |
| language  | Dies ist optional. Language-Attribut kann verwendet werden, an der standardmäßigen Sprache der alle \<Zeichenfolgen > Elemente in der Befehlstabelle.  Wenn die Sprache nicht angegeben ist, wird die Sprache des aktuellen Prozesses verwendet werden:<br /><br /> Language = "En-us" |
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Extern-Element](../extensibility/extern-element.md)|Dies ist optional. Enthält die präprozessoranweisungen für den Compiler.|  
|[Include-Element](../extensibility/include-element.md)|Dies ist optional. Enthält die Pfade für alle Dateien in die Kompilierung eingeschlossen werden sollen.|  
|[Define-Element](../extensibility/define-element.md)|Dies ist optional. Definiert ein Symbol mit dem angegebenen Namen und Wert.|  
|[Commands-Element](../extensibility/commands-element.md)|Dies ist optional. Das übergeordnete Element, definieren alle Befehle, die für das VSPackage, das alle anderen Elemente enthält.|  
|[CommandPlacements-Element](../extensibility/commandplacements-element.md)|Dies ist optional. Definiert, in dem auf der Befehlsleiste auf die Befehle, platziert werden soll.|  
|[VisibilityConstraints-Element](../extensibility/visibilityconstraints-element.md)|Dies ist optional. Bestimmt die statische Sichtbarkeit von Befehlen und Symbolleisten.|  
|[KeyBindings-Element](../extensibility/keybindings-element.md)|Dies ist optional. Gibt die Tastenkombinationen an, sofern vorhanden, für die Befehle.|  
|[UsedCommands-Element](../extensibility/usedcommands-element.md)|Dies ist optional. Ermöglicht einem VSPackages, implementieren Sie bei Bedarf eine eigene Version der Funktionen, die ursprünglich von anderen VSPackages unterstützt.|  
|[Symbols-Element](http://msdn.microsoft.com/en-us/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|Dies ist optional. Enthält alle Symboldaten--GUIDs, IDs und So weiter – für den Compiler an.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|Keiner||  
  
## <a name="see-also"></a>Siehe auch  
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)


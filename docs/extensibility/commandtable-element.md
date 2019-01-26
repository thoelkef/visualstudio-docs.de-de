---
title: CommandTable-Element | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fefaa84cb00bdf0ccabe825067cb86f6c231a840
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55017421"
---
# <a name="commandtable-element"></a>CommandTable-element
CommandTable ist das Stammelement der *VSCT* Datei. Dies ist die Datei, die definiert, die tatsächliche Layout und den Typ der Befehle, die eine VSPackage für der IDE bietet. Menüelemente, Menüs, Symbolleisten und Kombinationsfeldern folgende Befehle zählen. Weitere Informationen finden Sie unter [Visual Studio-Befehlstabellen (VSCT) Befehlsdateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="syntax"></a>Syntax  
  
```xml  
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
  
| Attribut | Beschreibung |
|-----------| - |
| xmlns | Erforderlich. XML-Namespaces:<br /><br /> xmlns="<http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable>"<br /><br /> xmlns:xs="<http://www.w3.org/2001/XMLSchema>" |
| language | Dies ist optional. Language-Attribut kann verwendet werden, an der standardmäßigen Sprache der alle \<Zeichenfolgen > Elemente in der Befehlstabelle.  Wenn die Sprache nicht angegeben ist, wird die Sprache des aktuellen Prozesses verwendet werden:<br /><br /> language="en-us" |
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Extern-element](../extensibility/extern-element.md)|Dies ist optional. Enthält die präprozessoranweisungen für den Compiler.|  
|[Include-element](../extensibility/include-element.md)|Dies ist optional. Enthält die Pfade für alle Dateien in die Kompilierung eingeschlossen werden sollen.|  
|[Definieren Sie element](../extensibility/define-element.md)|Dies ist optional. Definiert ein Symbol mit dem angegebenen Namen und Wert.|  
|[Commands-element](../extensibility/commands-element.md)|Dies ist optional. Das übergeordnete Element, definieren alle Befehle, die für das VSPackage, das alle anderen Elemente enthält.|  
|[CommandPlacements-element](../extensibility/commandplacements-element.md)|Dies ist optional. Definiert, in dem auf der Befehlsleiste auf die Befehle, platziert werden soll.|  
|[VisibilityConstraints-element](../extensibility/visibilityconstraints-element.md)|Dies ist optional. Bestimmt die statische Sichtbarkeit von Befehlen und Symbolleisten.|  
|[KeyBindings-element](../extensibility/keybindings-element.md)|Dies ist optional. Gibt die Tastenkombinationen an, sofern vorhanden, für die Befehle.|  
|[UsedCommands-element](../extensibility/usedcommands-element.md)|Dies ist optional. Ermöglicht einem VSPackages, implementieren Sie bei Bedarf eine eigene Version der Funktionen, die ursprünglich von anderen VSPackages unterstützt.|  
|[Symbols-element](https://www.microsoft.com/download/details.aspx?id=55984)|Dies ist optional. Enthält alle Symboldaten--GUIDs, IDs und So weiter – für den Compiler an.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|Keine||  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Befehlstabellen (VSCT)-Befehlsdateien](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
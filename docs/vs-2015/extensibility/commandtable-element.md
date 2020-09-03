---
title: Commandtable-Element | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bb2b874f7bbe94e383e9e7fba755dcc373a93150
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "77477050"
---
# <a name="commandtable-element"></a>CommandTable-Element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Commandtable ist das Stamm Element der vsct-Datei. Dies ist die Datei, die das tatsächliche Layout und den Typ der Befehle definiert, die ein VSPackage für die IDE bereitstellt. Befehle können Menü Elemente, Menüs, Symbolleisten und Kombinations Felder enthalten. Weitere Informationen finden Sie unter [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
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
  
| attribute |                                                                                                                   BESCHREIBUNG                                                                                                                   |
|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   xmlns   |                                   Erforderlich. XML-Namespaces:<br /><br /> `xmlns="<http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable>"`<br /><br /> `xmlns:xs="<http://www.w3.org/2001/XMLSchema>"`                                   |
| language  | Optional. Das Language-Attribut kann verwendet werden, um die Standardsprache aller \<Strings> Elemente in der Befehls Tabelle anzugeben.  Wenn die Sprache nicht angegeben wird, wird die Sprache des aktuellen Prozesses verwendet:<br /><br /> language = "en-US" |
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|BESCHREIBUNG|  
|-------------|-----------------|  
|[Extern-Element](../extensibility/extern-element.md)|Optional. Enthält Präprozessordirektiven für den Compiler.|  
|[Include-Element](../extensibility/include-element.md)|Optional. Enthält Pfade zu allen Dateien, die in die Kompilierung eingeschlossen werden sollen.|  
|[Define-Element](../extensibility/define-element.md)|Optional. Definiert ein Symbol anhand seines Namens und Werts.|  
|[Commands-Element](../extensibility/commands-element.md)|Optional. Das übergeordnete Element, das alle Befehle für das VSPackage definiert, das alle anderen Elemente enthält.|  
|[CommandPlacements-Element](../extensibility/commandplacements-element.md)|Optional. Definiert, wo in der Befehlsleiste die Befehle platziert werden sollen.|  
|[VisibilityConstraints-Element](../extensibility/visibilityconstraints-element.md)|Optional. Bestimmt die statische Sichtbarkeit von Befehlen und Symbolleisten.|  
|[KeyBindings-Element](../extensibility/keybindings-element.md)|Optional. Gibt ggf. die Tastenkombinationen für die Befehle an.|  
|[UsedCommands-Element](../extensibility/usedcommands-element.md)|Optional. Ermöglicht einem VSPackage, optional seine eigene Version der Funktionalität zu implementieren, die ursprünglich von anderen VSPackages unterstützt wurde.|  
|[Symbols-Element](https://msdn.microsoft.com/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|Optional. Enthält beliebige Symbol Daten-GUIDs, IDs usw. für den Compiler.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|BESCHREIBUNG|  
|-------------|-----------------|  
|Keine||  
  
## <a name="see-also"></a>Weitere Informationen  
 [VSCT-Dateien (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

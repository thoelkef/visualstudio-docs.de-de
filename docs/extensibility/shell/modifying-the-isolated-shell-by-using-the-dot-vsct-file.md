---
title: "Ändern von Isolated Shell mithilfe der. VSCT-Datei | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode, .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fcdaab4c5c9f0ee5522ae372e4a0cd94fb113eed
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>Ändern von Isolated Shell mithilfe der. VSCT-Datei
Das UI-Projekt für eine Visual Studio isolated Shell-Projekt enthält eine VSCT-Datei, mit dem Sie angeben, welche Anwendungsgruppen und die einzelnen Befehle in der Anwendung verfügbar sind. Im folgenden ist ein Auszug aus einer nicht geänderten VSCT-Datei.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 Standardmäßig sind die meisten Befehle und Befehlsgruppen enthalten. Um einen Befehl oder die Befehlsgruppe auszuschließen, kommentieren Sie einfach den Befehl oder die Gruppe.  
  
 Angenommen, um den nächsten und vorherigen Bereich Befehle zu entfernen, heben Sie die auskommentierung der `No_PaneNextPaneCommand` und `No_PanePrevPaneCommand` Einträge:  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Ein Beispiel für diese Anpassungen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Basic-isolierten Shellanwendung](walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>Die Dateien verwiesen wird  
 Die standardmäßige VSCT-Datei für eine Anwendung verweist auf die folgenden Dateien. Diese Dateien befinden sich im Unterverzeichnis \VisualStudioIntegration\Common\Inc\ des SDK für Visual Studio-Installationsverzeichnisses.  
  
|Datei|Beschreibung|  
|----------|-----------------|  
|wbids.h|UI-Identitäten für das Paket Internet surfen.|  
|AppIDCmdUsed.vsct|Befehlstabelle für Visual Studio-Benutzeroberfläche Hauptelemente.|  
|EmulatorCmdUsed.vsct|Befehlstabelle für Emacs und kurze-Editor-Emulation-Benutzeroberflächenelemente.|  
|Vsdebugguids.h|Definiert die GUIDs der Befehle, Seite "Optionen" und anderen Funktionen von Visual Studio-Debugger an.|  
|VsDbgCmdUsed.vsct|Befehlstabelle für den Debugger.|  
  
 Die AppIDCmdUsed.vsct-Datei enthält Visual Studio-UI-Elementen, die basierend auf VSCT-Datei der Anwendung definierten Symbole.  
  
 Weitere Informationen finden Sie unter [XML-Befehl-Tabelle entwerfen (. VSCT)-Dateien](../internals/designing-xml-command-table-dot-vsct-files.md) und [VSCT-XML-Schemareferenz](../vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio Isolated Shell](visual-studio-isolated-shell.md)
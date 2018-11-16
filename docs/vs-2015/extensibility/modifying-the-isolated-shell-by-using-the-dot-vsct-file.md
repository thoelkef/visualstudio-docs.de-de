---
title: Ändern der Isolated Shell mithilfe der. VSCT-Datei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0eb5b110386f4a696c228e746223d745df6b18f7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817606"
---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>Ändern der Isolated Shell mithilfe der. VSCT-Datei
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das UI-Projekt für ein Visual Studio isolierte Shell-Projekt enthält eine VSCT-Datei, mit dem Sie angeben, welche Gruppen für Anwendungen und einzelne Befehle in der Anwendung verfügbar sind. Folgendes ist ein Auszug aus einer unveränderten VSCT-Datei.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 Standardmäßig sind die meisten Befehle und Befehlsgruppen enthalten. Um einen Befehl oder die Befehlsgruppe auszuschließen, entfernen Sie einfach diesen Befehl oder diese Gruppe.  
  
 Z. B. um den nächsten und vorherigen Bereich Befehle zu entfernen, heben Sie die auskommentierung der `No_PaneNextPaneCommand` und `No_PanePrevPaneCommand` Einträge:  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Ein Beispiel für diese Anpassungen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Basic-isolierten Shellanwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>Die Dateien verwiesen wird  
 Die Standard-VSCT-Datei für eine Anwendung verweist auf die folgenden Dateien. Diese Dateien befinden sich im Unterverzeichnis "\VisualStudioIntegration\Common\Inc\" des Visual Studio SDK-Installationsverzeichnisses.  
  
|Datei|Beschreibung|  
|----------|-----------------|  
|wbids.h|UI-Identitäten für das Paket des Internets.|  
|AppIDCmdUsed.vsct|Befehlstabelle für primären Benutzeroberfläche von Visual Studio-Elemente.|  
|EmulatorCmdUsed.vsct|Befehlstabelle für Emacs und kurze-Editor-Emulation-Benutzeroberflächenelemente.|  
|Vsdebugguids.h|Definiert die GUIDs der Befehle, Seite "Optionen" und anderen Funktionen von Visual Studio-Debugger an.|  
|VsDbgCmdUsed.vsct|Befehlstabelle für den Debugger.|  
  
 Die AppIDCmdUsed.vsct-Datei enthält die Benutzeroberfläche von Visual Studio-Elemente, die basierend auf dem die Symbole in der VSCT-Datei der Anwendung definiert.  
  
 Weitere Informationen finden Sie unter [Entwerfen von XML-Command Table (. VSCT) Dateien](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md) und [VSCT-XML-Schemareferenz](../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)


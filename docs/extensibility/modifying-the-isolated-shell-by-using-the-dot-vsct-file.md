---
title: "Ändern die isolierte Shell mithilfe der. VSCT-Datei | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode, .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 9044821c2bfee0dba8ffa91f3d91afd565b8d957
ms.openlocfilehash: a20b546c6e8d6d70a17d3d0bae575a5b2898d781
ms.lasthandoff: 02/22/2017

---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>Ändern die isolierte Shell mithilfe der. VSCT-Datei
Das UI-Projekt für Visual Studio isolierte Shell-Projekt enthält eine VSCT-Datei, mit der Sie angeben, welche Gruppen und einzelne Befehle in der Anwendung verfügbar sind. Im folgenden ist ein Auszug aus einer nicht geänderten VSCT-Datei.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 Standardmäßig sind die meisten Befehle und Befehlsgruppen enthalten. Um einen Befehl oder die Befehlsgruppe auszuschließen, kommentieren Sie einfach den Befehl oder die Gruppe.  
  
 Um den nächsten Bereich und die vorherigen Bereich Befehle zu entfernen, kommentieren Sie z. B. die `No_PaneNextPaneCommand` und `No_PanePrevPaneCommand` Einträge:  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Ein Beispiel für diese Anpassungen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer einfachen Anwendung für isolierte Shell](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>Die Dateien verwiesen wird  
 Die standardmäßige VSCT-Datei für eine Anwendung verweist auf die folgenden Dateien. Diese Dateien befinden sich im Unterverzeichnis \VisualStudioIntegration\Common\Inc\ des Verzeichnisses mit den Visual Studio SDK.  
  
|Datei|Beschreibung|  
|----------|-----------------|  
|wbids.h|Identitäten, die Benutzeroberfläche für das Paket Web durchsuchen.|  
|AppIDCmdUsed.vsct|Befehlstabelle für die primäre Benutzeroberfläche von Visual Studio-Elemente.|  
|EmulatorCmdUsed.vsct|Befehlstabelle für Emacs sowie kurze-Editor-Emulation-Benutzeroberflächenelemente.|  
|Vsdebugguids.h|Definiert die GUIDs für die Befehle, Optionen und andere Funktionen von Visual Studio-Debugger.|  
|VsDbgCmdUsed.vsct|Befehlstabelle für den Debugger.|  
  
 Die AppIDCmdUsed.vsct-Datei enthält die Benutzeroberfläche von Visual Studio-Elemente, die auf der Grundlage der Symbole in der VSCT-Datei definiert.  
  
 Weitere Informationen finden Sie unter [XML-Befehl-Tabelle entwerfen (. VSCT) Dateien](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md) und [VSCT XML Schema Reference](../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio Shell Isolated](../extensibility/visual-studio-isolated-shell.md)

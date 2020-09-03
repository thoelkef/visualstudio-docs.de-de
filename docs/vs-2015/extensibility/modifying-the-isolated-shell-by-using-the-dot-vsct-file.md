---
title: Ändern der isolierten Shell mithilfe von. Vsct-Datei | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c106a04e809e772ac3b8a77192fb2f101161e9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194233"
---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>Ändern der Isolated Shell mithilfe der VSCT-Datei
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das UI-Projekt für ein isoliertes Visual Studio-shellprojekt enthält eine vsct-Datei, mit der Sie angeben können, welche Anwendungs Gruppen und einzelnen Befehle in der Anwendung verfügbar sind. Im folgenden finden Sie einen Auszug aus einer unveränderten vsct-Datei.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 Standardmäßig sind die meisten Befehle und Befehls Gruppen enthalten. Um einen Befehl oder eine Befehlsgruppe auszuschließen, heben Sie die Auskommentierung des Befehls oder der Gruppe auf.  
  
 Wenn Sie z. b. die Befehle Nächster Bereich und Vorheriger Bereich entfernen möchten, heben Sie die Auskommentierung der `No_PaneNextPaneCommand` Einträge und auf `No_PanePrevPaneCommand` :  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Ein ausführlicheres Beispiel für diese Anpassungen finden Sie unter Exemplarische Vorgehensweise [: Erstellen einer einfachen isolierten Shellanwendung](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>Referenzierte Dateien  
 Die vsct-Standarddatei für eine Anwendung verweist auf die folgenden Dateien. Diese Dateien befinden sich im Unterverzeichnis "\visualstudiointegration\common\inc\" des Visual Studio SDK-Installationsverzeichnisses.  
  
|Datei|Beschreibung|  
|----------|-----------------|  
|wbots. h|Benutzeroberflächen Identitäten für das Web-Browse-Paket.|  
|Appidcmdused. vsct|Befehls Tabelle für primäre Visual Studio-Benutzeroberflächen Elemente.|  
|Emuatorcmdused. vsct|Befehls Tabelle für Emacs und kurze Benutzeroberflächen Elemente der Editor Emulation.|  
|Vsdebugguids. h|Definiert die GUIDs der Befehle, der Optionsseite und anderer Funktionen des Visual Studio-Debuggers.|  
|Vsdbgcmdused. vsct|Befehls Tabelle für den Debugger.|  
  
 Die appidcmdused. vsct-Datei enthält Visual Studio-Benutzeroberflächen Elemente auf der Grundlage der Symbole, die in der Datei "Application. vsct" definiert sind.  
  
 Weitere Informationen finden Sie unter [Entwerfen einer XML-Befehls Tabelle (. Vsct-Dateien](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md) und die [vsct-XML-Schema Referenz](../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Visual Studio Isolated Shell](../extensibility/visual-studio-isolated-shell.md)

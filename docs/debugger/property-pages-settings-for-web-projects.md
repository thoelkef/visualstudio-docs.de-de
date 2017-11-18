---
title: "Eigenschaftenseiten für Webprojekte Einstellungen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Web applications
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- debugging Web applications, project settings
- debug configurations, Web projects
ms.assetid: 8ec5160a-6408-4f47-8d41-f0e20e79a3b9
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6c86e45ea5108361271658d5dd8e7dfadbde2012
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="property-pages-settings-for-web-projects"></a>Einstellungen von Eigenschaftenseiten für Webprojekte
Sie können die eigenschafteneinstellungen für eine Website-Debugkonfiguration im Ändern der **Eigenschaftenseiten** (Dialogfeld), wie in beschrieben [Debug- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md). Die folgenden Tabellen zeigen, wo die debuggerspezifischen Einstellungen im Suchen der **Eigenschaftenseiten** (Dialogfeld).  
  
### <a name="configuration-properties-folder-start-options-category"></a>Ordner "Konfigurationseigenschaften" (Kategorie "Startoptionen")  
  
|**Einstellung**|**Beschreibung**|  
|-----------------|---------------------|  
|**Startaktion**|Überschrift, unter der sich Optionen für den Anwendungsstart befinden.|  
|**Verwenden Sie die aktuelle Seite**|Legt die aktuelle Seite als Ausgangspunkt für das Debuggen fest.|  
|**Bestimmte Seite:**|Gibt die Webseite an, bei der das Debuggen beginnen soll.|  
|**Starten Sie externes Programm:**|Gibt den Startbefehl für das Programm an, das gedebuggt werden soll.|  
|**Befehlszeilenargumente:**|Gibt Argumente für den oben aufgeführten Befehl an.|  
|**Arbeitsverzeichnis:**|Gibt das Arbeitsverzeichnis des Programms an, das gerade gedebuggt wird. Das Arbeitsverzeichnis in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ist das Verzeichnis, über das die Anwendung gestartet wird: standardmäßig \bin\debug.|  
|**Start-URL**|Gibt den Pfad der Webanwendung an, die gedebuggt werden soll.|  
|**Keine Seite öffnen, Eine Anforderung einer externen Anwendung warten**|Legt fest, dass auf die Anforderung einer externen Anwendung gewartet wird. Mit dieser Option wird weder Internet Explorer noch eine andere Anwendung gestartet. Sie wird lediglich zum Debuggen vorbereitet, wenn sie von einer Anwendung aufgerufen wird.|  
|**Server**|Überschrift, unter der sich Optionen zum zu verwendenden Server befinden.|  
|**Standardwebserver verwenden**|Legt fest, dass der Standardwebserver verwendet wird.|  
|**Benutzerdefinierten Server verwenden**|Ermöglicht es Ihnen, die Basis-URL einzugeben, die als Server verwendet werden soll.|  
|**Debugger**|Überschrift, unter der sich Optionen zum Debugtyp befinden.|  
|**ASP.NET-Debuggen**|Ermöglicht das Debuggen von Serverseiten, die für die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Entwicklungsplattform geschrieben wurden. Sie müssen eine URL angeben **Start-URL**.|  
|**Debuggen von systemeigenem code**|Bietet die Möglichkeit, Aufrufe von systemeigenem (nicht verwaltetem) Win32-Code von einer verwalteten Anwendung aus zu debuggen.|  
|**SQL Server-Debuggen**|Ermöglicht das Debuggen von SQL Server-Datenbankobjekten.|  
|**Silverlight-debugging**|Ermöglicht das Debuggen von Silverlight-Komponenten.|  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)
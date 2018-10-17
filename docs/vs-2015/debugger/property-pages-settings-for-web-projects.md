---
title: Einstellungen für Webprojekte von Eigenschaftenseiten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], Web applications
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- debugging Web applications, project settings
- debug configurations, Web projects
ms.assetid: 8ec5160a-6408-4f47-8d41-f0e20e79a3b9
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a472e134869ff48a21480ede42f330d968262d38
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49179984"
---
# <a name="property-pages-settings-for-web-projects"></a>Einstellungen von Eigenschaftenseiten für Webprojekte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die eigenschafteneinstellungen für eine Website-Debugkonfiguration im Ändern der **Eigenschaftenseiten** Dialogfeld wie in beschrieben [Debug- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md). Die folgenden Tabellen zeigen, wo Sie debuggerspezifischen Einstellungen im finden die **Eigenschaftenseiten** Dialogfeld.  
  
### <a name="configuration-properties-folder-start-options-category"></a>Ordner "Konfigurationseigenschaften" (Kategorie "Startoptionen")  
  
|**Einstellung**|**Beschreibung**|  
|-----------------|---------------------|  
|**Startaktion**|Überschrift, unter der sich Optionen für den Anwendungsstart befinden.|  
|**Aktuelle Seite verwenden**|Legt die aktuelle Seite als Ausgangspunkt für das Debuggen fest.|  
|**Bestimmte Seite:**|Gibt die Webseite an, bei der das Debuggen beginnen soll.|  
|**Starten Sie externes Programm:**|Gibt den Startbefehl für das Programm an, das gedebuggt werden soll.|  
|**Befehlszeilenargumente:**|Gibt Argumente für den oben aufgeführten Befehl an.|  
|**Arbeitsverzeichnis:**|Gibt das Arbeitsverzeichnis des Programms an, das gerade gedebuggt wird. Das Arbeitsverzeichnis in [!INCLUDE[csprcs](../includes/csprcs-md.md)] ist das Verzeichnis, über das die Anwendung gestartet wird: standardmäßig \bin\debug.|  
|**Start-URL**|Gibt den Pfad der Webanwendung an, die gedebuggt werden soll.|  
|**Keine Seite öffnen, Eine Anforderung einer externen Anwendung warten**|Legt fest, dass auf die Anforderung einer externen Anwendung gewartet wird. Mit dieser Option wird weder Internet Explorer noch eine andere Anwendung gestartet. Sie wird lediglich zum Debuggen vorbereitet, wenn sie von einer Anwendung aufgerufen wird.|  
|**Server**|Überschrift, unter der sich Optionen zum zu verwendenden Server befinden.|  
|**Standardwebserver verwenden**|Legt fest, dass der Standardwebserver verwendet wird.|  
|**Benutzerdefinierten Server verwenden**|Ermöglicht es Ihnen, die Basis-URL einzugeben, die als Server verwendet werden soll.|  
|**Debugger**|Überschrift, unter der sich Optionen zum Debugtyp befinden.|  
|**Debuggen von ASP.NET:**|Ermöglicht das Debuggen von Serverseiten, die für die [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]-Entwicklungsplattform geschrieben wurden. Sie müssen eine URL angeben **Start-URL**.|  
|**Debuggen von nativem code**|Bietet die Möglichkeit, Aufrufe von systemeigenem (nicht verwaltetem) Win32-Code von einer verwalteten Anwendung aus zu debuggen.|  
|**SQL Server-debugging**|Ermöglicht das Debuggen von SQL Server-Datenbankobjekten.|  
|**Silverlight-debugging**|Ermöglicht das Debuggen von Silverlight-Komponenten.|  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggereinstellungen und -vorbereitung](../debugger/debugger-settings-and-preparation.md)




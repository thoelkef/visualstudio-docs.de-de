---
title: "Einstellungen von Eigenschaftenseiten f&#252;r Webprojekte | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debugbuilds, Projekteinstellungen"
  - "Debugkonfigurationen, Webprojekte"
  - "Debuggen [Visual Studio], Webanwendungen"
  - "Debuggen von Webanwendungen, Projekteinstellungen"
  - "Projekteinstellungen [Visual Studio], Debugkonfigurationen"
  - "Projekte [Visual Studio], Debugkonfigurationen"
ms.assetid: 8ec5160a-6408-4f47-8d41-f0e20e79a3b9
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Einstellungen von Eigenschaftenseiten f&#252;r Webprojekte
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die Eigenschafteneinstellungen für eine Website\-Debugkonfiguration im Dialogfeld **Eigenschaftenseiten** ändern. Eine genaue Anweisung finden Sie unter [Debug\- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md).  Anhand der folgenden Tabellen erfahren Sie, wo die debuggerspezifischen Einstellungen im Dialogfeld **Eigenschaftenseiten** zu finden sind.  
  
### Ordner "Konfigurationseigenschaften" \(Kategorie "Startoptionen"\)  
  
|**Einstellung**|**Beschreibung**|  
|---------------------|----------------------|  
|**Startaktion**|Überschrift, unter der sich Optionen für den Anwendungsstart befinden.|  
|**Aktuelle Seite verwenden**|Legt die aktuelle Seite als Ausgangspunkt für das Debuggen fest.|  
|**Bestimmte Seite:**|Gibt die Webseite an, bei der das Debuggen beginnen soll.|  
|**Externes Programm starten:**|Gibt den Startbefehl für das Programm an, das gedebuggt werden soll.|  
|**Befehlszeilenargumente:**|Gibt Argumente für den oben aufgeführten Befehl an.|  
|**Arbeitsverzeichnis:**|Gibt das Arbeitsverzeichnis des Programms an, das gerade gedebuggt wird.  Das Arbeitsverzeichnis in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] ist das Verzeichnis, über das die Anwendung gestartet wird: standardmäßig \\bin\\debug.|  
|**Start\-URL**|Gibt den Pfad der Webanwendung an, die gedebuggt werden soll.|  
|**Öffnen Sie keine Seite.  Warten Sie auf eine Anforderung von einer externen Anwendung.**|Legt fest, dass auf die Anforderung einer externen Anwendung gewartet wird.  Mit dieser Option wird weder Internet Explorer noch eine andere Anwendung gestartet.  Sie wird lediglich zum Debuggen vorbereitet, wenn sie von einer Anwendung aufgerufen wird.|  
|**Server**|Überschrift, unter der sich Optionen zum zu verwendenden Server befinden.|  
|**Standardwebserver verwenden**|Legt fest, dass der Standardwebserver verwendet wird.|  
|**Benutzerdefinierten Server verwenden**|Ermöglicht es Ihnen, die Basis\-URL einzugeben, die als Server verwendet werden soll.|  
|**Debugger**|Überschrift, unter der sich Optionen zum Debugtyp befinden.|  
|**ASP.NET\-Debuggen**|Ermöglicht das Debuggen von Serverseiten, die für die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Entwicklungsplattform geschrieben wurden.  Sie müssen unter **Start\-URL** eine URL angeben.|  
|**Debuggen von systemeigenem Code**|Bietet die Möglichkeit, Aufrufe von systemeigenem \(nicht verwaltetem\) Win32\-Code von einer verwalteten Anwendung aus zu debuggen.|  
|**SQL Server\-Debuggen**|Ermöglicht das Debuggen von SQL Server\-Datenbankobjekten.|  
|**Silverlight\-Debugging**|Ermöglicht das Debuggen von Silverlight\-Komponenten.|  
  
## Siehe auch  
 [Einstellungen und Vorbereitung für das Debuggen](../debugger/debugger-settings-and-preparation.md)
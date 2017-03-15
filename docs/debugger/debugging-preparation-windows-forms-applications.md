---
title: "Vorbereitung zum Debuggen: Windows&#160;Forms-Anwendungen | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Debuggen [C#], Windows-Anwendungen"
  - "Debuggen [J#], Windows-Anwendungen"
  - "Debuggen [Visual Basic], Windows-Anwendungen"
  - "Debuggen [Visual Studio], Windows-Anwendungen"
  - "Debuggen von Windows-Anwendungen"
  - "Windows-Anwendungen, Debuggen"
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vorbereitung zum Debuggen: Windows&#160;Forms-Anwendungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Windows Forms\-Projektvorlage erstellt eine Windows Forms\-Anwendung.  Das Debuggen dieses Anwendungstyps in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ist einfach.  Weitere Informationen hierzu finden Sie unter [Creating a Windows Application Project](http://msdn.microsoft.com/de-de/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Wenn Sie ein Windows Forms\-Projekt mit der Projektvorlage erstellen, werden die erforderlichen Einstellungen für die Debug\- und Releasekonfigurationen automatisch durch [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] festgelegt.  Diese Einstellungen können ggf. geändert werden.  Diese Einstellungen können im Dialogfeld **\<Projektname\> Eigenschaftenseiten** \(in Visual Basic unter **Mein Projekt**\) geändert werden.  
  
 Weitere Informationen finden Sie unter [Empfohlene Eigenschafteneinstellungen](../debugger/managed-debugging-recommended-property-settings.md).  
  
 Eine zusätzlich empfohlene Eigenschafteneinstellung wird in der folgenden Tabelle angezeigt.  
  
### Konfigurationseigenschaften auf der Registerkarte "Debuggen"  
  
|**Eigenschaftenname**|**Einstellung**|  
|---------------------------|---------------------|  
|**Startaktion**|-   In den meisten Fällen stellen Sie **Projekt starten** ein.  Wählen Sie **Externes Programm starten**, wenn Sie zu Beginn des Debuggens eine andere ausführbare Datei starten möchten \(normalerweise für das Debuggen von DLLs\).|  
  
 Sie können Windows Forms\-Anwendungen aus [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] heraus debuggen oder durch das Anfügen zu einer bereits laufenden Anwendung.  Weitere Informationen zum Anfügen finden Sie unter [Anhängen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
### So debuggen Sie eine C\#\-, F\#\- oder Visual Basic\-Windows Forms\-Anwendung  
  
1.  Öffnen Sie das Projekt in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2.  Erstellen Sie Haltepunkte nach Bedarf.  
  
     Da Windows Forms\-Anwendungen ereignisgesteuert sind, gehen die Haltepunkte entweder in den Ereignishandlercode oder in Methoden, die vom Ereignishandlercode aufgerufen werden.  Typische Ereignisse, in denen Haltepunkte platziert werden sollte, sind z. B. folgende:  
  
    1.  Einem Steuerelement zugeordnete Ereignisse, z. B. Klicken, Drücken der Eingabetaste usw.  
  
    2.  Ereignisse, die dem Start bzw. Herunterfahren der Anwendung zugeordnet sind, z. B. Laden, Aktivierung usw.  
  
    3.  Fokusereignisse und Validierungsereignisse.  
  
     Weitere Informationen hierzu finden Sie unter [Erstellen von Ereignishandlern in Windows Forms](../Topic/Creating%20Event%20Handlers%20in%20Windows%20Forms.md).  
  
3.  Klicken Sie im Menü **Debuggen** auf **Starten**.  
  
4.  Debuggen Sie mit den in [Debugger – Grundlagen](../debugger/debugger-basics.md) besprochenen Techniken.  
  
## Siehe auch  
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)   
 [C\#\-, F\#\- und Visual Basic\-Projekttypen](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Gewusst wie: Festlegen von Debug\- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Projekteinstellungen für C\#\-Debugkonfigurationen](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Projekteinstellungen für eine Visual Basic\-Debugkonfiguration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Anhängen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows Forms](../Topic/Windows%20Forms.md)
---
title: "Gewusst wie: Anf&#252;gen eines Profilers an einen laufenden Prozess und Trennen eines Profilers von einem laufenden Prozess | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.attach"
helpviewer_keywords: 
  - "Leistungstools, Anfügen eines Prozesses"
  - "Profilerstellungstools, Trennen eines Prozesses"
  - "Profilerstellungstools, Anfügen eines Prozesses"
  - "Leistungstools, Trennen eines Prozesses"
  - "Profiler"
ms.assetid: 56a99c39-e7f6-4f48-ae56-04ab8e022bf7
caps.latest.revision: 30
caps.handback.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Anf&#252;gen eines Profilers an einen laufenden Prozess und Trennen eines Profilers von einem laufenden Prozess
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der Profiler ermöglicht Ihnen das Anfügen an einen laufenden Prozess bzw. das Trennen von einem laufenden Prozess, um das Sampling und Erfassen von Leistungsdaten zu erleichtern.  Verwenden Sie diese Methode, um ein Profil für einen Prozess zu erstellen, wenn keine Daten zur Ladedauer der Anwendung gesammelt werden sollen oder um die Leistung eines Prozesses zu überwachen, nachdem dieser einen bestimmten Zustand erreicht hat.  
  
> [!NOTE]
>  Führen Sie die folgenden Schritten zum Anfügen bzw. Trennen von Prozessen innerhalb der integrierten Entwicklungsumgebung \(IDE\) von [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] aus.  Informationen zum Verwenden von Befehlszeilentools finden Sie unter [Profilerstellung mithilfe der Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md).  Informationen zur Profilerstellung für Dienste finden Sie unter [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md).  
  
 Welche Prozesse für die Profilerstellung verfügbar sind, richtet sich nach den vom Administrator des Computers festgelegten Zugriffsberechtigungen des Benutzers.  Der Benutzer eines Kontos kann z. B. berechtigt sein,  
  
-   erweiterte Profilerstellungsfeatures zu nutzen, wenn der Administrator festgelegt hat, dass Treiber und Dienst gestartet werden.  
  
-   die Profilerstellung nur im Samplingmodus auszuführen \(Domänenbenutzer\).  
  
-   allen Benutzern den Zugriff auf die Profilerstellung zu verweigern.  
  
 Weitere Informationen finden Sie unter [Profilerstellung und Sicherheit in Windows Vista](../profiling/profiling-and-windows-vista-security.md) und in den ADMIN\-Optionen unter [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### So fügen Sie einen Profiler an einen laufenden Prozess an  
  
1.  Zeigen Sie im Menü **Analyse** auf **Profiler**, und klicken Sie dann auf **Anfügen\/Trennen**.  
  
     – oder –  
  
     Klicken Sie im **Leistungs\-Explorer** mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie dann auf **Anfügen\/Trennen**.  
  
     Das Dialogfeld **Profiler an Prozess anfügen** wird angezeigt.  
  
2.  Klicken Sie auf den Namen des Prozesses, den Sie anfügen möchten.  
  
3.  Klicken Sie auf **Anfügen**.  
  
### So trennen Sie einen Profiler von einem laufenden Prozess  
  
1.  Zeigen Sie im Menü **Analyse** auf **Profiler**, und klicken Sie dann auf **Anfügen\/Trennen**.  
  
     – oder –  
  
     Klicken Sie im **Leistungs\-Explorer** mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie dann auf **Anfügen\/Trennen**.  
  
     Das Dialogfeld **Profiler an Prozess anfügen** wird angezeigt.  
  
2.  Klicken Sie auf den Namen des Abbilds, das getrennt werden soll.  
  
3.  Klicken Sie auf **Trennen**.  
  
## Siehe auch  
 [Steuern der Datensammlung](../profiling/controlling-data-collection.md)   
 [Übersicht über Leistungssitzungen](../profiling/performance-session-overview.md)   
 [Gewusst wie: Starten und Beenden der Profilerstellung](../profiling/how-to-start-and-end-performance-data-collection.md)   
 [Profilerstellung und Sicherheit in Windows Vista](../profiling/profiling-and-windows-vista-security.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)
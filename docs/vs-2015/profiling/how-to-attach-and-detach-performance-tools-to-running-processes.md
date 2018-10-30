---
title: 'Vorgehensweise: Anfügen eines Profilers an einen laufenden Prozess und Trennen eines Profilers an einen laufenden Prozess | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.attach
helpviewer_keywords:
- performance tools, attach process
- profiling tools, detach process
- profiling tools, attach process
- performance tools, detach process
- profiler
ms.assetid: 56a99c39-e7f6-4f48-ae56-04ab8e022bf7
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ee38f210585124f8492f6aed9f062003602f287
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49895315"
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Vorgehensweise: Anfügen eines Profilers an einen laufenden Prozess und Trennen eines Profilers an einen laufenden Prozess
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Profiler kann verwendet werden, um an einen laufenden Prozess angefügt zu werden oder um von ihm getrennt zu werden, damit das Sampling und Sammeln von Leistungsdaten vereinfacht wird. Sie können diese Methode zum Erstellen eines Profils verwenden, wenn Sie das Sammeln von Daten über Anwendungsladezeiten vermeiden wollen oder nachdem es einen bestimmten Zustand erreicht hat.  
  
> [!NOTE]
>  Die folgenden Schritte gelten für das Anfügen und Trennen von Prozessen innerhalb der integrierten Entwicklungsumgebung [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] (IDE) Informationen zur Verwendung von Befehlszeilentools finden Sie unter [Profilerstellung mithilfe der Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md). Informationen zur Erstellung von Dienstprofilen finden Sie unter [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md).  
  
 Die Prozesse, die zur Profilerstellung verfügbar sind, hängen von den Benutzerzugriffsberechtigungen ab, die von einem Administrator des Computers festgelegt wurde. Ein Benutzerkonto kann z.B. Berechtigungen für eines der Folgenden haben:  
  
- Erweiterte Profilerstellungsfunktionen, wenn der Administrator Treiber und Dienste gestartet hat.  
  
- Nur Beispiel-Profilerstellung (Domänenbenutzer).  
  
- Zugriff zur Profilerstellung für alle Benutzer verweigern.  
  
  Weitere Informationen finden Sie unter [Profilerstellung und Sicherheit in Windows Vista](../profiling/profiling-and-windows-vista-security.md) und den ADMIN-Optionen in [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-attach-to-a-running-process"></a>So fügen Sie einen Profiler an einen laufenden Prozess an  
  
1.  Zeigen Sie im Menü **Analysieren** auf **Profiler**, und klicken Sie anschließend auf **Anfügen/Trennen**.  
  
     \- oder –  
  
     Klicken Sie im **Leistungs-Explorer**mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie dann auf **Anfügen/Trennen**.  
  
     Das Dialogfeld **Profiler an den Prozess anhängen** wird angezeigt.  
  
2.  Klicken Sie auf den Prozessnamen, mit dem eine Verbindung hergestellt werden soll.  
  
3.  Klicken Sie auf **Anfügen**.  
  
### <a name="to-detach-from-a-running-process"></a>So trennen Sie den Profiler von einem laufenden Prozess  
  
1.  Zeigen Sie im Menü **Analysieren** auf **Profiler**, und klicken Sie anschließend auf **Anfügen/Trennen**.  
  
     \- oder –  
  
     Klicken Sie im **Leistungs-Explorer**mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie dann auf **Anfügen/Trennen**.  
  
     Das Dialogfeld **Profiler an den Prozess anhängen** wird angezeigt.  
  
2.  Klicken Sie auf den Imagenamen, von dem Sie den Profiler trennen möchten.  
  
3.  Klicken Sie auf **Trennen**.  
  
## <a name="see-also"></a>Siehe auch  
 [Steuern der Datensammlung](../profiling/controlling-data-collection.md)   
 [Übersicht über Leistungssitzungen](../profiling/performance-session-overview.md)   
 [Vorgehensweise: Starten und Beenden der Sammlung von Leistungsdaten](../profiling/how-to-start-and-end-performance-data-collection.md)   
 [Profilerstellung und Sicherheit in Windows Vista](../profiling/profiling-and-windows-vista-security.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)




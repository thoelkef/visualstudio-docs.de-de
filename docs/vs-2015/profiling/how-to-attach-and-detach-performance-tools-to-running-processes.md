---
title: 'Vorgehensweise: Anfügen eines Profilers an einen laufenden Prozess und Trennen eines Profilers an einen laufenden Prozess | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0b8fc664ee47cd34ab984d1ac448b45c2f17c5b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841042"
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Vorgehensweise: Anfügen eines Profilers an einen laufenden Prozess und Trennen eines Profilers an einen laufenden Prozess
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Profiler kann verwendet werden, um an einen laufenden Prozess angefügt zu werden oder um von ihm getrennt zu werden, damit das Sampling und Sammeln von Leistungsdaten vereinfacht wird. Sie können diese Methode zum Erstellen eines Profils verwenden, wenn Sie das Sammeln von Daten über Anwendungsladezeiten vermeiden wollen oder nachdem es einen bestimmten Zustand erreicht hat.  
  
> [!NOTE]
> Die folgenden Schritte gelten für das Anfügen und Trennen von Prozessen innerhalb der integrierten Entwicklungsumgebung [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] (IDE) Informationen zur Verwendung von Befehlszeilentools finden Sie unter [Profilerstellung mithilfe der Befehlszeile](../profiling/using-the-profiling-tools-from-the-command-line.md). Informationen zur Erstellung von Dienstprofilen finden Sie unter [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md).  
  
 Die Prozesse, die zur Profilerstellung verfügbar sind, hängen von den Benutzerzugriffsberechtigungen ab, die von einem Administrator des Computers festgelegt wurde. Ein Benutzerkonto kann z.B. Berechtigungen für eines der Folgenden haben:  
  
- Erweiterte Profilerstellungsfunktionen, wenn der Administrator Treiber und Dienste gestartet hat.  
  
- Nur Beispiel-Profilerstellung (Domänenbenutzer).  
  
- Zugriff zur Profilerstellung für alle Benutzer verweigern.  
  
  Weitere Informationen finden Sie unter [Profilerstellung und Windows Vista-Sicherheit](../profiling/profiling-and-windows-vista-security.md) sowie in den Admin-Optionen in [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-attach-to-a-running-process"></a>So fügen Sie einen Profiler an einen laufenden Prozess an  
  
1. Zeigen Sie im Menü **Analysieren** auf **Profiler**, und klicken Sie anschließend auf **Anfügen/Trennen**.  
  
     \- oder -  
  
     Klicken Sie im **Leistungs-Explorer**mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie dann auf **Anfügen/Trennen**.  
  
     Das Dialogfeld **Profiler an den Prozess anhängen** wird angezeigt.  
  
2. Klicken Sie auf den Prozessnamen, mit dem eine Verbindung hergestellt werden soll.  
  
3. Klicken Sie auf **Anfügen**aus.  
  
### <a name="to-detach-from-a-running-process"></a>So trennen Sie den Profiler von einem laufenden Prozess  
  
1. Zeigen Sie im Menü **Analysieren** auf **Profiler**, und klicken Sie anschließend auf **Anfügen/Trennen**.  
  
     \- oder -  
  
     Klicken Sie im **Leistungs-Explorer**mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie dann auf **Anfügen/Trennen**.  
  
     Das Dialogfeld **Profiler an den Prozess anhängen** wird angezeigt.  
  
2. Klicken Sie auf den Imagenamen, von dem Sie den Profiler trennen möchten.  
  
3. Klicken Sie auf **Trennen**.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Steuern der Datensammlung](../profiling/controlling-data-collection.md)   
 [Übersicht über Leistungs Sitzungen](../profiling/performance-session-overview.md)   
 [Gewusst wie: starten und Beenden der Sammlung von Leistungsdaten](../profiling/how-to-start-and-end-performance-data-collection.md)   
 [Profilerstellung und Sicherheit in Windows Vista](../profiling/profiling-and-windows-vista-security.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)

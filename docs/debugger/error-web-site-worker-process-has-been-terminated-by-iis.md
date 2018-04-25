---
title: 'Fehler: Websiteworkerprozess wurde beendet von IIS | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.web_server_process_terminated
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ca76a0e66073d0102adb97d8cc4ca35087399297
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>Fehler: Websiteworkerprozess wurde von IIS beendet
Der Debugger hat die Codeausführung auf der Website beendet. Dadurch gehen die Internetinformationsdienste (IIS) davon aus, dass der Arbeitsprozess nicht mehr reagiert. Folglich wurde der Arbeitsprozess von IIS beendet.  
  
 Um das Debuggen fortzusetzen, müssen Sie IIS so konfigurieren, dass der Arbeitsprozess fortgesetzt wird. Diese Fehlermeldung wird erst ab IIS 7 angezeigt.  
  
### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>So konfigurieren Sie IIS 7 für die Fortsetzung des Arbeitsprozesses  
  
1.  Öffnen der **Verwaltung** Fenster.  
  
    1.  Klicken Sie auf **starten**, und wählen Sie dann **Systemsteuerung**.  
  
    2.  In **Systemsteuerung**, wählen Sie **zur klassischen Ansicht wechseln**, falls erforderlich, und doppelklicken Sie dann auf **Verwaltung**.  
  
2.  In der **Verwaltung** Fenster, doppelklicken Sie auf **(Internet Information Services, IIS) Manager**.  
  
     Der IIS-Manager wird geöffnet.  
  
3.  In der **Verbindungen** Bereich, erweitern Sie die \<Computername > Knoten bei Bedarf.  
  
4.  Klicken Sie unter der \<Computername > Knoten, klicken Sie auf **Anwendungspools**.  
  
5.  In der **Anwendungspools** auflisten, mit der rechten Maustaste in des Namens des Pools für Ihre Anwendung ausgeführt wird, und klicken Sie dann auf **Erweiterte Einstellungen**.  
  
6.  In der **Erweiterte Einstellungen** Dialogfeld Suchen der **Prozessmodell** Abschnitt, und führen Sie eine der folgenden Aktionen:  
  
    -   Legen Sie **Ping aktiviert** auf **"false"**.  
  
    -   Legen Sie **maximale Ping-Antwortzeit** auf einen Wert, der größer als 90 Sekunden ist.  
  
     Festlegen von **Ping aktiviert** auf **"false"** überprüft, ob der Arbeitsprozess wird jedoch weiter ausgeführt und den Arbeitsprozess aktiv, hält bis Sie des Debugprozesses IIS nicht mehr. Festlegen von **maximale Ping-Antwortzeit** auf einen hohen Wert können Sie IIS für die Überwachung des Arbeitsprozesses fort.  
  
7.  Klicken Sie auf **OK** schließen die **Erweiterte Einstellungen** (Dialogfeld).  
  
8.  Schließen Sie den IIS-Manager und die **Verwaltung** Fenster.  
  
## <a name="see-also"></a>Siehe auch  
 [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)
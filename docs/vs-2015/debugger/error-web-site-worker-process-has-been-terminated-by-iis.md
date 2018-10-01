---
title: 'Fehler: Websiteworkerprozess wurde vom beendet IIS | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.web_server_process_terminated
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 5707b972-71a6-4cc6-ab99-c7c00ca8628c
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81396165841b0c23a317a857e73d7adbf88971dc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47521001"
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>Fehler: Websiteworkerprozess wurde von IIS beendet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Fehler: Websiteworkerprozess wurde von IIS beendet](https://docs.microsoft.com/visualstudio/debugger/error-web-site-worker-process-has-been-terminated-by-iis).  
  
Der Debugger hat die Codeausführung auf der Website beendet. Dadurch gehen die Internetinformationsdienste (IIS) davon aus, dass der Arbeitsprozess nicht mehr reagiert. Folglich wurde der Arbeitsprozess von IIS beendet.  
  
 Um das Debuggen fortzusetzen, müssen Sie IIS so konfigurieren, dass der Arbeitsprozess fortgesetzt wird. Diese Fehlermeldung wird erst ab IIS 7 angezeigt.  
  
### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>So konfigurieren Sie IIS 7 für die Fortsetzung des Arbeitsprozesses  
  
1.  Öffnen der **Verwaltung** Fenster.  
  
    1.  Klicken Sie auf **starten**, und wählen Sie dann **Systemsteuerung**.  
  
    2.  In **Systemsteuerung**, wählen Sie **zur klassischen Ansicht wechseln**, falls erforderlich, und doppelklicken Sie dann auf **Verwaltung**.  
  
2.  In der **Verwaltung** Fenster, doppelklicken Sie auf **(Internet Information Services, IIS) Manager**.  
  
     Der IIS-Manager wird geöffnet.  
  
3.  In der **Verbindungen** Bereich, erweitern Sie die \<Computername > Knoten bei Bedarf.  
  
4.  Unter den \<Computername > Knoten, klicken Sie auf **Anwendungspools**.  
  
5.  In der **Anwendungspools** auflisten, mit der rechten Maustaste in des Namens des Pools, die Ihre Anwendung ausgeführt wird, und klicken Sie dann auf **Erweiterte Einstellungen**.  
  
6.  In der **Erweiterte Einstellungen** Dialogfeld Suchen der **Prozessmodell** aus, und führen Sie eine der folgenden Aktionen aus:  
  
    -   Legen Sie **Ping aktiviert** zu **"false"**.  
  
    -   Legen Sie **maximale Ping-Antwortzeit** auf einen Wert, der größer als 90 Sekunden ist.  
  
     Festlegen von **Ping aktiviert** zu **"false"** verhindert, dass IIS überprüft, ob der Arbeitsprozess wird weiterhin ausgeführt und den Arbeitsprozess aktiv, hält bis Sie Ihre debuggten Prozess beenden. Festlegen von **maximale Ping-Antwortzeit** auf einen hohen Wert können Sie IIS für die Überwachung des Arbeitsprozesses fort.  
  
7.  Klicken Sie auf **OK** schließen die **Erweiterte Einstellungen** Dialogfeld.  
  
8.  Schließen Sie den IIS-Manager und die **Verwaltung** Fenster.  
  
## <a name="see-also"></a>Siehe auch  
 [Remotedebuggen – Fehler und Problembehandlung](../debugger/remote-debugging-errors-and-troubleshooting.md)




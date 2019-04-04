---
title: Debuggen von 64-Bit-Anwendungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], 64-bit
- 64-bit debugging
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 600166699a40ac91d403d7b76948ac924b4a35c2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58960357"
---
# <a name="debug-64-bit-applications"></a>Debuggen von 64-Bit-Anwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Debuggen von 64-Bit-Anwendungen](https://docs.microsoft.com/visualstudio/debugger/debug-64-bit-applications) .  
  
Sie können eine 64-Bit-Anwendung debuggen, die auf dem lokalen Computer oder einem Remotecomputer ausgeführt wird.  
  
 Informationen zum Debuggen einer 64-Bit-Anwendung, die auf einem Remotecomputer ausgeführt wird, finden Sie unter [Remote Debugging](../debugger/remote-debugging.md).  
  
 Um 64-Bit-Anwendungen lokal zu debuggen, verwendet Visual Studio einen 64-Bit-Arbeitsprozess (msvsmon.exe), um die die Low-Level-Vorgänge auszuführen, die nicht im 32-Bit-Visual Studio-Prozess ausgeführt werden können.  
  
 Debuggen im gemischten Modus wird nicht für 64-Bit-Prozesse unterstützt, in denen .NET Framework Version 3.5 oder früher verwendet wird.  
  
## <a name="debug-a-64-bit-application"></a>Debuggen einer 64-Bit-Anwendung  
 So können Sie eine 64-Bit-Anwendung debuggen:  
  
1.  Erstellen Sie eine Visual Studio-Projektmappe z. B. ein C#-Konsolenanwendungsprojekt.  
  
2.  Legen Sie die Konfiguration mit dem Konfigurations-Manager auf 64-Bit fest. Weitere Informationen finden Sie unter [Vorgehensweise: Konfigurieren von Projekten für Zielplattformen](../ide/how-to-configure-projects-to-target-platforms.md).  
  
3.  Nun wird die 64-Bit-Version des Remotedebuggers (msvsmon.exe) gestartet. Diese wird ausgeführt, solange die Projektmappe mit der 64-Bit-Konfiguration geöffnet ist.  
  
4.  Beginnen Sie mit dem Debuggen. Ihnen sollte dieselbe Funktionalität zur Verfügung stehen wie bei einer 32-Bit-Konfiguration. Informationen zur Vorgehensweise bei Fehlern finden Sie nachstehend im Abschnitt „Problembehandlung“.  
  
## <a name="troubleshooting-64-bit-debugging"></a>Problembehandlung beim 64-Bit-Debuggen  
 Sie können ein Fehler angezeigt: "Ein 64-Bit-debuggingvorgang dauert länger als erwartet." In diesem Fall hat Visual Studio eine Anforderung an die 64-Bit-Version von „msvsmon.exe“ gesendet, und es hat sehr lange gedauert , bis das Ergebnis dieser Anforderung eingetroffen ist.  
  
 Für diesen Fehler gibt es zwei Hauptursachen:  
  
-   Sie haben Netzwerksicherheitssoftware auf dem Computer installiert, die dazu geführt hat, dass der Netzwerkstapel unzuverlässig wurde und über Localhost gesendete Pakete gelöscht wurden. Deaktivieren Sie jegliche Netzwerksicherheitssoftware, und ermitteln Sie, ob das Problem damit behoben ist. Wenn ja, teilen Sie dem Hersteller der Netzwerksicherheitssoftware mit, dass die Software zu einem Konflikt mit Localhost-Datenverkehr führt.  
  
-   Sie treffen auf ein Absturz- oder Leistungsproblem mit Visual Studio. Tritt dieses Problem regelmäßig auf, können Sie Speicherabbilder von Visual Studio (devenv.exe) und vom Arbeitsprozess (msvsmon.exe) sammeln und diese an Microsoft senden. 
  
## <a name="see-also"></a>Siehe auch  
 [64-Bit-Anwendungen](http://msdn.microsoft.com/library/fd4026bc-2c3d-4b27-86dc-ec5e96018181)   
 [Konfigurieren von Programmen für 64-Bit](http://msdn.microsoft.com/library/cb99f72b-8c74-48f4-846a-8921b37b97e9)   
 [Visual Studio-IDE-64-Bit-Unterstützung](../ide/visual-studio-ide-64-bit-support.md)   
 [Verwenden von Dumpdateien](../debugger/using-dump-files.md)   
 [Remote Debugging](../debugger/remote-debugging.md)

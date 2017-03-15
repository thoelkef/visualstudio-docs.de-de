---
title: "Debuggen von 64-Bit-Anwendungen | Microsoft Docs"
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
helpviewer_keywords: 
  - "Debuggen [Visual Studio], 64-Bit"
  - "64-Bit-Debuggen"
ms.assetid: db648e5f-6375-4e2d-aa98-eb7261958927
caps.latest.revision: 32
caps.handback.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Debuggen von 64-Bit-Anwendungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können eine 64\-Bit\-Anwendung debuggen, die auf dem lokalen Computer oder einem Remotecomputer ausgeführt wird.  
  
 Informationen zum Debuggen einer 64\-Bit\-Anwendung, die auf einem Remotecomputer ausgeführt wird, finden Sie unter [Remotedebugging](../debugger/remote-debugging.md).  
  
 Um 64\-Bit\-Anwendungen lokal zu debuggen, verwendet Visual Studio einen 64\-Bit\-Arbeitsprozess \(msvsmon.exe\), um die die Low\-Level\-Vorgänge auszuführen, die nicht im 32\-Bit\-Visual Studio\-Prozess ausgeführt werden können.  
  
 Debuggen im gemischten Modus wird nicht für 64\-Bit\-Prozesse unterstützt, in denen .NET Framework Version 3.5 oder früher verwendet wird.  
  
## Debuggen einer 64\-Bit\-Anwendung  
 So können Sie eine 64\-Bit\-Anwendung debuggen:  
  
1.  Erstellen Sie eine Visual Studio\-Projektmappe z. B. ein C\#\-Konsolenanwendungsprojekt.  
  
2.  Legen Sie die Konfiguration mit dem Konfigurations\-Manager auf 64\-Bit fest. Weitere Informationen finden Sie unter [Gewusst wie: Konfigurieren von Projekten für Zielplattformen](../ide/how-to-configure-projects-to-target-platforms.md).  
  
3.  Nun wird die 64\-Bit\-Version des Remotedebuggers \(msvsmon.exe\) gestartet. Diese wird ausgeführt, solange die Projektmappe mit der 64\-Bit\-Konfiguration geöffnet ist.  
  
4.  Beginnen Sie mit dem Debuggen. Ihnen sollte dieselbe Funktionalität zur Verfügung stehen wie bei einer 32\-Bit\-Konfiguration. Informationen zur Vorgehensweise bei Fehlern finden Sie nachstehend im Abschnitt „Problembehandlung“.  
  
## Problembehandlung beim 64\-Bit\-Debuggen  
 Möglicherweise wird folgende Fehlermeldung angezeigt: „Ein 64\-Bit\-Debuggingvorgang dauert länger als erwartet.“ In diesem Fall hat Visual Studio eine Anforderung an die 64\-Bit\-Version von „msvsmon.exe“ gesendet, und es hat sehr lange gedauert , bis das Ergebnis dieser Anforderung eingetroffen ist.  
  
 Für diesen Fehler gibt es zwei Hauptursachen:  
  
-   Sie haben Netzwerksicherheitssoftware auf dem Computer installiert, die dazu geführt hat, dass der Netzwerkstapel unzuverlässig wurde und über Localhost gesendete Pakete gelöscht wurden. Deaktivieren Sie jegliche Netzwerksicherheitssoftware, und ermitteln Sie, ob das Problem damit behoben ist. Wenn ja, teilen Sie dem Hersteller der Netzwerksicherheitssoftware mit, dass die Software zu einem Konflikt mit Localhost\-Datenverkehr führt.  
  
-   Sie treffen auf ein Absturz\- oder Leistungsproblem mit Visual Studio. Tritt dieses Problem regelmäßig auf, können Sie Speicherabbilder von Visual Studio \(devenv.exe\) und vom Arbeitsprozess \(msvsmon.exe\) sammeln und diese an Microsoft senden. Weitere Informationen zum Berichten eines Problems finden Sie unter [Melden eines Problems mit Visual Studio](../Topic/How%20to%20Report%20a%20Problem%20with%20Visual%20Studio.md).  
  
## Siehe auch  
 [64\-Bit\-Anwendungen](../Topic/64-bit%20Applications.md)   
 [Konfigurieren von Programmen für 64\-Bit](/visual-cpp/build/configuring-programs-for-64-bit-visual-cpp)   
 [Visual Studio\-IDE\-64\-Bit\-Unterstützung](../ide/visual-studio-ide-64-bit-support.md)   
 [Debuggen einer Anwendung mit Dumpdateien, falls sie abstürzt oder nicht mehr reagiert](../debugger/using-dump-files.md)   
 [Remotedebugging](../debugger/remote-debugging.md)
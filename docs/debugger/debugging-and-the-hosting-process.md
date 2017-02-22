---
title: "Debuggen und der Hostprozess | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
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
  - "Debuggen [Visual Studio], Hostingprozess"
  - "Hostingprozess"
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Debuggen und der Hostprozess
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der Visual Studio\-Hostprozess verbessert die Debugleistung und ermöglicht neue Debuggerfeatures, z. B. das Debuggen von teilweise vertrauenswürdigen Anwendungen und die Ausdrucksauswertung zur Entwurfszeit. Falls erforderlich, können Sie den Hostprozess deaktivieren. Weitere Informationen finden Sie unter [Gewusst wie: Deaktivieren des Hostprozesses](../ide/how-to-disable-the-hosting-process.md). In den folgenden Abschnitten werden einige der Unterschiede beschrieben, die zwischen dem Debuggen mit und ohne den Hostprozess bestehen.  
  
## Debuggen teilweise vertrauenswürdiger Anwendungen und ClickOnce\-Sicherheit  
 Zum Debuggen teilweise vertrauenswürdiger Anwendungen ist der Hostprozess erforderlich. Wenn Sie den Hostprozess deaktivieren, ist das Debuggen teilweise vertrauenswürdiger Anwendungen nicht möglich, selbst wenn auf der **Sicherheitsseite** der **Projekteigenschaften** die Sicherheit bei teilweiser Vertrauenswürdigkeit aktiviert wurde. Weitere Informationen finden Sie unter [Gewusst wie: Deaktivieren des Hostprozesses](../ide/how-to-disable-the-hosting-process.md) und [Gewusst wie: Debuggen einer teilweise vertrauenswürdigen Anwendung](../debugger/how-to-debug-a-partial-trust-application.md).  
  
## Ausdrucksauswertung zur Entwurfszeit  
 Bei der Ausdrucksauswertung zur Entwurfszeit wird stets auf den Hostprozess zugegriffen. Wird der Hostprozess in den **Projekteigenschaften** deaktiviert, so wird damit auch die Ausdrucksauswertung zur Entwurfszeit für Klassenbibliotheksprojekte deaktiviert. Für die anderen Projekttypen steht die Ausdrucksauswertung zur Entwurfszeit weiterhin zur Verfügung. Visual Studio startet stattdessen die eigentliche ausführbare Datei und verwendet diese zur Evaluierung während der Entwurfszeit, ohne auf den Hostprozess zuzugreifen. Dies führt möglicherweise zu abweichenden Ergebnissen.  
  
## Unterschiede bezüglich "AppDomain.CurrentDomain.FriendlyName"  
 Abhängig davon, ob der Hostprozess aktiviert ist oder nicht, liefert `AppDomain.CurrentDomain.FriendlyName` unterschiedliche Ergebnisse. Wenn Sie `AppDomain.CurrentDomain.FriendlyName` bei aktiviertem Hostprozess aufrufen, wird *app\_name*`.vhost.exe` zurückgegeben. Wenn der Aufruf bei deaktiviertem Hostprozess erfolgt, wird *app\_name*`.exe` zurückgegeben.  
  
## Unterschiede bezüglich "Assembly.GetCallingAssembly\(\).FullName"  
 Abhängig davon, ob der Hostprozess aktiviert ist oder nicht, liefert `Assembly.GetCallingAssembly().FullName` unterschiedliche Ergebnisse. Wenn Sie `Assembly.GetCallingAssembly().FullName` bei aktiviertem Hostprozess aufrufen, wird `mscorlib` zurückgegeben. Wird `Assembly.GetCallingAssembly().FullName` bei deaktiviertem Hostprozess aufgerufen, wird der Anwendungsname zurückgegeben.  
  
## Siehe auch  
 [Hostprozess \(vshost.exe\)](../ide/hosting-process-vshost-exe.md)   
 [Gewusst wie: Debuggen einer teilweise vertrauenswürdigen Anwendung](../debugger/how-to-debug-a-partial-trust-application.md)   
 [Gewusst wie: Deaktivieren des Hostprozesses](../ide/how-to-disable-the-hosting-process.md)
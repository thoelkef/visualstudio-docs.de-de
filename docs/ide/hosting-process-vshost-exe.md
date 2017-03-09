---
title: "Hostprozess (vshost.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Hostingprozess"
  - "vshost.exe"
ms.assetid: c6b9e2be-f18d-4d75-ac52-56d55784734b
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Hostprozess (vshost.exe)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der Hostprozess ist ein Feature in Visual Studio, die Debugleistung verbessert, Debuggen teilweise vertrauenswürdiger Anwendungen ermöglicht und die Ausdrucksauswertung zur Entwurfszeit ermöglicht.  Die zum Hostprozess gehörigen Dateien sind am Begriff "vshost" im Dateinamen erkennbar und werden im Ausgabeordner des jeweiligen Projekts abgelegt.  Weitere Informationen finden Sie unter [Debuggen und der Hostprozess](../debugger/debugging-and-the-hosting-process.md).  
  
> [!NOTE]
>  Hosting Prozessdateien \(. vshost.exe\) sind für die Verwendung von Visual Studio und sollte nicht direkt ausgeführt oder mit der Anwendung bereitgestellt.  
  
## Verbesserte Debugleistung  
 Der Hostprozess erstellt eine Anwendungsdomäne und ordnet der Anwendung den Debugger zu.  Diese Schritte können eine erhebliche Verzögerung zwischen dem Start des Debugvorgangs und dem Start der Anwendungsausführung bewirken.  Der Hostprozess unterstützt die Leistungsoptimierung, indem die Erstellung der Anwendungsdomäne und die Zuordnung des Debuggers im Hintergrund erfolgen. Außerdem werden die Anwendungsdomäne und der Debuggerzustand zwischen den Ausführungszyklen der Anwendung gespeichert.  Weitere Informationen zu Anwendungsdomänen finden Sie unter [Anwendungsdomänen](../Topic/Application%20Domains.md).  
  
## Debuggen von teilweise vertrauenswürdigen Anwendungen  
 Eine Anwendung kann auf der [Seite Sicherheit](../ide/reference/security-page-project-designer.md) des **Projekt\-Designers** als teilweise vertrauenswürdige Anwendung definiert werden.  Zum Debuggen einer teilweise vertrauenswürdigen Anwendung ist eine spezielle Initialisierung der Anwendungsdomäne erforderlich.  Diese Initialisierung erfolgt über den Hostprozess.  
  
## Ausdrucksauswertung zur Entwurfszeit  
 Durch die Ausdrucksauswertung zur Entwurfszeit können Sie Code über das **Direktfenster** testen, ohne dass die Anwendung ausgeführt werden muss.  Dieser Code wird während der Ausdrucksauswertung zur Entwurfszeit vom Hostprozess ausgeführt.  Weitere Informationen finden Sie unter [Direktfenster](../ide/reference/immediate-window.md).  
  
## Siehe auch  
 [Debuggen und der Hostprozess](../debugger/debugging-and-the-hosting-process.md)   
 [Gewusst wie: Deaktivieren des Hostprozesses](../ide/how-to-disable-the-hosting-process.md)   
 [Direktfenster](../ide/reference/immediate-window.md)   
 [Anwendungsdomänen](../Topic/Application%20Domains.md)
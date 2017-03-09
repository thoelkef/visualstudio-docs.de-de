---
title: "Debuggen von ASP.NET- und AJAX-Anwendungen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "Debuggen [ASP.NET], Informationen über ASP.NET-Debuggen"
  - "Debuggen von ASP.NET-Webanwendungen"
  - "Debuggen, WCF"
  - "WCF, Debuggen"
ms.assetid: 9d531913-541b-47b8-864d-138021fca0c6
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Debuggen von ASP.NET- und AJAX-Anwendungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Debuggen von [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webanwendungen ähnelt dem Debuggen von Windows Forms oder anderen Windows\-Anwendungen, da beide Arten von Anwendungen Steuerelemente und Ereignisse enthalten.  Aber es gibt auch grundlegende Unterschiede zwischen den beiden Anwendungsarten:  
  
-   Die Zustandsüberwachung ist in einer Webanwendung komplexer.  
  
-   In einer Windows\-Anwendung befindet sich der zu debuggende Code meistens an einem Ort. Bei einer Webanwendung kann der Code auf dem Client und auf dem Server vorhanden sein.  Obwohl sich der gesamte [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Code auf dem Server befindet, kann auf dem Client auch JavaScript\- oder [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Code vorhanden sein.  
  
## In diesem Abschnitt  
 [Vorbereitungen zum Debuggen von ASP.NET](../debugger/preparing-to-debug-aspnet.md)  
 Beschreibt die erforderlichen Schritte, um das Debuggen von [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Anwendungen zu ermöglichen.  
  
 [Debuggen von Webanwendungen](../debugger/debugging-web-applications.md)  
 Erläutert das Debuggen einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Anwendung, einschließlich AJAX\-fähiger Skriptanwendungen.  
  
## Verwandte Abschnitte  
 [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md)  
 Erläutert, warum Nur mein Code zum Debuggen von [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Ausnahmen aktiviert werden muss.  
  
 [Debugging and Tracing Ajax Applications Overview](../Topic/Debugging%20and%20Tracing%20Ajax%20Applications%20Overview.md)  
 Es werden einige Techniken und Tools erläutert, die Ihnen beim Debuggen Ihres AJAX\-Codes helfen können.  
  
 [Verwenden von IntelliTrace](../debugger/intellitrace.md)  
 Debuggen Sie den Code schneller, indem Sie mit IntelliTrace einen Verlauf vom Zustand der Anwendung aufzuzeichnen und überprüfen, ohne die Anwendung so oft neu zu starten.  Sie können Informationen zu Ereignissen und Aufrufen, die während der Ausführung der Anwendung auftreten, anzeigen und das Debuggen ab diesen Zeitpunkten starten.  Erfordert Visual Studio Ultimate.  
  
## Siehe auch  
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Debuggen von Webanwendungen und Skripts](../debugger/debugging-web-applications-and-script.md)   
 [Einstellungen und Vorbereitung für das Debuggen](../debugger/debugger-settings-and-preparation.md)   
 [Debugger – Grundlagen](../debugger/debugger-basics.md)
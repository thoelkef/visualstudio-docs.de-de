---
title: "Diagnosemeldungen im Ausgabefenster | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.output"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debug-Klasse"
  - "Debug.Print-Ersetzungen"
  - "Debugger, Ausgabefenster"
  - "Debuggen [Visual Studio], Diagnosemeldungen im Ausgabefenster"
  - "Diagnose"
  - "Diagnosemeldungen [C#]"
  - "Diagnose"
  - "Meldungen, Diagnose"
  - "Ausgabefenster, Diagnosemeldungen"
  - "System.Diagnostics.Debug-Klasse, Ausgabefenster"
  - "System.Diagnostics.Trace-Klasse, Ausgabefenster"
  - "Trace-Klasse, Diagnosemeldungen"
ms.assetid: 386e9524-be17-4573-83fb-4f7c5cae0be0
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Diagnosemeldungen im Ausgabefenster
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Laufzeitmeldungen können im Ausgabefenster mithilfe der Debug\-Klasse oder der Trace\-Klasse ausgegeben werden. Beide sind Bestandteil der <xref:System.Diagnostics>\-Klassenbibliothek.  Falls die Ausgabe lediglich in der Debugversion des Programms erfolgen soll, verwenden Sie die **Debug**\-Klasse.  Soll die Ausgabe sowohl in der Debug\- als auch in der Releaseversion erfolgen, verwenden Sie die **Trace**\-Klasse.  
  
## Ausgabemethoden  
 Die <xref:System.Diagnostics.Trace>\-Klasse und die <xref:System.Diagnostics.Debug>\-Klasse stellen die folgenden Ausgabemethoden bereit:  
  
-   Verschiedene `Write`\-Methoden, die die Ausgabe von Informationen ermöglichen, ohne dass die Ausführung unterbrochen wird.  Diese Methoden ersetzen die `Debug.Print`\-Methode, die in früheren Versionen von Visual Basic verwendet wurde.  
  
-   Die <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>\-Methode und die <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>\-Methode, durch die die Ausführung unterbrochen wird und Informationen ausgegeben werden, wenn eine festgelegte Bedingung nicht erfüllt ist.  Standardmäßig werden die Informationen der `Assert`\-Methode in einem Dialogfeld angezeigt.  Weitere Informationen finden Sie unter [Assertionen in verwaltetem Code](../debugger/assertions-in-managed-code.md).  
  
-   Die <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName>\-Methode und die <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName>\-Methode, durch die die Ausführung stets unterbrochen wird und Informationen ausgegeben werden.  Standardmäßig werden die Informationen der `Fail`\-Methoden in einem Dialogfeld angezeigt.  
  
 Neben Programmausgabe der Anwendung kann das **Ausgabefenster** Informationen anzeigen über:  
  
-   Module, die der Debugger geladen oder entladen hat.  
  
-   Ausnahmen, die ausgelöst werden.  
  
-   Prozesse, die beendet werden.  
  
-   Threads, die beendet werden.  
  
## Siehe auch  
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Ausgabefenster](../ide/reference/output-window.md)   
 [Tracing and Instrumenting Applications](../Topic/Tracing%20and%20Instrumenting%20Applications.md)   
 [Introduction to Instrumentation and Tracing](http://msdn.microsoft.com/de-de/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)   
 [C\#\-, F\#\- und Visual Basic\-Projekttypen](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
---
title: Diagnosemeldungen im Ausgabefenster senden | Microsoft Docs
ms.custom: ''
ms.date: 04/25/2017
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- diagnostic messages [C#]
- System.Diagnostics.Debug class, Output window
- messages, diagnostic
- Debug.Print replacements
- diagnosis
- Output window, diagnostic messages
- System.Diagnostics.Trace class, Output window
- Trace class, diagnostic messages
- diagnostics
- debugger, Output window
- debugging [Visual Studio], diagnostic messages in Output window
- Debug class
ms.assetid: 386e9524-be17-4573-83fb-4f7c5cae0be0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 36b85d16fffe8ddf6e0523eecca09e044283b7e3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="send-diagnostic-messages-to-the-output-window"></a>Diagnosemeldungen im Ausgabefenster senden
Können Sie laufzeitmeldungen zum Schreiben der **Ausgabe** unter Verwendung der `Debug` Klasse oder die `Trace` -Klasse, die Teil von der <xref:System.Diagnostics> -Klassenbibliothek. Falls die Ausgabe lediglich in der Debugversion des Programms erfolgen soll, verwenden Sie die Debug-Klasse. Soll die Ausgabe sowohl in der Debug- als auch in der Releaseversion erfolgen, verwenden Sie die Trace-Klasse.  
  
## <a name="output-methods"></a>Ausgabemethoden  
 Die <xref:System.Diagnostics.Trace>-Klasse und die <xref:System.Diagnostics.Debug>-Klasse stellen die folgenden Ausgabemethoden bereit:  
  
-   Verschiedene `Write`-Methoden, die die Ausgabe von Informationen ermöglichen, ohne dass die Ausführung unterbrochen wird. Diese Methoden ersetzen die `Debug.Print`-Methode, die in früheren Versionen von Visual Basic verwendet wurde.  
  
-   Die <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>-Methode und die <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>-Methode, durch die die Ausführung unterbrochen wird und Informationen ausgegeben werden, wenn eine festgelegte Bedingung nicht erfüllt ist. Standardmäßig werden die Informationen der `Assert`-Methode in einem Dialogfeld angezeigt. Weitere Informationen finden Sie unter [Assertionen in verwaltetem Code](../debugger/assertions-in-managed-code.md).  
  
-   Die <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName>-Methode und die <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName>-Methode, durch die die Ausführung stets unterbrochen wird und Informationen ausgegeben werden. Standardmäßig werden die Informationen der `Fail`-Methoden in einem Dialogfeld angezeigt.  
  
 Neben Programmausgabe der Anwendung die **Ausgabe** Fenster können die Informationen zu angezeigt:  
  
-   Module, die der Debugger geladen oder entladen hat.  
  
-   Ausnahmen, die ausgelöst werden.  
  
-   Prozesse, die beendet werden.  
  
-   Threads, die beendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Ausgabefenster](../ide/reference/output-window.md)   
 [Ablaufverfolgung und Instrumentieren von Anwendungen](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)  
 [C#-, F#- und Visual Basic-Projekttypen](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
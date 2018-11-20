---
title: Senden von Nachrichten an das Ausgabefenster | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/08/2018
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 02bdd2c6d83e13887a8051ab4101627ba14220fa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724484"
---
# <a name="send-messages-to-the-output-window"></a>Senden von Nachrichten an das Fenster "Ausgabe"

Können Sie laufzeitmeldungen zum Schreiben der **Ausgabe** unter Verwendung der <xref:System.Diagnostics.Debug> Klasse oder die <xref:System.Diagnostics.Trace> -Klasse, die Teil von der <xref:System.Diagnostics> -Klassenbibliothek. Verwenden der <xref:System.Diagnostics.Debug> Klasse, wenn Sie nur Ausgabe die *Debuggen* Version des Programms. Verwenden der <xref:System.Diagnostics.Trace> Klasse, wenn die Ausgabe in beiden soll die *Debuggen* und *Version* Versionen.  
  
## <a name="output-methods"></a>Ausgabemethoden  
 Die <xref:System.Diagnostics.Trace>-Klasse und die <xref:System.Diagnostics.Debug>-Klasse stellen die folgenden Ausgabemethoden bereit:  
  
- Verschiedene `Write`-Methoden, die die Ausgabe von Informationen ermöglichen, ohne dass die Ausführung unterbrochen wird. Diese Methoden ersetzen die `Debug.Print`-Methode, die in früheren Versionen von Visual Basic verwendet wurde.  
  
- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> und <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> -Methoden, die Ausführung und die Ausgabe unterbrechen, wenn eine angegebene Bedingung nicht erfüllt. Standardmäßig werden die Informationen der `Assert`-Methode in einem Dialogfeld angezeigt. Weitere Informationen finden Sie unter [Assertionen in verwaltetem Code](../debugger/assertions-in-managed-code.md).  
  
- Die <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> und <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> -Methoden, die Ausführung und die Ausgabe immer dann unterbrochen. Standardmäßig werden die Informationen der `Fail`-Methoden in einem Dialogfeld angezeigt.  
  
Die **Ausgabe** Fenster auch Informationen zum Anzeigen:  
  
- Module, die der Debugger geladen oder entladen hat.  
  
- Ausnahmen, die ausgelöst werden.  
  
- Prozesse, die beendet werden.  
  
- Threads, die beendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Fenster "Ausgabe"](../ide/reference/output-window.md)   
 [Ablaufverfolgung und Instrumentieren von Anwendungen](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)  
 [C#, F#, und Visual Basic-Projekttypen](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Debuggen von verwaltetem code](../debugger/debugging-managed-code.md)

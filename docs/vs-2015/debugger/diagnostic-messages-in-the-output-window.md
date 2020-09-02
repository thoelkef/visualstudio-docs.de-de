---
title: Diagnosemeldungen im Ausgabefenster | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.output
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 60f8da2430e1c84af3c26be31c6de561291c8c6e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695295"
---
# <a name="diagnostic-messages-in-the-output-window"></a>Diagnosemeldungen im Ausgabefenster
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Laufzeitmeldungen können im Ausgabefenster mithilfe der Debug-Klasse oder der Trace-Klasse ausgegeben werden. Beide sind Bestandteil der <xref:System.Diagnostics>-Klassenbibliothek. Falls die Ausgabe lediglich in der Debugversion des Programms erfolgen soll, verwenden Sie die Debug-Klasse. Soll die Ausgabe sowohl in der Debug- als auch in der Releaseversion erfolgen, verwenden Sie die Trace-Klasse.  
  
## <a name="output-methods"></a>Ausgabemethoden  
 Die <xref:System.Diagnostics.Trace>-Klasse und die <xref:System.Diagnostics.Debug>-Klasse stellen die folgenden Ausgabemethoden bereit:  
  
- Verschiedene `Write`-Methoden, die die Ausgabe von Informationen ermöglichen, ohne dass die Ausführung unterbrochen wird. Diese Methoden ersetzen die `Debug.Print`-Methode, die in früheren Versionen von Visual Basic verwendet wurde.  
  
- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> und- <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> Methoden, die die Ausführung unterbrechen und Informationen ausgeben, wenn eine angegebene Bedingung fehlschlägt. Standardmäßig werden die Informationen der `Assert`-Methode in einem Dialogfeld angezeigt. Weitere Informationen finden Sie unter [Assertionen in verwaltetem Code](../debugger/assertions-in-managed-code.md).  
  
- Die <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName>-Methode und die <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName>-Methode, durch die die Ausführung stets unterbrochen wird und Informationen ausgegeben werden. Standardmäßig werden die Informationen der `Fail`-Methoden in einem Dialogfeld angezeigt.  
  
  Zusätzlich zum Programm aus der Anwendung können im **Ausgabe** Fenster folgende Informationen angezeigt werden:  
  
- Module, die der Debugger geladen oder entladen hat.  
  
- Ausnahmen, die ausgelöst werden.  
  
- Prozesse, die beendet werden.  
  
- Threads, die beendet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Debugger-Sicherheit](../debugger/debugger-security.md)   
 [Ausgabefenster](../ide/reference/output-window.md)   
 [Ablaufverfolgung und Instrumentieren von Anwendungen](https://msdn.microsoft.com/library/773b6fc4-9013-4322-b728-5dec7a72e743)   
 [Einführung in Instrumentation und Ablauf Verfolgung](https://msdn.microsoft.com/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)   
 [C#-, F #-und Visual Basic-Projekttypen](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)

---
title: Senden von Nachrichten an das Ausgabefenster | Microsoft-Dokumentation
ms.date: 11/08/2018
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47b563f58d08a732ec224bb8bbf47ad807c4e81d
ms.sourcegitcommit: ce1ab8a25c66a83e60eab80ed8e1596fe66dd85c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2019
ms.locfileid: "68605375"
---
# <a name="send-messages-to-the-output-window"></a>Senden von Meldungen an das Ausgabefenster

Sie können Lauf Zeit Meldungen in das **Ausgabe** Fenster schreiben, indem Sie <xref:System.Diagnostics.Debug> die-Klasse <xref:System.Diagnostics.Trace> oder die- <xref:System.Diagnostics> Klasse verwenden, die Teil der-Klassenbibliothek sind. Verwenden Sie <xref:System.Diagnostics.Debug> die-Klasse, wenn Sie nur die Ausgabe in der *Debugversion* des Programms verwenden möchten. Verwenden Sie <xref:System.Diagnostics.Trace> die-Klasse, wenn Sie sowohl in der *Debug* -als auch in der *Releaseversion* eine Ausgabe

## <a name="output-methods"></a>Ausgabemethoden
 Die <xref:System.Diagnostics.Trace>-Klasse und die <xref:System.Diagnostics.Debug>-Klasse stellen die folgenden Ausgabemethoden bereit:

- Verschiedene `Write`-Methoden, die die Ausgabe von Informationen ermöglichen, ohne dass die Ausführung unterbrochen wird. Diese Methoden ersetzen die `Debug.Print`-Methode, die in früheren Versionen von Visual Basic verwendet wurde.

- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName>und <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> -Methoden, die die Ausführungs-und Ausgabeinformationen unterbrechen, wenn eine angegebene Bedingung fehlschlägt. Standardmäßig werden die Informationen der `Assert`-Methode in einem Dialogfeld angezeigt. Weitere Informationen finden Sie unter [Assertionen in verwaltetem Code](../debugger/assertions-in-managed-code.md).

- Die <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> - <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> Methode und die-Methode, die Ausführungs-und Ausgabeinformationen immer unterbrechen. Standardmäßig werden die Informationen der `Fail`-Methoden in einem Dialogfeld angezeigt.

Im Fenster **Ausgabe** können auch Informationen zu folgenden Informationen angezeigt werden:

- Module, die der Debugger geladen oder entladen hat.

- Ausnahmen, die ausgelöst werden.

- Prozesse, die beendet werden.

- Threads, die beendet werden.

## <a name="see-also"></a>Siehe auch
- [Debuggersicherheit](../debugger/debugger-security.md)
- [Ausgabefenster](../ide/reference/output-window.md)
- [Trace und Instrumentieren von Anwendungen](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)
- [C#-, F#- und Visual Basic-Projekttypen](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)

---
title: Dialog Feld "Microsoft Visual Studio Debugger (Ausnahme ausgelöst)" | Microsoft-Dokumentation
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.exceptions.thrown
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8376d0cd82e309c2c8db94e38b8c6a2083bd429a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731208"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Microsoft Visual Studio Debugger (Ausnahmeverweis) (Dialogfeld)
Im Programm ist eine Ausnahme aufgetreten. In diesem Dialogfeld wird die Art der ausgelösten Ausnahme angezeigt. Die Ausnahme muss durch den Code behandelt werden. Folgende Optionen stehen für das Behandeln der Ausnahme zur Verfügung:

 **Abbrechen** Ermöglicht die Ausführung in den Debugger. Der Ausnahmehandler wird vor der Unterbrechung nicht aufgerufen. Wenn Sie ab der Unterbrechung fortsetzen, wird der Ausnahmehandler aufgerufen.

 **Fortfahren** Ermöglicht, dass die Ausführung fortgesetzt wird, sodass der Ausnahmehandler die Ausnahme behandeln kann. Diese Option ist für bestimmte Ausnahmetypen nicht verfügbar. Mit **Weiter** kann die Anwendung fortgesetzt werden. In einer systemeigenen Anwendung wird die Ausnahme bei dieser Option erneut ausgelöst. In einer verwalteten Anwendung wird dadurch entweder das Programm beendet oder die Ausnahme wird von einer Hostanwendung behandelt.

> [!NOTE]
> In verwaltetem Code können Sie die Ausführung nach einem Ausnahmefehler nicht fortsetzen. Wenn Sie nach einem Ausnahmefehler in verwaltetem Code auf **Weiter** klicken, wird das Debuggen beendet.

 **Ignorieren** Ermöglicht das Fortsetzen der Ausführung ohne Aufrufen des Ausnahme Handlers. Dies kann sich weiter auswirken und beispielsweise zu weiteren Ausnahmen und Fehlern führen. Diese Option ist für bestimmte Ausnahmetypen nicht verfügbar.

## <a name="see-also"></a>Siehe auch
- [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md)
- [Bewährte Methoden für Ausnahmen](/dotnet/standard/exceptions/best-practices-for-exceptions)
- [Ausnahmebehandlung](/cpp/extensions/exception-handling-cpp-component-extensions)
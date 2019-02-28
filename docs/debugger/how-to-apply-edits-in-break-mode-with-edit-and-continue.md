---
title: Anwenden von Bearbeitungen im Unterbrechungsmodus mit bearbeiten und fortfahren | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d885cdc3d4321737541cd178d546c37e71ce42b7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56684181"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue-visual-basic"></a>Vorgehensweise: Anwenden von Bearbeitungen im Unterbrechungsmodus mit bearbeiten und Fortfahren (Visual Basic)
Sie können mit Bearbeiten und Fortfahren den Code im Unterbrechungsmodus bearbeiten und anschließend fortfahren, ohne die Codeausführung anzuhalten und erneut starten zu müssen.

Einschränkungen zur Verwendung von während des Debuggens bearbeiten und fortfahren, finden Sie unter [Supported Code Changes (C# und Visual Basic)](../debugger/supported-code-changes-csharp.md).

### <a name="to-edit-code-in-break-mode"></a>So bearbeiten Sie Code im Unterbrechungsmodus

1.  Wechseln Sie in den Unterbrechungsmodus, indem Sie folgendermaßen vorgehen:

    -   Legen Sie einen Breakpoint im Code fest, wählen Sie im Menü **Debuggen** den Befehl **Debuggen starten** aus, und warten Sie, bis die Anwendung den Breakpoint erreicht.

         - oder -

    -   Beginnen Sie mit dem Debuggen, und wählen Sie anschließend im Menü **Debuggen** den Befehl **Alle unterbrechen** aus.

         - oder -

    -   Wenn eine Ausnahme auftritt, wählen Sie **Bearbeiten aktivieren** auf die **Ausnahmen-Assistent**.

2.  Stellen Sie alle gewünschten und unterstützte codeänderungen.

     Weitere Informationen finden Sie unter [Supported Code Changes (C# und Visual Basic)](../debugger/supported-code-changes-csharp.md).

    > [!NOTE]
    >  Bei dem Versuch, mit Bearbeiten und Fortfahren eine nicht zulässige Änderung vorzunehmen, wird die bearbeitete Stelle violett wellenförmig unterstrichen, und in der Aufgabeliste wird eine Aufgabe angezeigt. Sie können mit der Codeausführung erst fortfahren, nachdem Sie die nicht zulässige Codeänderung rückgängig gemacht haben.

3.  Klicken Sie im Menü **Debuggen** auf **Weiter**, um mit der Ausführung fortzufahren.

     Der Code wird nun einschließlich der vorgenommenen Änderungen ausgeführt, die jetzt Teil des Projekts sind.

## <a name="see-also"></a>Siehe auch
- [Unterstützte Codeänderungen (C# und Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Bearbeiten und Fortfahren (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)

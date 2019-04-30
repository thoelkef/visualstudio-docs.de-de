---
title: 'Vorgehensweise: Debuggen von ActiveX-Steuerelementen | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vc.controls.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c76167468d9eb6fbe93c3bef0c4ae8c15634fc5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894429"
---
# <a name="how-to-debug-an-activex-control"></a>Vorgehensweise: Debuggen von ActiveX-Steuerelementen

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der Hilfe beschriebenen. Klicken Sie im Menü Extras auf Einstellungen importieren und exportieren, um die Einstellungen zu ändern. Weitere Informationen finden Sie unter [Reset settings (Zurücksetzen der Einstellungen)](../ide/environment-settings.md#reset-settings).

Um das ActiveX-Steuerelement zu debuggen, müssen Sie einen Container (ausführbare Datei) angeben, in dem das Steuerelement ausgeführt werden kann.

## <a name="to-specify-a-container-for-the-debug-session"></a>So legen Sie einen Container für die Debugsitzung fest

1. Wählen Sie im Projektmappen-Explorer das Projekt aus.

2. Von der **Ansicht** Menü wählen **Eigenschaftenseiten**.

3. Öffnen Sie im Dialogfeld **Projekteigenschaftenseiten** den Ordner **Konfigurationseigenschaften**, und wählen Sie **Debuggen** aus.

4. Suchen Sie in der Kategorie **Debuggen** die Eigenschaft **Befehl**.

5. Geben Sie den Pfadnamen für den Container an. Beispielsweise C:\Programme\Internet Explorer\IEXPLORE.EXE.

6. Wenn Sie Internet Explorer als Container festlegen und Active Desktop verwenden, geben Sie `/new` in das Feld **Befehlsargumente** ein.

7. Klicken Sie auf **OK**.

     Wenn Sie keinen Container im Dialogfeld **Projekteigenschaftenseiten** festlegen, können Sie dies zu Beginn des Debuggens nachholen. Falls Sie zum Starten des Debugvorgangs einen Ausführungsbefehl wählen, wird das Dialogfeld [Executable for Debugging Session](../debugger/executable-for-debugging-session-dialog-box.md) (Ausführbare Datei für die Debugsitzung) angezeigt. Geben Sie den Pfadnamen des Containers im Dialogfeld an.

## <a name="see-also"></a>Siehe auch

- [ActiveX-Steuerelemente](/cpp/mfc/activex-controls)
- [Testen der Eigenschaften und Ereignisse mit Test Container](/cpp/mfc/testing-properties-and-events-with-test-container)
- [Debuggen von COM und ActiveX](../debugger/com-and-activex-debugging.md)
- [Debuggen in Visual Studio](../debugger/index.md)
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
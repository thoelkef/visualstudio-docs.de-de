---
title: 'Vorgehensweise: Starten von Spy++ | Microsoft-Dokumentation'
ms.date: 12/16/2018
ms.topic: how-to
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b659350adc39fd1088964976b8bcdef629bad44b
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349003"
---
# <a name="how-to-start-spy"></a>Vorgehensweise: Starten von Spy++

Sie können Spy++ entweder über Visual Studio oder eine Eingabeaufforderung starten.

 Wenn beim Starten von Spy++ eine Meldung angezeigt wird, um Berechtigungen zum Vornehmen von Änderungen am Computer anzufordern, klicken Sie auf **Ja**.

> [!NOTE]
> Sie können nur eine Instanz von Spy++ ausführen. Wenn Sie versuchen, eine zweite Instanz zu starten, bewirkt dies lediglich, dass die aktuell ausgeführte Instanz den Fokus erhält.

## <a name="prerequisites"></a>Voraussetzungen

Die folgenden Komponenten sind für Spy++ erforderlich. Sie können diese Komponenten im Visual Studio-Installer auswählen, indem Sie die Registerkarte **Einzelne Komponenten** und dann die folgenden Komponenten auswählen.

* Wählen Sie unter „Debuggen und Testen“ die Option **C++-Profilerstellungstools** aus.
* Wählen Sie unter „Entwicklungsaktivitäten“ die Option **C++-Kernfeatures** aus.

Wenn Sie Änderungen vorgenommen haben, befolgen Sie die Anweisungen zum Installieren dieser Komponenten.

## <a name="start-spy-from-visual-studio"></a>Starten von Spy++ über Visual Studio

Klicken Sie im Menü **Extras** auf **Spy++** .

Da Spy++ unabhängig ausgeführt wird, können Sie Visual Studio schließen, nachdem Sie Spy++ gestartet haben.

> [!NOTE]
> Das Protokollieren von Meldungen mit Spy++ kann dazu führen, dass das Betriebssystem langsamer ausgeführt wird.

## <a name="start-spy-at-a-command-prompt"></a>Starten von Spy++ über eine Eingabeaufforderung

1. Ändern Sie das Verzeichnis in einem Eingabeaufforderungsfenster in den Ordner, der die ausführbare Datei „spyxx.exe“ enthält. Normalerweise lautet der Pfad zu diesem Ordner ..\\*Visual Studio installation folder*\Common7\Tools\\.

2. Geben Sie **spyxx.exe** ein.

## <a name="see-also"></a>Siehe auch
- [Verwenden von Spy++](../debugger/using-spy-increment.md)
- [Spy++-Ansichten](../debugger/spy-increment-views.md)
- [Spy++-Referenz](../debugger/spy-increment-reference.md)

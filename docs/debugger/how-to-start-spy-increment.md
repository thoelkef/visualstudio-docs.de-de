---
title: 'Gewusst wie: Starten von Spy + + | Microsoft-Dokumentation'
ms.date: 12/16/2018
ms.topic: conceptual
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70874d70dd5f845e7b627f2aeb7ae51bafe45995
ms.sourcegitcommit: 7b07e7b5e06e2e13f622445c568b78a284e1a40d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2020
ms.locfileid: "76542619"
---
# <a name="how-to-start-spy"></a>Gewusst wie: Starten von Spy++

Sie können Spy + + entweder über Visual Studio oder an einer Eingabeaufforderung starten.

 Wenn Sie Spy + + starten und eine Meldung angezeigt wird, um die Berechtigung zum vornehmen von Änderungen am Computer zu stellen, wählen Sie **Ja**aus.

> [!NOTE]
> Sie können nur eine Instanz von Spy + + ausführen. Wenn Sie versuchen, eine zweite Instanz zu starten, bewirkt dies lediglich, dass die aktuell laufende Instanz den Fokus erhält.

## <a name="prerequisites"></a>Erforderliche Komponenten

Spy + + erfordert die folgenden Komponenten. Sie können diese Komponenten aus dem Visual Studio-Installer auswählen, indem Sie die Registerkarte **einzelne Komponenten** auswählen und dann die folgenden Komponenten auswählen.

* Wählen Sie  **C++ unter Debuggen und testen Profil Erstellungs Tools**
* Wählen Sie  **C++ unter Entwicklungsaktivitäten die Option Kern Features aus.**

Wenn Sie Änderungen vorgenommen haben, befolgen Sie die Anweisungen, um diese Komponenten zu installieren.

## <a name="start-spy-from-visual-studio"></a>Spy + + aus Visual Studio starten

Wählen Sie **im Menü Extras** die Option **Spy + +** aus.

Da Spy + + unabhängig ausgeführt wird, können Sie nach dem Starten von Visual Studio schließen.

> [!NOTE]
> Wenn Sie Nachrichten mit Spy + + protokollieren, kann dies dazu führen, dass das Betriebssystem langsamer ausgeführt wird.

## <a name="start-spy-at-a-command-prompt"></a>Spy + + an einer Eingabeaufforderung starten

1. Wechseln Sie in einem Eingabe Aufforderungs Fenster in den Ordner, der "spyxx. exe" enthält. In der Regel lautet der Pfad zu diesem Ordner.\\*Visual Studio-Installationsordner*\Common7\Tools\\.

2. Geben Sie **spyxx.exe** ein.

## <a name="see-also"></a>Siehe auch
- [Verwenden von Spy++](../debugger/using-spy-increment.md)
- [Spy++-Ansichten](../debugger/spy-increment-views.md)
- [Spy++-Referenz](../debugger/spy-increment-reference.md)

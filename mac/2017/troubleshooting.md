---
title: Problembehandlung
description: Häufige Probleme und deren mögliche Lösungen für Visual Studio für Mac-Benutzer
ms.topic: troubleshooting
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: CE860D79-E29E-4B93-B094-BE74B35FC1C2
ms.openlocfilehash: 3a5ea59e6f98891cd113ccad9a74038ca52cccf8
ms.sourcegitcommit: da73f7a0cf1795d5d400c0897ae3326191435dd0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2019
ms.locfileid: "58568192"
---
# <a name="troubleshooting"></a>Problembehandlung

## <a name="viewing-logs-in-visual-studio-for-mac"></a>Anzeigen von Protokollen in Visual Studio für Mac

Protokolle können Sie über das Menüelement **Hilfe > Protokollverzeichnis öffnen** wie unten gezeigt gesucht werden:

![Menüelement „Protokollverzeichnis öffnen“](media/troubleshooting-image1.png)

## <a name="viewing-exceptions"></a>Anzeigen von Ausnahmen

Wenn eine Ausnahme abgefangen wird, wird eine Ausnahmenblase angezeigt. Um mehr Details anzuzeigen, wählen Sie **Details anzeigen** aus:

![Weitere Details zu einer Ausnahme](media/troubleshooting-image2.png)

Daraufhin wird das Dialogfeld **Details anzeigen** mit weiteren Informationen hinsichtlich der Ausnahme angezeigt:

![Dialogfeld „Details anzeigen“](media/troubleshooting-image3.png)

Wichtige Abschnitte des Dialogfelds sind in der oberen Abbildung nummeriert, und werden nachfolgend detailliert beschrieben:

1. Der Ausnahmetyp, der den vollständigen Namen des Ausnahmetyps anzeigt, der beobachtet wird
2. Die Ausnahmemeldung, die den Wert der „message“-Eigenschaft des Ausnahmeobjekts enthält
3. Der innere Ausnahmetyp, der den vollständigen Namen des Ausnahmetyps für die aktuell ausgewählte Ausnahme in der Strukturansicht der inneren Ausnahme anzeigt
4. Die Meldung der inneren Ausnahme, zeigt den Wert der „message“-Eigenschaft für die ausgewählte Ausnahme in der Strukturansicht der inneren Ausnahme an
5. StackTrace-Ansicht. Diese kann über den Abwärtspfeil geschlossen werden und enthält Stapelrahmeneinträge.
6. Beispiel für nicht-benutzerseitige Codeeinträge
7. Beispiel für benutzerseitige Codeeinträge
8. Ansicht „Eigenschaften“, die alle Eigenschaften und Felder der Ausnahme darstellt Sie kann über einen Abwärtspfeil geschlossen werden.
9. Strukturansicht der internen Ausnahme Wählen Sie in dieser Ansicht über die Pfeiltasten nach oben/unten, mit der Maus oder mit dem Trackpad innere Ausnahmen aus.
10. Standardmäßig entspricht diese Option der Option **Nur Projektcode debuggen** in den Debuggereinstellungen. Durch Aktivieren dieses Kontrollkästchens kann der ganze nichtbenutzerseitige Code in eine Zeile im Stacktrace reduziert werden.
11. Eine Kopierschaltfläche, damit die `exception.ToString()`-Ausgabe im die Zwischenablage kopiert wird.

Beachten Sie, dass einige dieser Abschnitte nur sichtbar sind, wenn die Ausnahme eine innere Ausnahme hat.

## <a name="see-also"></a>Siehe auch

- [Ressourcen für die Problembehandlung bei IDE-Fehlern (Visual Studio unter Windows)](/visualstudio/ide/reference/resources-for-troubleshooting-integrated-development-environment-errors)
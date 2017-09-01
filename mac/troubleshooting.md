---
title: Problembehandlung
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: CE860D79-E29E-4B93-B094-BE74B35FC1C2
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: a820423704b6f656b55b7e33f15d1c7880d2e27d
ms.contentlocale: de-de
ms.lasthandoff: 08/11/2017

---

# <a name="troubleshooting"></a>Problembehandlung

## <a name="viewing-logs-in-visual-studio-for-mac"></a>Anzeigen von Protokollen in Visual Studio für Mac
 
Protokolle können Sie über das Menüelement **Hilfe > Protokollverzeichnis öffnen** wie unten gezeigt gesucht werden:

![Menüelement „Protokollverzeichnis öffnen“](media/troubleshooting-image1.png)

## <a name="viewing-exceptions"></a>Anzeigen von Ausnahmen

Wenn eine Ausnahme abgefangen wurde, wird eine Ausnahmenblase angezeigt. Um mehr Details anzuzeigen, wählen Sie **Details anzeigen** aus:

![Weitere Details zu einer Ausnahme](media/troubleshooting-image2.png)

Daraufhin wird das Dialogfeld **Details anzeigen** mit weiteren Informationen hinsichtlich der Ausnahme angezeigt:

![](media/troubleshooting-image3.png)

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

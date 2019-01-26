---
title: Problembehandlung bei Erweiterungen für Abhängigkeitsdiagramme
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- dependency diagrams, extension errors
- dependency diagrams, troubleshooting extensions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 01b8486c9ca0ffc62d338b9d9a46e50248182581
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55028594"
---
# <a name="troubleshoot-extensions-for-dependency-diagrams"></a>Problembehandlung bei Erweiterungen für Abhängigkeitsdiagramme

In diesem Thema werden einige Probleme behandelt, die möglicherweise beim Erstellen von Ebenenmodellerweiterungen auftreten.

## <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-dependency-diagrams-in-the-experimental-instance-of-visual-studio"></a>Wenn ich F5 zum Debuggen meiner Erweiterung drücke, werden meine Befehle, Gestenhandler, validierungserweiterungen oder benutzerdefinierten Eigenschaften nicht auf von Abhängigkeitsdiagrammen in der experimentellen Instanz von Visual Studio angezeigt

1. Öffnen Sie die Erweiterungsprojektmappe in der experimentellen Instanz von Visual Studio, und klicken Sie auf die **erstellen** Menü klicken Sie auf **Projektmappe neu erstellen**.

2. Drücken Sie **F5** oder **STRG + F5** die experimentelle Instanz von Visual Studio zu starten. Öffnen Sie ein Abhängigkeitsdiagramm, und Testen Sie die Erweiterung.

   Fahren Sie ggf. mit der nächsten Prozedur fort.

## <a name="an-old-version-of-my-extension-runs"></a>Eine alte Version meiner Erweiterung wird ausgeführt.

1. Stellen Sie sicher, dass keine experimentelle Instanz von Visual Studio ausgeführt wird.

2. Löschen Sie den folgenden Ordner: %LocalAppData%\Microsoft\VisualStudio\\[Version] \ComponentModelCache

   > [!NOTE]
   > %LocalAppData% ist in der Regel *DriveName*: \Users\\*Benutzername*\AppData\Local.

   Fahren Sie ggf. mit der nächsten Prozedur fort.

## <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Eine alte Version der Validierungsergebnisse wird angezeigt, oder die Validierungsmethode wird nicht aufgerufen.

1.  In der experimentellen Instanz von Visual Studio auf die **erstellen** Menü klicken Sie auf **Projektmappe bereinigen**. Damit werden die zwischengespeicherten Ergebnisse der vorherigen Validierungsanalyse gelöscht.

2.  Stellen Sie sicher, dass die Ebenen im Modell Codeelementen zugeordnet sind, und dass es mindestens einen Abhängigkeitslink im Modell gibt. Die Validierung wird nicht aufgerufen, wenn es nichts zu überprüfen gibt.

3.  Reguläre Haltepunkte funktionieren möglicherweise in einer Validierungsmethode nicht, da diese in einem separaten Prozess ausgeführt wird. Sie müssen einen Aufruf für `System.Diagnostics.Debugger.Launch()` einfügen, wenn Sie die Methode schrittweise durchlaufen möchten.

4.  In **"Source.Extension.vsixmanifest"** im Ebenenvalidierungsprojekt, stellen Sie sicher, dass Sie, sowohl hinzugefügt haben eine **MEF-Komponente** Element und ein **Benutzerdefinierter Erweiterungstyp** Element **Content**.

## <a name="see-also"></a>Siehe auch

- [Erweitern von Abhängigkeitsdiagrammen](../modeling/extend-layer-diagrams.md)

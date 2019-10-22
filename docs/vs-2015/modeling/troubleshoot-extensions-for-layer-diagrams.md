---
title: Problembehandlung bei Erweiterungen für ebenendiagramme | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: troubleshooting
helpviewer_keywords:
- layer diagrams, extension errors
- layer diagrams, troubleshooting extensions
ms.assetid: 1fda4f8a-38b8-482b-87b8-eade1a4e5662
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dd4560673259373b68b370e73a43de424fb7bdb7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658474"
---
# <a name="troubleshoot-extensions-for-layer-diagrams"></a>Problembehandlung bei Erweiterungen für Ebenendiagramme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema werden einige Probleme behandelt, die möglicherweise beim Erstellen von Ebenenmodellerweiterungen auftreten.

#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-layer-diagrams-in-the-experimental-instance-of-includevsprvsincludesvsprvs-mdmd"></a>Wenn ich F5 zum Debuggen meiner Erweiterung drücke, werden meine Befehle, Gestenhandler, Validierungserweiterungen oder benutzerdefinierten Eigenschaften nicht in Ebenendiagrammen der experimentellen Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] angezeigt

1. Öffnen Sie die Erweiterungsprojekt Mappe in der experimentellen Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], und klicken Sie im Menü **Erstellen** auf Projekt Mappe **neu erstellen**.

2. Drücken Sie **F5** oder **STRG + F5** , um die experimentelle Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zu starten. Öffnen Sie ein Ebenendiagramm, und testen Sie die Erweiterung.

   Fahren Sie ggf. mit der nächsten Prozedur fort.

#### <a name="an-old-version-of-my-extension-runs"></a>Eine alte Version meiner Erweiterung wird ausgeführt.

1. Stellen Sie sicher, dass keine experimentelle Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ausgeführt wird.

2. Löschen Sie den folgenden Ordner:%localappdata%\microsoft\visualstudio \\ [Version] \componentmodelcache

   > [!NOTE]
   > % LocalAppData% ist in der Regel *driveName*: \Users \\*username*\AppData\Local.

   Fahren Sie ggf. mit der nächsten Prozedur fort.

#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Eine alte Version der Validierungsergebnisse wird angezeigt, oder die Validierungsmethode wird nicht aufgerufen.

1. Klicken Sie in der experimentellen Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] im Menü **Build** auf Projekt Mappe **Bereinigen**. Damit werden die zwischengespeicherten Ergebnisse der vorherigen Validierungsanalyse gelöscht.

2. Stellen Sie sicher, dass die Ebenen im Modell Codeelementen zugeordnet sind, und dass es mindestens einen Abhängigkeitslink im Modell gibt. Die Validierung wird nicht aufgerufen, wenn es nichts zu überprüfen gibt.

3. Reguläre Haltepunkte funktionieren möglicherweise in einer Validierungsmethode nicht, da diese in einem separaten Prozess ausgeführt wird. Sie müssen einen Aufruf für `System.Diagnostics.Debugger.Launch()` einfügen, wenn Sie die Methode schrittweise durchlaufen möchten.

4. Stellen Sie in der Datei **Source. Extension. vsixmanifest** im ebenenvalidierungsprojekt sicher, dass Sie unter **Inhalt**sowohl ein **MEF-Komponenten** Element als auch ein **benutzerdefiniertes Erweiterungs** Element hinzugefügt haben.

## <a name="see-also"></a>Siehe auch
 [Erweitern von Ebenendiagrammen](../modeling/extend-layer-diagrams.md)

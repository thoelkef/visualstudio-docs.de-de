---
title: Problembehandlung bei Erweiterungen für Ebenendiagramme | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: troubleshooting
helpviewer_keywords:
- layer diagrams, extension errors
- layer diagrams, troubleshooting extensions
ms.assetid: 1fda4f8a-38b8-482b-87b8-eade1a4e5662
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ba45ba733f5447523b6793d4f5e2946c3507c82e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60098688"
---
# <a name="troubleshoot-extensions-for-layer-diagrams"></a>Problembehandlung bei Erweiterungen für Ebenendiagramme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema werden einige Probleme behandelt, die möglicherweise beim Erstellen von Ebenenmodellerweiterungen auftreten.  
  
#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-layer-diagrams-in-the-experimental-instance-of-includevsprvsincludesvsprvs-mdmd"></a>Wenn ich F5 zum Debuggen meiner Erweiterung drücke, werden meine Befehle, Gestenhandler, Validierungserweiterungen oder benutzerdefinierten Eigenschaften nicht in Ebenendiagrammen der experimentellen Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] angezeigt  
  
1. Öffnen Sie die Erweiterungsprojektmappe in der experimentellen Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], und klicken Sie auf die **erstellen** Menü klicken Sie auf **Projektmappe neu erstellen**.  
  
2. Drücken Sie **F5** oder **STRG + F5** , starten Sie die experimentelle Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Öffnen Sie ein Ebenendiagramm, und testen Sie die Erweiterung.  
  
   Fahren Sie ggf. mit der nächsten Prozedur fort.  
  
#### <a name="an-old-version-of-my-extension-runs"></a>Eine alte Version meiner Erweiterung wird ausgeführt.  
  
1. Stellen Sie sicher, dass keine experimentelle Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ausgeführt wird.  
  
2. Löschen Sie den folgenden Ordner: %LocalAppData%\Microsoft\VisualStudio\\[Version] \ComponentModelCache  
  
   > [!NOTE]
   >  %LocalAppData% ist in der Regel *DriveName*: \Users\\*Benutzername*\AppData\Local.  
  
   Fahren Sie ggf. mit der nächsten Prozedur fort.  
  
#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Eine alte Version der Validierungsergebnisse wird angezeigt, oder die Validierungsmethode wird nicht aufgerufen.  
  
1. In der experimentellen Instanz von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]auf die **erstellen** Menü klicken Sie auf **Projektmappe bereinigen**. Damit werden die zwischengespeicherten Ergebnisse der vorherigen Validierungsanalyse gelöscht.  
  
2. Stellen Sie sicher, dass die Ebenen im Modell Codeelementen zugeordnet sind, und dass es mindestens einen Abhängigkeitslink im Modell gibt. Die Validierung wird nicht aufgerufen, wenn es nichts zu überprüfen gibt.  
  
3. Reguläre Haltepunkte funktionieren möglicherweise in einer Validierungsmethode nicht, da diese in einem separaten Prozess ausgeführt wird. Sie müssen einen Aufruf für `System.Diagnostics.Debugger.Launch()` einfügen, wenn Sie die Methode schrittweise durchlaufen möchten.  
  
4. In **"Source.Extension.vsixmanifest"** im Ebenenvalidierungsprojekt, stellen Sie sicher, dass Sie, sowohl hinzugefügt haben eine **MEF-Komponente** Element und ein **Benutzerdefinierter Erweiterungstyp** Element **Content**.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Ebenendiagrammen](../modeling/extend-layer-diagrams.md)

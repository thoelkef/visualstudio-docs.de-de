---
title: "Problembehandlung bei Erweiterungen für Abhängigkeit Diagramme | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, extension errors
- dependency diagrams, troubleshooting extensions
ms.assetid: 1fda4f8a-38b8-482b-87b8-eade1a4e5662
caps.latest.revision: "25"
author: alexhomer1
ms.author: ahomer
manager: douge
ms.openlocfilehash: fae53e45b231292df8b7a6ae8bf4f2babc5d9e88
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="troubleshoot-extensions-for-dependency-diagrams"></a>Problembehandlung bei Erweiterungen für Abhängigkeit-Diagramme
In diesem Thema werden einige Probleme behandelt, die möglicherweise beim Erstellen von Ebenenmodellerweiterungen auftreten.  
  
#### <a name="when-i-press-f5-to-debug-my-extension-my-commands-gesture-handlers-validation-extensions-or-custom-properties-do-not-appear-on-dependency-diagrams-in-the-experimental-instance-of-includevsprvscode-qualityincludesvsprvsmdmd"></a>Wenn ich F5 zum Debuggen meiner Erweiterung drücke, werden meine Befehle, Gestenhandler, validierungserweiterungen oder benutzerdefinierten Eigenschaften nicht in Abhängigkeit von Diagrammen in der experimentellen Instanz von angezeigt[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
  
1.  Öffnen Sie die Erweiterungsprojektmappe in der experimentellen Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], und klicken Sie auf die **erstellen** Menü klicken Sie auf **Projektmappe neu erstellen**.  
  
2.  Drücken Sie **F5** oder **STRG + F5** , starten Sie die experimentelle Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Öffnen Sie ein Diagramm der Abhängigkeit, und Testen Sie die Erweiterung.  
  
 Fahren Sie ggf. mit der nächsten Prozedur fort.  
  
#### <a name="an-old-version-of-my-extension-runs"></a>Eine alte Version meiner Erweiterung wird ausgeführt.  
  
1.  Stellen Sie sicher, dass keine experimentelle Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausgeführt wird.  
  
2.  Löschen Sie den folgenden Ordner: %LocalAppData%\Microsoft\VisualStudio\\\ComponentModelCache [Version]  
  
    > [!NOTE]
    >  %LocalAppData% ist in der Regel *DriveName*: \Users\\*Benutzername*\AppData\Local.  
  
 Fahren Sie ggf. mit der nächsten Prozedur fort.  
  
#### <a name="an-old-version-of-my-validation-results-appears-or-my-validation-method-is-not-called"></a>Eine alte Version der Validierungsergebnisse wird angezeigt, oder die Validierungsmethode wird nicht aufgerufen.  
  
1.  In der experimentellen Instanz von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]auf die **erstellen** Menü klicken Sie auf **Projektmappe bereinigen**. Damit werden die zwischengespeicherten Ergebnisse der vorherigen Validierungsanalyse gelöscht.  
  
2.  Stellen Sie sicher, dass die Ebenen im Modell Codeelementen zugeordnet sind, und dass es mindestens einen Abhängigkeitslink im Modell gibt. Die Validierung wird nicht aufgerufen, wenn es nichts zu überprüfen gibt.  
  
3.  Reguläre Haltepunkte funktionieren möglicherweise in einer Validierungsmethode nicht, da diese in einem separaten Prozess ausgeführt wird. Sie müssen einen Aufruf für `System.Diagnostics.Debugger.Launch()` einfügen, wenn Sie die Methode schrittweise durchlaufen möchten.  
  
4.  In **"Source.Extension.vsixmanifest"** im Ebenenvalidierungsprojekt, stellen Sie sicher, dass Sie beide hinzugefügt haben eine **MEF-Komponente** Element und ein **Custom Extension Type** Element unter **Content**.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Abhängigkeitsdiagrammen](../modeling/extend-layer-diagrams.md)

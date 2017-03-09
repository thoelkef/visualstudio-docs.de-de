---
title: "Die folgende Projektkonfiguration(en) ist/sind nicht mehr aktuell: &lt;Konfiguration&gt;. M&#246;chten Sie sie erstellen? | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.Message.BuildOutOfDateProjects"
ms.assetid: d0711f3b-3a2e-4247-afad-9e6468f9df96
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Die folgende Projektkonfiguration(en) ist/sind nicht mehr aktuell: &lt;Konfiguration&gt;. M&#246;chten Sie sie erstellen?
Sie bearbeiten gerade ein Visual Studio\-Projekt oder haben im Projektmappen\-Explorer ein Projekt ausgewählt und den Befehl „Starten“ \(F5\) oder „Starten ohne Debugging“ \(STRG\+F5\) für das Projekt ausgewählt. Für ein oder mehrere Projekte ist ein Debugging ohne Neuerstellung zulässig, auch wenn das Projekt nach dem letzten Build geändert wurde.  
  
 Daher fragt die integrierte Entwicklungsumgebung \(IDE\) nach, ob Projekte, für ein Debugging ohne Neuerstellung zulässig ist, neu erstellt werden sollen.  
  
### So reagieren Sie auf diese Meldung  
  
-   Klicken Sie auf eine der Schaltflächen im unteren Bereich der Meldung. Folgende Optionen stehen zur Verfügung:  
  
|Begriff|Definition|  
|-------------|----------------|  
|**Ja**|Nicht mehr aktuelle Projekte werden neu erstellt. Dies bedeutet Folgendes:<br /><br /> -   Wenn das Projekt noch nicht erstellt wurde, geschieht dies jetzt.<br />-   Wenn das Projekt nach dem letzten Build geändert wurde, wird es neu erstellt.<br />-   Es wird ein Debugging für das Projekt ausgeführt, oder das Projekt wird ohne Debugging gestartet.|  
|**Nein**|Es werden nur die nicht mehr aktuellen Projekte neu erstellt, die vor dem Debuggen neu erstellt werden müssen. Dies bedeutet Folgendes:<br /><br /> -   Wenn für das Projekt ein Debugging ohne Neuerstellung zulässig ist \(z. B. bei Visual C\+\+\-MFC\-Anwendungsprojekten\), wird das Projekt nicht neu erstellt.<br />-   Wenn das Projekt vor dem Debuggen neu erstellt werden muss \(z. B. bei Visual Basic\-Projekten\), wird das Projekt neu erstellt.<br />-   Es wird ein Debugging für das Projekt ausgeführt, oder das Projekt wird ohne Debugging gestartet.|  
|**Abbrechen**|Der aktuelle Vorgang wird abgebrochen. Es wird kein Projekt erstellt oder gestartet oder ein Debugging für ein Projekt ausgeführt.|  
  
## Siehe auch  
 [Dialogfeld „Konfigurations\-Manager“](http://msdn.microsoft.com/de-de/fa182dca-282e-4ae5-bf37-e155344ca18b)   
 [Gewusst wie: Erstellen der Buildkonfigurationen von Projektmappen und Projekten](../Topic/How%20to:%20Create%20Solution%20and%20Project%20Build%20Configurations.md)   
 [Gewusst wie: Erstellen und Entfernen von Projektabhängigkeiten](../ide/how-to-create-and-remove-project-dependencies.md)   
 [Project Dependencies Dialog Box](http://msdn.microsoft.com/de-de/d66e48c3-3722-40dd-99b4-53d93cac128e)   
 [Project Dependencies, Common Properties, Solution Property Pages Dialog Box](http://msdn.microsoft.com/de-de/2ba638fc-719c-4a79-b166-3455a4374e31)   
 [Anwendungen in Visual Studio erstellen](../ide/compiling-and-building-in-visual-studio.md)   
 [Grundlagen der Buildkonfiguration](../ide/understanding-build-configurations.md)   
 [NIB:Projekte als Container](http://msdn.microsoft.com/de-de/87d40f63-f487-4767-8963-64beec27ba1b)   
 [NIB: Elementverwaltung in Projekten](http://msdn.microsoft.com/de-de/762e606b-7f44-4b66-97a1-e30a703654a0)
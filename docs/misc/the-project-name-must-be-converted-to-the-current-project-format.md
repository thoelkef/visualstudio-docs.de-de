---
title: "Das Projekt &lt;Name&gt; muss in das aktuelle Projektformat konvertiert werden. | Microsoft Docs"
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
  - "VC.Project.Conversion7"
  - "vs.UpgradeWarningDlg"
ms.assetid: e27d58e5-c270-468b-bb98-3163d40900bc
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Das Projekt &lt;Name&gt; muss in das aktuelle Projektformat konvertiert werden.
Sie haben ein Projekt geöffnet, das in einer früheren Version von Visual Studio erstellt wurde. Die Projektdateien müssen in die aktuellen Formate konvertiert werden, bevor ein Projekt in der auf dem Computer installierten Version von Visual Studio geöffnet und bearbeitet werden kann. Sie können auswählen, ob dieses Projekt jetzt konvertiert werden soll. Die Konvertierung des Formats kann nicht rückgängig gemacht werden.  
  
> [!CAUTION]
>  Wenn das Projekt in einem Quellcodeverwaltungssystem gespeichert ist und das konvertierte Projekt wieder eingecheckt werden soll, sollten Sie zuerst ermitteln, ob es auch von anderen Projektmappen genutzt wird. Checken Sie kein konvertiertes Projekt ein, das in anderen, nicht konvertierten Projektmappen in Verwendung ist. Dadurch werden die Abhängigkeiten in den betreffenden Projektmappen aufgehoben, und die Projektmappen können dann nicht mehr geöffnet oder ordnungsgemäß erstellt werden.  
  
 Sie sollten vor dem Konvertieren der Projektdateien Sicherungskopien erstellen.  
  
> [!NOTE]
>  Bei der Konvertierung bestimmter Projekttypen, z. B. Visual C\+\+\-Projekten, werden die vorherigen Projektdateien mit der Dateinamenerweiterung „.old“ gekennzeichnet und im Projektverzeichnis gespeichert.  
  
 Schreibgeschützte Projekte können nicht konvertiert werden. Diese Projekte können nur von Benutzern konvertiert werden, die über die Berechtigung verfügen, Projekte zu bearbeiten. Bevor ein Projekt in einer konvertierten Projektmappe verwendet werden kann, müssen die Projektdateien in die aktuellen Formate konvertiert werden. Nachdem ein Projekt konvertiert wurde, können Sie eine Projektmappe, die das Projekt enthält, in früheren Versionen von Visual Studio nicht mehr bearbeiten, erstellen oder ausführen.  
  
### So reagieren Sie auf diese Meldung  
  
1.  Wählen Sie **Ja** oder **Nein**.  
  
    -   **Ja** – Wenn das Projekt bearbeitet werden kann, wird es in das Format konvertiert, das von der auf diesem Computer installierten Version von Visual Studio verwendet wird. Wenn das konvertierte Projekt in einem Quellcodeverwaltungssystem gespeichert ist, wird es auf das lokale Laufwerk ausgecheckt und zum Bearbeiten geöffnet.  
  
    -   **No** – Das Projekt wird nicht konvertiert, nicht aus der Quellcodeverwaltung ausgecheckt und nicht geöffnet.  
  
 Wenn Sie Mitglied eines Entwicklungsteams sind, müssen alle Entwickler, die an einem Projekt arbeiten, die gleiche Version von Visual Studio auf den lokalen Computern installiert haben. Um sicherzustellen, dass die Projekte zugänglich bleiben, stimmen Sie sich regelmäßig mit dem Team ab.  
  
## Siehe auch  
 [Project Dependencies Dialog Box](http://msdn.microsoft.com/de-de/d66e48c3-3722-40dd-99b4-53d93cac128e)   
 [Anwendungen in Visual Studio erstellen](../ide/compiling-and-building-in-visual-studio.md)
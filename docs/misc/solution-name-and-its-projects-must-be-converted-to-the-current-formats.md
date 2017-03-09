---
title: "Die Projektmappe „&lt;Name&gt;“ und die enthaltenen Projekte m&#252;ssen in die aktuellen Formate konvertiert werden. | Microsoft Docs"
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
  - "vs.querymigratesolution"
ms.assetid: 1ecb09ab-1283-4ba5-874c-f675905a3b7b
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Die Projektmappe „&lt;Name&gt;“ und die enthaltenen Projekte m&#252;ssen in die aktuellen Formate konvertiert werden.
Sie haben eine Projektmappe geöffnet, die in einer früheren Version von Visual Studio erstellt wurde. Die Projektmappe und Projektdateien müssen in die aktuellen Formate konvertiert werden, bevor eine Projektmappe in der auf dem Computer installierten Version von Visual Studio geöffnet und bearbeitet werden kann. Sie können auswählen, ob diese Projektmappe jetzt konvertiert werden soll. Die Konvertierung des Formats kann nicht rückgängig gemacht werden.  
  
> [!CAUTION]
>  Wenn die Projektmappe in einem Quellcodeverwaltungssystem gespeichert ist und die konvertierte Projektmappe wieder eingecheckt werden soll, sollten Sie zuerst ermitteln, ob eines der Projekte auch von anderen Projektmappen genutzt wird. Checken Sie keine Projektmappe mit konvertierten Projekten ein, die in anderen, nicht konvertierten Projektmappen verwendet werden. Dadurch werden die Abhängigkeiten in den betreffenden Projektmappen aufgehoben, und die Projektmappen können dann nicht mehr geöffnet oder ordnungsgemäß erstellt werden.  
  
 Sie sollten vor dem Konvertieren der Projektmappe und Projektdateien Sicherungskopien erstellen.  
  
> [!NOTE]
>  Da Visual Studio\-Projektmappen konvertiert werden, werden die vorherigen Projektmappendateien mit der Dateinamenerweiterung „.old“ markiert und im Projektmappenverzeichnis der obersten Ebene gespeichert. Bei der Konvertierung bestimmter Projekttypen, z. B. Visual C\+\+\-Projekten, werden die vorherigen Projektdateien ebenfalls mit der Dateinamenerweiterung „.old“ gekennzeichnet und im Projektverzeichnis gespeichert.  
  
 Schreibgeschützte Projekte werden nicht konvertiert. Diese Projekte können nur von Benutzern konvertiert werden, die über die Berechtigung verfügen, Projekte zu bearbeiten. Bevor ein Projekt in einer konvertierten Projektmappe verwendet werden kann, müssen die Projektdateien in die aktuellen Formate konvertiert werden. Nachdem eine Projektmappe oder eines der enthaltenen Projekte konvertiert wurde, können Sie die Projektmappe nicht mehr in früheren Versionen von Visual Studio bearbeiten, erstellen oder ausführen.  
  
### So reagieren Sie auf diese Meldung  
  
1.  Wählen Sie **Ja** oder **Nein**.  
  
    -   **Ja**: Die Projektmappendatei sowie die Dateien für die bearbeitbaren Projekte werden in die Formate konvertiert, die von der auf Ihrem Computer installierten Visual Studio\-Version verwendet werden. Wenn die konvertierte Projektmappe in einem Quellcodeverwaltungssystem gespeichert ist, wird es auf das lokale Laufwerk ausgecheckt und zum Bearbeiten geöffnet.  
  
    -   **Nein**: Die Projektmappe und deren Projekte werden nicht konvertiert, nicht vom Quellcodeverwaltungssystem ausgecheckt und lassen sich nicht öffnen.  
  
 Wenn Sie Mitglied eines Entwicklungsteams sind, müssen alle Entwickler, die an einer Projektmappe arbeiten, die gleiche Version von Visual Studio auf den lokalen Computern installiert haben. Um sicherzustellen, dass die Projektmappen und Projekte zugänglich bleiben, stimmen Sie sich regelmäßig mit dem Team ab.  
  
## Siehe auch  
 [Project Dependencies Dialog Box](http://msdn.microsoft.com/de-de/d66e48c3-3722-40dd-99b4-53d93cac128e)   
 [Anwendungen in Visual Studio erstellen](../ide/compiling-and-building-in-visual-studio.md)
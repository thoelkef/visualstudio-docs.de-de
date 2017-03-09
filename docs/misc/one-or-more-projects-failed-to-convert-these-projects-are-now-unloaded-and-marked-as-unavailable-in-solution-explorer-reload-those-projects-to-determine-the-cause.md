---
title: "Mindestens ein Projekt konnte nicht konvertiert werden. Diese Projekte werden jetzt entladen und im Projektmappen-Explorer als nicht verf&#252;gbar markiert. Laden Sie diese Projekte erneut, um die Fehlerursache zu bestimmen. | Microsoft Docs"
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
  - "vs.projectmigrationsfailed"
ms.assetid: c2fd3bbd-15f0-4b30-97f5-59abeae02141
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Mindestens ein Projekt konnte nicht konvertiert werden. Diese Projekte werden jetzt entladen und im Projektmappen-Explorer als nicht verf&#252;gbar markiert. Laden Sie diese Projekte erneut, um die Fehlerursache zu bestimmen.
Sie haben versucht, eine Projektmappe mit einem oder mehreren Projekten zu öffnen, die in einer früheren Version von Visual Studio erstellt wurden. Bestimmte Projekte konnten nicht konvertiert werden und werden im Projektmappen\-Explorer als \(nicht verfügbar\) markiert. Diese Projekte müssen in die aktuellen Formate konvertiert werden, bevor die Projektmappe in der auf dem Computer installierten Version von Visual Studio geöffnet und bearbeitet und die reparierten Projekte verwendet werden können.  
  
### So reagieren Sie auf diese Meldung  
  
1.  Wählen Sie **Ja**, um das Dialogfeld zu schließen.  
  
     Projekte, die nicht konvertiert werden konnten, werden im Projektmappen\-Explorer als **\(nicht verfügbar\)** gekennzeichnet.  
  
2.  Laden Sie die Projekte erneut, die nicht konvertiert werden konnten.  
  
    1.  Wählen Sie im Projektmappen\-Explorer jedes Projekt, das als **\(nicht verfügbar\)** gekennzeichnet ist, in der aktiven Projektmappe aus.  
  
    2.  Klicken Sie im Menü **Projekt** auf **Projekt erneut laden**.  
  
3.  Überprüfen Sie sorgfältig alle Fehlermeldungen, die Informationen über Probleme in Zusammenhang mit Projekten anzeigen. Folgende Probleme sind möglich:  
  
    1.  Das Projekt ist schreibgeschützt. Schreibgeschützte Projekte können nicht konvertiert werden. Diese Projekte können nur von Benutzern konvertiert werden, die über die Berechtigung verfügen, Projekte zu bearbeiten.  
  
    2.  Das Projekt wurde an einen anderen Benutzer exklusiv ausgecheckt. Der betreffende Benutzer muss das Projekt erst wieder einchecken, bevor Sie es auschecken können.  
  
    3.  Das Projekt konnte nicht aus einem Netzwerkserver ausgecheckt werden. Bestätigen Sie die Netzwerkbedingungen, und versuchen Sie es erneut.  
  
    4.  Das Projekt ist beschädigt und muss neu erstellt werden.  
  
4.  Beheben Sie die angegebenen Probleme, wenn Sie versuchen, die als **\(nicht verfügbar\)** gekennzeichneten Projekte erneut zu laden.  
  
5.  Öffnen Sie diese Projekte erneut, und konvertieren Sie sie. Sie sollten vor dem Konvertieren der Projektdateien Sicherungskopien erstellen.  
  
    > [!NOTE]
    >  Bei der Konvertierung bestimmter Projekttypen, z. B. Visual C\+\+\-Projekten, werden die vorherigen Projektdateien mit der Dateinamenerweiterung „.old“ gekennzeichnet und im Projektverzeichnis gespeichert.  
  
 Wenn Sie Mitglied eines Entwicklungsteams sind, müssen alle Entwickler, die an einem Projekt arbeiten, die gleiche Version von Visual Studio auf den lokalen Computern installiert haben. Um sicherzustellen, dass die Projekte zugänglich bleiben, stimmen Sie sich regelmäßig mit dem Team ab.  
  
> [!CAUTION]
>  Wenn die Projekte der Projektmappe in einem Quellcodeverwaltungssystem gespeichert sind und die konvertierten Projekte wieder eingecheckt werden sollen, sollten Sie zuerst ermitteln, ob diese Projekte auch von anderen Projektmappen genutzt werden. Checken Sie keine konvertierten Projekte ein, die in nicht konvertierten Projektmappen in Verwendung sind. Dadurch werden die Abhängigkeiten in den betreffenden Projektmappen aufgehoben, und die Projektmappen können dann nicht mehr geöffnet oder ordnungsgemäß erstellt werden.  
  
## Siehe auch  
 [NIB:Gewusst wie: Entladen und erneutes Laden von Projekten](http://msdn.microsoft.com/de-de/abc0155b-8fcb-4ffc-95b6-698518a7100b)   
 [Project Dependencies Dialog Box](http://msdn.microsoft.com/de-de/d66e48c3-3722-40dd-99b4-53d93cac128e)   
 [Anwendungen in Visual Studio erstellen](../ide/compiling-and-building-in-visual-studio.md)
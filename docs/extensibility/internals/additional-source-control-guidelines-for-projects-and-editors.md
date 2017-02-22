---
title: "Richtlinien f&#252;r zus&#228;tzliche Quelle f&#252;r Projekte und Editoren | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Datenquellen-Steuerelement [Visual Studio SDK], Richtlinien für Projekte und Editoren"
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Richtlinien f&#252;r zus&#228;tzliche Quelle f&#252;r Projekte und Editoren
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Es gibt einige Richtlinien, die Projekte und Editoren befolgen sollten, um die Quellcodeverwaltung zu unterstützen.  
  
## Richtlinien  
 Das Projekt oder der Editor können auch Folgendes tun, um die Quellcodeverwaltung zu unterstützen:  
  
|Bereich|Project|Editor|Details|  
|-------------|-------------|------------|-------------|  
|Private Kopien von Dateien|X||Die Umgebung unterstützt private Kopien von Dateien.  Das heißt, verfügt jede Person, die im Projekt eingetragen wird, dessen\/eigene private Kopie der Dateien in diesem Projekt.|  
|ANSI\-\/Unicode Dauerhaftigkeit|X|X|Wenn Sie die Persistenz von Code schreiben, behalten Sie die Dateien in der ANSI\-Form bei, da die meisten Sources kontrollprogramme Unicode nicht unterstützen.|  
|Auflisten von Dateien|X||Das Projekt muss eine bestimmte Liste aller Dateien darin enthalten und muss in der Lage sein, die Liste der Dateien mit <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> \(VSH\_PROPID\_First\_Child\/Next\_Sibling\) aufzulisten.  Das Projekt sollte Elementnamen über seine <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> Implementation und Support \(einschließlich\) Gerätedateien Name der durch seine Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> auch verfügbar machen.|  
|Textstil|X|X|Sofern möglich, sollten Dateien im Textformat sein, damit der Zusammenführung der verschiedenen Versionen zu unterstützen.  Dateien, die nicht im Textformat wurden, können nicht mit anderen Versionen der Datei später zusammengeführt werden.  Das bevorzugte Textstil ist XML.|  
|Verweisbasiert|X||Bereit zur Quellcodeverwaltung Verweisbasierte Projekte werden unterstützt.  verzeichnisbasierte Projekte werden jedoch auch über die Quellcodeverwaltung unterstützt, solange das Projekt eine Liste der Dateien bei Bedarf vorlegen kann, unabhängig davon, ob diese Dateien auf dem Datenträger vorhanden sind.  Wenn Sie ein Projekt aus der Quellcodeverwaltung öffnen, wird die Projektdatei vor allen zugehörigen Dateien zunächst gesenkt.|  
|Beibehalten von Objekten und Eigenschaften in der Reihenfolge bei vorhersagbaren|X|X|Behalten Sie die Dateien auf vorhersehbare Reihenfolge zusammenführen, z. B. alphabetischer Reihenfolge zu erleichtern.|  
|Lädt|X|X|Wenn eine Datei auf dem Datenträger geändert wird, muss der Editor in der Lage sein, diese erneut zu laden.  Wenn Sie eine Verbindung mit der Quellcodeverwaltung beteiligt sind, die Umgebung erneut lädt, indem Sie Daten für die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> Implementierung aufgerufen wird.  Der schwierigste Lädt kasten ist, wenn ein Auschecken erfolgt, wenn Sie IVsQueryEditQuerySave: aufgerufen haben:<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> und verarbeitet Informationen.  Allerdings muss der erneuten Laden von Code in der Lage sein, in dieser Situation ausgeführt werden.<br /><br /> In der Umgebung von Projektdateien automatisch neu.  Allerdings muss ein Projekt <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> implementieren, wenn es Hierarchien geschachtelt wurde, um das erneute Laden von geschachtelten Projektdateien zu unterstützen.|  
  
## Siehe auch  
 [Unterstützung von Datenquellen\-Steuerelement](../../extensibility/internals/supporting-source-control.md)
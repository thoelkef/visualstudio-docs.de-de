---
title: "Bearbeiten der Abfragen speichern (Source Control VSPackage) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "QEQS-Ereignisse"
  - "Bearbeiten Sie die Abfrage speichern Abfrageereignissen"
  - "Quellcode-Verwaltungspaketen, Ereignisse Abfrage bearbeiten Abfrage speichern."
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Bearbeiten der Abfragen speichern (Source Control VSPackage)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Editoren können Ereignisse der Abfragen\-Bearbeitungs\-Abfragen\-Abwehr übertragen \(QEQS\).  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Quellcodeverwaltungs\-Stub implementiert den QEQS\-Dienst, sodass sie die Empfänger QEQS\-Ereignissen ist.  Diese Ereignisse werden dann der derzeit aktiven Quellcodeverwaltung VSPackage delegiert.  Die aktive Quellcodeverwaltung VSPackage implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> und ihre Methoden.  Die Methoden der `IVsQueryEditQuerySave2`\-Schnittstelle werden i. d. R. aufgerufen, unmittelbar bevor ein Dokument zum ersten Mal verarbeitet wurde und gleichzeitig bevor ein Dokument gespeichert wird.  
  
## QueryEditQuerySave\-Ereignisse  
 Die Quellcodeverwaltung VSPackage muss die QEQS\-Ereignisse behandeln, indem sie die `IVsQueryEditQuerySave2`\-Schnittstelle und die erforderlichen Methoden implementiert.  Im Folgenden finden Sie eine kurze Beschreibung der zwei Methoden, die an mindestens ein VSPackage implementieren muss.  Die tatsächliche Implementierung muss in Abhängigkeit von der Logik des modells Quellcodeverwaltung entsprechen.  
  
### QueryEditFiles\-Methode  
 Das <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> wird aufgerufen, wenn ein beliebiges Projekt oder Editor eine Datei bearbeiten möchte.  Im Idealfall wird diese Methode aufgerufen *zuvor* , das die Datei geändert wurde und ob eine Datei gespeichert wird.  Wenn sie aufgerufen wird, überprüft die `IVsQueryEditQuerySave2::QueryEditFiles`\-Methode, ob die angegebenen Dateien unter Quellcodeverwaltung sind, ob sie ausgecheckt werden müssen, und ob sie erneut geladen werden können.  Wenn sich die Umstände bearbeitbar verhindern, weist die `IVsQueryEditQuerySave2::QueryEditFiles`\-Methode das aufrufende Programm mit, um den Bearbeitungsvorgang abzubrechen.  Es ist auch möglich, einen Aufruf für den Aufrufer Modus anzugeben.  Im Modus“ Automatisch „führt diese Methode nur, wenn sie keine Benutzeroberfläche angezeigt wird.  Wenn Benutzeroberfläche ist unvermeidbar, muss ein Flag zurückgegeben werden, um das Problem anzugeben.  
  
 Die Methode verhält sich in einer transaktionalen Weise. das heißt wenn die Bearbeitung in einer einzelnen Datei abgebrochen wird, wird der Bearbeitungsvorgang für alle Dateien abgebrochen.  Wenn die Bearbeitung zulässig ist, wird sie für alle Dateien zulässt.  Wenn diese Methode einmal bearbeiten einen angegebenen Satz von Dateien zulässt, muss sie auf Bearbeiten nachfolgenden Aufrufen für den gleichen Satz von Dateien immer ermöglichen.  Die Bearbeitung ALLOW Schleife wird fortgesetzt, bis die Datei geschlossen und erneut geladen, gespeichert sind. nachdem ihre Änderung der Attribute \(Eigenschaften\); Quellcodeverwaltung ist oder bis das Paket geändert.  Wenn Fälle zu berücksichtigen, die mehrere Dateien des `IVsQueryEditQuerySave2::QueryEditFiles`\-Methoden gehören, die Gerätedateien, Löschen und Bearbeitungen durch den Benutzer im Arbeitsspeicher implementiert werden.  
  
### QuerySaveFiles\-Methode  
 Das <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> wird aufgerufen, wenn ein beliebiges Projekt oder Editor eine Gruppe von Dateien speichern muss.  Wenn diese Methoden `IVsQueryEditQuerySave2::QuerySaveFiles` , die überprüft, ob die angegebenen Dateien schreibgeschützt sind und ob sie in der Quellcodeverwaltung aufgerufen werden.  Wenn die Dateien ausgecheckt werden müssen, wird der Aufruf an das Paket Quellcodeverwaltung delegiert.  Wenn Umständen die Dateien gespeichert sind, verhindern, muss die `IVsQueryEditQuerySave2::QuerySaveFiles`\-Methode den Editor mitteilen, um die Speicherung abzubrechen.  Wie bei der `IVsQueryEditQuerySave2::QueryEditFiles`\-Methode, kann der Aufrufer den Modus eines Aufrufs anzugeben.  Im Modus“ Automatisch „führt diese Methode nur, wenn sie keine Benutzeroberfläche angezeigt wird.  Wenn Benutzeroberfläche ist unvermeidbar, muss ein Flag zurückgegeben werden, um das Problem anzugeben.  
  
 Diese Methode muss in einer transaktionalen Weise verhalten. das heißt wenn die Speicherung in einer einzigen Datei abgebrochen wird, wird die Speicherung für alle Dateien abgebrochen.  Wenn die Speicherung zugelassen ist, muss es für alle Dateien zugelassen werden.  Wie bei der `IVsQueryEditQuerySave2::QueryEditFiles`\-Methode zu fällen, die mehrere Dateien des `IVsQueryEditQuerySave2::QuerySaveFiles`\-Methoden gehören, die Gerätedateien, Löschen und Bearbeitungen durch den Benutzer im Arbeitsspeicher implementiert werden.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
---
title: "Benutzeroptionen bei Projektmappen (. Datei Suo) | Microsoft Docs"
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
  - ".suo-Dateien, VSPackages"
  - "SUO-Dateien, VSPackages"
  - ".suo-Dateien-Projektmappen"
  - "Projektmappen, Optionen für Benutzer"
  - "Projektmappen-Benutzeroptionendatei (.suo)"
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Benutzeroptionen bei Projektmappen (. Datei Suo)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Der Projektmappen\-Benutzeroptionendatei \(.suo\) enthält Lösungsoptionen pro Benutzer. Diese Datei sollte nicht Quellcodeverwaltungssystem eingecheckt werden.  
  
 Der Projektmappen\-Benutzeroptionendatei \(.suo\) ist eine strukturierten Speicher oder zusammengesetzte, Datei, die in einem binären Format gespeichert. Sie speichern Benutzerinformationen in Streams mit dem Namen des Datenstroms wird der Schlüssel, der verwendet wird, um die Informationen in der SUO\-Datei zu identifizieren. Der Projektmappen\-Benutzeroptionendatei Benutzervoreinstellungen gespeichert und wird automatisch erstellt, wenn eine Lösung von Visual Studio gespeichert.  
  
 Wenn die Umgebung eine SUO\-Datei geöffnet wird, listet er alle derzeit geladenen VSPackages. Wenn ein VSPackage implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> \-Schnittstelle, und klicken Sie dann auf die Umgebung Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> Methode für das VSPackage fordern sie alle zugehörigen Daten aus der SUO\-Datei zu laden.  
  
 Es ist in der SUO\-Datei des VSPackage Verantwortung zu wissen, was es streams geschrieben hätte. Für jeden Datenstrom, der geschrieben wurde, das VSPackage Aufruf zurück an die Umgebung über <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> einen besonderen Datenstrom geladen, die durch den Schlüssel identifiziert wird, wird der Name des Datenstroms. Die Umgebung ruft dann zurück an das VSPackage diesen bestimmten Stream übergeben Sie den Namen des Streams gelesen und ein `IStream` Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> Methode.  
  
 Ein weiterer Aufruf wird an diesem Punkt wird versucht, `LoadUserOptions` ob es ist einem anderen Bereich der SUO\-Datei, die gelesen werden. Dieser Prozess wird fortgesetzt, bis alle der Datenströme in der SUO\-Datei gelesen und von der Umgebung verarbeitet wurden.  
  
 Wenn die Projektmappe gespeichert oder geschlossen, die Umgebung Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> Methode mit einem Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> Methode. Ein `IStream` übergeben wird, enthält die binäre Informationen gespeichert werden die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> \-Methode, die dann die Informationen in der SUO\-Datei und ruft schreibt die `SaveUserOptions` Methode erneut, um festzustellen, ob es einen anderen Stream der Informationen, die in der SUO\-Datei zu schreiben.  
  
 Diese beiden Methoden `SaveUserOptions` und `WriteUserOptions`, rekursiv aufgerufen werden, für jeden Datenstrom Informationen speichern in der SUO\-Datei übergeben, in dem Sie auf `IVsSolutionPersistence`. Sie werden rekursiv ermöglichen das Schreiben von mehreren Streams in der SUO\-Datei aufgerufen. Auf diese Weise Benutzerinformationen wird mit der Projektmappe beibehalten und gewährleistet ist es das nächste Mal, wenn, das die Projektmappe geöffnet wird.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [Projektmappen](../../extensibility/internals/solutions.md)
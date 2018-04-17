---
title: Benutzeroptionen bei Projektmappen (. Suo) Datei | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0b96e3ad2ec29402dddc7354df46293b99bac3ec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="solution-user-options-suo-file"></a>Benutzeroptionen bei Projektmappen (. Suo)-Datei
Der Projektmappen-Benutzeroptionendatei (.suo) enthält benutzerspezifische Projektmappenoptionen. Diese Datei sollte nicht Quellcodeverwaltungssystem eingecheckt werden.  
  
 Der Projektmappen-Benutzeroptionendatei (.suo) ist eine strukturierten Speicher oder ein zusammengesetztes Element sein, Datei, die in einem binären Format gespeichert. Speichern Sie Benutzerinformationen in Streams mit dem Namen des Datenstroms wird der Schlüssel, der verwendet wird, um die Informationen in der SUO-Datei zu identifizieren. Der Projektmappen-Benutzeroptionendatei dient zum Speichern von benutzereinstellungseinstellungen und wird automatisch erstellt, wenn eine Projektmappe von Visual Studio gespeichert.  
  
 Wenn die Umgebung eine SUO-Datei geöffnet wird, listet sie alle derzeit geladenen VSPackages. Wenn eine VSPackage implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> -Schnittstelle, und klicken Sie dann auf die Umgebung Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> Methode für das VSPackage, fordern sie alle zugehörigen Daten aus der SUO-Datei geladen.  
  
 Es ist, dass die VSPackage Verantwortung wissen, was es streamt in der SUO-Datei geschrieben sein kann. Für alle Datenströme, die es geschrieben hat, das VSPackage einen Rückruf in die Umgebung durch <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> einen besonderen Datenstrom geladen, die durch den Schlüssel identifiziert wird, den Namen des Datenstroms. Die Umgebung ruft dann wieder auf das VSPackage, um diese besonderen Datenstrom übergeben Sie den Namen des Streams gelesen und ein `IStream` Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> Methode.  
  
 Zu diesem Zeitpunkt wird eine andere Aufruf ausgelöst, um `LoadUserOptions` um festzustellen, ob es einem anderen Bereich der SUO-Datei, die gelesen werden. Dieser Prozess wird fortgesetzt, bis alle-Datenströme in der SUO-Datei gelesen und von der Umgebung verarbeitet wurden.  
  
 Wenn die Projektmappe gespeichert ist, oder "geschlossen", "die Umgebung Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> Methode mit einem Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> Methode. Ein `IStream` übergeben wird, enthält die binäre Informationen gespeichert werden, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> -Methode, die schreibt dann die Informationen auf der SUO-Datei und in Aufrufen der `SaveUserOptions` Methode erneut aus, um festzustellen, ob es einen anderen Datenstrom, der Informationen zum Schreiben in die SUO die Datei.  
  
 Diese beiden Methoden `SaveUserOptions` und `WriteUserOptions`, heißen rekursiv für alle Datenströme von Informationen in der SUO-Datei, und übergeben des Zeigers auf gespeichert werden sollen `IVsSolutionPersistence`. Sie werden rekursiv ermöglichen das Schreiben von mehreren Datenströmen in der SUO-Datei aufgerufen. Auf diese Weise Benutzerinformationen wird mit der Lösung beibehalten und gewährleistet ist es das nächste Mal die Projektmappe geöffnet wird.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [Projektmappen](../../extensibility/internals/solutions.md)
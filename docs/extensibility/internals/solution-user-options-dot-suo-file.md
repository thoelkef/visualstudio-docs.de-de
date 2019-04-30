---
title: Benutzeroptionen bei Projektmappen (. Suo)-Datei | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fab823a9057c44eca9928b1b1f97ec446fb251c4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62908708"
---
# <a name="solution-user-options-suo-file"></a>Datei mit Benutzeroptionen in Projektmappen (SUO)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Der Projektmappen-Benutzeroptionendatei (.suo) enthält Projektmappenoptionen pro Benutzer. Diese Datei sollte nicht auf die quellcodeverwaltung eingecheckt werden.  
  
 Der Projektmappen-Benutzeroptionendatei (.suo) ist eine strukturierte Speicherung oder zusammengesetzte, Datei, die in einem binären Format gespeichert. Sie speichern Benutzerinformationen in Streams mit dem Namen des Datenstroms wird der Schlüssel, der verwendet wird, um die Informationen in der SUO-Datei zu identifizieren. Die projektmappenbenutzer-Optionsdatei wird verwendet, um die bevorzugten benutzereinstellungen speichern und wird automatisch erstellt, wenn eine Projektmappe von Visual Studio gespeichert.  
  
 Wenn die Umgebung eine SUO-Datei geöffnet wird, listet sie alle aktuell geladenen VSPackages. Wenn eine VSPackage implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> -Schnittstelle, und klicken Sie dann auf die Umgebung Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> Methode für das VSPackage aufgefordert wird, um alle zugehörigen Daten aus der SUO-Datei zu laden.  
  
 Es ist, dass die VSPackage Verantwortung wissen, was sie Datenströme in die SUO-Datei geschrieben hätte. Für jeden Stream, der es geschrieben hat, das VSPackage einen Rückruf in die Umgebung über <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> einen besonderen Datenstrom geladen, die nach dem Schlüssel identifiziert wird, die den Namen des Datenstroms darstellt. Die Umgebung ruft dann wieder auf das VSPackage, um den bestimmten Stream übergeben Sie den Namen des Streams gelesen und ein `IStream` Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> Methode.  
  
 Ein weiterer Aufruf wird an diesem Punkt versucht, `LoadUserOptions` um festzustellen, ob es ist einem anderen Abschnitt der SUO-Datei, die gelesen werden. Dieser Prozess wird fortgesetzt, bis alle Datenstreams in der SUO-Datei zu lesen und von der Umgebung verarbeitet wurden.  
  
 Wenn die Lösung gespeichert ist, oder geschlossen werden, die Umgebung Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> Methode mit einem Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> Methode. Ein `IStream` übergeben wird, die die binäre Informationen gespeichert werden, enthält die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> -Methode, die dann die Informationen in der SUO-Datei und ruft schreibt die `SaveUserOptions` Methode erneut aus, um festzustellen, ob ein weiterer Datenstrom mit Informationen zum Schreiben in die SUO die Datei.  
  
 Diese zwei Methoden, `SaveUserOptions` und `WriteUserOptions`, rekursiv aufgerufen werden, für jeden Stream, der Informationen, die in der SUO-Datei, und übergeben des Zeigers auf gespeichert werden `IVsSolutionPersistence`. Heißen sie rekursiv, um das Schreiben von mehreren Datenströmen in der SUO-Datei zu ermöglichen. Auf diese Weise Benutzerinformationen werden mit der Lösung beibehalten und gewährleistet ist es das nächste Mal, wenn, das die Projektmappe geöffnet wird.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [Projektmappen](../../extensibility/internals/solutions-overview.md)

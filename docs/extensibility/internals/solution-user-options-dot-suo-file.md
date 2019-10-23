---
title: Projektmappenbenutzeroptionen (. SUO-Datei | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6f21e4a4a6530692709247e64b0d84aa7b06eb3a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723813"
---
# <a name="solution-user-options-suo-file"></a>Datei mit Benutzeroptionen in Projektmappen (SUO)
Die Benutzeroptionen für die Projekt Mappe (. suo) enthalten Optionen für benutzerspezifische Lösungen. Diese Datei sollte nicht in die Quell Code Verwaltung eingeklickt werden.

 Bei der Projektmappen-Benutzeroptionen Datei (. suo) handelt es sich um eine strukturierte Speicher-oder Verbund Datei, die in einem binären Format gespeichert ist. Sie speichern Benutzerinformationen in Streams mit dem Namen des Streams, der der Schlüssel ist, der zum Identifizieren der Informationen in der SUO-Datei verwendet wird. Die Benutzer Optionsdatei für die Projekt Mappe wird zum Speichern der Benutzer Einstellungs Einstellungen verwendet und automatisch erstellt, wenn Visual Studio eine Projekt Mappe speichert.

 Wenn die Umgebung eine SUO-Datei öffnet, listet Sie alle zurzeit geladenen VSPackages auf. Wenn ein VSPackage die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>-Schnittstelle implementiert, ruft die Umgebung die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A>-Methode für das VSPackage auf, um alle Daten aus der SUO-Datei zu laden.

 Es liegt in der Verantwortung des VSPackages, zu wissen, welche Streams es möglicherweise in die SUO-Datei geschrieben hat. Für jeden geschriebenen Stream ruft das VSPackage über <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> an die Umgebung zurück, um einen bestimmten Datenstrom zu laden, der durch den Schlüssel identifiziert wird. Dies ist der Name des Datenstroms. Die Umgebung ruft dann an das VSPackage zurück, um den betreffenden Stream zu lesen und den Namen des Streams und einen `IStream` Zeiger an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A>-Methode zu übergeben.

 An diesem Punkt wird `LoadUserOptions` aufgerufen, um zu überprüfen, ob ein anderer Abschnitt der SUO-Datei vorhanden ist, der gelesen werden muss. Dieser Prozess wird fortgesetzt, bis alle Datenströme in der SUO-Datei von der Umgebung gelesen und verarbeitet wurden.

 Wenn die Lösung gespeichert oder geschlossen wird, ruft die Umgebung die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A>-Methode mit einem Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A>-Methode auf. Eine `IStream`, die die zu speichernden Binär Informationen enthält, wird an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A>-Methode weitergegeben, die die Informationen dann in die SUO-Datei schreibt und die `SaveUserOptions`-Methode erneut aufruft, um festzustellen, ob ein anderer Datenstrom zum Schreiben in die SUO-Datei vorhanden ist.

 Diese beiden Methoden, `SaveUserOptions` und `WriteUserOptions`, werden rekursiv für jeden Datenstrom aufgerufen, der in der SUO-Datei gespeichert werden soll, und übergeben den Zeiger auf `IVsSolutionPersistence`. Sie werden rekursiv aufgerufen, um das Schreiben mehrerer Streams in die SUO-Datei zu ermöglichen. Auf diese Weise werden die Benutzerinformationen mit der Projekt Mappe beibehalten und sind beim nächsten Öffnen der Lösung garantiert.

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Projektmappen](../../extensibility/internals/solutions-overview.md)
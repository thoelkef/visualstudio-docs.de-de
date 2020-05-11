---
title: Lösungsbenutzeroptionen (. Suo) Datei | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9469663d3ac258e1c568778894d8584c68c13632
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705318"
---
# <a name="solution-user-options-suo-file"></a>Datei mit Benutzeroptionen in Projektmappen (SUO)
Die Lösungsbenutzeroptionsdatei (.suo) enthält benutzerspezifische Lösungsoptionen. Diese Datei sollte nicht in die Quellcodeverwaltung eingecheckt werden.

 Die Lösung Benutzeroptionen (.suo) Datei ist ein strukturierter Speicher, oder zusammengesetzt, Datei in einem binären Format gespeichert. Sie speichern Benutzerinformationen in Streams, wobei der Name des Streams der Schlüssel ist, der zum Identifizieren der Informationen in der .suo-Datei verwendet wird. Die Projektmappenbenutzeroptionsdatei wird zum Speichern von Benutzereinstellungen verwendet und automatisch erstellt, wenn Visual Studio eine Projektmappe speichert.

 Wenn die Umgebung eine .suo-Datei öffnet, werden alle aktuell geladenen VSPackages aufgezählt. Wenn ein VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> die Schnittstelle implementiert, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> ruft die Umgebung die Methode auf dem VSPackage auf, die sie auffordert, alle ihre Daten aus der .suo-Datei zu laden.

 Es liegt in der Verantwortung des VSPackage zu wissen, welche Streams es in die .suo-Datei geschrieben haben könnte. Für jeden Stream, den es geschrieben hat, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> ruft das VSPackage an die Umgebung zurück, um einen bestimmten Stream zu laden, der durch den Schlüssel identifiziert wird, der der Name des Streams ist. Die Umgebung ruft dann zum VSPackage zurück, um den bestimmten `IStream` Stream zu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> lesen, der den Namen des Streams und einen Zeiger auf die Methode übergibt.

 An diesem Punkt wird ein `LoadUserOptions` weiterer Aufruf getätigt, um zu sehen, ob es einen anderen Abschnitt der .suo-Datei gibt, der gelesen werden muss. Dieser Vorgang wird fortgesetzt, bis alle Datenströme in der .suo-Datei von der Umgebung gelesen und verarbeitet wurden.

 Wenn die Lösung gespeichert oder geschlossen <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> wird, ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> Umgebung die Methode mit einem Zeiger auf die Methode auf. Ein, `IStream` der die zu speichernden <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> Binärinformationen enthält, wird an die Methode übergeben, `SaveUserOptions` die dann die Informationen in die .suo-Datei schreibt und die Methode erneut aufruft, um zu sehen, ob es einen weiteren Informationsstrom gibt, der in die .suo-Datei geschrieben werden soll.

 Diese beiden `SaveUserOptions` Methoden `WriteUserOptions`und werden rekursiv für jeden Informationsstrom aufgerufen, der in der .suo-Datei gespeichert werden soll, und im Zeiger an `IVsSolutionPersistence`übergeben. Sie werden rekursiv aufgerufen, um das Schreiben mehrerer Streams in die .suo-Datei zu ermöglichen. Auf diese Weise werden Benutzerinformationen mit der Lösung beibehalten und sind garantiert, dass sie beim nächsten Öffnen der Lösung vorhanden sind.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>
- [Lösungen](../../extensibility/internals/solutions-overview.md)

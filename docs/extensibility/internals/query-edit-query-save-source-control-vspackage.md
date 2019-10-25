---
title: Abfrage zum Bearbeiten der Abfrage bearbeiten (Quellcodeverwaltungs-VSPackage) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be12297bdaeb112d7421b02da1153ed62d6d14f8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724768"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>QueryEditQuerySave (Quellcodeverwaltungs-VSPackage)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-Editoren können Abfrage Edit Query Save-Ereignisse (QEQS) senden. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Quellcodeverwaltungs-Stub implementiert den QEQS-Dienst, sodass er der Empfänger von QEQS-Ereignissen ist. Diese Ereignisse werden dann an das derzeit aktive Quellcodeverwaltungs-VSPackage delegiert. Das VSPackage für die aktive Quell Code Verwaltung implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> und die zugehörigen Methoden. Die Methoden der `IVsQueryEditQuerySave2`-Schnittstelle werden in der Regel unmittelbar vor dem erstmaligen Bearbeiten eines Dokuments und unmittelbar vor dem Speichern eines Dokuments aufgerufen.

## <a name="queryeditquerysave-events"></a>Queryeditquerysave-Ereignisse
 Das VSPackage der Quell Code Verwaltung muss die QEQS-Ereignisse behandeln, indem die `IVsQueryEditQuerySave2`-Schnittstelle und die erforderlichen Methoden implementiert werden. Im folgenden finden Sie eine kurze Beschreibung der beiden Methoden, die das VSPackage mindestens implementieren muss. Die tatsächliche Implementierung muss mit der Logik des Quell Code Verwaltungsmodells übereinstimmen.

### <a name="queryeditfiles-method"></a>QueryEditFiles-Methode
 Der <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> wird aufgerufen, wenn ein Projekt oder ein Editor eine Datei ändern möchte. Im Idealfall wird diese Methode aufgerufen, *bevor* die Datei geändert und eine Datei gespeichert wird. Beim Aufrufen überprüft die `IVsQueryEditQuerySave2::QueryEditFiles`-Methode, ob die angegebenen Dateien der Quell Code Verwaltung unterliegen, ob Sie ausgecheckt werden müssen und ob Sie erneut geladen werden können. Wenn die Umstände verhindern, dass die Dateien bearbeitet werden können, weist die `IVsQueryEditQuerySave2::QueryEditFiles`-Methode das aufrufende Programm an, die Bearbeitung abzubrechen. Es ist auch möglich, dass der Aufrufer einen Aufruf Modus angibt. Im Modus "unbeaufsichtigt" führt diese Methode nur dann Aktionen aus, wenn keine Benutzeroberfläche angezeigt wird. Wenn die Benutzeroberfläche unvermeidlich ist, muss ein Flag zurückgegeben werden, um das Problem anzugeben.

 Die Methode verhält sich auf transaktionale Weise. Das heißt, wenn der Bearbeitungsvorgang für eine einzelne Datei abgebrochen wird, wird der Bearbeitungsvorgang für alle Dateien abgebrochen. Wenn die Bearbeitung hingegen zulässig ist, ist Sie für alle Dateien zulässig. Wenn diese Methode eine einmalige Bearbeitung für einen bestimmten Satz von Dateien zulässt, muss Sie für nachfolgende Aufrufe für denselben Satz von Dateien immer bearbeitet werden können. Die "Allow-Edit"-Schleife wird fortgesetzt, bis die Dateien geschlossen, gespeichert und erneut geladen werden. bis die Attribute (Eigenschaften) ändern; oder bis das Quell Code Verwaltungspaket geändert wird. Fälle, die bei der Implementierung der `IVsQueryEditQuerySave2::QueryEditFiles` Methode berücksichtigt werden sollten, sind mehrere Dateien, Sonderdateien, Abbruch von Benutzern und in-Memory-Änderungen.

### <a name="querysavefiles-method"></a>Querysavefiles-Methode
 Der <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> wird aufgerufen, wenn ein Projekt oder Editor einen Satz von Dateien speichern muss. Beim Aufrufen überprüft die `IVsQueryEditQuerySave2::QuerySaveFiles`-Methode, ob die angegebenen Dateien schreibgeschützt sind und ob Sie der Quell Code Verwaltung unterliegen. Wenn die Dateien ausgecheckt werden müssen, wird der-Befehl an das Quell Code Verwaltungspaket delegiert. Wenn die Dateien nicht gespeichert werden, muss die `IVsQueryEditQuerySave2::QuerySaveFiles` Methode den Editor anweisen, den Speichervorgang abzubrechen. Wie bei der `IVsQueryEditQuerySave2::QueryEditFiles`-Methode ist es möglich, dass der Aufrufer einen Aufruf Modus angibt. Im Modus "unbeaufsichtigt" führt diese Methode nur dann Aktionen aus, wenn keine Benutzeroberfläche angezeigt wird. Wenn die Benutzeroberfläche unvermeidlich ist, muss ein Flag zurückgegeben werden, um das Problem anzugeben.

 Diese Methode muss sich auf transaktionale Weise Verhalten. Das heißt, wenn der Speichervorgang für eine einzelne Datei abgebrochen wird, wird der Speichervorgang für alle Dateien abgebrochen. Umgekehrt muss, wenn die Speicherung zulässig ist, für alle Dateien zulässig sein. Wie bei der `IVsQueryEditQuerySave2::QueryEditFiles` Methode sind auch Fälle, die beim Implementieren der `IVsQueryEditQuerySave2::QuerySaveFiles` Methode zu berücksichtigen sind, mehrere Dateien, Sonderdateien, Abbruch von Benutzern und in-Memory-Änderungen.

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
---
title: Abfragebearbeiten Query Speichern (Quellcodeverwaltung VSPackage) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c09ac0cb4f51b8f2484b95d403ff6d0445631479
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705962"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>QueryEditQuerySave (Quellcodeverwaltungs-VSPackage)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Editoren können QEQS-Ereignisse (Query Edit Query Save) übertragen. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Source Control Stub implementiert den QEQS-Dienst, sodass er der Empfänger von QEQS-Ereignissen ist. Diese Ereignisse werden dann an das aktuell aktive Quellcodeverwaltungs-VSPackage delegiert. Die aktive Quellcodeverwaltung VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> implementiert die und ihre Methoden. Die Methoden `IVsQueryEditQuerySave2` der Schnittstelle werden in der Regel unmittelbar vor der ersten Bearbeitung eines Dokuments und unmittelbar vor dem Speichern eines Dokuments aufgerufen.

## <a name="queryeditquerysave-events"></a>QueryEditQuerySave-Ereignisse
 Das Quellcodeverwaltungs-VSPackage muss die QEQS-Ereignisse verarbeiten, indem die `IVsQueryEditQuerySave2` Schnittstelle und die erforderlichen Methoden implementiert werden. Im Folgenden finden Sie eine kurze Beschreibung der beiden Methoden, die das VSPackage mindestens implementieren muss. Die eigentliche Implementierung muss der Logik des Quellcodeverwaltungsmodells entsprechen.

### <a name="queryeditfiles-method"></a>QueryEditFiles-Methode
 Der <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> wird aufgerufen, wenn ein Projekt oder Editor eine Datei ändern möchte. Im Idealfall wird diese Methode aufgerufen, *bevor* die Datei geändert wird und wenn eine Datei gespeichert wird. Beim Aufruf überprüft `IVsQueryEditQuerySave2::QueryEditFiles` die Methode, ob die angegebenen Dateien unter Quellcodeverwaltung stehen, ob sie ausgecheckt werden müssen und ob sie neu geladen werden können. Wenn die Umstände verhindern, dass `IVsQueryEditQuerySave2::QueryEditFiles` die Dateien bearbeitet werden können, weist die Methode das aufrufende Programm an, die Bearbeitung abzubrechen. Es ist auch möglich, dass der Aufrufer einen Aufrufmodus angibt. Im "stillen" Modus wird diese Methode nur dann ausgeführt, wenn keine Benutzeroberfläche angezeigt wird. Wenn die Benutzeroberfläche unvermeidbar ist, muss ein Flag zurückgegeben werden, um das Problem anzuzeigen.

 Die Methode verhält sich transaktional; Wenn die Bearbeitung für eine einzelne Datei abgebrochen wird, wird die Bearbeitung für alle Dateien abgebrochen. Umgekehrt ist die Bearbeitung zulässig, wenn die Bearbeitung zulässig ist. Wenn diese Methode die Bearbeitung einmal für einen bestimmten Satz von Dateien zulässt, muss sie immer die Bearbeitung bei nachfolgenden Aufrufen für denselben Satz von Dateien zulassen. Die Allow-Edit-Schleife wird fortgesetzt, bis die Dateien geschlossen, gespeichert und neu geladen werden. bis sich ihre Attribute (Eigenschaften) ändern; oder bis das Quellcodeverwaltungspaket geändert wird. Zu den Fällen, `IVsQueryEditQuerySave2::QueryEditFiles` die bei der Implementierung der Methode zu berücksichtigen sind, gehören mehrere Dateien, spezielle Dateien, Abbrechen vom Benutzer und Bearbeitungen im Arbeitsspeicher.

### <a name="querysavefiles-method"></a>QuerySaveFiles-Methode
 Der <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> wird aufgerufen, wenn ein Projekt oder Editor eine Reihe von Dateien speichern muss. Beim Aufruf überprüft `IVsQueryEditQuerySave2::QuerySaveFiles` die Methode, ob die angegebenen Dateien schreibgeschützt sind und ob sie sich unter Quellcodeverwaltung befinden. Wenn die Dateien ausgecheckt werden müssen, wird der Aufruf an das Quellcodeverwaltungspaket delegiert. Wenn die Umstände verhindern, dass `IVsQueryEditQuerySave2::QuerySaveFiles` die Dateien gespeichert werden, muss die Methode den Editor anweisen, den Speicher vorgangsweise abzubrechen. Wie bei `IVsQueryEditQuerySave2::QueryEditFiles` der Methode ist es für den Aufrufer möglich, einen Aufrufmodus anzugeben. Im "stillen" Modus wird diese Methode nur dann ausgeführt, wenn keine Benutzeroberfläche angezeigt wird. Wenn die Benutzeroberfläche unvermeidbar ist, muss ein Flag zurückgegeben werden, um das Problem anzuzeigen.

 Diese Methode muss sich transaktional verhalten. Wenn der Speicher in einer einzelnen Datei abgebrochen wird, wird die Speicherung für alle Dateien abgebrochen. Umgekehrt muss das Speichern für alle Dateien zulässig sein, wenn das Speichern zulässig ist. Wie bei `IVsQueryEditQuerySave2::QueryEditFiles` der Methode umfassen die `IVsQueryEditQuerySave2::QuerySaveFiles` Fälle, die bei der Implementierung der Methode zu berücksichtigen sind, mehrere Dateien, spezielle Dateien, Abbrechen vom Benutzer und In-Memory-Bearbeitungen.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>

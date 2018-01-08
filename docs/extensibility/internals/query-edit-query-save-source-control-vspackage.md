---
title: Fragen Sie die Abfrage speichern (Source Control VSPackage) bearbeiten | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e3428e51dda2f8cc8410b6ac67f5779f7c2300ed
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Edit-Abfrage speichern (Source Control VSPackage)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Editoren können Ereignisse Abfrage bearbeiten Abfrage speichern (QEQS) übertragen. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Source Control Stub implementiert den Dienst QEQS, damit sie die Empfänger von QEQS Ereignissen ist. Diese Ereignisse werden dann an das derzeit aktive Quellsteuerelement VSPackage delegiert. Die aktive Datenquellen-Steuerelements, das VSPackage implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> und die zugehörigen Methoden. Die Methoden der `IVsQueryEditQuerySave2` Schnittstelle werden in der Regel aufgerufen, unmittelbar bevor ein Dokument bearbeitet wird, zum ersten Mal und unmittelbar bevor ein Dokument gespeichert wird.  
  
## <a name="queryeditquerysave-events"></a>QueryEditQuerySave-Ereignisse  
 Die Datenquellen-Steuerelements VSPackage muss die QEQS Ereignisse behandeln, durch die Implementierung der `IVsQueryEditQuerySave2` Schnittstelle und die erforderlichen Methoden. Es folgt eine kurze Beschreibung der beiden Methoden, die mindestens das VSPackage implementieren müssen. Die tatsächliche Implementierung muss gemäß der Logik des Quellmodells Steuerelement sein.  
  
### <a name="queryeditfiles-method"></a>QueryEditFiles-Methode  
 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> wird aufgerufen, wenn einem Projekt oder Editor eine Datei bearbeiten möchte. Diese Methode wird aufgerufen, idealerweise *vor* die Datei geändert wird und wenn eine Datei gespeichert wird. Beim Aufrufen der `IVsQueryEditQuerySave2::QueryEditFiles` Methode überprüft, ob die angegebenen Dateien unter quellcodeverwaltung sind, gibt an, ob die benötigte ausgecheckt werden, und gibt an, ob sie erneut geladen werden können. Wenn Umständen verhindern, dass die Dateien bearbeitet werden, wird die `IVsQueryEditQuerySave2::QueryEditFiles` Methode teilt das aufrufende Programm die Bearbeitung abgebrochen. Es ist auch möglich, dass der Aufrufer einen Aufruf-Modus angeben. Im Modus "im Hintergrund" wird diese Methode die Aktion nur dann, wenn sie nicht über die Benutzeroberflächen angezeigt werden kann. Wenn UI unvermeidlich ist, muss ein Flag zurückgegeben werden, um das Problem hinweisen.  
  
 Das Verhalten der-Methode in Form einer Transaktion; Wenn auf eine einzelne Datei die Bearbeitung abgebrochen wird, wird die Bearbeitung für alle Dateien abgebrochen. Wenn die Bearbeitung zulässig ist, ist es hingegen für alle Dateien zulässig. Wenn diese Methode ermöglicht das Bearbeiten von einmal für eine bestimmte Gruppe von Dateien, muss es immer zulässt, bei nachfolgenden Aufrufen auf den gleichen Satz von Dateien bearbeiten. Die Schleife zulassen bearbeiten wird fortgesetzt, bis die Dateien geschlossen, gespeichert und erneut geladen werden; bis Sie geändert werden, deren Attribute (Eigenschaften); oder bis das Quellcodeverwaltungspaket geändert wird. Fälle berücksichtigt bei der Implementierung der `IVsQueryEditQuerySave2::QueryEditFiles` Methode mehrere Includedateien spezielle Dateien, aus Benutzer und in-Memory-Bearbeitung abbrechen.  
  
### <a name="querysavefiles-method"></a>QuerySaveFiles-Methode  
 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> wird aufgerufen, wenn einem Projekt oder Editor einen Satz von Dateien zu speichern muss. Beim Aufrufen der `IVsQueryEditQuerySave2::QuerySaveFiles` Methode überprüft, wenn die angegebenen Dateien schreibgeschützt sind und ob sie in der quellcodeverwaltung sind. Wenn die Dateien werden ausgecheckt müssen, wird der Aufruf an das Quellcodeverwaltungspaket delegiert. Wenn Umständen verhindern, dass die Dateien gespeichert, die `IVsQueryEditQuerySave2::QuerySaveFiles` Methode muss Teilen Sie den Editor, um den Speichervorgang abzubrechen. Wie bei der `IVsQueryEditQuerySave2::QueryEditFiles` -Methode, es ist möglich, dass der Aufrufer einen Aufruf-Modus angeben. Im Modus "im Hintergrund" wird diese Methode die Aktion nur dann, wenn sie nicht über die Benutzeroberflächen angezeigt werden kann. Wenn UI unvermeidlich ist, muss ein Flag zurückgegeben werden, um das Problem hinweisen.  
  
 Diese Methode muss auf transaktionale Weise Verhalten. Wenn der Speichervorgang auf eine einzelne Datei abgebrochen wird, wird speichern, also für alle Dateien abgebrochen. Umgekehrt, wenn der Speichervorgang zulässig ist, muss er für alle Dateien zulässig sein. Wie bei der `IVsQueryEditQuerySave2::QueryEditFiles` -Methode, die Fälle, die bei der Implementierung sollten die `IVsQueryEditQuerySave2::QuerySaveFiles` Methode mehrere Includedateien spezielle Dateien, aus Benutzer und in-Memory-Bearbeitung abbrechen.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
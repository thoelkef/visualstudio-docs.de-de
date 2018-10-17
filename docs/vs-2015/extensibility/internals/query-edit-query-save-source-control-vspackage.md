---
title: Fragen Sie die Abfrage speichern (Quellcodeverwaltungs-VSPackage) bearbeiten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 612bd94ba360f496c08ea25fd1a45e15c88edb6e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49172392"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>QueryEditQuerySave (Quellcodeverwaltungs-VSPackage)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Editoren können die Abfrage bearbeiten Abfrage speichern (QEQS) Ereignisse senden. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Quellcode-Verwaltungsstub implementiert den QEQS-Dienst, sodass der Empfänger von Ereignissen von QEQS. Diese Ereignisse werden dann an das derzeit aktive Quellcodeverwaltungs-VSPackage delegiert. Die aktiven Datenquellen-Steuerelement, das VSPackage implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> und die zugehörigen Methoden. Die Methoden der `IVsQueryEditQuerySave2` Schnittstelle werden in der Regel aufgerufen, unmittelbar bevor ein Dokument bearbeitet wird, zum ersten Mal und unmittelbar bevor ein Dokument gespeichert wird.  
  
## <a name="queryeditquerysave-events"></a>QueryEditQuerySave-Ereignisse  
 Das Quellcodeverwaltungs-VSPackage muss die QEQS-Ereignisse behandeln, durch die Implementierung der `IVsQueryEditQuerySave2` Schnittstelle und die erforderlichen Methoden. Es folgt eine kurze Beschreibung der beiden Methoden, die das VSPackage mindestens implementieren müssen. Die tatsächliche Implementierung muss in Übereinstimmung mit der Logik des Quellmodells Steuerelement sein.  
  
### <a name="queryeditfiles-method"></a>QueryEditFiles-Methode  
 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> wird aufgerufen, wenn keine Projekte oder -Editor eine Datei ändern möchte. Diese Methode wird aufgerufen, im Idealfall *vor* die Datei wird geändert, und wenn eine Datei gespeichert ist. Wenn aufgerufen, die `IVsQueryEditQuerySave2::QueryEditFiles` Methode überprüft, ob die angegebenen Dateien unter quellcodeverwaltung stehen, ob sie ausgecheckt werden müssen und gibt an, ob sie neu geladen werden können. Wenn Situationen verhindern, dass die Dateien bearbeitet werden kann, wird die `IVsQueryEditQuerySave2::QueryEditFiles` Methode teilt dem aufrufende Programm die Bearbeitung abgebrochen. Es ist auch möglich, dass der Aufrufer einen Aufruf-Modus angeben. Im Modus "silent" akzeptiert diese Methode die Aktion nur dann, wenn es nicht führt, dass keine Benutzeroberfläche angezeigt werden. Wenn Benutzeroberfläche unvermeidlich ist, muss ein Flag zurückgegeben werden, um das Problem hinweisen.  
  
 Die Methode verhält sich auf transaktionale Weise fehl. Wenn für eine einzelne Datei die Bearbeitung abgebrochen wird, wird die Bearbeitung, also für alle Dateien abgebrochen. Wenn die Bearbeitung zulässig ist, ist es hingegen für alle Dateien zulässig. Wenn diese Methode ermöglicht das Bearbeiten sich einmal für einen angegebenen Satz von Dateien, muss es immer möglich, bei nachfolgenden Aufrufen für den gleichen Satz von Dateien bearbeiten. Die zulassen-Edit-Schleife wird fortgesetzt, bis die Dateien geschlossen, gespeichert und erneut geladen werden; bis die Attribute (Eigenschaften) ändern; oder bis das Quellcodeverwaltungspaket geändert wird. Fälle berücksichtigt bei der Implementierung der `IVsQueryEditQuerySave2::QueryEditFiles` Methode Gerätedateien, die mehrere Dateien enthalten, brechen Sie vom Benutzer, und bearbeiten im Speicher.  
  
### <a name="querysavefiles-method"></a>QuerySaveFiles-Methode  
 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> wird aufgerufen, wenn es sich bei jedem Projekt oder ein Editor einen Satz von Dateien zu speichern muss. Wenn aufgerufen, die `IVsQueryEditQuerySave2::QuerySaveFiles` Methode überprüft, wenn die angegebenen Dateien schreibgeschützt sind, und ob sie sich unter quellcodeverwaltung sind. Wenn die Dateien werden ausgecheckt müssen, wird der Aufruf an das Quellcodeverwaltungspaket delegiert. Wenn die Bedingungen verhindert, dass die Dateien gespeichert, die `IVsQueryEditQuerySave2::QuerySaveFiles` Methode muss Teilen Sie den Editor, um den Speichervorgang abzubrechen. Wie bei der `IVsQueryEditQuerySave2::QueryEditFiles` -Methode, es ist möglich, dass der Aufrufer einen Aufruf-Modus angeben. Im Modus "silent" akzeptiert diese Methode die Aktion nur dann, wenn es nicht führt, dass keine Benutzeroberfläche angezeigt werden. Wenn Benutzeroberfläche unvermeidlich ist, muss ein Flag zurückgegeben werden, um das Problem hinweisen.  
  
 Diese Methode muss auf transaktionale Weise Verhalten. Wenn der Speichervorgang für eine einzelne Datei abgebrochen wird, wird der Speichervorgang, also für alle Dateien abgebrochen. Im Gegensatz dazu, wenn der Speichervorgang zulässig ist, müssen sie für alle Dateien zugelassen werden. Wie bei der `IVsQueryEditQuerySave2::QueryEditFiles` -Methode, die Fälle berücksichtigt bei der Implementierung der `IVsQueryEditQuerySave2::QuerySaveFiles` Methode Gerätedateien, die mehrere Dateien enthalten, brechen Sie vom Benutzer, und bearbeiten im Speicher.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>


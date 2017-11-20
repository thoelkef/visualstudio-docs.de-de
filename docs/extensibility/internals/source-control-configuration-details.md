---
title: Source Control Konfigurationsdetails | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 17e14d4f8d3d62297ae1d2f3e62a9ed0574fef9f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="source-control-configuration-details"></a>Konfigurationsdetails für Datenquellen-Steuerelement
Um die Datenquellen-Steuerelement zu implementieren, müssen Sie Ihrem Projektsystem oder -Editor Folgendes ordnungsgemäß zu konfigurieren:  
  
-   Eine Berechtigung für den Übergang in den geänderten Zustand anfordern  
  
-   Anfordern von Berechtigungen zum Speichern einer Datei  
  
-   Fordern Sie über die Berechtigung zum Hinzufügen, entfernen oder Umbenennen von Dateien im Projekt  
  
## <a name="request-permission-to-transition-to-changed-state"></a>Eine Berechtigung für den Übergang in den geänderten Zustand anfordern  
 Ein Projekt oder eine Editor muss eine Berechtigung anfordern, für den Übergang in den geänderten (dirty) Zustand durch Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>. Die einzelnen Editoren, die implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> müssen Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> und Genehmigung, um das Dokument aus der Umgebung vor der Rückgabe ändern `True` für `M:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty(System.Int32@)`. Ein Projekt ist im Wesentlichen ein Editor für eine Projektdatei, und daher hat die gleiche Verantwortung für die Implementierung geändert-Status-Überwachung für die Projektdatei aus, wie in ein Text-Editor für die Dateien. Die Umgebung behandelt den geänderten Zustand der Lösung, jedoch müssen Sie den geänderten Zustand eines beliebigen Objekts aus die Projektmappe verweist jedoch nicht gespeichert, z. B. einer Projektdatei oder dessen Elemente behandeln. Im Allgemeinen, wenn das Projekt oder die-Editor für die Verwaltung von Persistenz für ein Element zuständig ist, ist es für die Implementierung geändert Zustand Tracking verantwortlich.  
  
 Als Antwort auf die `IVsQueryEditQuerySave2::QueryEditFiles` aufrufen, die Umgebung folgende Möglichkeiten:  
  
-   Lehnen Sie den Aufruf zu ändern, in dem Fall die-Editor oder das Projekt (bereinigt) unverändert bleiben muss.  
  
-   Geben Sie an, dass die Daten neu geladen werden soll. Die Umgebung wird für ein Projekt das die Daten für das Projekt neu. Ein Editor muss laden die Daten vom Datenträger über seine <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> Implementierung. In beiden Fällen können den Kontext im Projekt oder -Editor ändern, wenn die Daten geladen werden.  
  
 Es ist eine komplex und schwierig Aufgabe geeignete überarbeiten `IVsQueryEditQuerySave2::QueryEditFiles` Aufrufe auf eine vorhandene Codebasis. Daher sollte diese Aufrufe während der Erstellung des Projekts oder -Editor integriert werden.  
  
## <a name="request-permission-to-save-a-file"></a>Anfordern von Berechtigungen zum Speichern einer Datei  
 Bevor ein Projekt oder -Editor eine Datei gespeichert wird, rufen sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>. Projektdateien sind diese Aufrufe automatisch von der Lösung abgeschlossen weiß, wann eine Projektdatei zu speichern. Editoren sind dafür verantwortlich, dass diese Aufrufe, es sei denn, die Implementierung des `IVsPersistDocData2` verwendet die Hilfsfunktion <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>. Wenn der Editor implementiert `IVsPersistDocData2` in auf diese Weise, und klicken Sie dann auf den Aufruf von `IVsQueryEditQuerySave2::QuerySaveFile` oder `IVsQueryEditQuerySave2::QuerySaveFiles` für Sie vorgenommen wird.  
  
> [!NOTE]
>  Stellen Sie diese Aufrufe immer präemptiv – d. h. zu einem Zeitpunkt, wenn der Editor ist ein "Abbrechen" empfangen.  
  
## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Fordern Sie über die Berechtigung zum Hinzufügen, entfernen oder Umbenennen von Dateien im Projekt  
 Bevor ein Projekt hinzufügen, umbenennen oder einer Datei oder eines Verzeichnisses entfernen kann, müssen die entsprechenden Aufrufen `IVsTrackProjectDocuments2::OnQuery*` Anfrageberechtigungen aufzurufende Methode aus der Umgebung. Wenn die Berechtigung wird erteilt, das Projekt muss der Vorgang abgeschlossen und rufen Sie die entsprechende `IVsTrackProjectDocuments2::OnAfter*` Methode, um der Umgebung zu benachrichtigen, dass der Vorgang abgeschlossen ist. Das Projekt muss rufen Sie die Methoden von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> Schnittstelle für alle Dateien (z. B. spezielle Dateien) und nicht nur die übergeordneten-Dateien. Datei-Aufrufe sind obligatorisch, aber Directory Aufrufe sind optional. Wenn das Projekt umfasst Verzeichnisinformationen, sollten Sie den entsprechenden Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> Methoden, aber wenn er verfügt nicht über diese Informationen, und klicken Sie dann die Umgebung wird Verzeichnisinformationen abzuleiten.  
  
 Das Projekt sollte nicht die Methoden der Aufrufen `IVsTrackProjectDocuments2` am Projekt zu öffnen oder schließen. Listener, die diese Informationen beim Starten des sollen können, bis die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> Ereignis und durchlaufen Sie die Lösung für die Informationen zu ermitteln, sie benötigen. Beim Herunterfahren wird diese Informationen nicht benötigt. `IVsTrackProjectDocuments2`wird bereitgestellt, aus der <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>.  
  
 Für jede hinzufügen, umbenennen und die Aktion zum Entfernen, es ist ein `OnQuery*` Methode und eine `OnAfter*` Methode. Rufen Sie die `OnQuery*` Methode über die Berechtigung zum Hinzufügen, um Unterstützung bitten, umbenennen oder entfernen Sie die Datei oder das Verzeichnis. Rufen Sie die `OnAfter*` -Methode auf, nachdem die Datei oder das Verzeichnis wurde hinzugefügt, umbenannt, oder entfernt und des Projektzustands den neuen Status zeigt.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>   
 [Unterstützen der Quellcodeverwaltung](../../extensibility/internals/supporting-source-control.md)
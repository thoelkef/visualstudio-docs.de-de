---
title: Konfigurationsdetails für die Datenquelle | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 51fac40d0bffe570ac1f374872fb4572c1c83441
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60109464"
---
# <a name="source-control-configuration-details"></a>Konfigurationsdetails für die Quellcodeverwaltung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Um die Datenquellen-Steuerelement zu implementieren, müssen Sie zum ordnungsgemäßen Konfigurieren von Ihrem Projektsystem oder Editor, um die folgenden Schritte ausführen:  
  
- Berechtigung zum Übergang in den geänderten Zustand anfordern  
  
- Berechtigung zum Speichern einer Datei  
  
- Fordern Sie über die Berechtigung zum Hinzufügen, entfernen oder Umbenennen von Dateien im Projekt  
  
## <a name="request-permission-to-transition-to-changed-state"></a>Berechtigung zum Übergang in den geänderten Zustand anfordern  
 Ein Projekt oder eine Editor muss über die Berechtigung zum Übergang in den Zustand der geänderten (geändert) anfordern, indem er <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>. Jede-Editor, der implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> müssen Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> und Genehmigung zum Wechseln des Dokuments aus der Umgebung vor der Rückgabe `True` für `M:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty(System.Int32@)`. Ein Projekt ist im Wesentlichen ein Editor für eine Projektdatei, und daher hat die gleiche Verantwortung für die Implementierung geändert-statusüberwachung für die Projektdatei aus, wie in ein Text-Editor für die Dateien. Die Umgebung verarbeitet den geänderten Zustand der Lösung, jedoch müssen Sie den geänderten Zustand eines Objekts die Projektmappe verweist, jedoch nicht gespeichert, z. B. einer Projektdatei oder seiner Elemente behandeln. Im Allgemeinen, wenn Ihrem Projekt oder den Editor zum Verwalten der Persistenz für ein Element verantwortlich ist, ist dann verantwortlich für die Implementierung geändert-statusüberwachung.  
  
 Als Reaktion auf die `IVsQueryEditQuerySave2::QueryEditFiles` aufrufen, die Umgebung folgende Möglichkeiten:  
  
- Ändern Sie den Aufruf zurückweisen, in diesem Fall den Editor oder Projekt (bereinigen) unverändert bleiben muss.  
  
- Geben Sie an, dass die Dokumentendaten erneut geladen werden soll. Für ein Projekt wird in die Umgebung die Daten für das Projekt neu geladen. Ein Editor muss erneut laden, die Daten vom Datenträger über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> Implementierung. In beiden Fällen kann im Kontext des Projekts oder -Editor ändern, wenn die Daten erneut geladen werden.  
  
  Es ist eine komplex und schwierig Aufgabe geeignete überarbeiten `IVsQueryEditQuerySave2::QueryEditFiles` Anrufe an eine bereits vorhandene Codebasis. Daher sollte diese Aufrufe während der Erstellung des Projekts oder der-Editor integriert werden.  
  
## <a name="request-permission-to-save-a-file"></a>Berechtigung zum Speichern einer Datei  
 Bevor ein Projekt oder der Editor eine Datei gespeichert wird, muss er Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>. Für Projektdateien werden diese Aufrufe automatisch von der Lösung durchgeführt, die weiß, wann eine Projektdatei zu speichern. Editoren sind dafür verantwortlich, dass diese Aufrufe, es sei denn, die Implementierung von `IVsPersistDocData2` verwendet die Hilfsfunktion <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>. Wenn Ihr Editor implementiert `IVsPersistDocData2` in auf diese Weise, und klicken Sie dann auf den Aufruf von `IVsQueryEditQuerySave2::QuerySaveFile` oder `IVsQueryEditQuerySave2::QuerySaveFiles` für Sie vorgenommen wird.  
  
> [!NOTE]
>  Stellen Sie diese Aufrufe immer präemptiv, d. h. zu einem Zeitpunkt, wenn der Editor ist einen Abbruch zu empfangen.  
  
## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Fordern Sie über die Berechtigung zum Hinzufügen, entfernen oder Umbenennen von Dateien im Projekt  
 Bevor ein Projekt hinzufügen, umbenennen oder einer Datei oder eines Verzeichnisses entfernen kann, müssen die entsprechenden Aufrufen `IVsTrackProjectDocuments2::OnQuery*` Methode um eine Berechtigung aus der Umgebung. Wenn die Berechtigung erteilt, und klicken Sie dann das Projekt muss der Vorgang abgeschlossen und rufen Sie dann auf die entsprechende `IVsTrackProjectDocuments2::OnAfter*` Methode, um der Umgebung zu benachrichtigen, dass der Vorgang abgeschlossen ist. Das Projekt muss Aufrufen der Methoden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> Schnittstelle für alle Dateien (z. B. spezielle Dateien) und nicht nur die übergeordneten-Dateien. Datei-Aufrufe sind obligatorisch, aber Directory-Aufrufe sind optional. Wenn Ihr Projekt Verzeichnisinformationen, sollten Sie den entsprechenden Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> Methoden, aber wenn keine dieser Informationen, und klicken Sie dann die Umgebung Verzeichnisinformationen folgert.  
  
 Das Projekt sollte nicht die Methoden der Aufrufen `IVsTrackProjectDocuments2` am Projekt zu öffnen oder schließen. Listener, die diese Informationen beim Starten können, bis die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> Ereignis und durchlaufen Sie die Lösung für die Informationen zu finden, sie benötigen. Beim Herunterfahren wird diese Informationen nicht benötigt. `IVsTrackProjectDocuments2` wird bereitgestellt, aus der <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>.  
  
 Für jede hinzufügen, umbenennen und eine Aktion zum Entfernen, ist ein `OnQuery*` Methode und eine `OnAfter*` Methode. Rufen Sie die `OnQuery*` Methode, um Fragen über die Berechtigung zum Hinzufügen, umbenennen oder entfernen Sie die Datei oder das Verzeichnis. Rufen Sie die `OnAfter*` -Methode auf, nachdem die Datei oder das Verzeichnis verfügt über wurde hinzugefügt, umbenannt oder entfernt und der Zustand des Projekts den neuen Status zeigt.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>   
 [Unterstützen der Quellcodeverwaltung](../../extensibility/internals/supporting-source-control.md)

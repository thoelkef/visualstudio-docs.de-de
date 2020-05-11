---
title: Details zur Quellcodeverwaltung - Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7cf4a5c55e8093e5dcd6406cde1c60f642188495
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705294"
---
# <a name="source-control-configuration-details"></a>Konfigurationsdetails für die Quellcodeverwaltung
Um die Quellcodeverwaltung zu implementieren, müssen Sie Ihr Projektsystem oder den Editor ordnungsgemäß konfigurieren, um Folgendes zu tun:

- Permission zum Übergang in den geänderten Zustand anfordern

- Permission zum Speichern einer Datei anfordern

- Permission zum Hinzufügen, Entfernen oder Umbenennen von Dateien im Projekt anfordern

## <a name="request-permission-to-transition-to-changed-state"></a>Permission zum Übergang in den geänderten Zustand anfordern
 Ein Projekt oder Editor muss die Berechtigung zum Übergang <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>in den geänderten (schmutzigen) Zustand durch Aufrufen anfordern. Jeder Editor, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> der <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> implementiert, muss die Genehmigung aufrufen und `True` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A>erhalten, um das Dokument aus der Umgebung zu ändern, bevor er für zurückkehrt. Ein Projekt ist im Wesentlichen ein Editor für eine Projektdatei und hat daher die gleiche Verantwortung für die Implementierung der Änderungsstatusverfolgung für die Projektdatei wie ein Texteditor für seine Dateien. Die Umgebung behandelt den geänderten Status der Projektmappe, aber Sie müssen den geänderten Status eines Objekts behandeln, auf das die Projektmappe verweist, aber nicht gespeichert wird, z. B. eine Projektdatei oder deren Elemente. Wenn Ihr Projekt oder Editor für die Verwaltung der Persistenz für ein Element verantwortlich ist, ist es im Allgemeinen für die Implementierung der Nachverfolgung des geänderten Status verantwortlich.

 Als Reaktion `IVsQueryEditQuerySave2::QueryEditFiles` auf den Aufruf kann die Umgebung Folgendes tun:

- Lehnen Sie den Aufruf zur Änderung ab, in diesem Fall muss der Editor oder das Projekt im unveränderten (sauberen) Zustand verbleiben.

- Geben Sie an, dass die Dokumentdaten neu geladen werden sollen. Bei einem Projekt lädt die Umgebung die Daten für das Projekt neu. Ein Editor muss die Daten über <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> seine Implementierung vom Datenträger neu laden. In beiden Fällen kann sich der Kontext im Projekt oder Editor ändern, wenn die Daten neu geladen werden.

  Es ist eine komplexe und schwierige `IVsQueryEditQuerySave2::QueryEditFiles` Aufgabe, entsprechende Aufrufe auf eine vorhandene Codebasis nachzurüsten. Daher sollten diese Aufrufe während der Erstellung des Projekts oder Editors integriert werden.

## <a name="request-permission-to-save-a-file"></a>Permission zum Speichern einer Datei anfordern
 Bevor ein Projekt oder Editor eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> Datei <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>speichert, muss es aufrufen oder . Bei Projektdateien werden diese Aufrufe automatisch von der Projektmappe abgeschlossen, die weiß, wann eine Projektdatei gespeichert werden soll. Die Redakteure sind für diese Aufrufe `IVsPersistDocData2` verantwortlich, es <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>sei denn, die Editor-Implementierung von verwendet die Hilfsfunktion . Wenn Ihr Editor `IVsPersistDocData2` auf diese Weise implementiert `IVsQueryEditQuerySave2::QuerySaveFile` `IVsQueryEditQuerySave2::QuerySaveFiles` wird, dann wird der Aufruf an oder für Sie gemacht.

> [!NOTE]
> Führen Sie diese Anrufe immer präventiv aus, d. h. zu einem Zeitpunkt, zu dem Ihr Editor einen Abbruch erhalten kann.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Permission zum Hinzufügen, Entfernen oder Umbenennen von Dateien im Projekt anfordern
 Bevor ein Projekt eine Datei oder ein Verzeichnis hinzufügen, umbenennen `IVsTrackProjectDocuments2::OnQuery*` oder entfernen kann, muss es die entsprechende Methode aufrufen, um die Berechtigung von der Umgebung anzufordern. Wenn die Berechtigung erteilt wird, muss das Projekt `IVsTrackProjectDocuments2::OnAfter*` den Vorgang abschließen und dann die entsprechende Methode aufrufen, um die Umgebung zu benachrichtigen, dass der Vorgang abgeschlossen ist. Das Projekt muss die <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> Methoden der Schnittstelle für alle Dateien (z. B. spezielle Dateien) aufrufen und nicht nur die übergeordneten Dateien. Dateiaufrufe sind obligatorisch, Verzeichnisaufrufe sind jedoch optional. Wenn Das Projekt über Verzeichnisinformationen verfügt, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> sollte es die entsprechenden Methoden aufrufen, aber wenn es nicht über diese Informationen verfügt, leitet die Umgebung Verzeichnisinformationen ab.

 Das Projekt sollte die `IVsTrackProjectDocuments2` Methoden des Projekts nicht als offen oder schließend aufrufen. Listener, die diese Informationen beim <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> Start wünschen, können auf das Ereignis warten und die Lösung durchlaufen, um die benötigten Informationen zu finden. Beim Herunterfahren werden diese Informationen nicht benötigt. `IVsTrackProjectDocuments2`wird von <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>der bereitgestellt.

 Für jedes Hinzufügen, Umbenennen und Entfernen `OnQuery*` von Aktionen `OnAfter*` gibt es eine Methode und eine Methode. Rufen `OnQuery*` Sie die Methode auf, um die Berechtigung zum Hinzufügen, Umbenennen oder Entfernen der Datei oder des Verzeichnisses zu erfragen. Rufen `OnAfter*` Sie die Methode auf, nachdem die Datei oder das Verzeichnis hinzugefügt, umbenannt oder entfernt wurde, und der Projektstatus spiegelt den neuen Status wider.

## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Unterstützen der Quellcodeverwaltung](../../extensibility/internals/supporting-source-control.md)

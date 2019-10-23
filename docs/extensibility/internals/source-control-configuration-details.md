---
title: Details zur Konfiguration der Quell Code Verwaltung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], configuration details
ms.assetid: adbee9fc-7a2e-4abe-a3b8-e6615bcd797f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a6c51dfe4ad9378af04da61dbd7e9011c4678f1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723793"
---
# <a name="source-control-configuration-details"></a>Konfigurationsdetails für die Quellcodeverwaltung
Um die Quell Code Verwaltung zu implementieren, müssen Sie das Projekt System oder den Editor ordnungsgemäß für folgende Aufgaben konfigurieren:

- Anfordern der Berechtigung für den Übergang in den geänderten Zustand

- Anfordern der Berechtigung zum Speichern einer Datei

- Anfordern der Berechtigung zum Hinzufügen, entfernen oder Umbenennen von Dateien im Projekt

## <a name="request-permission-to-transition-to-changed-state"></a>Anfordern der Berechtigung für den Übergang in den geänderten Zustand
 Ein Projekt oder Editor muss die Berechtigung zum Übergang in den geänderten Zustand (geändert) anfordern, indem <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> aufgerufen wird. Jeder Editor, der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> implementiert, muss <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> anrufen und die Genehmigung erhalten, das Dokument aus der Umgebung zu ändern, bevor `True` für <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData.IsDocDataDirty%2A> zurückgegeben werden. Bei einem Projekt handelt es sich im Wesentlichen um einen Editor für eine Projektdatei. Daher ist die gleiche Verantwortung für die Implementierung der Änderungs Zustandsüberwachung für die Projektdatei, wie ein Text-Editor für die Dateien. Die Umgebung verarbeitet den geänderten Zustand der Projekt Mappe, aber Sie müssen den geänderten Status aller Objekte, die die Projekt Mappe referenziert, aber nicht speichert, wie z. b. eine Projektdatei oder deren Elemente, verarbeiten. Wenn das Projekt oder der Editor für die Verwaltung der Persistenz eines Elements zuständig ist, ist es im Allgemeinen für die Implementierung der Änderungs Zustandsüberwachung verantwortlich.

 Als Reaktion auf den `IVsQueryEditQuerySave2::QueryEditFiles`-Befehl kann die Umgebung folgende Aktionen ausführen:

- Ablehnen Sie den aufzurufenden Änderungs Wechsel. in diesem Fall muss der Editor oder das Projekt im unveränderten Zustand bleiben.

- Geben Sie an, dass die Dokument Daten neu geladen werden sollen. Bei einem Projekt lädt die Umgebung die Daten für das Projekt neu. Ein Editor muss die Daten vom Datenträger über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> Implementierung neu laden. In beiden Fällen kann sich der Kontext im Projekt oder im Editor ändern, wenn die Daten erneut geladen werden.

  Es ist eine komplexe und schwierige Aufgabe, geeignete `IVsQueryEditQuerySave2::QueryEditFiles` Aufrufe an eine vorhandene Codebasis zu über. Daher sollten diese Aufrufe während der Erstellung des Projekts oder Editors integriert werden.

## <a name="request-permission-to-save-a-file"></a>Anfordern der Berechtigung zum Speichern einer Datei
 Bevor ein Projekt oder Editor eine Datei speichert, muss <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> aufgerufen werden. Bei Projektdateien werden diese Aufrufe automatisch von der Projekt Mappe abgeschlossen, die weiß, wann eine Projektdatei gespeichert werden soll. Editoren sind für diese Aufrufe zuständig, es sei denn, die Editor-Implementierung von `IVsPersistDocData2` verwendet die Hilfsfunktion <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>. Wenn Ihr Editor `IVsPersistDocData2` auf diese Weise implementiert, wird der `IVsQueryEditQuerySave2::QuerySaveFile` oder `IVsQueryEditQuerySave2::QuerySaveFiles` aufgerufen.

> [!NOTE]
> Nehmen Sie diese Aufrufe immer vorzeitig an – d. h., wenn der Editor in der Lage ist, einen Abbruch zu empfangen.

## <a name="request-permission-to-add-remove-or-rename-files-in-the-project"></a>Anfordern der Berechtigung zum Hinzufügen, entfernen oder Umbenennen von Dateien im Projekt
 Bevor ein Projekt eine Datei oder ein Verzeichnis hinzufügen, umbenennen oder entfernen kann, muss die entsprechende `IVsTrackProjectDocuments2::OnQuery*` Methode aufgerufen werden, um die Berechtigung aus der Umgebung anzufordern. Wenn die Berechtigung erteilt wird, muss das Projekt den Vorgang beenden und dann die entsprechende `IVsTrackProjectDocuments2::OnAfter*`-Methode aufzurufen, um die Umgebung zu benachrichtigen, dass der Vorgang beendet ist. Das Projekt muss die Methoden der <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>-Schnittstelle für alle Dateien (z. b. spezielle Dateien) und nicht nur für die übergeordneten Dateien aufzurufen. Datei Aufrufe sind obligatorisch, aber Verzeichnis Aufrufe sind optional. Wenn Ihr Projekt über Verzeichnisinformationen verfügt, sollten Sie die entsprechenden <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> Methoden aufzurufen. wenn diese Informationen jedoch nicht vorhanden sind, werden die Verzeichnisinformationen von der Umgebung abgeleitet.

 Das Projekt sollte die Methoden von `IVsTrackProjectDocuments2` beim Öffnen oder Schließen des Projekts nicht aufzurufen. Listener, die diese Informationen beim Start wünschen, können auf das <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenSolution%2A> Ereignis warten und die Lösung durchlaufen, um die benötigten Informationen zu finden. Beim Herunterfahren sind diese Informationen nicht erforderlich. `IVsTrackProjectDocuments2` wird vom <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> bereitgestellt.

 Für jede Aktion zum Hinzufügen, umbenennen und entfernen gibt es eine `OnQuery*`-Methode und eine `OnAfter*`-Methode. Ruft die `OnQuery*`-Methode auf, um die Berechtigung zum Hinzufügen, umbenennen oder Entfernen der Datei oder des Verzeichnisses anzufordern. Ruft die `OnAfter*`-Methode auf, nachdem die Datei oder das Verzeichnis hinzugefügt, umbenannt oder entfernt wurde und der Projektzustand den neuen Zustand widerspiegelt.

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SaveDocDataToFile%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>
- [Unterstützen der Quellcodeverwaltung](../../extensibility/internals/supporting-source-control.md)
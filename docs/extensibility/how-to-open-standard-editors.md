---
title: 'Vorgehensweise: Öffnen Sie die Standard-Editoren | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f34a239628c3ed9e8bccaa8590cb22100d7d290f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60042435"
---
# <a name="how-to-open-standard-editors"></a>Vorgehensweise: Open-standard-Editoren
Wenn Sie einen standard-Editor öffnen, können Sie die IDE einen standard-Editor für einen angegebenen Dateityp, anstatt einen projektspezifischen Editor für die Datei zu bestimmen.

 Das folgende Verfahren zum Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> Methode. Dadurch wird eine Projektdatei in einem standard-Editor geöffnet.

## <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>So implementieren Sie die OpenItem-Methode mit einem standard-editor

1. Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> (`RDT_EditLock`) zu bestimmen, ob die Datendatei Objekt das Dokument bereits geöffnet ist.

2. Wenn die Datei bereits geöffnet ist, diesem die Datei durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> Methode, die Angabe des Werts `IDO_ActivateIfOpen` für die `grfIDO` Parameter.

     Wenn die Datei geöffnet ist, und das Dokument ist im Besitz eines anderen Projekts als des aufrufenden Projekts, erhält das Projekt eine Warnung, die der Editor geöffnet wird aus einem anderen Projekt ist. Fenster "Datei" wird dann angezeigt.

3. Wenn das Dokument nicht geöffnet ist oder nicht in der Tabelle aktiver Dokumente vorhanden ist, rufen die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode (`OSE_ChooseBestStdEditor`) zu einen standard-Editor für die Datei zu öffnen.

     Wenn Sie die Methode aufrufen, führt die IDE die folgenden Aufgaben aus:

    1. Die IDE überprüft die Editoren / {GuidEditorType} / Unterschlüssel in der Registrierung, um zu bestimmen, welcher Editor Extensions kann die Datei öffnen, und hat die höchste Priorität, um dieses Ziel erreichen.

    2. Nachdem die IDE ermittelt hat, welcher Editor die Datei öffnen kann, ruft die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>. Die Anmerkung der Redaktion Implementierung dieser Methode Informationen zurückgegeben, die für die IDE aufgerufen werden muss <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> und das neu geöffnete Dokument.

    3. Zum Schluss die IDE, lädt das Dokument mithilfe der üblichen beibehaltungsschnittstelle, wie z. B. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>.

    4. Wenn die IDE zuvor erkannt wurde, dass die Hierarchie oder das hierarchienelement verfügbar ist, ruft die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> Methode auf das Projekt für ein Projekt auf Dokumentebene Kontext <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> Zeiger auf das erneute übergeben die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> Methodenaufruf.

4. Zurückgeben einer <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> Zeiger auf die IDE, wenn die IDE aufruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> auf Ihr Projekt aus, wenn Sie die Editor-Get-Kontext aus Ihrem Projekt informieren möchten.

     Durch diesen Schritt können zusätzliche Dienste die Projekt-Angebot in den Editor.

     Wenn die Dokumentenansicht oder dokumentenansichtsobjekt erfolgreich im Rahmen eines Fenster platziert wurde, wird das Objekt mit den Daten durch den Aufruf initialisiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>.

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Öffnen und Speichern von Projektelementen](../extensibility/internals/opening-and-saving-project-items.md)
- [Vorgehensweise: Öffnen von projektspezifischen Editoren](../extensibility/how-to-open-project-specific-editors.md)
- [Vorgehensweise: Öffnen von Editoren für geöffnete Dokumente](../extensibility/how-to-open-editors-for-open-documents.md)
- [Anzeigen von Dateien mithilfe des Befehls Öffnen von Dateien](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
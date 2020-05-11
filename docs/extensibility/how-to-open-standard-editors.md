---
title: 'Gewusst wie: Öffnen von Standard-Editoren | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f42cfa64106acc41358568f4c8f6bca2cd1141fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710792"
---
# <a name="how-to-open-standard-editors"></a>Gewusst wie: Öffnen von Standard-Editoren
Wenn Sie einen Standard-Editor öffnen, lassen Sie die IDE einen Standard-Editor für einen bestimmten Dateityp bestimmen, anstatt einen projektspezifischen Editor für die Datei anzugeben.

 Führen Sie das folgende <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> Verfahren aus, um die Methode zu implementieren. Dadurch wird eine Projektdatei in einem Standardeditor geöffnet.

## <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>So implementieren Sie die OpenItem-Methode mit einem Standard-Editor

1. Rufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> `RDT_EditLock`Sie auf ( ), um zu ermitteln, ob die Dokumentdatenobjektdatei bereits geöffnet ist.

2. Wenn die Datei bereits geöffnet ist, tauchen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> Sie die Datei `IDO_ActivateIfOpen` erneut `grfIDO` auf, indem Sie die Methode aufrufen und einen Wert von für den Parameter angeben.

     Wenn die Datei geöffnet ist und das Dokument einem anderen Projekt als dem aufrufenden Projekt gehört, erhält das Projekt eine Warnung, dass der geöffnete Editor von einem anderen Projekt stammt. Das Dateifenster wird dann angezeigt.

3. Wenn das Dokument in der laufenden Dokumenttabelle nicht <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> oder`OSE_ChooseBestStdEditor`nicht geöffnet ist, rufen Sie die Methode ( ) auf, um einen Standardeditor für die Datei zu öffnen.

     Wenn Sie die Methode aufrufen, führt die IDE die folgenden Aufgaben aus:

    1. Die IDE scannt den Unterschlüssel Editors/-guidEditorType/Extensions in der Registrierung, um zu ermitteln, welcher Editor die Datei öffnen kann und die höchste Priorität dafür hat.

    2. Nachdem die IDE bestimmt hat, welcher Editor <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>die Datei öffnen kann, ruft die IDE auf. Die Implementierung dieser Methode durch den Editor gibt Informationen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> zurück, die erforderlich sind, damit die IDE das neu geöffnete Dokument aufrufen und veranlassen kann.

    3. Schließlich lädt die IDE das Dokument mithilfe der üblichen <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>Persistenzschnittstelle, z. B. .

    4. Wenn die IDE zuvor festgestellt hat, dass das Hierarchie- oder Hierarchieelement verfügbar ist, ruft die IDE die IDE-Aufrufmethode <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> für das Projekt auf, um einen Kontextzeiger <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> auf Projektebene abzurufen, der mit dem <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> Methodenaufruf zurückreicht.

4. Geben <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> Sie einen Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> IDE zurück, wenn die IDE Ihr Projekt aufruft, wenn Sie dem Editor den Kontext aus Ihrem Projekt abrufen lassen möchten.

     Durch ausführen dieses Schritts kann das Projekt dem Editor zusätzliche Dienste anbieten.

     Wenn das Dokumentansichts- oder Dokumentansichtsobjekt erfolgreich in einem Fensterrahmen erstellt <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>wurde, wird das Objekt mit seinen Daten initialisiert, indem es aufgerufen wird.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Öffnen und Speichern von Projektelementen](../extensibility/internals/opening-and-saving-project-items.md)
- [Gewusst wie: Öffnen sie projektspezifische Editoren](../extensibility/how-to-open-project-specific-editors.md)
- [Gewusst wie: Öffnen von Editoren für geöffnete Dokumente](../extensibility/how-to-open-editors-for-open-documents.md)
- [Anzeigen von Dateien mithilfe des Befehls Datei öffnen](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)

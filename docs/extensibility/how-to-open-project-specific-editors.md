---
title: 'Gewusst wie: Öffnen Sie projektspezifische Editoren | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3cb6e360a38d64de4976f83b0167d47dc03fbc87
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710844"
---
# <a name="how-to-open-project-specific-editors"></a>Gewusst wie: Öffnen sie projektspezifische Editoren
Wenn eine Elementdatei, die von einem Projekt geöffnet wird, untrennbar mit dem jeweiligen Editor für dieses Projekt verbunden ist, muss das Projekt die Datei mithilfe eines projektspezifischen Editors öffnen. Die Datei kann nicht an den IDE-Mechanismus zum Auswählen eines Editors delegiert werden. Anstatt beispielsweise einen Standard-Bitmap-Editor zu verwenden, können Sie diese projektspezifische Editor-Option verwenden, um einen bestimmten Bitmap-Editor anzugeben, der Informationen in der Datei erkennt, die für Ihr Projekt eindeutig sind.

 Die IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> ruft die Methode auf, wenn sie feststellt, dass eine Datei von einem bestimmten Projekt geöffnet werden soll. Weitere Informationen finden Sie unter [Anzeigen von Dateien mithilfe des Befehls Datei öffnen](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Verwenden Sie die folgenden `OpenItem` Richtlinien, um die Methode zu implementieren, mit der das Projekt eine Datei mithilfe eines projektspezifischen Editors öffnet.

## <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>So implementieren Sie die OpenItem-Methode mit einem projektspezifischen Editor

1. Rufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> Sie`RDT_EditLock`die Methode ( ) auf, um zu bestimmen, ob die Datei (Dokumentdatenobjekt) bereits geöffnet ist.

    > [!NOTE]
    > Weitere Informationen zu Dokumentdaten und Dokumentansichtsobjekten finden Sie unter [Dokumentdaten und Dokumentansicht in benutzerdefinierten Editoren](../extensibility/document-data-and-document-view-in-custom-editors.md).

2. Wenn die Datei bereits geöffnet ist, tauchen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> Sie die Datei erneut auf, indem Sie die Methode aufrufen und den Wert IDO_ActivateIfOpen für den `grfIDO` Parameter angeben.

     Wenn die Datei geöffnet ist und das Dokument im Besitz eines anderen Projekts als dem aufrufenden Projekt ist, wird dem Benutzer eine Warnung angezeigt, dass der geöffnete Editor aus einem anderen Projekt stammt. Das Dateifenster wird dann angezeigt.

3. Wenn Ihr Textpuffer (Dokumentdatenobjekt) bereits geöffnet ist und Sie ihm eine andere Ansicht anfügen möchten, sind Sie für das Verbinden dieser Ansicht verantwortlich. Der empfohlene Ansatz zum Instanziieren einer Ansicht (Dokumentansichtsobjekt) aus dem Projekt lautet wie folgt:

    1. Rufen `QueryService` Sie <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> den Dienst auf, <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> um einen Zeiger auf die Schnittstelle zu erhalten.

    2. Rufen <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> Sie die Methode zum Erstellen einer Instanz der Dokumentansichtsklasse auf.

4. Rufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> Sie die Methode auf und geben Sie ihr Dokumentansichtsobjekt an.

     Diese Methode verortet das Dokumentansichtsobjekt in einem Dokumentfenster.

5. Führen Sie die entsprechenden <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> Aufrufe <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> entweder der oder der Methoden aus.

     An diesem Punkt sollte die Ansicht vollständig initialisiert und geöffnet werden.

6. Rufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> Sie die Methode auf, um die Ansicht anzuzeigen und zu öffnen.

## <a name="see-also"></a>Weitere Informationen
- [Öffnen und Speichern von Projektelementen](../extensibility/internals/opening-and-saving-project-items.md)
- [Gewusst wie: Öffnen von Standard-Editoren](../extensibility/how-to-open-standard-editors.md)
- [Gewusst wie: Öffnen von Editoren für geöffnete Dokumente](../extensibility/how-to-open-editors-for-open-documents.md)

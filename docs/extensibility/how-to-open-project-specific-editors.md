---
title: 'Vorgehensweise: Öffnen von projektspezifischen Editoren | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8482f2704fe81482d95c2c8e73ae6e8c8ffd272d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63417134"
---
# <a name="how-to-open-project-specific-editors"></a>Vorgehensweise: Öffnen von projektspezifischen Editoren
Wenn eine Elementdatei, die von einem Projekt geöffnet wird systemintern auf den bestimmten Editor für das Projekt gebunden ist, muss das Projekt die Datei öffnen, mit einem projektspezifischen-Editor. Die Datei kann nicht auf den Mechanismus der IDE für das Auswählen eines Editors delegiert werden. Anstatt einen standard-Bitmap-Editor zu verwenden, können Sie z. B. diese projektspezifischer Editor-Option verwenden, an einem bestimmten Bitmap-Editor, der Informationen in der Datei, die dem Projekt eindeutig ist, erkennt.

 Die IDE-Aufrufe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> Methode, wenn er feststellt, dass eine Datei von einem bestimmten Projekt geöffnet werden soll. Weitere Informationen finden Sie unter [Anzeigen von Dateien mit den Befehl Open File](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Verwenden Sie die folgenden Richtlinien zum Implementieren der `OpenItem` Methode, um Ihr Projekt eine Datei mit einem projektspezifischen-Editor zu öffnen.

## <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>So implementieren Sie die OpenItem-Methode mit einem projektspezifischen editor

1. Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> Methode (`RDT_EditLock`) zu bestimmen, ob die Datei (dokumentdatenobjekt) bereits geöffnet ist.

    > [!NOTE]
    > Weitere Informationen zu Dokumentdaten und dokumentenansichtsobjekten finden Sie unter [Dokumentieren von Daten und das Dokument anzeigen, in benutzerdefinierten Editoren](../extensibility/document-data-and-document-view-in-custom-editors.md).

2. Wenn die Datei bereits geöffnet ist, diesem die Datei durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> -Methode und geben einen Wert von IDO_ActivateIfOpen für den `grfIDO` Parameter.

     Wenn die Datei geöffnet ist, und das Dokument von einem anderen Projekt als dem aufrufenden Projekt gehört, wird eine Warnung, die dem Benutzer angezeigt werden, die der Editor geöffnet wird aus einem anderen Projekt ist. Fenster "Datei" wird dann angezeigt.

3. Wenn Ihr Textpuffer (dokumentdatenobjekt) bereits geöffnet ist, und Sie eine andere Ansicht anfügen möchten, sind Sie verantwortlich für das Einbinden dieser Ansicht. Die empfohlene Vorgehensweise für das Instanziieren einer Ansicht (dokumentenansichtsobjekt) aus dem Projekt, lautet wie folgt aus:

    1. Rufen Sie `QueryService` auf die <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> Dienst um einen Zeiger auf die <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> Schnittstelle.

    2. Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> Methode, um eine Instanz der Ansichtsklasse Dokument zu erstellen.

4. Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> Methode, geben Sie Ihrem dokumentenansichtsobjekt.

     Diese Methode Standorte das dokumentenansichtsobjekt in einem Dokumentfenster angezeigt.

5. Führen Sie die entsprechenden Aufrufe an die <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> oder <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> Methoden.

     An diesem Punkt sollte die Ansicht vollständig initialisiert und bereit, die geöffnet werden.

6. Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> Methode zum Anzeigen und öffnen Sie die Ansicht.

## <a name="see-also"></a>Siehe auch
- [Öffnen und Speichern von Projektelementen](../extensibility/internals/opening-and-saving-project-items.md)
- [Vorgehensweise: Open-standard-Editoren](../extensibility/how-to-open-standard-editors.md)
- [Vorgehensweise: Öffnen von Editoren für geöffnete Dokumente](../extensibility/how-to-open-editors-for-open-documents.md)
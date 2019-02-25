---
title: Bestimmen, welcher Editor eine Datei in einem Projekt öffnet | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 13b39d52f574c90cf1a4ead8e47e7d24aac94708
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56627960"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>Bestimmen Sie, welcher Editor eine Datei in einem Projekt öffnet
Wenn ein Benutzer eine Datei in einem Projekt geöffnet wird, durchläuft die Umgebung einen Abruf-Prozess, und öffnen schließlich die geeigneten Editor oder Designer für diese Datei. Das erste Verfahren eingesetzt, die von der Umgebung ist für Standard- und benutzerdefinierte Editoren identisch. Die Umgebung verwendet eine Vielzahl von Kriterien aus, wenn der Editor zum Öffnen einer Datei abrufen und das VSPackage mit der Umgebung koordinieren muss, während dieses Vorgangs.

 Wählt z. B. wenn ein Benutzer die **öffnen** Befehl der **Datei** Menü und wählt dann *filename.rtf* (oder eine andere Datei mit einer *RTF*Erweiterung), die Umgebung Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Implementierung für jedes Projekt, und schließlich werden alle Instanzen von Project in der Lösung durchlaufen. Projekte zurückzugeben, einen Satz von Flags, die Ansprüche in einem Dokument nach Priorität zu identifizieren. Verwenden die höchste Priorität, die Umgebung Ruft die entsprechende <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> Methode. Weitere Informationen zu den Prozess abrufen, finden Sie unter [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md).

 Das Projekt verschiedene Dateien Ansprüche werden alle Dateien, die nicht von anderen Projekten in Anspruch genommen werden. Auf diese Weise können benutzerdefinierte Editoren Dokumente öffnen, bevor sie standard-Editoren zu öffnen. Wenn ein Projekt verschiedene Dateien auf eine Datei Ansprüche, die Umgebung Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode, um die Datei mit einem standard-Editor zu öffnen. Die Umgebung überprüft ihre interne Liste der registrierten Editoren für eine, die behandelt *RTF* Dateien. Diese Liste befindet sich in der Registrierung unter folgendem Schlüssel:

 **HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\\<Version > \Editors\\\<Editorfactory-Guid > \Extensions**

 Die Umgebung überprüft auch die Klassenbezeichner der **HKEY_CLASSES_ROOT\CLSID** Schlüssel für alle Objekte, die über einen Unterschlüssel **DocObject**. Wenn die Dateierweiterung dort gefunden wird, wird eine eingebettete Version von der Anwendung, z.B. Microsoft Word ein direktes in Visual Studio erstellt. Diese Dokumentobjekte müssen compound-Dateien, die implementiert werden die <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> -Schnittstelle, oder das Objekt muss implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> Schnittstelle.

 Es ist keine Editor-Factory für *RTF* Dateien in der Registrierung, und klicken Sie dann die Umgebung in sucht der **HKEY_CLASSES_ROOT\\RTF** gedrückt, und die dort angegebenen Editor geöffnet. Wenn die Dateierweiterung nicht, im gefunden wird **HKEY_CLASSES_ROOT**, und klicken Sie dann die Umgebung der Visual Studio-Kern-Text-Editor verwendet, um die Datei zu öffnen, wenn es sich um eine Textdatei ist.

 Wenn der kerntext-Editors ein Fehler auftritt, tritt auf, die, wenn die Datei nicht um eine Textdatei ist, klicken Sie dann die Umgebung der binären-Editor für die Datei verwendet.

 Wenn die Umgebung für einen Editor findet die *RTF* Erweiterung in der Registrierung, lädt er das VSPackage, das dieser Editorfactory implementiert. Die Umgebung Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Methode für das VSPackage, neue. Die VSPackage-Aufrufe `QueryService` für `SID_SVsRegistorEditor`unter Verwendung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> Methode, um die Editor-Factory mit der Umgebung zu registrieren.

 Die Umgebung jetzt wurden seine interne Liste der registrierten-Editoren, suchen die neu registrierte Editorfactory für *RTF* Dateien. Die Umgebung ruft Ihre Implementierung von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Methode und übergeben den Dateityp Namen und die Ansicht zu erstellen.

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>
- <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
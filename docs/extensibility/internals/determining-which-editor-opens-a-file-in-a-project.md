---
title: Bestimmen, welche Editor eine Datei in einem Projekt öffnet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d8fe054fa8e630b2f6c54cb78ef75b6c10ff74d3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>Bestimmen daraufhin-Editor eine Datei in einem Projekt
Wenn ein Benutzer eine Datei in einem Projekt geöffnet wird, wechselt die Umgebung durch einen Abruf-Prozess, schließlich Öffnen der entsprechenden Editor bzw. Designer für diese Datei. Das erste Verfahren eingesetzt werden, von der Umgebung entspricht dem standardmäßigen und benutzerdefinierten Editoren. Die Umgebung verwendet eine Vielzahl von Kriterien aus, wenn der Editor zum Öffnen einer Datei abrufen und das VSPackage muss die Umgebung koordinieren, während dieses Vorgangs.  
  
 Wählt z. B. wenn ein Benutzer die **öffnen** Befehl die **Datei** Menü und wählt dann `filename`RTF (oder eine andere Datei mit der Erweiterung RTF) die Umgebung Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> die Implementierung für jedes Projekt, und schließlich alle Instanzen von Project in der Projektmappe durchlaufen. Projekte zurück als Gruppe von Flags, die Ansprüche in einem Dokument nach Priorität zu identifizieren. Verwenden die höchste Priorität, die Umgebung Ruft die entsprechende <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> Methode. Weitere Informationen über den Prozess Abruf [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 Das Projekt verschiedene Dateien Ansprüche alle Dateien, die nicht von anderen Projekten in Anspruch genommen werden. Auf diese Weise können benutzerdefinierte Editoren Dokumente öffnen, bevor sie standard-Editor zu öffnen. Wenn ein Projekt verschiedene Dateien eine Datei Ansprüche, die Umgebung Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode, um die Datei mit einem standard-Editor zu öffnen. Die Umgebung überprüft ihre interne Liste von registrierten Editoren für die RTF-Dateien behandelt. Diese Liste befindet sich in der Registrierung unter folgendem Schlüssel:  
  
 [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<`version`> \Editors\\{<`editor factory guid`>} \Extensions]  
  
 Die Umgebung überprüft auch die Klassenbezeichner im Schlüssel HKEY_CLASSES_ROOT\CLSID für alle Objekte, die einen Unterschlüssel DocObject verfügen. Wenn es die Erweiterung gefunden wird, wird eine eingebettete Version von der Anwendung, z. B. Microsoft Word, direkte in Visual Studio erstellt. Diese Document-Objekte Verbunddateien, die implementiert werden müssen die <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> -Schnittstelle, oder das Objekt muss implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> Schnittstelle.  
  
 Wenn keine Editor-für .rtf-Dateien in der Registrierung Factory, und klicken Sie dann die Umgebung in der HKEY_CLASSES_ROOT sieht \\RTF-Schlüssel und öffnet der-Editor vorhanden angegebenen. Wenn die Dateierweiterung in HKEY_CLASSES_ROOT nicht gefunden wird, verwendet die Umgebung der Visual Studio Core-Text-Editor zum Öffnen der Datei, wenn es sich um eine Textdatei handelt.  
  
 Fällt die Core-Text-Editor aus, die tritt auf, wenn die Datei nicht um eine Textdatei ist, klicken Sie dann die Umgebung der binären-Editor für die Datei verwendet.  
  
 Wenn die Umgebung ein Editors für die RTF-Erweiterung in der Registrierung gefunden wird, lädt er das VSPackage, das dieser Editorfactory implementiert. Die Umgebung Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Methode für das neue VSPackage. Die VSPackage-Aufrufe `QueryService` für `SID_SVsRegistorEditor`unter Verwendung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> Methode, um die Editor-Factory mit der Umgebung zu registrieren.  
  
 Die Umgebung überprüft erneut jetzt seine interne Liste der registrierten Editoren verwenden, um den neu registrierten Editorfactory für .rtf-Dateien zu suchen. Die Umgebung ruft Ihre Implementierung von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> -Methode auf und übergibt den Dateityp Namen und die Ansicht zu erstellen.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
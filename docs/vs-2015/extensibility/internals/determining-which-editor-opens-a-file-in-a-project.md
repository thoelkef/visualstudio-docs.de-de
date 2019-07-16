---
title: Bestimmen, welcher Editor eine Datei in einem Projekt öffnet | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1c79860f770a6b04a17786cfb281fc3c0e4dffda
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196761"
---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>Bestimmen, welcher Editor eine Datei in einem Projekt öffnet
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wenn ein Benutzer eine Datei in einem Projekt geöffnet wird, durchläuft die Umgebung einen Abruf-Prozess, und öffnen schließlich die geeigneten Editor oder Designer für diese Datei. Das erste Verfahren eingesetzt, die von der Umgebung ist für Standard- und benutzerdefinierte Editoren identisch. Die Umgebung verwendet eine Vielzahl von Kriterien aus, wenn der Editor zum Öffnen einer Datei abrufen und das VSPackage mit der Umgebung koordinieren muss, während dieses Vorgangs.  
  
 Wählt z. B. wenn ein Benutzer die **öffnen** Befehl die **Datei** Menü und wählt dann `filename`RTF (oder jede andere Datei mit der Erweiterung RTF), die Umgebung Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> die Implementierung für jedes Projekt, und schließlich werden alle Instanzen von Project in der Lösung durchlaufen. Projekte zurückzugeben, einen Satz von Flags, die Ansprüche in einem Dokument nach Priorität zu identifizieren. Verwenden die höchste Priorität, die Umgebung Ruft die entsprechende <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> Methode. Weitere Informationen zu den Benachrichtigungsabrufprozesses [Hinzufügen von Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 Das Projekt verschiedene Dateien Ansprüche werden alle Dateien, die nicht von anderen Projekten in Anspruch genommen werden. Auf diese Weise können benutzerdefinierte Editoren Dokumente öffnen, bevor sie standard-Editoren zu öffnen. Wenn ein Projekt verschiedene Dateien auf eine Datei Ansprüche, die Umgebung Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode, um die Datei mit einem standard-Editor zu öffnen. Die Umgebung überprüft ihre interne Liste von registrierten Editoren für das RTF-Dateien behandelt. Diese Liste befindet sich in der Registrierung unter folgendem Schlüssel:  
  
 [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<`version`>\Editors\\{<`editor factory guid`>}\Extensions]  
  
 Die Umgebung überprüft auch die Klassenbezeichner im HKEY_CLASSES_ROOT\CLSID Schlüssel für alle Objekte, die Unterschlüssel DocObject aufweisen. Wenn die Dateierweiterung dort gefunden wird, wird eine eingebettete Version von der Anwendung, z.B. Microsoft Word ein direktes in Visual Studio erstellt. Diese Dokumentobjekte müssen compound-Dateien, die implementiert werden die <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> -Schnittstelle, oder das Objekt muss implementieren die <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> Schnittstelle.  
  
 Wenn kein Editor-Factory für die RTF-Dateien in der Registrierung vorhanden ist, und dann die Umgebung in den HKEY_CLASSES_ROOT sucht \\RTF-Schlüssel und die angegebene der Editor geöffnet. Wenn die Dateierweiterung in HKEY_CLASSES_ROOT nicht gefunden wird, verwendet die Umgebung der Visual Studio-Kern-Text-Editor zum Öffnen der Datei, wenn es sich um eine Textdatei handelt.  
  
 Wenn der kerntext-Editors ein Fehler auftritt, tritt auf, die, wenn die Datei nicht um eine Textdatei ist, klicken Sie dann die Umgebung der binären-Editor für die Datei verwendet.  
  
 Wenn die Umgebung ein Editors für die RTF-Erweiterung in die Registrierung findet, lädt es das VSPackage, das dieser Editorfactory implementiert. Die Umgebung Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Methode für das VSPackage, neue. Die VSPackage-Aufrufe `QueryService` für `SID_SVsRegistorEditor`unter Verwendung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> Methode, um die Editor-Factory mit der Umgebung zu registrieren.  
  
 Die Umgebung überprüft erneut nun seine interne Liste der registrierten-Editoren, um die neu registrierte Editorfactory für RTF-Dateien zu finden. Die Umgebung ruft Ihre Implementierung von der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Methode und übergeben den Dateityp Namen und die Ansicht zu erstellen.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>

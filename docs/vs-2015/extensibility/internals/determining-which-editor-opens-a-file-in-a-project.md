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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196761"
---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>Bestimmen, welcher Editor eine Datei in einem Projekt öffnet
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wenn ein Benutzer eine Datei in einem Projekt öffnet, durchläuft die Umgebung einen Abruf Vorgang und öffnet schließlich den entsprechenden Editor oder Designer für diese Datei. Das erste Verfahren, das von der Umgebung verwendet wird, ist für Standard-und benutzerdefinierte Editoren identisch. Die Umgebung verwendet eine Vielzahl von Kriterien, wenn abgefragt wird, welcher Editor zum Öffnen einer Datei verwendet werden soll, und das VSPackage muss sich während dieses Vorgangs mit der Umgebung koordinieren.  
  
 Wenn ein Benutzer beispielsweise den Befehl **Öffnen** im Menü **Datei** auswählt und dann die `filename` Datei. RTF (oder eine beliebige andere Datei mit der Erweiterung. RTF) auswählt, ruft die Umgebung die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Implementierung für jedes Projekt auf und durchläuft schließlich alle Projekt Instanzen in der Projekt Mappe. Projekte geben einen Satz von Flags zurück, die Ansprüche in einem Dokument nach Priorität identifizieren. Mit der höchsten Priorität Ruft die Umgebung die entsprechende- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> Methode auf. Weitere Informationen zum Abruf Vorgang finden Sie unter [Hinzufügen von Projekt-und Projekt Element Vorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 Das Projekt "sonstige Dateien" beansprucht alle Dateien, die nicht von anderen Projekten beansprucht werden. Auf diese Weise können benutzerdefinierte Editoren Dokumente öffnen, bevor Sie von Standard Editoren geöffnet werden. Wenn ein Projekt für verschiedene Dateien eine Datei beansprucht, ruft die Umgebung die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode auf, um die Datei mit einem Standard-Editor zu öffnen. Die Umgebung überprüft die interne Liste der registrierten Editoren auf eine, die RTF-Dateien verarbeitet. Diese Liste befindet sich in der Registrierung unter folgendem Schlüssel:  
  
 [HKEY_LOCAL_MACHINE \software\microsoft\visualstudio \\ < `version`> \editoren \\ {<`editor factory guid`>} \extensions]  
  
 Die Umgebung überprüft auch die Klassen Bezeichner im HKEY_CLASSES_ROOT \CLSID-Schlüssel für alle Objekte, die über ein untergeordnetes DocObject-Objekt verfügen. Wenn die Dateierweiterung dort gefunden wird, wird eine eingebettete Version der Anwendung (z. b. Microsoft Word) direkt in Visual Studio erstellt. Diese Dokument Objekte müssen Verbund Dateien sein, die die- <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> Schnittstelle implementieren, oder das-Objekt muss die- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> Schnittstelle implementieren.  
  
 Wenn in der Registrierung keine Editorfactory für RTF-Dateien vorhanden ist, sucht die Umgebung in der HKEY_CLASSES_ROOT \\ . RTF-Taste und öffnet den dort angegebenen Editor. Wenn die Dateierweiterung in HKEY_CLASSES_ROOT nicht gefunden wird, verwendet die Umgebung den Visual Studio-Kern Text-Editor, um die Datei zu öffnen, falls es sich um eine Textdatei handelt.  
  
 Wenn der Kerntext-Editor fehlschlägt, der auftritt, wenn es sich bei der Datei nicht um eine Textdatei handelt, verwendet die Umgebung den Binär-Editor für die Datei.  
  
 Wenn die Umgebung in der Registrierung einen Editor für die RTF-Erweiterung findet, lädt Sie das VSPackage, das diese Editorfactory implementiert. Die Umgebung Ruft die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Methode für das neue VSPackage auf. Das VSPackage ruft `QueryService` für mit `SID_SVsRegistorEditor` der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> Methode auf, um die Editorfactory bei der-Umgebung zu registrieren.  
  
 Die Umgebung prüft nun die interne Liste der registrierten Editoren erneut, um die neu registrierte Editorfactory für RTF-Dateien zu finden. Die Umgebung ruft Ihre Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> -Methode auf und übergibt den zu erstellenden Dateinamen und Ansichtstyp.  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>

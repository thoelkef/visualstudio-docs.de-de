---
title: Bestimmen, welcher Editor eine Datei in einem Projekt öffnet | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af7037a3b4bfbae1801e802256af240d017d2789
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708661"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>Bestimmen, welcher Editor eine Datei in einem Projekt öffnet
Wenn ein Benutzer eine Datei in einem Projekt öffnet, durchläuft die Umgebung einen Abrufvorgang und öffnet schließlich den entsprechenden Editor oder Designer für diese Datei. Das anfängliche Verfahren, das von der Umgebung verwendet wird, ist für Standard- und benutzerdefinierte Editoren identisch. Die Umgebung verwendet beim Abrufen des Editors, der zum Öffnen einer Datei verwendet werden soll, eine Vielzahl von Kriterien, und das VSPackage muss sich während dieses Vorgangs mit der Umgebung abstimmen.

 Wenn ein Benutzer beispielsweise den Befehl **Öffnen** aus dem Menü **Datei** auswählt und dann *filename.rtf* (oder eine andere <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> Datei mit einer *.rtf-Erweiterung)* auswählt, ruft die Umgebung die Implementierung für jedes Projekt auf und durchfährt schließlich alle Projektinstanzen in der Projektmappe. Projekte geben eine Reihe von Flags zurück, die Ansprüche für ein Dokument nach Priorität identifizieren. Unter Verwendung der höchsten Priorität <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> ruft die Umgebung die entsprechende Methode auf. Weitere Informationen zum Abrufvorgang finden Sie unter Hinzufügen von [Projekt- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md).

 Das Projekt Verschiedene Dateien beansprucht alle Dateien, die nicht von anderen Projekten beansprucht werden. Auf diese Weise können benutzerdefinierte Editoren Dokumente öffnen, bevor Standardeditoren sie öffnen. Wenn ein Projekt "Verschiedene Dateien" eine Datei beansprucht, ruft die Umgebung die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> Methode auf, die Datei mit einem Standardeditor zu öffnen. Die Umgebung überprüft ihre interne Liste der registrierten Editoren auf einen, der *.rtf-Dateien* verarbeitet. Diese Liste befindet sich in der Registrierung unter folgendem Schlüssel:

 **\\\<HKEY_LOCAL_MACHINE-Software-Version,Microsoft-VisualStudio-Version\\\<>-Editors-Editor-Factory-Guid->-Erweiterungen**

 Die Umgebung überprüft auch die Klassenbezeichner im **HKEY_CLASSES_ROOT-CLSID-Schlüssel** für alle Objekte, die über einen Unterschlüssel **DocObject**verfügen. Wenn die Dateierweiterung dort gefunden wird, wird eine eingebettete Version der Anwendung, z. B. Microsoft Word, in Visual Studio an Ort und Stelle erstellt. Bei diesen Dokumentobjekten muss es <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> sich um zusammengesetzte <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> Dateien handelt, die die Schnittstelle implementieren, oder das Objekt muss die Schnittstelle implementieren.

 Wenn keine Editorfactory für *.rtf-Dateien* in der Registrierung vorhanden ist, sucht die Umgebung im **\\HKEY_CLASSES_ROOT .rtf-Taste** und öffnet den dort angegebenen Editor. Wenn die Dateierweiterung in **HKEY_CLASSES_ROOT**nicht gefunden wird, verwendet die Umgebung den Visual Studio-Kerntexteditor, um die Datei zu öffnen, wenn es sich um eine Textdatei handelt.

 Wenn der Kerntexteditor fehlschlägt, was auftritt, wenn es sich bei der Datei nicht um eine Textdatei handelt, verwendet die Umgebung den Binäreditor für die Datei.

 Wenn die Umgebung einen Editor für die *Erweiterung .rtf* in ihrer Registrierung findet, lädt sie das VSPackage, das diese Editorfactory implementiert. Die Umgebung <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> ruft die Methode für das neue VSPackage auf. Das VSPackage `QueryService` `SID_SVsRegistorEditor`ruft nach <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> auf, mit der Methode, die Editorfactory bei der Umgebung zu registrieren.

 Die Umgebung überprüft nun ihre interne Liste der registrierten Editoren, um die neu registrierte Editorfactory für *.rtf-Dateien* zu finden. Die Umgebung ruft Ihre <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> Implementierung der Methode auf und übergibt den zu erstellenden Dateinamen und Ansichtstyp.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>
- <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>

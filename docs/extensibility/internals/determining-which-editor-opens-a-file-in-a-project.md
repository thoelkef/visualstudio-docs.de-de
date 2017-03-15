---
title: "Bestimmen daraufhin-Editor eine Datei in einem Projekt | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK], bestimmen den Editor öffnet eine Datei"
  - "Projekte [Visual Studio SDK], bestimmen den Editor öffnet Datei"
  - "die Projekttypen, bestimmen den Editor öffnet eine Datei"
  - "Persistenz, bestimmen den Editor öffnet eine Datei"
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Bestimmen daraufhin-Editor eine Datei in einem Projekt
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Wenn ein Benutzer eine Datei in einem Projekt geöffnet wird, wird die Umgebung einen Abruf Prozess geöffnet und schließlich über den geeigneten Editor oder Designer für diese Datei.  Das erste Verfahren, das von der Umgebung versetzt wird, entspricht dem für die Standard\- und benutzerdefinierten Editoren.  Die Umgebung verwendet eine Vielzahl von Kriterien bei der Anforderung, die der Editor verwendet werden soll, um eine Datei zu öffnen und VSPackages mit der Umgebung während dieses Prozesses koordiniert werden muss.  
  
 Wenn ein Benutzer beispielsweise den **Öffnen** Befehl aus dem Menü **Datei** auswählt, und dann werden `filename`.rtf \(oder eine andere Datei mit einer .rtf\-Erweiterung\), die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> ruft die Implementierung der Umgebung für jedes Projekt aus, und schließlich wird von allen Instanzen Projekt in der Projektmappe rad.  Projekte geben einen Satz von Flags zurück, die Eine in einem Dokument nach Priorität identifizieren.  Verwenden des höchsten Priorität wird die Umgebung die entsprechende <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>\-Methode veranschaulicht.  Weitere Informationen über das Abrufen des [Hinzufügen von Projekt\- und Projektelementvorlagen](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 Das Projekt Verschiedene Dateien entspricht alle Dateien, die nicht von anderen Projekten Konformität deklariert werden.  Auf diese Weise können benutzerdefinierte Editoren geöffnete Dokumente, bevor sie editoren Standard zu öffnen.  Wenn ein Projekt mehrere Dateien eine Datei entspricht, wird die Umgebung die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>\-Methode auf, um die Datei mit einem standardmäßigen Editor zu öffnen.  Die Umgebung überprüft seine interne Liste der registrierten Editoren, der für einen .rtf\-Dateien bearbeitet.  Diese Liste ist in der Registrierung zu dem folgenden Schlüssel:  
  
 \[HKEY\_LOCAL\_MACHINE \\ Software \\ Microsoft \\ VisualStudio \\ \<`Version`\> \\ Editoren \\ {\<`factory Editor guid`\>} \\ Extensions\]  
  
 Die Umgebung überprüft auch den Klassenbezeichner in der HKEY\_CLASSES\_ROOT\- \\ CLSID Schlüssels für alle Objekte, die einen Unterschlüssel DocObject haben.  Wenn die Dateierweiterung dort gefunden wird, ist eine eingebettete Version der Anwendung wie Microsoft Word in Visual Studio erstelltes direkte.  Diese Dokumentobjekte müssen Verbunddateien sein, die die <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>\-Schnittstelle implementieren, oder das Objekt muss die <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>\-Schnittstelle implementieren.  
  
 Wenn keine Editor für .rtf\-Dateien factory in der Registrierung vorhanden ist, sieht die Umgebung in der HKEY\_CLASSES\_ROOT\- \\ .rtf\-Taste, der den Editor zu öffnen und dort angegeben wird.  Wenn die Dateierweiterung nicht in HKEY\_CLASSES\_ROOT gefunden wird, wird die Umgebung Visual Studio\-Kern text\-editor, um die Datei zu öffnen, wenn es sich um eine Textdatei ist.  
  
 Wenn der zentralen text\-editor fehlschlägt, der auftritt, wenn die Datei keine Textdatei ist, wird die Umgebung den binären Editor für die Datei.  
  
 Wenn die Umgebung einen Editor für die .rtf\-Erweiterung in der Registrierung findet, lädt sie VSPackages mit dieser Editor factory implementiert.  Die Umgebung wird die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>\-Methode auf Neuer VSPackage an.  VSPackage wird `QueryService` für `SID_SVsRegistorEditor`unter Verwendung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>\-Methode auf, um den Editor factory mit der Umgebung zu registrieren.  
  
 Die Umgebung neu überprüft jetzt die interne Liste der registrierten Editoren, um die neu registrierte factory Editor für .rtf\-Dateien zu suchen.  Die Umgebung wird die Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>\-Methode auf und übergibt den Ansichtstyp und Dateinamen\- zu erstellen.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
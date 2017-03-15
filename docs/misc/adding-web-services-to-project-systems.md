---
title: "Hinzuf&#252;gen von Webdiensten zu Projektsystemen | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Projektsysteme, Hinzufügen von Webdiensten"
  - "Webdienste, Hinzufügen zu VSPackage-Projektsystemen"
ms.assetid: 8efa078b-68b2-45a2-9be2-44f807bc0d7f
caps.latest.revision: 8
caps.handback.revision: 8
manager: "douge"
---
# Hinzuf&#252;gen von Webdiensten zu Projektsystemen
XML\-Webdienste sind im Allgemeinen URL\-adressierbare Ressourcen, die programmgesteuerte Informationen für das Projektsystem mithilfe des Protokolls der SOAP \(Simple Object Access Protocol\) zurückgeben.  Sie können Webdienste auf den VSPackage\-Projektsystem integrieren, indem Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2>\-Schnittstelle verwenden.  
  
### So erstellen Sie einen Webdienst, die dem Projektsystem hinzu  
  
1.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2>\-Schnittstelle für `QueryService` Aufruf von <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg> Dienst.  
  
2.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A>\-Methode auf.  Ruft beim Überschreiben in `pDiscoverySession``NULL`als Parameter übergeben, wird eine Suche eine für Sie erstellt, und die Sitzung wird zwischengespeichert, sodass es für spätere Verwendung durch die <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>\-Schnittstelle verfügbar ist.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A>\-Methode gibt einen Zeiger auf <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult2>zurück.  
  
3.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult.AddWebReference%2A>\-Methode auf.  Übergeben Sie den Ordner Automatisierungsobjekt für den Webdienst verweist `pUnkWebReferenceFolder` als Parameter.  Die Überprüfungen der Visual Studio\-Umgebung dann, wenn der Webdienst bereits vorhanden ist.  Wenn der Webdienst nicht vorhanden ist, lädt die Umgebung herunter und fügt den Webdienst einem Ordner und alle weiteren Dateien \(z\) .wsdl\-Dateien den untergeordneten Knoten des Ordners hinzu.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoverySession>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>
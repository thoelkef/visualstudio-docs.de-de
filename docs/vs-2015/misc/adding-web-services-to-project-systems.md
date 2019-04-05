---
title: Hinzufügen von Webdiensten zu Projektsystemen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- project systems, adding Web services
- Web services, adding to VSPackage project systems
ms.assetid: 8efa078b-68b2-45a2-9be2-44f807bc0d7f
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: 8143db95d2f892c7e3438f240aa5f22cdda53c7f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58956714"
---
# <a name="adding-web-services-to-project-systems"></a>Hinzufügen von Webdiensten zu Projektsystemen
XML-Webdienste sind im Allgemeinen eine URL-adressierbaren Ressourcen, die programmgesteuerte Informationen an das Projektsystem, die über SOAP (Simple Object Access Protocol) zurückgeben. Sie können Webdienste für Ihr VSPackage-Projekt-System integrieren, mithilfe der <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> Schnittstelle.  
  
### <a name="to-add-a-web-service-to-your-project-system"></a>So fügen Ihrem Projektsystem einen Webdienst hinzu  
  
1.  Rufen Sie `QueryService` für <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> Schnittstelle, über <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg> Service.  
  
2.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A>-Methode auf. Wenn Sie übergeben `pDiscoverySession` Parameter als `NULL`eine Discovery-Sitzung wird für Sie erstellt und die Sitzung wird zwischengespeichert, sodass sie für die zukünftige Verwendung von verfügbar ist die <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2> Schnittstelle. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> Methode gibt einen Zeiger auf <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult2>.  
  
3.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult.AddWebReference%2A>-Methode auf. Übergeben Sie das Automatisierungsobjekt für den Ordner der Web-Service-Verweise als die `pUnkWebReferenceFolder` Parameter. Visual Studio-Umgebung überprüft dann, wenn der Webdienst bereits vorhanden ist. Wenn der Webdienst nicht vorhanden ist, wird die Umgebung downloads und einen Ordner und alle zusätzlichen Dateien (z. B. WSDL-Dateien) die untergeordneten Knoten des Ordners und des Webdiensts hinzufügt.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoverySession>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>
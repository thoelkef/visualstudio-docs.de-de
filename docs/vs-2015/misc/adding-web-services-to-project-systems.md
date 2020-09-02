---
title: Hinzufügen von Webdiensten zu Projekt Systemen | Microsoft-Dokumentation
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
ms.openlocfilehash: f5b192be8e5f68ad9314fe08fff963c032013cb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "63002667"
---
# <a name="adding-web-services-to-project-systems"></a>Hinzufügen von Webdiensten zu Projektsystemen
XML-Webdienste sind im allgemeinen URL-adressierbare Ressourcen, die mithilfe des SOAP-Protokolls (Simple Object Access Protocol) programmgesteuerte Informationen an das Projekt System zurückgeben. Mithilfe der-Schnittstelle können Sie Webdienste in das VSPackage-Projekt System integrieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> .  
  
### <a name="to-add-a-web-service-to-your-project-system"></a>So fügen Sie dem Projekt System einen Webdienst hinzu  
  
1. `QueryService`Für die <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddProjectItemDlg2> Schnittstelle durch den Dienst aufzurufen <xref:Microsoft.VisualStudio.Shell.Interop.SVsAddWebReferenceDlg> .  
  
2. Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> -Methode auf. Wenn Sie `pDiscoverySession` den Parameter als übergeben `NULL` , wird eine Ermittlungs Sitzung für Sie erstellt, und die Sitzung wird zwischengespeichert, sodass Sie für die nachfolgende Verwendung durch die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2> Schnittstelle verfügbar ist. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2.AddWebReferenceDlg%2A> die Methode gibt einen Zeiger auf zurück <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult2> .  
  
3. Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult.AddWebReference%2A> -Methode auf. Übergeben Sie das Automatisierungs Objekt für den Ordner Webdienst Verweise als `pUnkWebReferenceFolder` Parameter. Die Visual Studio-Umgebung prüft dann, ob der Webdienst bereits vorhanden ist. Wenn der Webdienst nicht vorhanden ist, wird der Webdienst von der Umgebung heruntergeladen und einem Ordner sowie weiteren Dateien (z. b. WSDL-Dateien) für die untergeordneten Knoten des Ordners hinzugefügt.  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAddWebReferenceDlg2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoveryResult>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IDiscoverySession>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDiscoveryService>
---
title: Attribute für die Website Unterstützung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 75401eb0d5acd5d363d05aec57909eef5b9855e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144298"
---
# <a name="web-site-support-attributes"></a>Attribute der Websiteunterstützung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Das Website Projekt kann erweitert werden, um Unterstützung für webprogrammier Sprachen bereitzustellen. Die Sprache muss sich bei registrieren [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , damit Projektvorlagen im Dialogfeld **neue Website** angezeigt werden können, wenn die Sprache ausgewählt ist.  
  
 Das IronPython Studio-Beispiel enthält Website Unterstützung. Sie finden ihn mit den [VSSDK-Beispielen](../../misc/vssdk-samples.md). Sie enthält die folgenden Attribut Klassen, um IronPython als Code Behind-Sprache für neue Webprojekte zu registrieren.  
  
## <a name="websiteprojectattribute"></a>Websiteprojectattribute  
 Dieses Attribut wird in das Sprachprojekt eingefügt. Die Sprache wird der Liste der webprogrammier Sprachen in der Liste **Sprache** im Dialogfeld **neue Website** hinzugefügt. Im folgenden Beispiel wird IronPython zur Liste hinzugefügt:  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Dieses Attribut legt auch den Vorlagen Pfad so fest, dass er auf den Vorlagen Ordner verweist. Weitere Informationen zum Speicherort des Ordners "Vorlagen" finden Sie [unter Vorlagen für Website Unterstützung](../../extensibility/internals/web-site-support-templates.md).  
  
## <a name="websiteprojectrelatedfilesattribute"></a>Websiteprojectrelatedfilesattribute  
 Dieses Attribut wird in das Sprachprojekt eingefügt. Dadurch kann das Website Projekt einen Dateityp (Related) unter einem anderen Dateityp (primär) im **Projektmappen-Explorer**Schachteln.  
  
 Beispiel:  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Gibt an, dass eine IronPython-Code Behind-Datei mit einer ASPX-Datei verknüpft ist. Wenn eine neue ASPX-Webseite in einer IronPython-Website Lösung erstellt wird, wird eine neue py-Quelldatei generiert und als untergeordneter Knoten der ASPX-Seite angezeigt.  
  
## <a name="provideintellisenseproviderattribute"></a>Provideintellisentsproviderattribute  
 Dieses Attribut wird im Sprachprojekt Paket abgelegt. Er wählt den IntelliSense-Anbieter für die Sprache aus.  
  
 Beispiel:  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 Gibt an, dass eine Instanz von pythonintellisenseprovider, die implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject> , bei Bedarf erstellt werden soll, um Sprachdienste bereitzustellen.  
  
 Die ivsintellisenseproject-Implementierung behandelt Verweise und ruft den sprach Compiler auf, wenn eine Webseite mit Code angefordert, jedoch nicht zwischengespeichert wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Websiteunterstützung](../../extensibility/internals/web-site-support.md)

---
title: Attribute der Websiteunterstützung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 312d8a760cc7005afc4308b637b12a292bd20329
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756696"
---
# <a name="web-site-support-attributes"></a>Attribute der Websiteunterstützung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] -Websiteprojekt kann erweitert werden, um Unterstützung für Web bietet Programmiersprachen zu vergleichen. Die Sprache muss selbst registrieren, mit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , damit Projektvorlagen angezeigt werden können, in der **neue Website** im Dialogfeld, wenn die Sprache ausgewählt ist.  
  
 Das IronPython Studio-Beispiel enthält der Support-Website. Sie finden ihn mit der [VSSDK-Beispiele](../../misc/vssdk-samples.md). Sie enthält die folgenden Attributklassen zum Registrieren von IronPython als eine Codebehind-Sprache für die neue Web-Projekte.  
  
## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute  
 Dieses Attribut befindet sich auf das Sprachprojekt. Die Liste der Web-Programmiersprachen, in der Sprache hinzugefügt der **Sprache** Liste der **neue Website** Dialogfeld. Z. B. die folgenden IronPython der Liste hinzugefügt:  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Dieses Attribut legt auch fest, den Vorlagenpfad zum Ordner "Templates" verweisen. Weitere Informationen zu den Speicherort der Ordner "Templates", finden Sie unter [Vorlagen für die Websiteunterstützung](../../extensibility/internals/web-site-support-templates.md).  
  
## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute  
 Dieses Attribut befindet sich auf das Sprachprojekt. Es ermöglicht das Websiteprojekt zu schachteln, einen Dateityp (verknüpft) unter einem anderen Dateityp (primär) in der **Projektmappen-Explorer**.  
  
 Zum Beispiel:  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Gibt an, dass eine IronPython-Codebehind-Datei mit einer ASPX-Datei verknüpft ist. Wenn eine neue ASPX-Webseite in einer Projektmappe der IronPython-Web-Standort erstellt wird, wird eine neue .py-Quelldatei wird generiert und als untergeordneter Knoten der ASPX-Seite angezeigt wird.  
  
## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute  
 Dieses Attribut wird auf das Sprachpaket für das Projekt eingefügt. Er wählt den Intellisense-Anbieter für die Sprache aus.  
  
 Zum Beispiel:  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 Gibt an, dass eine Instanz von PythonIntellisenseProvider, die implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, bei Bedarf auf Sprachdienste bieten erstellt werden soll.  
  
 Die IVsIntellisenseProject Implementierung Verweise verarbeitet und des Sprachcompilers aufruft, wenn eine Webseite mit Code angefordert wird jedoch nicht zwischengespeichert.  
  
## <a name="see-also"></a>Siehe auch  
 [Websiteunterstützung](../../extensibility/internals/web-site-support.md)


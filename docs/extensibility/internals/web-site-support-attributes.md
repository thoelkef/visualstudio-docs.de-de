---
title: "Attribute für Website-Support | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: web site projects, registration
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 868fe0785c90a174610b9fff837fc6fbfb084e83
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="web-site-support-attributes"></a>Attribute für Website-Unterstützung
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Website-Projekt kann zum Bereitstellen von Unterstützung für das Web erweitert Programmiersprachen zu vergleichen. Die Sprache muss selbst registrieren, mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , damit Projektvorlagen angezeigt werden können, in der **neue Website** (Dialogfeld), wenn die Sprache ausgewählt ist.  
  
 Das IronPython Studio-Beispiel enthält der Support-Website. Es enthält die folgenden Attributklassen um IronPython als Codebehind Sprache für die neue Webprojekte zu registrieren.  
  
## <a name="websiteprojectattribute"></a>WebSiteProjectAttribute  
 Dieses Attribut wird für das Language-Projekt eingefügt. Die Liste der Web-Programmiersprachen in der Sprache hinzugefügt der **Sprache** in Liste der **neue Website** (Dialogfeld). Z. B. die folgenden IronPython der Liste hinzugefügt:  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Dieses Attribut legt außerdem fest, die Vorlagen Pfad auf den Vorlagenordner verweist. Weitere Informationen zum Speicherort des-Vorlagenordners finden Sie unter [Websitevorlagen Unterstützung](../../extensibility/internals/web-site-support-templates.md).  
  
## <a name="websiteprojectrelatedfilesattribute"></a>WebSiteProjectRelatedFilesAttribute  
 Dieses Attribut wird für das Language-Projekt eingefügt. Er ermöglicht das Websiteprojekt einer Dateityp (verknüpft) geschachtelt unter einem anderen Dateiformat (primär) in der **Projektmappen-Explorer**.  
  
 Zum Beispiel:  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Gibt an, dass eine IronPython Codebehind-Datei in eine ASPX-Datei verknüpft ist. Wenn eine neue ASPX-Webseite in einer IronPython Web Site-Lösung erstellt wird, wird eine neue py-Quelldatei wird generiert und als untergeordneter Knoten der ASPX-Seite wird angezeigt.  
  
## <a name="provideintellisenseproviderattribute"></a>ProvideIntellisenseProviderAttribute  
 Dieses Attribut wird auf das Sprachpaket für das Projekt eingefügt. Er wählt die Intellisense-Anbieter für die Sprache aus.  
  
 Zum Beispiel:  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 Gibt an, dass eine Instanz von PythonIntellisenseProvider, die implementiert <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>, bei Bedarf, um die Sprache Dienstleistungen erstellt werden soll.  
  
 Die Implementierung IVsIntellisenseProject Verweise verarbeitet und des Sprachcompilers aufruft, wenn eine Webseite durch Code angefordert, aber wird nicht zwischengespeichert.  
  
## <a name="see-also"></a>Siehe auch  
 [Websiteunterstützung](../../extensibility/internals/web-site-support.md)
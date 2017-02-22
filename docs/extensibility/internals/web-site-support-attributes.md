---
title: "Website-Support-Attribute | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Website-Projekten, Registrierung"
ms.assetid: 46d52e2c-ca2a-4bbd-8500-5b0129768aec
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Website-Support-Attribute
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Websiteprojekt kann erweitert werden, um Unterstützung für Internet\-Programmiersprachen zu unterstützen.  Die Sprache muss mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] registrieren, damit Projektvorlagen in **Neue Website** Dialogfeld angezeigt werden können, wenn die Sprache ausgewählt wird.  
  
 Das Beispiel umfasst IronPython\-Studio Unterstützung für die Website ein.  Sie können ihn [VSSDK\-Beispiele](../../misc/vssdk-samples.md)suchen.  Es enthält die folgenden Attributklassen, um IronPython als codebehind Sprache für den neuen Webprojekten zu registrieren.  
  
## WebSiteProjectAttribute  
 Dieses Attribut wird auf das Sprachprojekt platziert.  Sie fügt die Sprache der Liste der Internet\-Programmiersprachen in der **Sprache** Liste im Dialogfeld **Neue Website** hinzu.  Zum Beispiel fügt der Liste IronPython Folgendes hinzu:  
  
```  
[WebSiteProject("IronPython", "Iron Python")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Dieses Attribut wird auch den Masterpfad fest, um auf das Vorlagenordner zu veranschaulichen.  Weitere Informationen zu den Speicherort des Vorlagenordners finden Sie unter [Unterstützung für Websitevorlagen](../../extensibility/internals/web-site-support-templates.md).  
  
## WebSiteProjectRelatedFilesAttribute  
 Dieses Attribut wird auf das Sprachprojekt platziert.  Es lässt sich das Websiteprojekt, einen Dateityp \(verknüpft\) unter einem anderen Dateityp \(primäre\) in **Projektmappen\-Explorer**zu schachteln.  
  
 Beispiele:  
  
```  
[WebSiteProjectRelatedFiles("aspx", "py")]public class PythonProjectPackage : ProjectPackage  
```  
  
 Gibt an, dass eine IronPython\-codebehind Datei in einer ASPX\-Datei bezieht.  Wenn eine neue .aspx\-Webseite IronPython\-Website in einer Projektmappe erstellt wird, wird eine neue .py\-Quelldatei generiert und wird als untergeordneter Knoten der ASPX\-Seite.  
  
## ProvideIntellisenseProviderAttribute  
 Dieses Attribut wird auf das Sprachprojekt Paket platziert.  Es wählt den IntelliSense\-Anbieter für die Sprache aus.  
  
 Beispiele:  
  
```  
[ProvideIntellisenseProvider(typeof(PythonIntellisenseProvider), "IronPythonCodeProvider", "Iron Python", ".py", "IronPython;Python", "IronPython")]public class PythonPackage : Package, IOleComponent  
```  
  
 Gibt an, dass eine Instanz von PythonIntellisenseProvider, das <xref:Microsoft.VisualStudio.Shell.Interop.IVsIntellisenseProject>implementiert, bei Bedarf erstellt werden soll, die Sprachendienste bereitzustellen.  
  
 Die IVsIntellisenseProject\-Implementierung Verweisen behandelt und ruft den Sprachcompiler an, ob eine Webseite mit Code angefordert wird, jedoch wird nicht zwischengespeichert.  
  
## Siehe auch  
 [Der Support\-Website](../../extensibility/internals/web-site-support.md)
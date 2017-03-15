---
title: "Managed Package Framework-Klassen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Managed Package Framework, Hilfsklassen"
  - "Managed Package-Hilfsklassen"
  - "Visual Studio SDK, Managed Package-Hilfsklassen"
  - "Klassen [Visual Studio SDK], Managed Package Framework"
ms.assetid: 15aedcc3-c79a-460b-b620-43223f1ae81e
caps.latest.revision: 24
caps.handback.revision: 24
manager: "douge"
---
# Managed Package Framework-Klassen
Die MPF\-Klassen \(Managed Package Framework\) können dazu verwendet werden, mit verwaltetem Code VSPackages zu erstellen. Diese Klassen stellen Standardimplementierungen für viele VSPackage\-Schnittstellen bereit. Dadurch, dass MPF Ihnen die Implementierungsdetails und \-komplexitäten erspart, können Sie mit MPF [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Integrationsprodukte mit einem Minimum an Code erstellen.  
  
> [!WARNING]
>  Die meisten Assemblys, die Managed Package Framework\-Klassen enthalten, gehören zum Lieferumfang des Visual Studio SDK. Sie können den Quellcode für Managed Packaged Framework for Projects von [Managed Package Framework for Projects](http://mpfproj11.codeplex.com/) herunterladen.  
  
## MPF\-Namespaces  
 In der folgenden Tabelle sind die MPF\-Namespaces aufgelistet, die vom [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] bereitgestellt werden.  
  
|Namespace|Inhalt|  
|---------------|------------|  
|<xref:Microsoft.VisualStudio>|Enthält Klassen für die Behandlung von COM\-Fehlern, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Konstanten und Win32\-Fenstern.|  
|<xref:Microsoft.VisualStudio.Package>|Beinhaltet Wrapper für verwalteten Code für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Projekte, Editoren und MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell>|Umfasst MPF\-Basisklassen, aus denen Sie eine Implementierung vieler allgemeiner Visual Studio\-Objekte ableiten können.|  
|<xref:Microsoft.VisualStudio.Shell.Design>|Enthält [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Designer\-Erweiterungen.|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization>|Enthält [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Serialisierungs\-Designer\-Erweiterungen.|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization.CodeDom>|Enthält [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] CodeDom\-Designer\-Erweiterungen.|  
|<xref:Microsoft.VisualStudio.Shell.Flavor>|Unterstützt Projektuntertypen \(werden auch als „Konfigurationen“ bezeichnet\).|  
  
## Siehe auch  
 [VSPackages und das Managed Package Framework](../misc/vspackages-and-the-managed-package-framework.md)   
 [Mithilfe von Interop\-Assemblys von Visual Studio](../extensibility/internals/using-visual-studio-interop-assemblies.md)   
 [VSPackages und das Managed Package Framework](../misc/vspackages-and-the-managed-package-framework.md)
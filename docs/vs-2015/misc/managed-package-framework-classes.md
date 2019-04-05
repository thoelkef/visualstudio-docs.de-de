---
title: Managed Package Framework-Klassen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, helper classes
- managed package helper classes
- Visual Studio SDK, managed package helper classes
- classes [Visual Studio SDK], managed package framework
ms.assetid: 15aedcc3-c79a-460b-b620-43223f1ae81e
caps.latest.revision: 24
manager: jillfra
ms.openlocfilehash: d8e2bbf51aa6266411558e91f3c17905d0c8605c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58959722"
---
# <a name="managed-package-framework-classes"></a>Managed Package Framework-Klassen
Die MPF-Klassen (Managed Package Framework) können dazu verwendet werden, mit verwaltetem Code VSPackages zu erstellen. Diese Klassen stellen Standardimplementierungen für viele VSPackage-Schnittstellen bereit. Dadurch, dass MPF Ihnen die Implementierungsdetails und -komplexitäten erspart, können Sie mit MPF [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Integrationsprodukte mit einem Minimum an Code erstellen.  
  
> [!WARNING]
>  Die meisten Assemblys, die Managed Package Framework-Klassen enthalten, gehören zum Lieferumfang des Visual Studio SDK. Sie können den Quellcode für Managed Packaged Framework for Projects von [Managed Package Framework for Projects](http://mpfproj11.codeplex.com/)herunterladen.  
  
## <a name="mpf-namespaces"></a>MPF-Namespaces  
 In der folgenden Tabelle sind die MPF-Namespaces aufgelistet, die vom [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]bereitgestellt werden.  
  
|Namespace|Inhalt|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio>|Enthält Klassen für die Behandlung von COM-Fehlern, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Konstanten und Win32-Fenstern.|  
|<xref:Microsoft.VisualStudio.Package>|Beinhaltet Wrapper für verwalteten Code für [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Projekte, Editoren und MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell>|Umfasst MPF-Basisklassen, aus denen Sie eine Implementierung vieler allgemeiner Visual Studio-Objekte ableiten können.|  
|<xref:Microsoft.VisualStudio.Shell.Design>|Enthält [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Designer-Erweiterungen.|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization>|Enthält [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Serialisierungs-Designer-Erweiterungen.|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization.CodeDom>|Enthält [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] CodeDom-Designer-Erweiterungen.|  
|<xref:Microsoft.VisualStudio.Shell.Flavor>|Unterstützt Projektuntertypen (werden auch als „Konfigurationen“ bezeichnet).|  
  
## <a name="see-also"></a>Siehe auch  
 [VSPackages und das Managed Package Framework](../misc/vspackages-and-the-managed-package-framework.md)   
 [Mithilfe von Visual Studio-Interopassemblys](../extensibility/internals/using-visual-studio-interop-assemblies.md)   
 [VSPackages und das Managed Package Framework](../misc/vspackages-and-the-managed-package-framework.md)
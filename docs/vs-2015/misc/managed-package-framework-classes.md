---
title: Managed Package Framework Classes | Microsoft Docs
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
ms.openlocfilehash: 2e9fe1abb82d3d64232e3e5e2a6d117c1068aa1c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297704"
---
# <a name="managed-package-framework-classes"></a>Managed Package Framework-Klassen
Die MPF-Klassen (Managed Package Framework) können dazu verwendet werden, mit verwaltetem Code VSPackages zu erstellen. Diese Klassen stellen Standardimplementierungen für viele VSPackage-Schnittstellen bereit. Dadurch, dass MPF Ihnen die Implementierungsdetails und -komplexitäten erspart, können Sie mit MPF [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Integrationsprodukte mit einem Minimum an Code erstellen.  
  
> [!WARNING]
> Die meisten Assemblys, die Managed Package Framework-Klassen enthalten, gehören zum Lieferumfang des Visual Studio SDK. Sie können den Quellcode für Managed Packaged Framework for Projects von [Managed Package Framework for Projects](https://archive.codeplex.com/?p=mpfproj11)herunterladen.  
  
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
 [VSPackages and the Managed Package Framework](../misc/vspackages-and-the-managed-package-framework.md)   
 [Using Visual Studio Interop Assemblies](../extensibility/internals/using-visual-studio-interop-assemblies.md)   
 [VSPackages und das Managed Package Framework](../misc/vspackages-and-the-managed-package-framework.md)
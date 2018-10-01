---
title: Managed Package Framework-Klassen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managed package framework, helper classes
- managed package helper classes
- Visual Studio SDK, managed package helper classes
- classes [Visual Studio SDK], managed package framework
ms.assetid: 15aedcc3-c79a-460b-b620-43223f1ae81e
caps.latest.revision: 24
manager: douge
ms.openlocfilehash: 38f159df52c99554ed931269f29ad57e72745b5d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522545"
---
# <a name="managed-package-framework-classes"></a>Managed Package Framework-Klassen
Die MPF-Klassen (Managed Package Framework) können dazu verwendet werden, mit verwaltetem Code VSPackages zu erstellen. Diese Klassen stellen Standardimplementierungen für viele VSPackage-Schnittstellen bereit. Durch das Ausblenden von Implementierungsdetails und-Komplexitäten, MPF ermöglicht Ihnen die Erstellung [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Integrationsprodukte mit einer minimalen Menge an Code.  
  
> [!WARNING]
>  Die meisten Assemblys, die Managed Package Framework-Klassen enthalten, gehören zum Lieferumfang des Visual Studio SDK. Sie können den Quellcode für Managed Packaged Framework for Projects von [Managed Package Framework for Projects](http://mpfproj11.codeplex.com/)herunterladen.  
  
## <a name="mpf-namespaces"></a>MPF-Namespaces  
 Die folgende Tabelle enthält die MPF-Namespaces, die bereitgestellt werden, indem die [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].  
  
|Namespace|Inhalt|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio>|Enthält Klassen für COM-Fehlerbehandlung, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Konstanten und Win32-Windows.|  
|<xref:Microsoft.VisualStudio.Package>|Wrapper für verwalteten Code enthält [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Projekte, Editoren und MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell>|Umfasst MPF-Basisklassen, aus denen Sie eine Implementierung vieler allgemeiner Visual Studio-Objekte ableiten können.|  
|<xref:Microsoft.VisualStudio.Shell.Design>|Enthält [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Designer-Erweiterungen.|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization>|Enthält [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Serialisierungs-Designer-Erweiterungen.|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization.CodeDom>|Enthält [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] CodeDom-Designer-Erweiterungen.|  
|<xref:Microsoft.VisualStudio.Shell.Flavor>|Unterstützt Projektuntertypen (werden auch als „Konfigurationen“ bezeichnet).|  
  
## <a name="see-also"></a>Siehe auch  
 [VSPackages und das Managed Package Framework](../misc/vspackages-and-the-managed-package-framework.md)   
 [Mithilfe von Visual Studio-Interopassemblys](../extensibility/internals/using-visual-studio-interop-assemblies.md)   
 [VSPackages und das Managed Package Framework](../misc/vspackages-and-the-managed-package-framework.md)
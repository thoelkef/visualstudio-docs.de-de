---
title: Verwenden von MSBuild | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c8b776823c78835ad687a110c1fcc0ba1382bead
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511120"
---
# <a name="using-msbuild"></a>Verwenden von MSBuild
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Verwenden von MSBuild](https://docs.microsoft.com/visualstudio/extensibility/internals/using-msbuild).  
  
MSBuild stellt eine klar definierte, erweiterbares XML-Format für die Erstellung von Projektdateien, die vollständig Projektelemente erstellt werden beschreiben, erstellen Aufgaben und Konfigurationen zu erstellen.  
  
 Ein End-to-End-Beispiel für eine Sprache-Projektsystem auf MSBuild basierende, finden Sie unter der IronPython-Beispiel Deep Dive in die[VSSDK-Beispiele](../../misc/vssdk-samples.md).  
  
## <a name="general-msbuild-considerations"></a>Allgemeine MSBuild-Überlegungen  
 MSBuild-Projektdateien, z. B. [!INCLUDE[csprcs](../../includes/csprcs-md.md)] csproj und [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] VBPROJ-Dateien enthalten Daten, die zum Zeitpunkt der Erstellung verwendet werden, aber auch können enthalten Daten, die zur Entwurfszeit verwendet werden. Build-Time-Daten mithilfe von MSBuild primitive Typen, einschließlich gespeichert [Item-Element (MSBuild)](../../msbuild/item-element-msbuild.md) und [Property-Element (MSBuild)](../../msbuild/property-element-msbuild.md). Während der Entwurfszeit-Daten, die Daten, die für den Projekttyp und alle zugehörigen Projektuntertypen spezifisch sind, werden in der formfreien XML reserviert, damit es gespeichert.  
  
 MSBuild keine systemeigene Unterstützung für Objekte, jedoch bietet bedingte Attribute für das Configuration-spezifische Daten angeben. Zum Beispiel:  
  
```  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 Weitere Informationen zu bedingten Attribute, finden Sie unter [MSBuild Conditional Constructs](../../msbuild/msbuild-conditional-constructs.md).  
  
### <a name="extending-msbuild-for-your-project-type"></a>Erweitern von MSBuild für die Art Ihres Projekts  
 MSBuild-Schnittstellen und APIs unterliegen Änderungen in zukünftigen Versionen von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Aus diesem Grund ist es ratsam, die die verwaltetes Paket-Framework (MPF)-Klassen verwenden, da sie bieten Schutz vor Änderungen.  
  
 Das Managed Package Framework for Projects (MPFProj) stellt Hilfsklassen zum Erstellen und Verwalten von neuen Projektsystem bereit. Anweisungen finden Sie die Quelle Code und die Kompilierung auf [MPF für Visual Studio 2013-Projekte –](http://mpfproj12.codeplex.com/).  
  
 Die projektspezifische MPF-Klassen lauten wie folgt aus:  
  
|Klasse|Implementierung|  
|-----------|--------------------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement` Klasse ist ein Wrapper für MSBuild-Elemente.  
  
#### <a name="single-file-generators-vs-msbuild-tasks"></a>Im Vergleich mit Einzeldatei-Generatoren MSBuild-Aufgaben  
 Generatoren sind einzelne Datei zur Entwurfszeit nur zugegriffen werden kann, aber die MSBuild-Aufgaben zur Entwurfszeit- und Zeitpunkt der Erstellung verwendet werden können. Maximale Flexibilität erhalten müssen Sie daher verwenden Sie MSBuild-Aufgaben transformieren und Generieren von Code. Weitere Informationen finden Sie unter [benutzerdefinierte Tools](../../extensibility/internals/custom-tools.md).  
  
## <a name="see-also"></a>Siehe auch  
 [MSBuild Reference](../../msbuild/msbuild-reference.md)  (MSBuild-Referenz)  
 [MSBuild](http://msdn.microsoft.com/en-us/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)   
 [Benutzerdefinierte Tools](../../extensibility/internals/custom-tools.md)


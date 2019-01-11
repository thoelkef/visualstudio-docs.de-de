---
title: Verwenden von MSBuild | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: de9ab4a6a6591c4a45755b0a9f3682ac5e40c676
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53836766"
---
# <a name="using-msbuild"></a>Verwenden von MSBuild
MSBuild stellt eine klar definierte, erweiterbares XML-Format für die Erstellung von Projektdateien, die vollständig Projektelemente erstellt werden beschreiben, erstellen Aufgaben und Konfigurationen zu erstellen.  
  
## <a name="general-msbuild-considerations"></a>Allgemeine MSBuild-Überlegungen  
 MSBuild-Projektdateien, z. B. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] csproj und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] VBPROJ-Dateien enthalten Daten, die zum Zeitpunkt der Erstellung verwendet werden, aber auch können enthalten Daten, die zur Entwurfszeit verwendet werden. Build-Time-Daten mithilfe von MSBuild primitive Typen, einschließlich gespeichert [Item-Element (MSBuild)](../../msbuild/item-element-msbuild.md) und [Property-Element (MSBuild)](../../msbuild/property-element-msbuild.md). Während der Entwurfszeit-Daten, die Daten, die für den Projekttyp und alle zugehörigen Projektuntertypen spezifisch sind, werden in der formfreien XML reserviert, damit es gespeichert.  
  
 MSBuild keine systemeigene Unterstützung für Objekte, jedoch bietet bedingte Attribute für das Configuration-spezifische Daten angeben. Zum Beispiel:  
  
```xml  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 Weitere Informationen zu bedingten Attribute, finden Sie unter [MSBuild Conditional Constructs](../../msbuild/msbuild-conditional-constructs.md).  
  
### <a name="extending-msbuild-for-your-project-type"></a>Erweitern von MSBuild für die Art Ihres Projekts  
 MSBuild-Schnittstellen und APIs unterliegen Änderungen in zukünftigen Versionen von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Aus diesem Grund ist es ratsam, die die verwaltetes Paket-Framework (MPF)-Klassen verwenden, da sie bieten Schutz vor Änderungen.  
  
 Das Managed Package Framework for Projects (MPFProj) stellt Hilfsklassen zum Erstellen und Verwalten von neuen Projektsystem bereit. Anweisungen finden Sie die Quelle Code und die Kompilierung auf [MPF für Visual Studio 2013-Projekte –](https://github.com/tunnelvisionlabs/MPFProj10).  
  
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
 [MSBuild](../../msbuild/msbuild.md)   
 [Benutzerdefinierte Tools](../../extensibility/internals/custom-tools.md)
---
title: Verwenden von MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 4115d6f1b368734631acf3ee4395d71dbe418c07
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31141450"
---
# <a name="using-msbuild"></a>Verwenden von MSBuild
MSBuild stellt einen klar definierten, erweiterbare XML-Format für die Erstellung von Projektdateien, die vollständig Projektelemente erstellt werden beschreiben, erstellen Aufgaben und Buildkonfiguration.  
  
## <a name="general-msbuild-considerations"></a>MSBuild allgemeine Überlegungen  
 MSBuild-Projektdateien, z. B. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] csproj und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] VBPROJ-Dateien enthalten Daten, die während des Buildvorgangs verwendet, aber auch können Daten enthalten, die zur Entwurfszeit verwendet werden. Zur Buildzeit Daten mithilfe von MSBuild primitive Typen, einschließlich gespeichert [Item-Element (MSBuild)](../../msbuild/item-element-msbuild.md) und [Property-Element (MSBuild)](../../msbuild/property-element-msbuild.md). Entwurfszeitdaten, die Daten, die spezifisch für den Projekttyp und alle Untertypen verknüpftes Projekt ist, werden im Freiform-XML-Code für sie reserviert gespeichert.  
  
 MSBuild keine systemeigene Unterstützung für Konfigurationsobjekte jedoch leistet bedingte Attribute für die Konfiguration-spezifische Daten angeben. Zum Beispiel:  
  
```xml  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 Weitere Informationen über bedingte Attribute finden Sie unter [Bedingte Konstrukte](../../msbuild/msbuild-conditional-constructs.md).  
  
### <a name="extending-msbuild-for-your-project-type"></a>Erweitern von MSBuild für den Projekttyp  
 MSBuild-Schnittstellen und APIs sind, unterliegt in zukünftigen Versionen des [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Daher ist es unerlässlich, die verwaltete Package Framework (MPF) Klassen zu verwenden, da sie bieten Schutz vor Änderungen.  
  
 Das Managed Package Framework for Projects (MPFProj) stellt Hilfsklassen zum Erstellen und verwalten neue Projektsystem bereit. Code und Kompilierung Anweisungen an der Quelle gefunden [MPF für Visual Studio 2013-Projekte -](http://mpfproj12.codeplex.com/).  
  
 Die projektspezifische MPF-Klassen sind wie folgt:  
  
|Klasse|Implementierung|  
|-----------|--------------------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement` Klasse ist ein Wrapper für die MSBuild-Elemente.  
  
#### <a name="single-file-generators-vs-msbuild-tasks"></a>Im Vergleich mit Einzeldatei-Generatoren MSBuild-Aufgaben  
 Generatoren werden einzelne Datei zur Entwurfszeit nur zugegriffen werden kann, aber die MSBuild-Aufgaben, die zur Entwurfszeit und zur Buildzeit verwendet werden können. Maximale Flexibilität erhalten Sie deshalb verwenden Sie MSBuild-Aufgaben für die Transformierung und Generieren von Code. Weitere Informationen finden Sie unter [benutzerdefinierte Tools](../../extensibility/internals/custom-tools.md).  
  
## <a name="see-also"></a>Siehe auch  
 [MSBuild Reference](../../msbuild/msbuild-reference.md)  (MSBuild-Referenz)  
 [MSBuild](../../msbuild/msbuild.md)   
 [Benutzerdefinierte Tools](../../extensibility/internals/custom-tools.md)
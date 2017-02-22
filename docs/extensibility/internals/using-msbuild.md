---
title: "Verwenden von MSBuild | Microsoft Docs"
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
  - "VSPackages, Kompilieren mit MSBuild"
  - "MSBuild-Erweiterbarkeit"
  - "Pakete, die beim Kompilieren mit MSBuild"
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Verwenden von MSBuild
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

MSBuild stellt eine klar definierte, erweiterbare XML\-Format für Projektdateien, die vollständig beschreiben erstellt werden, das Erstellen von Aufgaben und das Buildkonfigurationen erstellen.  
  
 Ein End\-to\-End\-Beispiel von einer Sprache Projektsystem basierend auf MSBuild finden Sie unter der IronPython\-Beispiel tiefer in die[VSSDK\-Beispiele](../../misc/vssdk-samples.md).  
  
## Allgemeine MSBuild\-Aspekte  
 MSBuild\-Projektdateien, z. B. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] .csproj und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] VBPROJ\-Dateien enthalten Daten, die zur Buildzeit verwendet werden, aber auch können enthalten Daten, die zur Entwurfszeit verwendet werden. Zur Buildzeit mithilfe gespeichert MSBuild primitive Typen, einschließlich [Item Element \(MSBuild\)](../../msbuild/item-element-msbuild.md) und [Property Element \(MSBuild\)](../../msbuild/property-element-msbuild.md). Während der Entwurfszeit\-Daten, die Daten für den Projekttyp und alle Untertypen verknüpftes Projekt spezifisch sind, werden in freier Form XML reserviert gespeichert.  
  
 MSBuild bietet bedingten Attribute für die Angabe von Konfigurations\-spezifische Daten jedoch keine systemeigene Unterstützung für Objekte. Zum Beispiel:  
  
```  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 Weitere Informationen zu bedingten Attribute, finden Sie unter [Conditional Constructs](../../msbuild/msbuild-conditional-constructs.md).  
  
### Erweitern von MSBuild für den Projekttyp  
 MSBuild\-Schnittstellen und APIs werden in zukünftigen Versionen von geändert [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Aus diesem Grund ist es ratsam, die verwaltete Package Framework \(MPF\)\-Klassen verwenden, bieten Schutz vor Änderungen.  
  
 Der Managed Package Framework für Projekte \(MPFProj\) enthält Hilfsklassen für das Erstellen und Verwalten von neuen Projektsystem. Anweisungen finden Sie die Quelle erstellen und Kompilieren von Code zur [MPF für Visual Studio 2013\-Projekte \-](http://mpfproj12.codeplex.com/).  
  
 Die projektspezifische MPF\-Klassen sind wie folgt:  
  
|Klasse|Implementierung|  
|------------|---------------------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement` Klasse ist ein Wrapper für die MSBuild\-Elemente.  
  
#### Vs Einzeldatei\-Generatoren. MSBuild\-Aufgaben  
 Generatoren sind einzelne Datei zur Entwurfszeit nur zugegriffen werden kann, aber die MSBuild\-Aufgaben können zur Entwurfszeit und zur Buildzeit verwendet werden. Maximale Flexibilität erhalten Sie daher verwenden Sie MSBuild\-Aufgaben für die Transformierung und Generieren von Code. Weitere Informationen finden Sie unter [Benutzerdefinierte Tools](../../extensibility/internals/custom-tools.md).  
  
## Siehe auch  
 [MSBuild Reference](../../msbuild/msbuild-reference.md)   
 [MSBuild](http://msdn.microsoft.com/de-de/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)   
 [Benutzerdefinierte Tools](../../extensibility/internals/custom-tools.md)
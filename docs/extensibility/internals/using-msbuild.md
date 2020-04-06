---
title: Verwenden von MSBuild | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, compiling with MSBuild
- MSBuild, extensibility
- packages, compiling with MSBuild
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f961249ff584f7767dc2505bb20b1fb0961b7dd3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704285"
---
# <a name="using-msbuild"></a>Verwenden von MSBuild
MSBuild stellt ein klar definiertes, erweiterbares XML-Format zum Erstellen von Projektdateien bereit, in dem die zu erstellenden Projektelemente vollständig beschrieben, Aufgaben erstellt und Konfigurationen erstellt werden.

## <a name="general-msbuild-considerations"></a>Allgemeine MSBuild-Überlegungen
 MSBuild-Projektdateien, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] z. B. [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .csproj- und VBproj-Dateien, enthalten Daten, die zur Erstellungszeit verwendet werden, können aber auch Daten enthalten, die zur Entwurfszeit verwendet werden. Buildzeitdaten werden mit MSBuild-Primitiven gespeichert, einschließlich [Elementelement (MSBuild)](../../msbuild/item-element-msbuild.md) und [Eigenschaftselement (MSBuild)](../../msbuild/property-element-msbuild.md). Entwurfszeitdaten, bei denen es sich um Daten handelt, die für den Projekttyp und alle zugehörigen Projektuntertypen spezifisch sind, werden in Freiform-XML gespeichert, das für ihn reserviert ist.

 MSBuild unterstützt keine systemeigene Unterstützung für Konfigurationsobjekte, stellt jedoch bedingte Attribute zum Angeben konfigurationsspezifischer Daten bereit. Beispiel:

```xml
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>
```

 Weitere Informationen zu bedingten Attributen finden Sie unter [Bedingte Konstrukte](../../msbuild/msbuild-conditional-constructs.md).

### <a name="extending-msbuild-for-your-project-type"></a>Erweitern von MSBuild für Ihren Projekttyp
 MSBuild-Schnittstellen und APIs können sich in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]zukünftigen Versionen von ändern. Daher ist es ratsam, die MPF-Klassen (Managed Package Framework) zu verwenden, da sie eine Abschirmung vor Änderungen bieten.

 Das Managed Package Framework for Projects (MPFProj) bietet Hilfsklassen zum Erstellen und Verwalten eines neuen Projektsystems. Den Quellcode und die Kompilierungsanweisungen finden Sie unter [MPF for Projects - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Die projektspezifischen MPF-Klassen lauten wie folgt:

|Klasse|Implementierung|
|-----------|--------------------|
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|

 `Microsoft.VisualStudio.Package.ProjectElement`Class ist ein Wrapper für MSBuild-Elemente.

#### <a name="single-file-generators-vs-msbuild-tasks"></a>Einzeldateigeneratoren im Vergleich zu MSBuild-Aufgaben
 Auf einzelne Dateigeneratoren kann nur zur Entwurfszeit zugegriffen werden, msBuild-Aufgaben können jedoch zur Entwurfszeit und zur Buildzeit verwendet werden. Verwenden Sie daher MSBuild-Aufgaben, um Code zu transformieren und zu generieren, um maximale Flexibilität zu erzielen. Weitere Informationen finden Sie unter [Benutzerdefinierte Tools](../../extensibility/internals/custom-tools.md).

## <a name="see-also"></a>Weitere Informationen
- [MSBuild Reference](../../msbuild/msbuild-reference.md) (MSBuild-Referenz)
- [MSBuild](../../msbuild/msbuild.md)
- [Benutzerdefinierte Tools](../../extensibility/internals/custom-tools.md)

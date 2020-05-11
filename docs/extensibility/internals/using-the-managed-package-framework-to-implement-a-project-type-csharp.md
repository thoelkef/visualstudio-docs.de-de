---
title: Verwenden des Verwalteten Paketframeworks für einen Projekttyp | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ca9dda0b699e0f70b0c945ab9ecfe9f9f4dcda6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704118"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Verwenden des Managed Package Framework zum Implementieren eines Projekttyps (C#)
Das Managed Package Framework (MPF) stellt C-Klassen bereit, von denen Sie ihre eigenen Projekttypen verwenden oder erben können. Das MPF implementiert viele der Schnittstellen, die Visual Studio von einem Projekttyp erwartet, sodass Sie sich auf die Implementierung der Besonderheiten Ihres Projekttyps konzentrieren können.

## <a name="using-the-mpf-project-source-code"></a>Verwenden des MPF-Projektquellcodes
 Das Managed Package Framework for Projects (MPFProj) bietet Hilfsklassen zum Erstellen und Verwalten eines neuen Projektsystems. Im Gegensatz zu anderen Klassen im MPF sind die Projektklassen nicht in den Assemblys enthalten, die mit Visual Studio ausgeliefert werden. Stattdessen werden die Projektklassen als Quellcode bei [MPF for Projects 2013](https://github.com/tunnelvisionlabs/MPFProj10)bereitgestellt.

 Gehen Sie wie folgt vor, um dieses Projekt zu Ihrer VSPackage-Lösung hinzuzufügen:

1. Laden Sie die MPFProj-Dateien auf *MPFProjectDir*herunter.

2. Ändern Sie in der *Datei MPFProjectDir*, Dev10, Src, CSharp, ProjectBase.file, den folgenden Block:

```
<!-- Provide a default value for $(ProjectBasePath) -->
  <PropertyGroup>
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>
  </PropertyGroup>
```

1. Erstellen Sie ein VSPackage-Projekt.

2. Entladen Sie das VSPackage-Projekt.

3. Bearbeiten Sie die VsPackage .csproj-Datei, `<Import>` indem Sie den folgenden Block vor den anderen Blöcken hinzufügen:

```
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />
  <PropertyGroup>
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.
    <TargetRegistryRoot></TargetRegistryRoot>-->
    <RegisterOutputPackage>true</RegisterOutputPackage>
    <RegisterWithCodebase>true</RegisterWithCodebase>
  </PropertyGroup>
```

1. Speichern Sie das Projekt.

2. Schließen Sie die VSPackage-Lösung, und öffnen Sie sie erneut.

3. Öffnen Sie das VSPackage-Projekt erneut. Es sollte ein neues Verzeichnis mit dem Namen ProjectBase angezeigt werden.

4. Fügen Sie den folgenden Verweis auf das VSPackage-Projekt hinzu:

     Microsoft.Build.Tasks.4.0

5. Erstellen Sie das Projekt.

## <a name="hierarchy-classes"></a>Hierarchieklassen
 In der folgenden Tabelle werden die Klassen im MPFProj zusammengefasst, die Projekthierarchien unterstützen. Weitere Informationen finden Sie unter [Hierarchien und Auswahl](../../extensibility/internals/hierarchies-and-selection.md).

|Klassenname|
|----------------|
|`Microsoft.VisualStudio.Package.HierarchyNode`|
|`Microsoft.VisualStudio.Package.ProjectNode`|
|`Microsoft.VisualStudio.Package.ProjectContainerNode`|
|`Microsoft.VisualStudio.Package.FileNode`|
|`Microsoft.VisualStudio.Package.FolderNode`|
|`Microsoft.VisualStudio.Package.ReferenceContainerNode`|
|`Microsoft.VisualStudio.Package.ReferenceNode`|
|`Microsoft.VisualStudio.Package.ProjectReferenceNode`|
|`Microsoft.VisualStudio.Package.ComReferenceNode`|
|`Microsoft.VisualStudio.Package.AssemblyReferenceNode`|
|`Microsoft.VisualStudio.Package.BuildDependency`|

## <a name="document-handling-classes"></a>Dokumentbehandlungsklassen
 In der folgenden Tabelle sind die Klassen in der MPF aufgeführt, die die Dokumentbehandlung unterstützen. Weitere Informationen finden Sie unter [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md).

|Klassenname|
|----------------|
|`Microsoft.VisualStudio.Package.DocumentManager`|
|`Microsoft.VisualStudio.Package.FileDocumentManager`|

## <a name="configuration-and-output-classes"></a>Konfigurations- und Ausgabeklassen
 In der folgenden Tabelle sind die Klassen in der MPF aufgeführt, die Projekttypen mehrere Konfigurationen unterstützen lassen, z. B. Debuggen und Release sowie Sammlungen von Projektausgaben. Weitere Informationen finden Sie unter [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md).

|Klassenname|
|----------------|
|`Microsoft.VisualStudio.Package.ConfigProvider`|
|`Microsoft.VisualStudio.Package.ProjectConfig`|
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|
|`Microsoft.VisualStudio.Package.OutputGroup`|
|`Microsoft.VisualStudio.Package.ProjectElement`|

## <a name="automation-support-classes"></a>Automatisierungs-Support-Klassen
 In der folgenden Tabelle sind die Klassen in der MPF aufgeführt, die die Automatisierung unterstützen, damit Benutzer Des Projekttyps Add-Ins schreiben können.

|Klassenname|
|----------------|
|`Microsoft.VisualStudio.Package.Automation.OAProject`|
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|

## <a name="properties-classes"></a>Eigenschaftenklassen
 In der folgenden Tabelle sind die Klassen in der MPF aufgeführt, mit denen Projekttypen Eigenschaften hinzufügen können, die Benutzer in einem Eigenschaftenbrowser durchsuchen und ändern können.

|Klassenname|
|----------------|
|`Microsoft.VisualStudio.Package.LocalizableProperties`|
|`Microsoft.VisualStudio.Package.NodeProperties`|
|`Microsoft.VisualStudio.Package.FileNodeProperties`|
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|

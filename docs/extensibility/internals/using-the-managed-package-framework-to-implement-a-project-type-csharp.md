---
title: "Mithilfe des Managed Package Framework für ein Projekt (c#) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 16e1d301e5a3977f656c52f9c97eb43ee216075f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Mithilfe des Managed Package Frameworks implementiert einen Projekttyp (c#)
Das Managed Package Framework (MPF) stellt die C#-Klassen, die Sie zum Implementieren Ihrer eigenen Projekttypen Vererben oder verwenden können. Das MPF implementiert viele der Schnittstellen, die Visual Studio ein Projekt bereitstellen, erwartet, verlassen Sie kann nach Belieben implementieren die Angaben für den Projekttyp konzentrieren.  
  
## <a name="using-the-mpf-project-source-code"></a>Verwenden den Quellcode des MPF-Projekt  
 Das Managed Package Framework for Projects (MPFProj) stellt Hilfsklassen zum Erstellen und verwalten neue Projektsystem bereit. Im Gegensatz zu anderen Klassen in das MPF sind die Projektklassen nicht in den Assemblys, die im Lieferumfang von Visual Studio enthalten. Stattdessen werden die Projektklassen bereitgestellt, als Quellcode an [MPF für Projekte 2013](http://mpfproj12.codeplex.com).  
  
 Um dieses Projekt zur Projektmappe VSPackage hinzuzufügen, führen Sie folgende Schritte aus:  
  
1.  Herunterladen von Dateien MPFProj *MPFProjectDir*.  
  
2.  In der *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file, ändern Sie den folgenden Block:  
  
```  
<!-- Provide a default value for $(ProjectBasePath) -->  
  <PropertyGroup>  
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>  
  </PropertyGroup>  
```  
  
1.  Erstellen Sie ein VSPackage-Projekt.  
  
2.  Entladen Sie das VSPackage-Projekt.  
  
3.  Bearbeiten Sie die VSPackage-CSPROJ-Datei durch den folgenden Block vor dem anderen hinzufügen `<Import>` blockiert:  
  
```  
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />  
  <PropertyGroup>  
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.  
    <TargetRegistryRoot></TargetRegistryRoot>-->  
    <RegisterOutputPackage>true</RegisterOutputPackage>  
    <RegisterWithCodebase>true</RegisterWithCodebase>  
  </PropertyGroup>  
```  
  
1.  Speichern Sie das Projekt.  
  
2.  Schließen Sie und öffnen Sie die VSPackage-Lösung.  
  
3.  Öffnen Sie das VSPackage-Projekt erneut. Ein neues Verzeichnis mit dem Namen ProjectBase sollte angezeigt werden.  
  
4.  Fügen Sie den folgenden Verweis auf das VSPackage-Projekt hinzu:  
  
     Microsoft.Build.Tasks.4.0  
  
5.  Erstellen Sie das Projekt.  
  
## <a name="hierarchy-classes"></a>Hierarchie-Klassen  
 In der folgenden Tabelle werden die Klassen in der MPFProj, Projekt-Hierarchien unterstützen, zusammengefasst. Weitere Informationen finden Sie unter [Hierarchien und Auswahl](../../extensibility/internals/hierarchies-and-selection.md).  
  
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
  
## <a name="document-handling-classes"></a>Handhabung Klassen  
 Die folgende Tabelle enthält die Klassen in das MPF, die Handhabung von Dokumenten zu unterstützen. Weitere Informationen finden Sie unter [öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md).  
  
|Klassenname|  
|----------------|  
|`Microsoft.VisualStudio.Package.DocumentManager`|  
|`Microsoft.VisualStudio.Package.FileDocumentManager`|  
  
## <a name="configuration-and-output-classes"></a>Konfiguration und Ausgabeklassen  
 Die folgende Tabelle enthält die Klassen in das MPF, mit denen Projekttypen, die mehrere Konfigurationen, z. B. Debug und Release sowie Auflistungen von Projektausgabe unterstützen können. Weitere Informationen finden Sie unter [Konfigurationsoptionen verwalten](../../extensibility/internals/managing-configuration-options.md).  
  
|Klassenname|  
|----------------|  
|`Microsoft.VisualStudio.Package.ConfigProvider`|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|  
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|  
|`Microsoft.VisualStudio.Package.OutputGroup`|  
|`Microsoft.VisualStudio.Package.ProjectElement`|  
  
## <a name="automation-support-classes"></a>Automatisierungsunterstützung Klassen  
 Die folgende Tabelle enthält die Klassen in das MPF, die Unterstützung der Automatisierung, damit Benutzer Ihres Typs Project-add-ins schreiben können.  
  
|Klassenname|  
|----------------|  
|`Microsoft.VisualStudio.Package.Automation.OAProject`|  
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|  
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|  
  
## <a name="properties-classes"></a>Eigenschaften von Klassen  
 Die folgende Tabelle enthält die Klassen in das MPF, mit denen Projekttypen können hinzufügen Eigenschaften im Eigenschaftenbrowser ändern, dass Benutzer navigieren können.  
  
|Klassenname|  
|----------------|  
|`Microsoft.VisualStudio.Package.LocalizableProperties`|  
|`Microsoft.VisualStudio.Package.NodeProperties`|  
|`Microsoft.VisualStudio.Package.FileNodeProperties`|  
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|  
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|  
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
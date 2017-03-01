---
title: "Mithilfe von verwalteten Paketframework für den Projekttyp (c#) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: 1d70a70b942b3722ed61e1e8a2f2e54d96b916e4
ms.lasthandoff: 02/22/2017

---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Mithilfe von verwalteten Paketframework implementieren einen Projekttyp (c#)
Managed Package Framework (MPF) bietet C#-Klassen, die Sie verwenden können, oder eigene Projekttypen implementieren erben. Die MPF implementiert viele Schnittstellen in Visual Studio einen Projekttyp bereit, erwartet verlassen Sie kostenlos die Konzentration auf die Angaben des Projekttyps implementieren.  
  
## <a name="using-the-mpf-project-source-code"></a>Verwenden den Quellcode der MPF-Projekt  
 Der Managed Package Framework für Projekte (MPFProj) enthält Hilfsklassen für das Erstellen und Verwalten von neuen Projektsystem. Im Gegensatz zu anderen Klassen in der MPF sind die Projektklassen in den Assemblys, die im Lieferumfang von Visual Studio nicht enthalten. Die Projektklassen werden stattdessen als Quellcode unter bereitgestellt [MPF für Projekte 2013](http://mpfproj12.codeplex.com).  
  
 Um dieses Projekt zur Projektmappe VSPackage hinzuzufügen, führen Sie folgende Schritte aus:  
  
1.  Laden Sie die MPFProj auf *MPFProjectDir*.  
  
2.  In der *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file, ändern Sie den folgenden Block:  
  
```  
<!-- Provide a default value for $(ProjectBasePath) -->  
  <PropertyGroup>  
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>  
  </PropertyGroup>  
```  
  
1.  Erstellen Sie ein VSPackage-Projekt.  
  
2.  Entladen Sie das VSPackage-Projekt wird.  
  
3.  Bearbeiten Sie die VSPackage CSPROJ-Datei durch den folgenden Block vor den anderen hinzufügen `<Import>` blockiert:  
  
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
  
2.  Schließen Sie und öffnen Sie die VSPackage-Projektmappe.  
  
3.  Öffnen Sie das VSPackage-Projekt erneut. Ein neues Verzeichnis namens ProjectBase sollte angezeigt werden.  
  
4.  Fügen Sie den folgenden Verweis in VSPackage-Projekt:  
  
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
 Die folgende Tabelle enthält die Klassen in der MPF, die Handhabung von Dokumenten unterstützen. Weitere Informationen finden Sie unter [öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md).  
  
|Klassenname|  
|----------------|  
|`Microsoft.VisualStudio.Package.DocumentManager`|  
|`Microsoft.VisualStudio.Package.FileDocumentManager`|  
  
## <a name="configuration-and-output-classes"></a>Konfiguration und Klassen für die Ausgabe  
 In der folgenden Tabelle werden die Klassen in der MPF, mit denen unterstützt mehrere Konfigurationen, z. B. Debug und Release und Sammlungen der Projektausgabe Projekttypen aufgeführt. Weitere Informationen finden Sie unter [Konfigurationsoptionen verwalten](../../extensibility/internals/managing-configuration-options.md).  
  
|Klassenname|  
|----------------|  
|`Microsoft.VisualStudio.Package.ConfigProvider`|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|  
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|  
|`Microsoft.VisualStudio.Package.OutputGroup`|  
|`Microsoft.VisualStudio.Package.ProjectElement`|  
  
## <a name="automation-support-classes"></a>Benutzeroberflächenautomatisierungs-Unterstützung Klassen  
 Die folgende Tabelle enthält die Klassen in der MPF, die die Automatisierung unterstützen, damit Benutzer des Projekttyps-add-ins schreiben können.  
  
|Klassenname|  
|----------------|  
|`Microsoft.VisualStudio.Package.Automation.OAProject`|  
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|  
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|  
  
## <a name="properties-classes"></a>Eigenschaften von Klassen  
 Die folgende Tabelle enthält die Klassen in der MPF, mit denen Projekttypen hinzufügen Eigenschaften im Eigenschaftenbrowser ändern, dass Benutzer navigieren können.  
  
|Klassenname|  
|----------------|  
|`Microsoft.VisualStudio.Package.LocalizableProperties`|  
|`Microsoft.VisualStudio.Package.NodeProperties`|  
|`Microsoft.VisualStudio.Package.FileNodeProperties`|  
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|  
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|  
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|

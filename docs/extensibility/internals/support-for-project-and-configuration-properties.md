---
title: "Unterst&#252;tzung f&#252;r Projekt- und Konfigurationseigenschaften | Microsoft Docs"
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
  - "Projekteigenschaften, die mit Visual Studio SDK"
  - "Konfigurationseigenschaften, Suppporting mit Visual Studio SDK"
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
---
# Unterst&#252;tzung f&#252;r Projekt- und Konfigurationseigenschaften
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die **Eigenschaften** Fenster in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung \(IDE\) kann Projekt\-und Konfiguration anzeigen. Sie können eine Eigenschaftenseite für Ihren eigenen Projekttyp bereitstellen, sodass der Benutzer die Eigenschaften für die Anwendung festlegen kann.  
  
 Durch Auswahl eines Knotens Projekt in **Projektmappen\-Explorer** und klicken Sie dann auf **Eigenschaften** auf der **Projekt** Menü öffnen Sie ein Dialogfeld, das Projekt und den Konfigurationseigenschaften enthält. In [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], und Projekttypen abgeleitet diese Sprachen wird das Dialogfeld angezeigt wird, als eine Seite im Registerformat, in der [Allgemein, Umgebung, Dialogfeld "Optionen"](../../ide/reference/general-environment-options-dialog-box.md). Weitere Informationen finden Sie unter [nicht im Build: Exemplarische Vorgehensweise: Verfügbarmachen von Projekt\- und Konfigurationseigenschaften \(c\#\)](http://msdn.microsoft.com/de-de/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).  
  
 Der Managed Package Framework für Projekte \(MPFProj\) enthält Hilfsklassen für das Erstellen und Verwalten von neuen Projektsystem. Anweisungen finden Sie die Quelle erstellen und Kompilieren von Code zur [MPF für Visual Studio 2013\-Projekte \-](http://mpfproj12.codeplex.com/).  
  
## Dauerhaftigkeit von Projekt\- und Konfigurationseigenschaften  
 Projekt\-und Konfiguration werden in einer Projektdatei beibehalten, die eine Erweiterung der Projekttyp zugeordnet sind, wie z. B. .csproj, .vbproj und .myproj verfügt. Sprachprojekte verwenden in der Regel eine Vorlagendatei, um die Datei zu generieren. Es gibt jedoch tatsächlich mehrere Methoden zum Zuordnen von Projekttypen und Vorlagen. Weitere Informationen finden Sie unter [NIB: Visual Studio\-Vorlagen](http://msdn.microsoft.com/de-de/141fccaa-d68f-4155-822b-27f35dd94041) und [Beschreibung der Vorlage Verzeichnis \(. VSDIR\)\-Dateien](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
 Projekt\-und Konfiguration werden durch Hinzufügen von Elementen in der Vorlagendatei erstellt. Diese Eigenschaften stehen dann zu einem Projekt erstellt, indem Sie mit dem Projekttyp, der diese Vorlage verwendet.[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Projekte und die MPFProj beide verwenden den [nicht im Build: Übersicht über MSBuild](http://msdn.microsoft.com/de-de/b588fd73-a45b-4706-908f-cc131bccfbde) Schema für Vorlagendateien. Diese Dateien haben einen Abschnitt "PropertyGroup" für jede Konfiguration. Eigenschaften von Projekten bleiben in der Regel im ersten Abschnitt PropertyGroup über eine konfigurationsargument auf eine leere Zeichenfolge festgelegt.  
  
 Der folgende Code zeigt den Anfang einer einfachen MSBuild\-Projektdatei.  
  
```  
<Project MSBuildVersion="2.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Name>SomeProjectSix</Name>  
    <SchemaVersion>2.0</SchemaVersion>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
    <Optimize>false</Optimize>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">  
    <Optimize>true</Optimize>  
```  
  
 In dieser Projektdatei `<Name>` und `<SchemaVersion>` werden Projekteigenschaften und `<Optimize>` sind eine Konfigurationseigenschaft.  
  
 Es ist die Aufgabe des Projekts, um das Projekt und den Konfigurationseigenschaften der Projektdatei beibehalten werden.  
  
> [!NOTE]
>  Ein Projekt kann Persistenz durch Beibehalten von nur Eigenschaftswerte optimieren, die von ihren Standardwerten abweichen.  
  
## Unterstützung für Projekt\- und Konfigurationseigenschaften  
 Die `Microsoft.VisualStudio.Package.SettingsPage` \-Klasse implementiert die Eigenschaftenseiten für Projekt und Konfiguration. Die standardmäßige Implementierung des `SettingsPage` öffentliche Eigenschaften für einen Benutzer in einem generischen Eigenschaftenraster bietet. Die `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` \-Methode wählt von abgeleitete Klassen `SettingsPage` für Projekt Eigenschaftenraster. Die `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` \-Methode wählt von abgeleitete Klassen `SettingsPage` für Konfiguration Eigenschaftenraster. Projekttyp sollten diese Methoden wählen Sie die entsprechenden Eigenschaftenseiten außer Kraft setzen.  
  
 Die `SettingsPage` Klasse und die `Microsoft.VisualStudio.Package.ProjectNode` \-Klasse bietet diese Methoden zum Projekt und den Konfigurationseigenschaften beibehalten:  
  
-   `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` und `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` Eigenschaften beizubehalten.  
  
-   `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` und `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` Eigenschaften beizubehalten.  
  
    > [!NOTE]
    >  Die Implementierungen der `Microsoft.VisualStudio.Package.SettingsPage` und `Microsoft.VisualStudio.Package.ProjectNode` Klassen verwenden die `Microsoft.Build.BuildEngine` \(MSBuild\) Methoden zum Abrufen und Festlegen von Projekt\-und Konfiguration aus der Projektdatei.  
  
 Die Klasse von ableiten `SettingsPage` implementieren müssen `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` und `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` Projekt oder die Konfiguration von Eigenschaften der Projektdatei beibehalten werden.  
  
## ProvideObjectAttribute und Registrierungspfad  
 Abgeleitete Klassen `SettingsPage` VSPackages gemeinsam verwendet werden sollen. Um ein VSPackage erstellen eine abgeleitete Klasse ermöglichen `SettingsPage`, Hinzufügen einer `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` zu einer Klasse abgeleitet `Microsoft.VisualStudio.Shell.Package`.  
  
 [!code-cs[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]  
  
 Das VSPackage, das das Attribut zugeordnet ist, ist unwichtig. Bei der Registrierung ein VSPackage mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], registriert die Klassen\-Id \(CLSID\) eines Objekts, das erstellt werden kann, damit ein Aufruf von <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> erstellen können.  
  
 Der Registrierungspfad der ein Objekt, das erstellt werden kann wird bestimmt durch Kombination von <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, die Word, CLSID und die Guid des Objekttyps. Wenn `MyProjectPropertyPage` \-Klasse verfügt über eine Guid vom {3c693da2\-5bca\-49b3\-bd95\-ffe0a39dd723} die UserRegistryRoot HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp ist, und der Registrierungspfad wäre HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp\\CLSID\\{3c693da2\-5bca\-49b3\-bd95\-ffe0a39dd723}.  
  
## Projekt und Konfigurationsattribute\-Eigenschaft und des Layouts  
 Die <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute>, und <xref:System.ComponentModel.DescriptionAttribute> Attribute bestimmen, Layout, Beschriftung und Beschreibung des Projekts und Konfiguration Eigenschaften eine generische Seite. Diese Attribute bestimmen Sie die Kategorie, Anzeigename und Beschreibung der Option bzw..  
  
> [!NOTE]
>  Entsprechende Attribute, SRCategory, LocDisplayName und SRDescription, verwenden von Zeichenfolgenressourcen für die Lokalisierung und werden in definiert [MPF für Visual Studio 2013\-Projekte \-](http://mpfproj12.codeplex.com/).  
  
 Betrachten Sie das folgende Codefragment:  
  
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-cs[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]  
  
 Die `MyConfigProp` Configuration\-Eigenschaft wird auf der Konfigurationsseite für die Eigenschaft als **Meine Konfigurationseigenschaft** in der Kategorie **Meine Kategorie**. Wenn die Option ausgewählt ist, die Beschreibung der **Meine Beschreibung**, wird im Beschreibungsbereich angezeigt.  
  
## Siehe auch  
 [Nicht im Build: Exemplarische Vorgehensweise: Verfügbarmachen von Projekt\- und Konfigurationseigenschaften \(c\#\)](http://msdn.microsoft.com/de-de/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)   
 [Hinzufügen und Entfernen von Eigenschaftenseiten](../../extensibility/adding-and-removing-property-pages.md)   
 [VSPackage\-Status](../../misc/vspackage-state.md)   
 [Projekte](../../extensibility/internals/projects.md)   
 [NIB: Visual Studio\-Vorlagen](http://msdn.microsoft.com/de-de/141fccaa-d68f-4155-822b-27f35dd94041)   
 [Beschreibung der Vorlage Verzeichnis \(. VSDIR\)\-Dateien](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
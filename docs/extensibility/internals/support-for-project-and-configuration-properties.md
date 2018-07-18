---
title: Unterstützung für das Projekt und Konfigurationseigenschaften | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, suppporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 823bfa0453d3e33fea2daa51779b1fe4800a1a86
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133574"
---
# <a name="support-for-project-and-configuration-properties"></a>Unterstützung für das Projekt und Konfigurationseigenschaften
Die **Eigenschaften** Fenster in den [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE)-Projekt und den Konfigurationseigenschaften anzeigen kann. Sie können eine Eigenschaftenseite für Ihren eigenen Projekttyp bereitstellen, damit der Benutzer die Eigenschaften für die Anwendung festlegen kann.  
  
 Dazu einen Projektknoten **Projektmappen-Explorer** und dann auf **Eigenschaften** auf die **Projekt** Menü öffnen Sie ein Dialogfeld, das Projekt und die Konfiguration enthält Eigenschaften. In [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], und Projekttypen abgeleitet wurde. diese Sprachen dieses Dialogfeld wird angezeigt, als eine Seite im Registerformat, in der [Allgemein, Umgebung, Optionen (Dialogfeld)](../../ide/reference/general-environment-options-dialog-box.md). Weitere Informationen finden Sie unter [nicht im Build: Exemplarische Vorgehensweise: Verfügbarmachen von Projekt- und Konfigurationseigenschaften (c#)](http://msdn.microsoft.com/en-us/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).  
  
 Das Managed Package Framework for Projects (MPFProj) stellt Hilfsklassen zum Erstellen und verwalten neue Projektsystem bereit. Code und Kompilierung Anweisungen an der Quelle gefunden [MPF für Visual Studio 2013-Projekte -](http://mpfproj12.codeplex.com/).  
  
## <a name="persistence-of-project-and-configuration-properties"></a>Dauerhaftigkeit von Projekt- und Konfigurationseigenschaften  
 Projekt-und Konfiguration werden in einer Projektdatei beibehalten, die Dateinamenerweiterung, die den Projekttyp zugeordnet sind, wie z. B., .csproj, .vbproj und .myproj verfügt. -Sprachprojekte verwenden in der Regel eine Datei für Prozessvorlagen, um die Projektdatei zu generieren. Es gibt jedoch tatsächlich mehrere Möglichkeiten zum Zuordnen von Projekttypen und Vorlagen. Weitere Informationen finden Sie unter [Vorlagenbeschreibung-Verzeichnis (. VSDIR)-Dateien](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
 Projekt-und Konfiguration werden durch Hinzufügen von Elementen in der Vorlagendatei erstellt. Diese Eigenschaften stehen dann zu einem Projekt erstellt, die mit den Projekttyp, der diese Vorlage verwendet. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Projekte und die MPFProj beide verwenden den [nicht im Build: Übersicht über MSBuild](http://msdn.microsoft.com/en-us/b588fd73-a45b-4706-908f-cc131bccfbde) Schema für die Vorlagendateien. Diese Dateien müssen einen PropertyGroup-Abschnitt für jede Konfiguration. Eigenschaften von Projekten werden in der Regel in den ersten Abschnitt PropertyGroup beibehalten besitzt eine konfigurationsargument, das auf eine null-Zeichenfolge festgelegt.  
  
 Der folgende Code zeigt den Anfang einer einfachen MSBuild-Projektdatei.  
  
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
  
 Es liegt die Verantwortung des Projekts, um das Projekt und den Konfigurationseigenschaften der Projektdatei beibehalten werden.  
  
> [!NOTE]
>  Ein Projekt kann Persistenz durch das Beibehalten von nur Eigenschaftswerte optimieren, die von ihren Standardwerten abweichen.  
  
## <a name="support-for-project-and-configuration-properties"></a>Unterstützung für das Projekt und Konfigurationseigenschaften  
 Die `Microsoft.VisualStudio.Package.SettingsPage` Klasse implementiert die Eigenschaftenseiten für Projekt und Konfiguration. Die standardmäßige Implementierung des `SettingsPage` öffentliche Eigenschaften für einen Benutzer in einem generischen Eigenschaftenraster bietet. Die `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` Methode wählt von abgeleitete Klassen `SettingsPage` für Projekt Eigenschaftenrastern. Die `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` Methode wählt von abgeleitete Klassen `SettingsPage` für die Konfiguration von Eigenschaftenrastern. Der Projekttyp sollten diese Methoden zum Auswählen der entsprechenden Eigenschaftenseiten überschreiben.  
  
 Die `SettingsPage` Klasse und die `Microsoft.VisualStudio.Package.ProjectNode` Klasse bieten diese Methoden zum Projekt und den Konfigurationseigenschaften beibehalten:  
  
-   `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` und `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` Projekteigenschaften beizubehalten.  
  
-   `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` und `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` Konfigurationseigenschaften beizubehalten.  
  
    > [!NOTE]
    >  Die Implementierungen der `Microsoft.VisualStudio.Package.SettingsPage` und `Microsoft.VisualStudio.Package.ProjectNode` Klassen verwenden die `Microsoft.Build.BuildEngine` (MSBuild) Methoden zum Abrufen und Festlegen von Projekt-und Konfiguration aus der Projektdatei.  
  
 Die Klasse, von ableiten `SettingsPage` implementieren müssen `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` und `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` Projekt oder die Konfiguration der Eigenschaften der Projektdatei beibehalten werden.  
  
## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute und Registrierungspfad  
 Abgeleitete Klassen von `SettingsPage` für VSPackages freigegeben werden sollen. Und es Ihnen ermöglicht für ein VSPackage erstellen eine Klasse abgeleitet `SettingsPage`, Hinzufügen einer `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` zu einer Klasse abgeleitet `Microsoft.VisualStudio.Shell.Package`.  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]  
  
 Das VSPackage, das das Attribut zugeordnet ist, ist unwichtig. Wenn eine VSPackage registriert wird, mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], die Klassen-Id (CLSID) für jedes Objekt, das erstellt werden kann, registriert ist, damit ein Aufruf von <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> erstellen können.  
  
 Der Registrierungspfad der ein Objekt, das erstellt werden kann richtet sich nach Kombination von <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, die Word, CLSID und die Guid des Objekttyps. Wenn `MyProjectPropertyPage` -Klasse verfügt über eine Guid vom {3c693da2-5bca-49b3-bd95-ffe0a39dd723} der UserRegistryRoot ist HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, und der Registrierungspfad wäre HKEY_CURRENT_USER\Software\Microsoft\VisualStudio \8.0Exp\CLSID\\{3c693da2-5bca-49b3-bd95-ffe0a39dd723}.  
  
## <a name="project-and-configuration-property-attributes-and-layout"></a>Projekt- und Konfiguration Eigenschaftenattribute und Layout  
 Die <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute>, und <xref:System.ComponentModel.DescriptionAttribute> Attribute bestimmen, die Layout, Bezeichnung und Beschreibung des Projekts und den Konfigurationseigenschaften auf der Eigenschaftenseite für eine generische. Diese Attribute ermitteln Sie die Kategorie ist, bzw. zeigen Sie Namen und Beschreibung der Option.  
  
> [!NOTE]
>  Entsprechende Attribute, SRCategory LocDisplayName und SRDescription, verwenden von Zeichenfolgenressourcen für die Lokalisierung und werden im definiert [MPF für Visual Studio 2013-Projekte -](http://mpfproj12.codeplex.com/).  
  
 Betrachten Sie das folgende Codefragment:  
  
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]  
  
 Die `MyConfigProp` Konfigurationseigenschaft wird angezeigt, auf der Konfigurationsseite für die Eigenschaft als **Meine Konfigurationseigenschaft** in der Kategorie **Meine Kategorie**. Wenn die Option ausgewählt ist, die Beschreibung **eigene Beschreibung**, im Beschreibungsbereich wird angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen und Entfernen von Eigenschaftenseiten](../../extensibility/adding-and-removing-property-pages.md)   
 [Projekte](../../extensibility/internals/projects.md)   
 [Dateien zur Beschreibung des Vorlagenverzeichnisses (VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

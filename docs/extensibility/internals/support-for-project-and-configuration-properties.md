---
title: Unterstützung für Projekt- und Konfigurationseigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5f137f5044c24ec9a187868c273b1dd752cd86a5
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513096"
---
# <a name="support-for-project-and-configuration-properties"></a>Unterstützung für Projekt- und Konfigurationseigenschaften
Die **Eigenschaften** Fenster in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE) kann Projekt- und Eigenschaften anzuzeigen. Sie können eine Eigenschaftenseite für Ihren eigenen Projekttyp bereitstellen, sodass der Benutzer die Eigenschaften für die Anwendung festlegen kann.  
  
 Wählen Sie einen Projektknoten **Projektmappen-Explorer** , und klicken Sie dann auf **Eigenschaften** auf die **Projekt** Menü können Sie ein Dialogfeld, das Projekt und die Konfiguration enthält öffnen Eigenschaften. In [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] und [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], und Projekttypen abgeleitet diese Sprachen dieses Dialogfeld wird angezeigt, als eine Seite im Registerformat, in der [Allgemein, Umgebung, Dialogfeld Optionen](../../ide/reference/general-environment-options-dialog-box.md). Weitere Informationen finden Sie unter [nicht im Build: Exemplarische Vorgehensweise: Verfügbarmachen von Projekt- und Konfigurationseigenschaften (c#)](http://msdn.microsoft.com/en-us/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).  
  
 Das Managed Package Framework for Projects (MPFProj) stellt Hilfsklassen zum Erstellen und Verwalten von neuen Projektsystem bereit. Anweisungen finden Sie die Quelle Code und die Kompilierung auf [MPF für Visual Studio 2013-Projekte –](http://mpfproj12.codeplex.com/).  
  
## <a name="persistence-of-project-and-configuration-properties"></a>Dauerhaftigkeit von Projekt- und Konfigurationseigenschaften  
 Projekt- und Eigenschaften werden in einer Projektdatei beibehalten, die über eine beliebige Dateinamenerweiterung, die vom Projekttyp zugeordnet sind, z. B., csproj, vbproj und .myproj verfügt. Sprachprojekte verwenden in der Regel eine Vorlagendatei, um die Datei zu generieren. Es gibt jedoch tatsächlich mehrere Möglichkeiten zum Zuordnen von Projekttypen und Vorlagen. Weitere Informationen finden Sie unter [Vorlagenbeschreibung-Verzeichnis (. VSDIR)-Dateien](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
 Projekt- und Eigenschaften werden durch Hinzufügen von Elementen in die Vorlagendatei erstellt. Diese Eigenschaften werden dann für jedes Projekt erstellt, mit der Projekttyp, der diese Vorlage verwendet. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Projekte und die MPFProj beide verwenden die [nicht im Build: Übersicht über MSBuild](http://msdn.microsoft.com/en-us/b588fd73-a45b-4706-908f-cc131bccfbde) Schema für die Vorlagendateien. Diese Dateien haben einen Abschnitt "PropertyGroup" für jede Konfiguration. Eigenschaften von Projekten werden in den ersten Abschnitt "PropertyGroup", mit einer konfigurationsargument, das auf eine null-Zeichenfolge festgelegt, in der Regel beibehalten.  
  
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
  
 Es ist die Verantwortung für das Projekt, um die Eigenschaften und Konfiguration der Projektdatei beibehalten.  
  
> [!NOTE]
>  Ein Projekt kann Persistenz durch Beibehalten von nur Eigenschaftswerte optimieren, die von ihren Standardwerten abweichen.  
  
## <a name="support-for-project-and-configuration-properties"></a>Unterstützung für Projekt- und Konfigurationseigenschaften  
 Die `Microsoft.VisualStudio.Package.SettingsPage` -Klasse implementiert die Eigenschaftenseiten für Projekt und die Konfiguration. Die standardmäßige Implementierung des `SettingsPage` öffentliche Eigenschaften zu einem Benutzer in einem generischen Eigenschaftenraster bietet. Die `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` Methode wählt von abgeleitete Klassen `SettingsPage` für Projekt Eigenschaftenrastern. Die `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` Methode wählt von abgeleitete Klassen `SettingsPage` für die Konfiguration von Eigenschaftenrastern. Ihr Projekttyp sollten diese Methoden zum Wählen Sie der entsprechenden Eigenschaftenseiten überschreiben.  
  
 Die `SettingsPage` Klasse und die `Microsoft.VisualStudio.Package.ProjectNode` bieten diese Methoden Projekt-und Konfiguration beibehalten werden:  
  
-   `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` und `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` Projekteigenschaften beibehalten.  
  
-   `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` und `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` Konfigurationseigenschaften beibehalten.  
  
    > [!NOTE]
    >  Die Implementierungen der `Microsoft.VisualStudio.Package.SettingsPage` und `Microsoft.VisualStudio.Package.ProjectNode` Klassen geben mit der `Microsoft.Build.BuildEngine` (MSBuild) Methoden zum Abrufen und Festlegen der Projekt- und Eigenschaften aus der Projektdatei.  
  
 Die Klasse, die Sie eine von Ableitung `SettingsPage` müssen implementieren `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` und `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` Projekt oder die Konfiguration von Eigenschaften der Projektdatei beibehalten werden.  
  
## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute und Registrierungspfad  
 Von abgeleiteten Klassen `SettingsPage` VSPackages gemeinsam verwendet werden sollen. Und es für ein VSPackage erstellen Sie eine Klasse, die von abgeleiteten `SettingsPage`, Hinzufügen einer `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` auf eine Klasse, die von abgeleiteten `Microsoft.VisualStudio.Shell.Package`.  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]  
  
 Das VSPackage, das an dem das Attribut angefügt ist, ist unwichtig. Wenn eine VSPackage registriert wird, mit [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], registriert die Klassen-Id (CLSID) von Objekten, die erstellt werden kann, damit ein Aufruf von <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> erstellen können.  
  
 Der Registrierungspfad der ein Objekt, das erstellt werden kann richtet sich nach der Kombination von <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, das Wort, CLSID und die Guid des Objekttyps. Wenn `MyProjectPropertyPage` -Klasse verfügt über eine Guid vom {3c693da2-5bca-49b3-bd95-ffe0a39dd723} und der UserRegistryRoot HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, dann wäre der Registrierungspfad HKEY_CURRENT_USER\Software\Microsoft\VisualStudio \8.0Exp\CLSID\\{3c693da2-5bca-49b3-bd95-ffe0a39dd723}.  
  
## <a name="project-and-configuration-property-attributes-and-layout"></a>Projekt und Konfigurationsattribute-Eigenschaft und des Layouts  
 Die <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute>, und <xref:System.ComponentModel.DescriptionAttribute> Attribute bestimmen das Layout, Bezeichnung und Beschreibung der Projekt- und Eigenschaften in einer generischen Eigenschaftenseite. Diese Attribute bestimmen Sie die Kategorie, zeigen bzw. Name und Beschreibung der Option.  
  
> [!NOTE]
>  Entsprechende Attribute, SRCategory, LocDisplayName SRDescription, verwenden von Zeichenfolgenressourcen für die Lokalisierung und sind in definiert [MPF für Visual Studio 2013-Projekte –](http://mpfproj12.codeplex.com/).  
  
 Betrachten Sie das folgende Codefragment:  
  
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]  
  
 Die `MyConfigProp` Configuration-Eigenschaft angezeigt wird, auf der Konfigurationsseite für die Eigenschaft als **Meine Konfigurationseigenschaft** in der Kategorie **My Category**. Wenn die Option ausgewählt ist, die Beschreibung und den **My Description**, im Beschreibungsbereich wird angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Hinzufügen und Entfernen von Eigenschaftenseiten](../../extensibility/adding-and-removing-property-pages.md)   
 [Projekte](../../extensibility/internals/projects.md)   
 [Dateien zur Beschreibung des Vorlagenverzeichnisses (VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

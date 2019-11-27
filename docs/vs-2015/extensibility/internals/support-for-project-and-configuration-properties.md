---
title: Unterstützung für Projekt-und Konfigurations Eigenschaften | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, suppporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b03bc04b1d5b87219110aa65bee53c4a4a8f77e2
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301064"
---
# <a name="support-for-project-and-configuration-properties"></a>Unterstützung für Projekt- und Konfigurationseigenschaften
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im **Eigenschaften** Fenster der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) von [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] können Projekt-und Konfigurations Eigenschaften angezeigt werden. Sie können eine Eigenschaften Seite für Ihren eigenen Projekttyp bereitstellen, sodass der Benutzereigenschaften für Ihre Anwendung festlegen kann.  
  
 Wenn Sie in **Projektmappen-Explorer** einen Projekt Knoten auswählen und dann im Menü **Projekt** auf **Eigenschaften** klicken, können Sie ein Dialogfeld öffnen, das Projekt-und Konfigurations Eigenschaften enthält. In [!INCLUDE[csprcs](../../includes/csprcs-md.md)] und [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]sowie in den Projekttypen, die von diesen Sprachen abgeleitet sind, wird dieses Dialogfeld im [Dialogfeld Allgemein, Umgebung, Optionen](../../ide/reference/general-environment-options-dialog-box.md)als Registerkarte angezeigt. Weitere Informationen finden Sie unter nicht im Build: Exemplarische Vorgehensweise: verfügbar machen von [ProjektC#-und Konfigurations Eigenschaften ()](https://msdn.microsoft.com/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).  
  
 Das Managed Package Framework for Projects (mpfproj) stellt Hilfsklassen zum Erstellen und Verwalten eines neuen Projekt Systems bereit. Den Quellcode und die Kompilierungs Anweisungen finden Sie unter [MPF for Projects-Visual Studio 2013](https://archive.codeplex.com/?p=mpfproj12).  
  
## <a name="persistence-of-project-and-configuration-properties"></a>Persistenz von Projekt-und Konfigurations Eigenschaften  
 Projekt-und Konfigurations Eigenschaften werden in einer Projektdatei gespeichert, die eine Dateinamenerweiterung aufweist, die dem Projekttyp zugeordnet ist, z. b. csproj,. vbproj und. MyProj. Sprachprojekte verwenden in der Regel eine Vorlagen Datei, um die Projektdatei zu generieren. Es gibt jedoch mehrere Möglichkeiten, Projekttypen und Vorlagen zuzuordnen. Weitere Informationen finden Sie unter [NIB: Visual Studio-Vorlagen](https://msdn.microsoft.com/141fccaa-d68f-4155-822b-27f35dd94041) und [Beschreibung des Vorlagen Verzeichnisses (. VSDIR-Dateien](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
 Projekt-und Konfigurations Eigenschaften werden durch das Hinzufügen von Elementen zur Vorlagen Datei erstellt. Diese Eigenschaften sind dann für jedes Projekt verfügbar, das mit dem Projekttyp erstellt wurde, der diese Vorlage verwendet. [!INCLUDE[csprcs](../../includes/csprcs-md.md)] Projekte und die "mpfproj" verwenden beide das Schema " [Not in Build: MSBuild Overview](https://msdn.microsoft.com/b588fd73-a45b-4706-908f-cc131bccfbde) " für Vorlagen Dateien. Diese Dateien verfügen über einen PropertyGroup-Abschnitt für jede Konfiguration. Eigenschaften von Projekten werden in der Regel im ersten PropertyGroup-Abschnitt persistent gespeichert, für den ein Konfigurations Argument auf eine NULL-Zeichenfolge festgelegt ist.  
  
 Der folgende Code zeigt den Anfang einer grundlegenden MSBuild-Projektdatei.  
  
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
  
 In dieser Projektdatei sind `<Name>` und `<SchemaVersion>` Projekteigenschaften, und `<Optimize>` ist eine Konfigurations Eigenschaft.  
  
 Es liegt in der Verantwortung des Projekts, die Projekt-und Konfigurations Eigenschaften der Projektdatei beizubehalten.  
  
> [!NOTE]
> Ein Projekt kann die Persistenz optimieren, indem nur Eigenschaftswerte beibehalten werden, die sich von den Standardwerten unterscheiden.  
  
## <a name="support-for-project-and-configuration-properties"></a>Unterstützung für Projekt- und Konfigurationseigenschaften  
 Die `Microsoft.VisualStudio.Package.SettingsPage`-Klasse implementiert Projekt-und Konfigurations Eigenschaften Seiten. Die Standard Implementierung von `SettingsPage` bietet einem Benutzer öffentliche Eigenschaften in einem generischen Eigenschaften Raster. Die `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids`-Methode wählt Klassen aus, die von `SettingsPage` für Projekteigenschaften Raster abgeleitet werden. Die `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids`-Methode wählt Klassen aus, die von `SettingsPage` für Konfigurations Eigenschaften Raster abgeleitet werden. Der Projekttyp sollte diese Methoden überschreiben, um die entsprechenden Eigenschaften Seiten auszuwählen.  
  
 Die `SettingsPage`-Klasse und die `Microsoft.VisualStudio.Package.ProjectNode`-Klasse bieten diese Methoden zum Speichern von Projekt-und Konfigurations Eigenschaften:  
  
- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` und `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` Projekteigenschaften beibehalten.  
  
- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty`-und `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` Beibehaltungs Konfigurations Eigenschaften.  
  
  > [!NOTE]
  > Die Implementierungen der Klassen `Microsoft.VisualStudio.Package.SettingsPage` und `Microsoft.VisualStudio.Package.ProjectNode` verwenden die-`Microsoft.Build.BuildEngine` (MSBuild)-Methoden, um Projekt-und Konfigurations Eigenschaften aus der Projektdatei zu erstellen und festzulegen.  
  
  Die Klasse, die Sie von `SettingsPage` ableiten, muss `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` implementieren und `Microsoft.VisualStudio.Package.SettingsPage.BindProperties`, um die Projekt-oder Konfigurations Eigenschaften der Projektdatei beizubehalten.  
  
## <a name="provideobjectattribute-and-registry-path"></a>Provide objectAttribute und Registrierungs Pfad  
 Klassen, die von `SettingsPage` abgeleitet werden, sind für die gemeinsame Nutzung von VSPackages konzipiert. Damit ein VSPackage eine von `SettingsPage`abgeleitete Klasse erstellen kann, fügen Sie einer Klasse, die von `Microsoft.VisualStudio.Shell.Package`abgeleitet ist, eine `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` hinzu.  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/vssdksupportprojectconfigurationpropertiespackage.cs#1)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/vssdksupportprojectconfigurationpropertiespackage.vb#1)]  
  
 Das VSPackage, an das das Attribut angefügt wird, ist unwichtig. Wenn ein VSPackage mit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]registriert wird, wird die Klassen-ID (CLSID) jedes Objekts, das erstellt werden kann, so registriert, dass es durch einen aufzurufenden <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> erstellt werden kann.  
  
 Der Registrierungs Pfad eines Objekts, das erstellt werden kann, wird bestimmt, indem <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, das Wort, die CLSID und die GUID des Objekt Typs kombiniert werden. Wenn `MyProjectPropertyPage` Klasse eine GUID von {3c693da2-5bca-49b3-BD95-ffe0a39dd723} und userregistryroot HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0exp lautet, dann lautet der Registrierungs Pfad HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0exp\clsid\\{3c693da2-5bca-49b3-BD95-ffe0a39dd723}.  
  
## <a name="project-and-configuration-property-attributes-and-layout"></a>Attribute und Layout von Projekt-und Konfigurations Eigenschaften  
 Die Attribute "<xref:System.ComponentModel.CategoryAttribute>", "<xref:System.ComponentModel.DisplayNameAttribute>" und "<xref:System.ComponentModel.DescriptionAttribute>" bestimmen Layout, Bezeichnung und Beschreibung der Projekt-und Konfigurations Eigenschaften auf einer generischen Eigenschaften Seite. Diese Attribute bestimmen die Kategorie, den anzeigen Amen und die Beschreibung der Option.  
  
> [!NOTE]
> Äquivalente Attribute, SRCategory, LocDisplayName und SRDescription, verwenden Zeichen folgen Ressourcen für die Lokalisierung und sind in [MPF für Projekte definiert-Visual Studio 2013](https://archive.codeplex.com/?p=mpfproj12).  
  
 Betrachten Sie das folgende Codefragment:  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/myprojectpropertypage.cs#2)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/myprojectpropertypage.vb#2)]  
  
 Die `MyConfigProp` Konfigurations Eigenschaft wird auf der Eigenschaften Seite Konfiguration als **Meine config-Eigenschaft** in der Kategorie **My Category**angezeigt. Wenn die Option ausgewählt ist, wird im Beschreibungs Panel die Beschreibung, **meine Beschreibung**, angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 Nicht im Build: Exemplarische Vorgehensweise: verfügbar machen von [ProjektC#-und Konfigurations Eigenschaften ()](https://msdn.microsoft.com/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)   
 [Hinzufügen und Entfernen von Eigenschaften Seiten](../../extensibility/adding-and-removing-property-pages.md)   
 [VSPackage-Status](../../misc/vspackage-state.md)   
 [Projekte](../../extensibility/internals/projects.md)   
 [NIB: Visual Studio-Vorlagen](https://msdn.microsoft.com/141fccaa-d68f-4155-822b-27f35dd94041)   
 [Dateien zur Beschreibung des Vorlagenverzeichnisses (VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

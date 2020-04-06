---
title: Unterstützung für Projekt- und Konfigurationseigenschaften | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c21d552e26add3a5159febd666c1f60573697535
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704900"
---
# <a name="support-for-project-and-configuration-properties"></a>Unterstützung für Projekt- und Konfigurationseigenschaften
Das **Fenster** Eigenschaften [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in der integrierten Entwicklungsumgebung (IDE) kann Projekt- und Konfigurationseigenschaften anzeigen. Sie können eine Eigenschaftenseite für Ihren eigenen Projekttyp bereitstellen, damit der Benutzer Eigenschaften für Ihre Anwendung festlegen kann.

 Wenn Sie einen Projektknoten im **Projektmappen-Explorer** auswählen und dann im Menü **Projekt** auf **Eigenschaften** klicken, können Sie ein Dialogfeld öffnen, das Projekt- und Konfigurationseigenschaften enthält. In [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]und und und von diesen Sprachen abgeleitete Projekttypen wird dieses Dialogfeld als Registerkarte im [Feld Allgemein, Umgebung, Optionen.](../../ide/reference/general-environment-options-dialog-box.md) Weitere Informationen finden Sie unter [Nicht in Build: Walkthrough: Offenlegen von Projekt- und Konfigurationseigenschaften (C)](https://msdn.microsoft.com/library/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).

 Das Managed Package Framework for Projects (MPFProj) bietet Hilfsklassen zum Erstellen und Verwalten eines neuen Projektsystems. Den Quellcode und die Kompilierungsanweisungen finden Sie unter [MPF for Projects - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="persistence-of-project-and-configuration-properties"></a>Persistenz von Projekt- und Konfigurationseigenschaften
 Projekt- und Konfigurationseigenschaften werden in einer Projektdatei beibehalten, der eine Dateinamenerweiterung zugeordnet ist, z. B. .csproj, .vbproj und .myproj. Sprachprojekte verwenden in der Regel eine Vorlagendatei, um die Projektdatei zu generieren. Es gibt jedoch mehrere Möglichkeiten, Projekttypen und Vorlagen zuzuordnen. Weitere Informationen finden Sie unter [Vorlagenverzeichnisbeschreibung (. Vsdir) Dateien](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

 Projekt- und Konfigurationseigenschaften werden durch Hinzufügen von Elementen zur Vorlagendatei erstellt. Diese Eigenschaften sind dann für jedes Projekt verfügbar, das mithilfe des Projekttyps erstellt wird, der diese Vorlage verwendet. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]Projekte und MPFProj verwenden beide das Schema [Not in Build: MSBuild Overview](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) für Vorlagendateien. Diese Dateien verfügen über einen PropertyGroup-Abschnitt für jede Konfiguration. Eigenschaften von Projekten werden in der Regel im ersten PropertyGroup-Abschnitt beibehalten, der ein Configuration-Argument auf eine NULL-Zeichenfolge festgelegt hat.

 Der folgende Code zeigt den Start einer grundlegenden MSBuild-Projektdatei.

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

 In dieser Projektdatei und `<Name>` `<SchemaVersion>` sind `<Optimize>` Projekteigenschaften und ist eine Konfigurationseigenschaft.

 Es liegt in der Verantwortung des Projekts, die Projekt- und Konfigurationseigenschaften der Projektdatei beizubehalten.

> [!NOTE]
> Ein Projekt kann die Persistenz optimieren, indem es nur Eigenschaftswerte beibehalten, die sich von ihren Standardwerten unterscheiden.

## <a name="support-for-project-and-configuration-properties"></a>Unterstützung für Projekt- und Konfigurationseigenschaften
 Die `Microsoft.VisualStudio.Package.SettingsPage` Klasse implementiert Projekt- und Konfigurationseigenschaftsseiten. Die Standardimplementierung `SettingsPage` von bietet einem Benutzer in einem generischen Eigenschaftenraster öffentliche Eigenschaften an. Die `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` Methode wählt Klassen `SettingsPage` aus, die für Projekteigenschaftsraster abgeleitet wurden. Die `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` Methode wählt Klassen `SettingsPage` aus, die für Konfigurationseigenschaftsraster abgeleitet wurden. Der Projekttyp sollte diese Methoden überschreiben, um die entsprechenden Eigenschaftenseiten auszuwählen.

 Die `SettingsPage` Klasse `Microsoft.VisualStudio.Package.ProjectNode` und die Klasse bieten die folgenden Methoden zum Beibehalten von Projekt- und Konfigurationseigenschaften an:

- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty`und `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` bleiben Projekteigenschaften bestehen.

- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty`und `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` beibehalten Konfigurationseigenschaften.

  > [!NOTE]
  > Die Implementierungen `Microsoft.VisualStudio.Package.SettingsPage` der `Microsoft.VisualStudio.Package.ProjectNode` und-Klassen verwenden die `Microsoft.Build.BuildEngine` (MSBuild)-Methoden, um Projekt- und Konfigurationseigenschaften aus der Projektdatei abzuspeichern und festzulegen.

  Die Klasse, aus `SettingsPage` der `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` Sie ableiten, muss projekt- oder konfigurationseigenschaften der Projektdatei implementieren und beibehalten.

## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute und Registrierungspfad
 Von den `SettingsPage` Klassen abgeleitete Klassen sind so konzipiert, dass sie in VSPackages gemeinsam genutzt werden. Um es einem VSPackage zu ermöglichen, `SettingsPage`eine von `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` abgeleitete Klasse `Microsoft.VisualStudio.Shell.Package`zu erstellen, fügen Sie einer von abgeleiteten Klasse eine hinzu.

 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]

 Das VSPackage, dem das Attribut zugeordnet ist, ist unwichtig. Wenn ein VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]bei registriert ist, wird die Klassen-ID (CLSID) eines <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> beliebigen Objekts, das erstellt werden kann, registriert, sodass ein Aufruf an dieses Objekt erstellt werden kann.

 Der Registrierungspfad eines Objekts, das erstellt <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>werden kann, wird durch Kombinieren von , des Wortes, der CLSID und der GUID des Objekttyps bestimmt. Wenn `MyProjectPropertyPage` die Klasse über die Guid von '3c693da2-5bca-49b3-bd95-ffe0a39dd723' verfügt und der UserRegistryRoot HKEY_CURRENT_USER'Software'Microsoft'VisualStudio'8.0Exp' lautet, Dann wäre der\\Registrierungspfad HKEY_CURRENT_USER-Software-Microsoft-VisualStudio-8.0Exp-CLSID-Nr. 3c693da2-5bca-49b3-bd95-ffe0a39dd723.

## <a name="project-and-configuration-property-attributes-and-layout"></a>Projekt- und Konfigurationseigenschaftsattribute und Layout
 Die <xref:System.ComponentModel.CategoryAttribute> <xref:System.ComponentModel.DisplayNameAttribute>, <xref:System.ComponentModel.DescriptionAttribute> und Attribute bestimmen das Layout, die Beschriftung und die Beschreibung von Projekt- und Konfigurationseigenschaften auf einer generischen Eigenschaftenseite. Diese Attribute bestimmen die Kategorie, den Anzeigenamen und die Beschreibung der Option.

> [!NOTE]
> Äquivalente Attribute, SRCategory, LocDisplayName und SRDescription, verwenden Zeichenfolgenressourcen für die Lokalisierung und sind in [MPF für Projekte - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10)definiert.

 Betrachten Sie das folgende Codefragment:

 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]

 Die `MyConfigProp` Konfigurationseigenschaft wird auf der Konfigurationseigenschaftsseite als **Meine Config-Eigenschaft** in der Kategorie **"Meine Kategorie"** angezeigt. Wenn die Option ausgewählt ist, wird die Beschreibung **"Meine Beschreibung "** im Beschreibungsbereich angezeigt.

## <a name="see-also"></a>Weitere Informationen
- [Hinzufügen und Entfernen von Eigenschaftenseiten](../../extensibility/adding-and-removing-property-pages.md)
- [Projekte](../../extensibility/internals/projects.md)
- [Dateien zur Beschreibung des Vorlagenverzeichnisses (VSDIR)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

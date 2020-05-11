---
title: Aktualisieren benutzerdefinierter Projekt- und Elementvorlagen für Visual Studio 2017
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 5f807e142b376d05e5a44600e8f6b24ddb3593be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698858"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Aktualisieren benutzerdefinierter Projekt- und Elementvorlagen für Visual Studio 2017

Ab Visual Studio 2017 ermittelt Visual Studio Projekt- und Elementvorlagen, die von einem VSix oder einer MSI auf andere Weise als frühere Versionen von Visual Studio installiert wurden. Wenn Sie Erweiterungen besitzen, die benutzerdefinierte Projekt- oder Elementvorlagen verwenden, müssen Sie die Erweiterungen aktualisieren. In diesem Artikel wird erläutert, was Sie tun müssen.

Diese Änderung wirkt sich nur auf Visual Studio 2017 aus. Frühere Versionen von Visual Studio sind davon nicht betroffen.

Wenn Sie ein Projekt oder eine Elementvorlage als Teil einer VSIX-Erweiterung erstellen möchten, finden Sie weitere Informationen unter [Erstellen benutzerdefinierter Projekt- und Elementvorlagen](../extensibility/creating-custom-project-and-item-templates.md).

## <a name="template-scanning"></a>Vorlagen-Scannen

In früheren Versionen von Visual Studio haben **devenv /setup** oder **devenv /installvstemplates** den lokalen Datenträger gescannt, um Projekt- und Elementvorlagen zu finden. Ab Visual Studio 2017 wird das Scannen nur für den Speicherort auf Benutzerebene durchgeführt. Der Standardspeicherort auf Benutzerebene ist **%USERPROFILE%-Dokumente\\<Visual\>Studio-Version .\\** Dieser Speicherort wird für Vorlagen verwendet, die mit dem Befehl > **Projektexportvorlagen...** generiert werden, wenn die Option **Automatisch importieren in Visual Studio** im Assistenten ausgewählt ist. **Project**

Für andere (Nicht-Benutzer-)Speicherorte müssen Sie eine manifest(.vstman)-Datei einfügen, die den Speicherort und andere Merkmale der Vorlage angibt. Die .vstman-Datei wird zusammen mit der für Vorlagen verwendeten .vstemplate-Datei generiert. Wenn Sie die Erweiterung mit einer .vsix installieren, können Sie dies erreichen, indem Sie die Erweiterung in Visual Studio 2017 neu kompilieren. Wenn Sie jedoch eine MSI verwenden, müssen Sie die Änderungen manuell vornehmen. Eine Liste der Maßnahmen, die Sie tun müssen, um diese Änderungen vorzunehmen, finden Sie unter **Upgrades für Erweiterungen, die mit einem installiert wurden. MSI** später auf dieser Seite.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Aktualisieren einer VSIX-Erweiterung mit Projekt- oder Elementvorlagen

1. Öffnen Sie die Lösung in Visual Studio 2017. Sie werden aufgefordert, den Code zu aktualisieren. Klicken Sie auf **OK**.

2. Nach Abschluss des Upgrades müssen Sie möglicherweise die Version des Installationsziels ändern. Öffnen Sie im VSIX-Projekt die Datei source.extension.vsixmanifest, und wählen Sie die Registerkarte **Ziele installieren** aus. Wenn das Feld **Versionsbereich** **[14.0]** lautet, klicken Sie auf **Bearbeiten,** und ändern Sie es so, dass Visual Studio 2017 eingeschlossen wird. Sie können es z. B. auf **[14.0,15.0]** festlegen, um die Erweiterung entweder auf Visual Studio 2015 oder Visual Studio 2017 oder **auf [15.0]** zu installieren, um sie nur auf Visual Studio 2017 zu installieren.

3. Kompilieren Sie den Code neu.

4. Schließen Sie Visual Studio.

5. Installieren Sie den VSIX.

6. Sie können das Update wie folgt testen:

    1. Die Änderung des Dateiscans wird durch den folgenden Registrierungsschlüssel aktiviert:

         **reg hinzufügen von hklm-software-microsoft-visualstudio-15.0-VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**

    2. Nachdem Sie den Schlüssel hinzugefügt haben, führen Sie **devenv /installvstemplates**aus.

    3. Öffnen Sie Visual Studio erneut. Sie sollten Ihre Vorlage am erwarteten Speicherort finden.

    > [!NOTE]
    > Die Visual Studio-Projektvorlagen für Extensibilität sind nicht verfügbar, wenn der Registrierungsschlüssel vorhanden ist. Sie müssen den Registrierungsschlüssel löschen (und **devenv /installvstemplates**erneut ausführen), um ihn verwenden zu können.

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Weitere Empfehlungen zum Bereitstellen von Projekt- und Elementvorlagen

- Vermeiden Sie die Verwendung von ZIP-Vorlagendateien. Gezippte Vorlagendateien müssen dekomprimiert werden, um Ressourcen und Inhalte abzurufen, damit sie teurer zu verwenden sind. Stattdessen sollten Sie Projekt- und Elementvorlagen als einzelne Dateien in ihrem eigenen Verzeichnis bereitstellen, um die Vorlageninitialisierung zu beschleunigen. Bei VSIX-Erweiterungen entpacken SDK-Buildaufgaben beim Erstellen der VSIX-Datei automatisch jede zipierte Vorlage.

- Vermeiden Sie die Verwendung von Paket-/Ressourcen-ID-Einträgen für den Vorlagennamen, die Beschreibung, das Symbol oder die Vorschau, um unnötige Ressourcenassembly-Lasten während der Vorlagenermittlung zu vermeiden. Stattdessen können Sie lokalisierte Manifeste verwenden, um einen Vorlageneintrag für jedes Gebietsschema zu erstellen, das lokalisierte Namen oder Eigenschaften verwendet.

- Wenn Sie Vorlagen als Dateielemente einschließen, liefert Ihnen die Manifestgenerierung möglicherweise nicht die erwarteten Ergebnisse. In diesem Fall müssen Sie dem VSIX-Projekt ein manuell generiertes Manifest hinzufügen.

## <a name="file-changes-in-project-and-item-templates"></a>Dateiänderungen in Projekt- und Elementvorlagen
Wir zeigen die Unterschiede zwischen den Visual Studio 2015- und Visual Studio 2017-Versionen der Vorlagendateien an, sodass Sie die neuen Dateien ordnungsgemäß erstellen können.

 Hier ist die Standardprojekt .vstemplate-Datei von Visual Studio 2015 erstellt:

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ProjectTemplate1</Name>
    <Description>ProjectTemplate1</Description>
    <Icon>ProjectTemplate1.ico</Icon>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <SortOrder>1000</SortOrder>
    <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
    <CreateNewFolder>true</CreateNewFolder>
    <DefaultName>ProjectTemplate1</DefaultName>
    <ProvideDefaultName>true</ProvideDefaultName>
  </TemplateData>
  <TemplateContent>
    <Project File="ProjectTemplate.csproj" ReplaceParameters="true">
      <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>
      <ProjectItem ReplaceParameters="true" OpenInEditor="true">Class1.cs</ProjectItem>
    </Project>
  </TemplateContent>
</VSTemplate>

```

 Hier ist die .vstman-Datei (Sie finden sie im Manifestverzeichnis des VSIX-Projekts), die sich aus der Neuerstellung des VSIX-Projekts ergab:

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\ProjectTemplate1</RelativePathOnDisk>
    <TemplateFileName>ProjectTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ProjectTemplate1</Name>
        <Description>ProjectTemplate1</Description>
        <Icon>ProjectTemplate1.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>ProjectTemplate1</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 Die vom [TemplateData-Element](../extensibility/templatedata-element-visual-studio-templates.md) bereitgestellten Informationen bleiben unverändert. Das ** \<>-Element VSTemplateContainer** verweist auf die .vstemplate-Datei für die zugehörige Vorlage.

 Hier ist das Standardelement .vstemplate Datei von Visual Studio 2015 erstellt:

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ItemTemplate1</Name>
    <Description>ItemTemplate1</Description>
    <Icon>ItemTemplate1.ico</Icon>
    <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    <DefaultName>Class.cs</DefaultName>
  </TemplateData>
  <TemplateContent>
    <References>
      <Reference>
        <Assembly>System</Assembly>
      </Reference>
    </References>
    <ProjectItem ReplaceParameters="true">Class.cs</ProjectItem>
  </TemplateContent>
</VSTemplate>

```

 Hier ist die .vstman-Datei (Sie finden sie im Manifestverzeichnis des VSIX-Projekts), die sich aus der Neuerstellung des VSIX-Projekts ergab:

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Item">
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ItemTemplate1</Name>
        <Description>ItemTemplate1</Description>
        <Icon>ItemTemplate1.ico</Icon>
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
        <DefaultName>Class.cs</DefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>
```

 Die vom ** \<TemplateData->-Element** bereitgestellten Informationen bleiben unverändert. Das ** \<>-Element VSTemplateContainer** verweist auf die .vstemplate-Datei für die zugehörige Vorlage

 Weitere Informationen zu den verschiedenen Elementen der .vstman-Datei finden Sie unter [Visual Studio Template Manifest Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Upgrades für Erweiterungen, die mit einer installiert wurden. Msi

Einige MSI-basierte Erweiterungen stellen Vorlagen an allgemeinen Vorlagenspeicherorten wie den folgenden Verzeichnissen bereit:

- **\<Visual Studio-Installationsverzeichnis>-Common7-IDE-<\\ ProjectTemplates/ItemTemplates\>**

- **\<Visual Studio-Installationsverzeichnis>-Common7-IDE-Erweiterungen\\<ExtensionName\> \\<Project/ItemTemplates\>**

Wenn Ihre Erweiterung eine MSI-basierte Bereitstellung durchführt, müssen Sie das Vorlagenmanifest manuell generieren und sicherstellen, dass es in der Erweiterungseinrichtung enthalten ist. Vergleichen Sie die oben aufgeführten .vstman-Beispiele und die [Visual Studio-Vorlagenmanifest-Schemareferenz](../extensibility/visual-studio-template-manifest-schema-reference.md).

Erstellen Sie separate Manifeste für Projekt- und Elementvorlagen, und sie sollten wie oben angegeben auf das Stammvorlagenverzeichnis verweisen. Erstellen Sie ein Manifest pro Erweiterung und Gebietsschema.

## <a name="see-also"></a>Weitere Informationen

- [Fehlerbehebung bei der Vorlagenermittlung](troubleshooting-template-discovery.md)
- [Erstellen benutzerdefinierter Projekt- und Elementvorlagen](creating-custom-project-and-item-templates.md)

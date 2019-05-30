---
title: Aktualisieren von benutzerdefinierten Projekt- und Elementvorlagen für Visual Studio 2017
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 9302ae3119bceb466e3d681036753bd8237cbeae
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316336"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Aktualisieren von benutzerdefinierten Projekt- und Elementvorlagen für Visual Studio 2017

Ab Visual Studio 2017, erkennt Visual Studio Projekt- und Elementvorlagen, die vom VSIX oder in eine MSI-Datei in eine andere Möglichkeit, frühere Versionen von Visual Studio installiert wurden. Wenn Sie Erweiterungen, die Verwenden von benutzerdefinierten Projekt- oder Elementvorlagen verfügen, müssen Sie Ihre Erweiterungen zu aktualisieren. In diesem Artikel wird erläutert, was Sie tun müssen.

Diese Änderung betrifft nur Visual Studio 2017. Es wirkt sich nicht auf frühere Versionen von Visual Studio aus.

Wenn Sie eine Projekt- oder Elementvorlage während der VSIX-Erweiterung erstellen möchten, finden Sie unter [Erstellen von benutzerdefinierten Projekt- und Elementvorlagen](../extensibility/creating-custom-project-and-item-templates.md).

## <a name="template-scanning"></a>Vorlage überprüfen

In früheren Versionen von Visual Studio **Devenv/Setup** oder **Devenv/installvstemplates** durchsucht den lokalen Datenträger aus, um die Projekt- und Elementvorlagen zu suchen. Ab Visual Studio 2017, Überprüfung nur für den Speicherort auf Benutzerebene erfolgt. Der Standardspeicherort für die Benutzerebene ist **%USERPROFILE%\Documents\\< Visual Studio-Version\>\Templates\\** . Dieser Speicherort wird für Vorlagen, die vom verwendet die **Projekt** > **Vorlagen exportieren...**  Befehl, wenn die **Vorlage automatisch in Visual Studio importieren** Option im Assistenten ausgewählt ist.

Für andere Speicherorte (nicht-Benutzer) müssen Sie eine Datei manifest(.vstman) einschließen, die den Speicherort und andere Merkmale der Vorlage angibt. Die vstman-Datei wird zusammen mit der Vorlagen zum VSTEMPLATE-Datei generiert. Wenn Sie die Erweiterung VSIX mit installieren, können Sie dies erreichen, durch das erneute Kompilieren der Erweiterungs in Visual Studio 2017. Aber wenn Sie eine MSI-Datei verwenden, müssen Sie die Änderungen manuell vornehmen. Eine Übersicht darüber, was Sie tun, um diese Änderungen vornehmen müssen, finden Sie unter **Upgrades für die Erweiterungen installiert, mit ein. MSI** weiter unten auf dieser Seite.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Aktualisieren Sie eine VSIX-Erweiterung mit Projekt- oder Elementvorlagen

1. Öffnen Sie die Projektmappe in Visual Studio 2017. Sie werden aufgefordert, den Code aktualisieren. Klicken Sie auf **OK**.

2. Nachdem das Upgrade abgeschlossen ist, müssen Sie die Version von des installationsziels ändern. Klicken Sie im VSIX-Projekt, öffnen Sie die Datei "Source.Extension.vsixmanifest", und wählen die **Ziele installieren** Registerkarte. Wenn die **Versionsbereich** Feld **[14.0]** , klicken Sie auf **bearbeiten** und ändern Sie diese Visual Studio 2017 enthalten. Angenommen, Sie können sie festlegen **[14.0,15.0]** zum Installieren der Erweiterung, um entweder Visual Studio 2015 oder Visual Studio 2017 oder **[15.0]** nur Visual Studio 2017 installieren.

3. Kompilieren Sie der Code neu.

4. Schließen Sie Visual Studio.

5. Installieren Sie die VSIX-Datei.

6. Sie können das Update testen, indem Sie wie folgt vorgehen:

    1. Die Datei, die Überprüfung ändern wird aktiviert, durch den folgenden Registrierungsschlüssel:

         **REG hinzufügen hklm\software\microsoft\visualstudio\15.0\VSTemplate/v DisableTemplateScanning/t REG_DWORD/d 1 /reg:32**

    2. Nachdem Sie den Schlüssel hinzugefügt haben, führen Sie **Devenv/installvstemplates**.

    3. Öffnen Sie Visual Studio erneut. Sie sollten Ihre Vorlage am erwarteten Speicherort finden.

    > [!NOTE]
    > Die Erweiterbarkeit von Visual Studio-Projektvorlagen sind nicht verfügbar, wenn der Registrierungsschlüssel vorhanden ist. Sie müssen den Registrierungsschlüssel löschen (und erneut ausführen **Devenv/installvstemplates**) ihre Verwendung.

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Weitere Empfehlungen für die Bereitstellung von Projekt- und Elementvorlagen

- Vermeiden Sie die Verwendung des ZIP-Vorlagendateien. ZIP-Vorlage, die Dateien, um Ressourcen und Inhalte abzurufen, dekomprimiert werden müssen, also Leistungsseite verwendet werden. Stattdessen sollten Sie die Projekt- und Elementvorlagen als einzelne Dateien unter einem eigenen Verzeichnis zur Beschleunigung von Vorlage-Initialisierung bereitstellen. VSIX-Erweiterungen vorliegen werden Buildaufgaben SDK automatisch alle ZIP-Vorlage Entzippen Sie beim Erstellen der VSIX-Datei.

- Vermeiden Sie die Verwendung der Ressource "Package" / ID-Einträge für den Namen, Beschreibung und Symbol oder eine Vorschau anzeigen Sie, um nicht benötigte Ressource Laden von Assemblys bei der vorlagenermittlung zu vermeiden. Stattdessen können Sie lokalisierte Manifeste verwenden, einen Vorlageneintrag für jedes Gebietsschema, zu erstellen, die lokalisierten Namen oder Eigenschaften verwendet.

- Wenn Sie Vorlagen, die als Dateielemente einschließen, Generierung von Manifesten Ihnen möglicherweise nicht die erwarteten Ergebnisse. In diesem Fall müssen Sie ein manuelles generiertes Manifest für das VSIX-Projekt hinzufügen.

## <a name="file-changes-in-project-and-item-templates"></a>Dateiänderungen auf Projekt- und Elementvorlagen
Wir zeigen die Punkte der Unterschied zwischen dem Visual Studio 2015 und Visual Studio 2017-Versionen von den Vorlagendateien, damit Sie die neuen Dateien korrekt erstellen zu können.

 Hier ist der Standard-Projekt VSTEMPLATE-Datei von Visual Studio 2015 erstellt:

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

 Hier ist die vstman-Datei (Sie es im manifest-Verzeichnis des VSIX-Projekts finden), die aus der Neuerstellung des VSIX-Projekts ein:

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

 Die Informationen der [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) Element bleibt unverändert. Die  **\<VSTemplateContainer >** -Element verweist auf die VSTEMPLATE-Datei für die zugeordnete Vorlage.

 So sieht die standardmäßige Element VSTEMPLATE-Datei von Visual Studio 2015 erstellte aus:

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

 Hier ist die vstman-Datei (Sie es im manifest-Verzeichnis des VSIX-Projekts finden), die aus der Neuerstellung des VSIX-Projekts ein:

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

 Die Informationen der  **\<TemplateData >** Element bleibt unverändert. Die  **\<VSTemplateContainer >** -Element verweist auf die VSTEMPLATE-Datei für die zugeordnete Vorlage

 Weitere Informationen zu den verschiedenen Elementen der vstman-Datei, finden Sie unter [Visual Studio-Manifest Schemareferenz zu Vorlagen](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Upgrades für Erweiterungen installiert, mit ein. MSI-DATEI

Einige MSI-basierte Erweiterungen Bereitstellen von Vorlagen in allgemeine Vorlage Speicherorte wie z. B. den folgenden Verzeichnissen:

- **\<Visual Studio-Installationsverzeichnis > \Common7\IDE\\< ProjectTemplates / "ItemTemplates" >**

- **\<Visual Studio-Installationsverzeichnis > \Common7\IDE\Extensions\\< ExtensionName\>\\< Project / "ItemTemplates" >**

Wenn die Erweiterung eine MSI-basierte Bereitstellung ausgeführt wird, müssen Sie das Vorlagemanifest manuell zu generieren, und stellen Sie sicher, dass sie in der Erweiterung-Setup enthalten ist. Vergleichen Sie die oben aufgeführten vstman-Beispiele und die [Visual Studio-Manifest Schemareferenz zu Vorlagen](../extensibility/visual-studio-template-manifest-schema-reference.md).

Erstellen separate Manifeste für Projekt- und Elementvorlagen, und diese Vorlage Stammverzeichnis wie oben zeigen sollte. Erstellen Sie ein Manifest pro Erweiterung und Gebietsschema.

## <a name="see-also"></a>Siehe auch

- [Problembehandlung bei der vorlagenerkennung](troubleshooting-template-discovery.md)
- [Erstellen von benutzerdefinierten Projekt- und Elementvorlagen](creating-custom-project-and-item-templates.md)

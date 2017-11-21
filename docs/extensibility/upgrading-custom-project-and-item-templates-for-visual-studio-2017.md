---
title: "Aktualisieren von benutzerdefinierten Projekt- und Elementvorlagen für Visual Studio-2017 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
caps.latest.revision: "3"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 76437dff5aa59e4864216318e64a07245c15c68d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="upgrading-custom-project-and-item-templates-for-visual-studio-2017"></a>Aktualisieren von benutzerdefinierten Projekt- und Elementvorlagen für Visual Studio-2017
Ab Visual Studio 2017, ist Visual Studio Ändern der Methode erkannten Projekt- und Elementvorlagen, die durch eine VSIX oder eine MSI-Datei installiert wurden. Wenn Sie Erweiterungen besitzen, die Verwenden von benutzerdefinierten Projekt- oder Elementvorlagen, müssen Sie Ihre Erweiterungen zu aktualisieren. In diesem Thema wird erläutert, was Sie tun müssen.  
  
 Diese Änderung betrifft nur die Visual Studio-2017. Er wirkt sich nicht auf frühere Versionen von Visual Studio aus.  
  
 Wenn Sie eine Projekt- oder Elementvorlage als Teil einer VSIX-Erweiterung erstellen möchten, finden Sie unter [Erstellen von benutzerdefinierten Projekt- und Elementvorlagen](../extensibility/creating-custom-project-and-item-templates.md).  
  
## <a name="template-scanning"></a>Vorlage Scannen  
 Zuvor **Devenv/Setup** oder **Devenv/installvstemplates** überprüft den lokalen Datenträger zum Suchen von Projekt- und Elementvorlagen. Ab Preview 4, Scan erfolgt nur für den Speicherort der Benutzerebene (**%USERPROFILE%\Documents\\< Visual Studio-Version\>\My Exported Templates\\**), die für verwendet wird Vorlagen, die generiert werden, indem Sie die **Datei / Exportieren von Vorlagen** Befehl.  
  
 Für andere Speicherorte (Nichtbenutzercode) müssen Sie eine manifest(.vstman)-Datei einschließen, die den Speicherort und andere Merkmale der Vorlage angibt. Die Datei .vstman zusammen mit der Vorlagen zum VSTEMPLATE-Datei generiert wurde. Bei der Installation der Erweiterungs mithilfe einer VSIX können Sie dies durch das erneute Kompilieren der Erweiterungs in Visual Studio 2017 zu erreichen. Aber wenn Sie eine MSI-Datei verwenden, müssen Sie die Änderungen manuell vornehmen. Eine Übersicht darüber, was Sie tun können, um diese Änderungen vornehmen müssen, finden Sie unter **Upgrades für Erweiterungen installiert mit ein. MSI-Datei** weiter unten in diesem Thema.  
  
## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Vorgehensweise beim Aktualisieren einer VSIX-Erweiterungs mit Projekt- oder Elementvorlagen  
 Dieses Verfahren wird erläutert, wie Visual Studio 2017 haben
1.  Öffnen Sie die Projektmappe in Visual Studio 2017. Sie werden aufgefordert, den Code aktualisieren. Klicken Sie auf **OK**.  
  
2.  Nach Abschluss des Upgrades müssen Sie die Version des Ziels Installation ändern. Klicken Sie im VSIX-Projekt, öffnen Sie die Datei "Source.Extension.vsixmanifest", und wählen die **Ziele installieren** Registerkarte. Wenn die **Versionsbereich** Feld **[14.0]**, klicken Sie auf **bearbeiten** , und ändern Sie sie, um Visual Studio 2017 einzuschließen. Angenommen, Sie können legen Sie sie auf **[14.0,15.0]** zum Installieren der Erweiterung für Visual Studio 2015 oder Visual Studio 2017, Sie und **[15.0]** nur Visual Studio 2017 Installationsspeicherorts.  
  
3.  Kompilieren Sie der Code neu.  
  
4.  Schließen Sie Visual Studio.  
  
5.  Installieren Sie die VSIX-Projekt.  
  
6.  Sie können das Update testen, indem Sie wie folgt:  
  
    1.  Die Datei Scannen ändern wird aktiviert, mit dem folgenden Registrierungsschlüssel:  
  
         **REG hinzufügen hklm\software\microsoft\visualstudio\15.0\VSTemplate/v DisableTemplateScanning/t REG_DWORD/d 1 /reg:32**  
  
    2.  Nachdem Sie den Schlüssel hinzugefügt haben, führen Sie **Devenv/installvstemplates**.  
  
    3.  Öffnen Sie Visual Studio erneut. Sie sollten Ihre Vorlage in den erwarteten Speicherort gefunden werden.  
  
    > [!NOTE]
    >  Die Erweiterbarkeit von Visual Studio-Projektvorlagen sind nicht verfügbar, wenn der Registrierungsschlüssel vorhanden ist. Sie müssen den Registrierungsschlüssel löschen (und führen Sie erneut aus **Devenv/installvstemplates**) zu verwenden.  
  
## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Empfehlungen für die Bereitstellung von Projekt- und Elementvorlagen  
  
-   Vermeiden Sie die Verwendung von ZIP-Dateien. ZIP-Vorlage, die Dateien dekomprimiert, damit Ressourcen und der Inhalt abgerufen werden müssen, sodass costlier verwendet werden. Stattdessen sollten Sie die Projekt- und Elementvorlagen als einzelne Dateien in ihre eigenen Verzeichnis zum Beschleunigen der Vorlage Initialisierung bereitstellen. Für VSIX-Erweiterungen werden Buildaufgaben SDK automatisch alle ZIP-Vorlage Entpacken Sie beim Erstellen der VSIX-Datei.  
  
-   Vermeiden Sie die Verwendung von/Ressource "Package" ID-Einträge für Vorlagennamen, Beschreibung, Symbol und Vorschau, um nicht benötigte Ressource beim Laden von Assemblys bei der Ermittlung der Vorlage zu vermeiden. Stattdessen können Sie lokalisierte Manifeste, für jedes Gebietsschema einen Vorlageneintrag für die erstellen, die lokalisierten Namen oder Eigenschaften verwendet.  
  
-   Wenn Sie Vorlagen als Dateielemente einschließen, Generierung von Manifesten Ihnen möglicherweise nicht die erwarteten Ergebnisse. In diesem Fall müssen Sie ein Manifest manuell generiert das VSIX-Projekt hinzufügen.  
  
## <a name="file-changes-in-project-and-item-templates"></a>Änderungen der Datenbankdatei im Projekt- und Elementvorlagen  
Der Unterschied zwischen dem Visual Studio 2015 und Visual Studio 2017 Versionen die Vorlagendateien zu Punkte aufgeführt, damit Sie die neuen Dateien korrekt erstellen zu können.  
  
 So sieht die standardmäßige Projekt VSTEMPLATE-Datei von Visual Studio 2015 erstellt:  
  
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
  
 So sieht die .vstman-Datei (Sie können sie die VSIX-Projekt manifest finden im Verzeichnis), die aufgrund eines die Neuerstellung des VSIX-Projekts aus:  
  
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
  
 Die Informationen der [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) Element bleibt unverändert. Die  **\<VSTemplateContainer >** -Element verweist auf die VSTEMPLATE-Datei für die zugehörige Vorlage.  
  
 So sieht die standardmäßige Element VSTEMPLATE-Datei von Visual Studio 2015 erstellt:  
  
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
  
 So sieht die .vstman-Datei (Sie können sie die VSIX-Projekt manifest finden im Verzeichnis), die aufgrund eines die Neuerstellung des VSIX-Projekts aus:  
  
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
  
 Die Informationen der  **\<TemplateData >** Element bleibt unverändert. Die  **\<VSTemplateContainer >** -Element verweist auf die VSTEMPLATE-Datei für die zugehörige Vorlage  
  
 Weitere Informationen über die verschiedenen Elemente der Datei .vstman finden Sie unter [Visual Studio Manifest Schemareferenz](../extensibility/visual-studio-template-manifest-schema-reference.md).  
  
## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Upgrades für Erweiterungen installiert mit ein. MSI-DATEI  
 Einige Erweiterungen MSI-basierte stellen Vorlagen für allgemeine Speicherorte für Vorlagen wie z. B. Folgendes bereit:  
  
-   **\<Visual Studio-Installationsverzeichnis > \Common7\IDE\\< ProjectTemplates/ItemTemplates >**  
  
-   **\<Visual Studio-Installationsverzeichnis > \Common7\IDE\Extensions\\<.-Kennung Erweiterungsname\>\\< Projekt/ItemTemplates >**  
  
 Wenn die Erweiterung eine MSI-basierte Bereitstellung ausgeführt werden, müssen Sie das Vorlagemanifest manuell zu generieren, und stellen Sie sicher, dass sie in der Erweiterung Setup enthalten ist. Sie sollten die oben aufgeführten .vstman Beispiele vergleichen und die [Visual Studio Manifest Schemareferenz](../extensibility/visual-studio-template-manifest-schema-reference.md). um festzustellen, was müssen Sie zum Hinzufügen  
  
 Sollten Sie separate Manifeste für Projekt- und Elementvorlagen erstellen, und sie sollten zeigen Sie auf der Vorlage Stammverzeichnis gemäß oben. Erstellen Sie ein Manifest pro Erweiterung und Gebietsschema.  
  
## <a name="troubleshooting-template-installation"></a>Problembehandlung bei der Vorlageninstallation  
 Wenn Sie Ihre Projekt- oder Elementvorlagen Bereitstellung Probleme auftreten, können Sie die diagnoseprotokollierung aktivieren.  
  
1.  Erstellen Sie eine Pkgdef-Datei im Ordner "Common7\IDE\CommonExtensions" für die Installation (z. B. C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef), mit dem folgenden Inhalt:  
  
     ```
     [$RootKey$\VsTemplate]
     "EnableTemplateDiscoveryLog"=dword:00000001
     ```

2. Öffnen Sie "Developer-Eingabeaufforderung" für die Installation, indem Sie in der Windows-Suche gesucht, und führen `devenv /updateConfiguration`.

3.  Starten Sie Visual Studio, und starten Sie die Dialogfenster des neues Projekt und neues Element zum Initialisieren der beiden Strukturen Vorlage. Das Protokoll für die Vorlage wird nun in **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (Instanceid entspricht die Installations-ID Ihrer Instanz von Visual Studio). Jede Vorlage Struktur Initialisierung fügt Einträge in dieses Protokoll.  
  
 Die Protokolldatei enthält die folgenden Spalten:  
  
-   **FullPathToTemplate**, dem hat die folgenden Werte:  
  
    -   1 für die Manifest-basierte Bereitstellung  
  
    -   0 für Datenträger-basierte Bereitstellung  
  
-   **TemplateFileName**  
  
-   Andere Vorlageneigenschaften

Hinweis: Um die Protokollierung deaktivieren möchten, entfernen Sie die Pkgdef-Datei oder ändern Sie den Wert der `EnableTemplateDiscoveryLog` auf `dword:00000000` und führen Sie `devenv /updateConfiguration` erneut aus.
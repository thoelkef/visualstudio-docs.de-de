---
title: Aktualisieren von benutzerdefinierten Projekt- und Elementvorlagen für Visual Studio "15" | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9137510f8d6949271a255b14b293f59366048f77
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49923445"
---
# <a name="upgrading-custom-project-and-item-templates-for-visual-studio-15"></a>Aktualisieren von benutzerdefinierten Projekt- und Elementvorlagen für Visual Studio "15"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ab Visual Studio "15" ändert Preview 4, Visual Studio sich die Methode erkannten Projekt- und Elementvorlagen, die vom VSIX oder in eine MSI-Datei installiert wurden. Wenn Sie Erweiterungen, die Verwenden von benutzerdefinierten Projekt- oder Elementvorlagen verfügen, müssen Sie Ihre Erweiterungen zu aktualisieren. In diesem Thema wird erläutert, was Sie tun müssen.  
  
 Diese Änderung betrifft nur Visual Studio "15". Es wirkt sich nicht auf frühere Versionen von Visual Studio aus.  
  
 Wenn Sie eine Projekt- oder Elementvorlage während der VSIX-Erweiterung erstellen möchten, finden Sie unter [Erstellen von benutzerdefinierten Projekt- und Elementvorlagen](../extensibility/creating-custom-project-and-item-templates.md).  
  
## <a name="template-scanning"></a>Vorlage überprüfen  
 Zuvor **Devenv/Setup** oder **Devenv/installvstemplates** durchsucht den lokalen Datenträger aus, um die Projekt- und Elementvorlagen zu suchen. Ab Preview 4 Überprüfung erfolgt nur für den Speicherort auf Benutzerebene (**%USERPROFILE%\Documents\\< Visual Studio-Version\>\My Exported Templates\\**), die für die verwendet wird Vorlagen, die von generiert die **Datei / Exportieren von Vorlagen** Befehl.  
  
 Für andere Speicherorte (nicht-Benutzer) müssen Sie eine Datei manifest(.vstman) einschließen, die den Speicherort und andere Merkmale der Vorlage angibt. Die vstman-Datei wird zusammen mit der Vorlagen zum VSTEMPLATE-Datei generiert. Wenn Sie die Erweiterung VSIX mit installieren, können Sie dies erreichen, durch das erneute Kompilieren der Erweiterungs in Visual Studio "15" Preview 2. Aber wenn Sie eine MSI-Datei verwenden, müssen Sie die Änderungen manuell vornehmen. Eine Übersicht darüber, was Sie tun, um diese Änderungen vornehmen müssen, finden Sie unter **Upgrades für die Erweiterungen installiert, mit ein. MSI** weiter unten in diesem Thema.  
  
## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Aktualisieren Sie eine VSIX-Erweiterung mit Projekt- oder Elementvorlagen  
 Dieses Verfahren wird erläutert, wie Visual Studio "15" Preview 2-Update haben Ihre vorhandene VSIX-Erweiterung.  
  
1.  Öffnen Sie die Projektmappe in Visual Studio "15" Preview 2. Sie werden aufgefordert, den Code aktualisieren. Klicken Sie auf **OK**.  
  
2.  Nachdem das Upgrade abgeschlossen ist, müssen Sie die Version von des installationsziels ändern. Klicken Sie im VSIX-Projekt, öffnen Sie die Datei "Source.Extension.vsixmanifest", und wählen die **Ziele installieren** Registerkarte. Wenn die **Versionsbereich** Feld **[14.0]**, klicken Sie auf **bearbeiten** und ändern Sie diese in Visual Studio "15" enthalten. Angenommen, Sie können sie festlegen **[14.0,15.0]** zum Installieren der Erweiterung Visual Studio 2015 oder Visual Studio "15" und um **[15.0]** zu Visual Studio "15" installiert.  
  
3.  Kompilieren Sie der Code neu.  
  
4.  Schließen Sie Visual Studio.  
  
5.  Installieren Sie die VSIX-Datei.  
  
6.  Sie können das Update testen, indem Sie wie folgt vorgehen:  
  
    1.  Die Datei, die Überprüfung ändern wird aktiviert, durch den folgenden Registrierungsschlüssel:  
  
         **REG hinzufügen hklm\software\microsoft\visualstudio\15.0\VSTemplate/v DisableTemplateScanning/t REG_DWORD/d 1 /reg:32**  
  
    2.  Nachdem Sie den Schlüssel hinzugefügt haben, führen Sie **Devenv/installvstemplates**.  
  
    3.  Öffnen Sie Visual Studio erneut. Sie sollten Ihre Vorlage am erwarteten Speicherort finden.  
  
    > [!NOTE]
    >  Die Erweiterbarkeit von Visual Studio-Projektvorlagen sind nicht verfügbar, wenn der Registrierungsschlüssel vorhanden ist. Sie müssen den Registrierungsschlüssel löschen (und erneut ausführen **Devenv/installvstemplates**) ihre Verwendung.  
  
## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Weitere Empfehlungen für die Bereitstellung von Projekt- und Elementvorlagen  
  
-   Vermeiden Sie die Verwendung des ZIP-Vorlagendateien. ZIP-Vorlage, die Dateien, um Ressourcen und Inhalte abzurufen, dekomprimiert werden müssen, also Leistungsseite verwendet werden. Stattdessen sollten Sie die Projekt- und Elementvorlagen als einzelne Dateien unter einem eigenen Verzeichnis zur Beschleunigung von Vorlage-Initialisierung bereitstellen. VSIX-Erweiterungen vorliegen werden Buildaufgaben SDK automatisch alle ZIP-Vorlage Entzippen Sie beim Erstellen der VSIX-Datei.  
  
-   Vermeiden Sie die Verwendung der Ressource "Package" / ID-Einträge nach dem Vorlagennamen, die Beschreibung "," Symbol "oder" (Vorschau), um unnötige Ressourcenassembly zu vermeiden, lädt während der vorlagenermittlung. Stattdessen können Sie lokalisierte Manifeste verwenden, einen Vorlageneintrag für jedes Gebietsschema, zu erstellen, die lokalisierten Namen oder Eigenschaften verwendet.  
  
-   Wenn Sie Vorlagen, die als Dateielemente einschließen, Generierung von Manifesten Ihnen möglicherweise nicht die erwarteten Ergebnisse. In diesem Fall müssen Sie ein Manifest manuell generierte VSIX-Projekt hinzu.  
  
## <a name="file-changes-in-project-and-item-templates"></a>Dateiänderungen auf Projekt- und Elementvorlagen  
 Zeigen wir die Punkte der Unterschied zwischen der Version von Visual Studio 2015 und Visual Studio "15"-Version der Vorlagendateien, sodass Sie die neuen Dateien korrekt erstellen zu können.  
  
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
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
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
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
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
 Einige MSI-basierte Erweiterungen Bereitstellen von Vorlagen in allgemeine Vorlage Speicherorte wie z. B. die folgenden:  
  
- **\<Visual Studio-Installationsverzeichnis > \Common7\IDE\\< ProjectTemplates / "ItemTemplates" >**  
  
- **\<Visual Studio-Installationsverzeichnis > \Common7\IDE\Extensions\\< ExtensionName\>\\< Project / "ItemTemplates" >**  
  
  Wenn die Erweiterung eine MSI-basierte Bereitstellung ausgeführt wird, müssen Sie das Vorlagemanifest manuell zu generieren, und stellen Sie sicher, dass sie in der Erweiterung-Setup enthalten ist. Sie sollten die oben aufgeführten vstman-Beispiele vergleichen und die [Visual Studio-Manifest Schemareferenz zu Vorlagen](../extensibility/visual-studio-template-manifest-schema-reference.md). um festzustellen, was Sie enthalten  
  
  Erstellen Sie separate Manifeste für Projekt- und Elementvorlagen, und diese Vorlage Stammverzeichnis wie oben zeigen sollte. Erstellen Sie ein Manifest pro Erweiterung und Gebietsschema.  
  
## <a name="troubleshooting-template-installation"></a>Problembehandlung bei der Vorlageninstallation  
 Wenn Sie Ihre Projekt- oder Elementvorlagen Bereitstellung Probleme auftreten, können Sie die diagnoseprotokollierung aktivieren.  
  
1. Führen Sie den folgenden Befehl aus, um den Registrierungsschlüssel zum Aktivieren der Protokollierung festlegen:  
  
    **REG hinzufügen HKCU\software\microsoft\visualstudio\15.0_Config\VSTemplate/v EnableTemplateDiscoveryLog/t REG_DWORD/d 1**  
  
2. Starten Sie Visual Studio, und starten Sie die Dialogfeldern "Neues Projekt und neues Element" zum Initialisieren der beiden Bäumen Vorlage. Das Protokoll für die Vorlage wird nun in **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0\VsTemplateDiagnosticsList.csv**. Jede Vorlage Struktur Initialisierung fügt Einträge in dieses Protokoll.  
  
   Die Protokolldatei enthält die folgenden Spalten:  
  
-   **FullPathToTemplate**, der hat die folgenden Werte:  
  
    -   1 für die Manifest-basierte Bereitstellung  
  
    -   0 für die Datenträger-basierte Bereitstellung  
  
-   **TemplateFileName**  
  
-   Andere Eigenschaften


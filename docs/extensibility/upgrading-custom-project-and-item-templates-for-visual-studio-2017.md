---
title: "Aktualisieren von benutzerdefinierten Projekt- und Elementvorlagen für Visual Studio &quot;15&quot; | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
caps.latest.revision: 3
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
ms.sourcegitcommit: 512014c5070e4314ad2b7d0e8c5c404c43f32cd9
ms.openlocfilehash: af2000e6c3649b625c54ed9dc2706d64642016ad
ms.lasthandoff: 02/22/2017

---
# <a name="upgrading-custom-project-and-item-templates-for-visual-studio-2017"></a>Aktualisieren von benutzerdefinierten Projekt- und Elementvorlagen für Visual Studio 2017
Ab Visual Studio 2017, ist Visual Studio Ändern der Anzeigemethode für Projekt- und Elementvorlagen ermittelt werden, die vom VSIX oder eine MSI-Datei installiert wurden. Wenn Sie Erweiterungen, die angepasste Projekt- oder Elementvorlagen verwenden besitzen, müssen Sie Ihre Erweiterungen zu aktualisieren. In diesem Thema wird erläutert, was Sie tun müssen.  
  
 Diese Änderung betrifft nur Visual Studio 2017. Es wirkt sich nicht auf frühere Versionen von Visual Studio aus.  
  
 Wenn Sie eine Projekt oder Elementvorlage als Teil einer VSIX-Erweiterung erstellen möchten, finden Sie unter [Erstellen von benutzerdefinierten Projekt- und Elementvorlagen](../extensibility/creating-custom-project-and-item-templates.md).  
  
## <a name="template-scanning"></a>Vorlage überprüfen  
 Zuvor **Devenv/Setup** oder **Devenv/installvstemplates** durchsucht den lokalen Datenträger zu Projekt- und Elementvorlagen. Ab Preview 4 Überprüfung erfolgt nur für den Speicherort der Benutzerebene (**%USERPROFILE%\Documents\\<Visual studio=""></Visual>\>\My Exported Templates\\**), für Vorlagen, die von generierten verwendet die **Datei / Export Vorlagen** Befehl.  
  
 Für andere Speicherorte (nicht-Benutzer) müssen Sie eine manifest(.vstman)-Datei einschließen, die den Speicherort und andere Merkmale der Vorlage angibt. Die .vstman-Datei wird zusammen mit der Vorlagen zum VSTEMPLATE-Datei generiert. Wenn Sie die Erweiterung mithilfe einer VSIX installieren, können Sie dies durch das erneute Kompilieren der Erweiterungs in Visual Studio 2017 erreichen. Aber wenn Sie eine MSI-Datei verwenden, müssen Sie manuell ändern. Eine Übersicht darüber, Sie tun was, um diese Änderungen vorgenommen haben, finden Sie unter **Upgrades für Erweiterungen installiert, mit ein. MSI-Datei** weiter unten in diesem Thema.  
  
## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Gewusst wie: Aktualisieren eine VSIX-Erweiterung mit Projekt- oder Elementvorlagen  
 Dieses Verfahren wird erläutert, wie Visual Studio 2017 haben
1.  Öffnen Sie die Projektmappe in Visual Studio 2017. Sie werden aufgefordert, den Code zu aktualisieren. Klicken Sie auf **OK**.  
  
2.  Nach Abschluss des Upgrades müssen Sie die Version der das Ziel der Installation ändern. Klicken Sie im VSIX-Projekt, öffnen Sie die Datei "Source.Extension.vsixmanifest", und wählen die **Ziele installieren** Registerkarte. Wenn die **Versionsbereich** Feld **[14.0]**, klicken Sie auf **bearbeiten** und ändern Sie diese Visual Studio 2017 enthalten. Angenommen, Sie können ihn auf festlegen **[14.0,15.0]** zum Installieren der Erweiterung Visual Studio 2015 oder Visual Studio 2017 oder zum **[15.0]** , nur für Visual Studio 2017 installieren.  
  
3.  Kompilieren Sie den Code neu.  
  
4.  Schließen Sie Visual Studio.  
  
5.  Installieren Sie die VSIX-Projekt.  
  
6.  Sie können das Update testen, wie folgt:  
  
    1.  Die Datei Scannen ändern wird aktiviert, durch den folgenden Registrierungsschlüssel:  
  
         **REG hklm\software\microsoft\visualstudio\15.0\VSTemplate/v DisableTemplateScanning/t REG_DWORD/d 1 /reg:32 hinzufügen**  
  
    2.  Nachdem Sie den Schlüssel hinzugefügt haben, führen Sie **Devenv/installvstemplates**.  
  
    3.  Öffnen Sie Visual Studio erneut. Finden Sie die Vorlage am erwarteten Speicherort.  
  
    > [!NOTE]
    >  Die Erweiterbarkeit von Visual Studio-Projektvorlagen sind nicht verfügbar, wenn der Registrierungsschlüssel vorhanden ist. Sie müssen den Registrierungsschlüssel löschen (und erneut ausführen **Devenv/installvstemplates**) verwenden.  
  
## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Andere Vorgehensweisen zum Bereitstellen von Projekt- und Elementvorlagen  
  
-   Vermeiden Sie die Verwendung von ZIP-Vorlagendateien. ZIP-Vorlage, die zum Abrufen von Ressourcen und Inhalt dekomprimiert werden müssen, sodass costlier verwendet werden. Stattdessen sollten Sie als einzelne Dateien in ihre eigenen Verzeichnis zur Beschleunigung der Vorlage Initialisierung Projekt- und Elementvorlagen bereitstellen. VSIX-Erweiterungen werden Buildaufgaben SDK automatisch eine ZIP-Vorlage dekomprimieren, beim Erstellen der VSIX-Datei.  
  
-   Verwenden Sie Paketressource/ID-Einträge für den Namen, Beschreibung, Symbol oder Vorschau, um nicht benötigte Ressourcen beim Laden von Assemblys bei der Ermittlung der Vorlage zu vermeiden. Lokalisierte Manifeste können Sie stattdessen einen Vorlageneintrag für jedes Gebietsschema erstellen, die lokalisierte Namen oder Eigenschaften verwendet.  
  
-   Wenn Sie Vorlagen als Dateielemente einschließen, Generierung von Manifesten Ihnen möglicherweise nicht die erwarteten Ergebnisse. In diesem Fall müssen Sie ein Manifest manuell generiert das VSIX-Projekt hinzufügen.  
  
## <a name="file-changes-in-project-and-item-templates"></a>Änderungen in den Projekt- und Elementvorlagen  
 Zeigen wir die Punkte der Unterschied zwischen der Version Visual Studio 2015 und Visual Studio "15"-Version, der die Vorlagendateien, damit Sie die neuen Dateien korrekt erstellen zu können.  
  
 Hier ist die standardmäßige Projekt VSTEMPLATE-Datei, die von Visual Studio 2015 erstellt:  
  
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
  
 Hier wird die .vstman-Datei (Sie können sie das VSIX-Projekt manifest finden im Verzeichnis), die aus dem Neuerstellen des VSIX-Projekts:  
  
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
  
 Die Angaben der [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) Element bleibt unverändert. Die ** \<VSTemplateContainer >** -Element verweist auf die VSTEMPLATE-Datei für die zugeordnete Vorlage.  
  
 Hier ist die standardmäßige Element VSTEMPLATE-Datei, die von Visual Studio 2015 erstellt:  
  
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
  
 Hier wird die .vstman-Datei (Sie können sie das VSIX-Projekt manifest finden im Verzeichnis), die aus dem Neuerstellen des VSIX-Projekts:  
  
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
  
 Die Angaben der ** \<TemplateData >** Element bleibt unverändert. Die ** \<VSTemplateContainer >** -Element verweist auf die VSTEMPLATE-Datei für die zugeordnete Vorlage  
  
 Weitere Informationen über die verschiedenen Elemente der Datei .vstman finden Sie unter [Visual Studio-Vorlage Manifest Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md).  
  
## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Upgrades für Erweiterungen installiert, mit ein. MSI-DATEI  
 Einige Erweiterungen MSI-basierte bereitstellen Vorlagen wie z. B. die folgenden allgemeinen Vorlagenpfade:  
  
-   **\<Visual Studio-Installationsverzeichnis > \Common7\IDE\\<ProjectTemplates temtemplates="">**</ProjectTemplates>  
  
-   **\<Visual Studio-Installationsverzeichnis > \Common7\IDE\Extensions\\<>\>\\<Project temtemplates="">**</Project>  
  
 Wenn die Erweiterung eine MSI-basierte Bereitstellung ausgeführt werden, müssen Sie das Vorlagemanifest manuell zu generieren, und stellen Sie sicher, dass er in der Erweiterung enthalten ist. Sie sollten die oben aufgeführten .vstman Beispiele vergleichen und die [Visual Studio-Vorlage Manifest Schema Reference](../extensibility/visual-studio-template-manifest-schema-reference.md). um zu ermitteln, müssen Sie  
  
 Erstellen Sie separate Manifeste für Projekt- und Elementvorlagen und Vorlage Stammverzeichnis gemäß oben zeigen soll. Erstellen Sie ein Manifest pro Erweiterung und Gebietsschema.  
  
## <a name="troubleshooting-template-installation"></a>Problembehandlung bei der Vorlageninstallation  
 Wenn Sie Ihre Projekt- oder Elementvorlagen Bereitstellung Probleme auftreten, können Sie die diagnoseprotokollierung aktivieren.  
  
1.  Führen Sie den folgenden Befehl zum Festlegen des Registrierungsschlüssels, um die Protokollierung zu aktivieren:  
  
     **REG HKCU\software\microsoft\visualstudio\15.0_Config\VSTemplate/v EnableTemplateDiscoveryLog/t REG_DWORD/d 1 hinzufügen**  
  
2.  Starten Sie Visual Studio, und starten Sie die Dialogfeldern Neues Projekt und neues Element zum Initialisieren der beiden Strukturen Vorlage. Das Protokoll für die Vorlage wird nun in **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0\VsTemplateDiagnosticsList.csv**. Jede Vorlage Struktur Initialisierung fügt Einträge in dieses Protokoll.  
  
 Die Protokolldatei enthält die folgenden Spalten:  
  
-   **FullPathToTemplate**, die hat die folgenden Werte:  
  
    -   1 für die Manifest-basierte Bereitstellung  
  
    -   0 für Datenträger-basierte Bereitstellung  
  
-   **TemplateFileName**  
  
-   Andere Eigenschaften

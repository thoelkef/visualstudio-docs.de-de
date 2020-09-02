---
title: Erstellen von benutzerdefinierten Projekt- und Elementvorlagen
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
caps.latest.revision: 11
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c6875e13baa83d349020f50a3fe448a87ec5fd30
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197396"
---
# <a name="creating-custom-project-and-item-templates"></a>Erstellen von benutzerdefinierten Projekt- und Elementvorlagen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Visual Studio SDK enthält Projektvorlagen, die eine benutzerdefinierte Projektvorlage und eine benutzerdefinierte Element Vorlage erstellen. Diese Vorlagen enthalten häufige Parameterersetzungen und sind als ZIP-Dateien gepackt. Sie werden nicht automatisch bereitgestellt und sind nicht in der experimentellen Instanz verfügbar. Kopieren Sie die ZIP-Datei an den Speicherort.

Mit den Vorlagen zur Vorlagenerstellung können Sie Vorlagen in größere Erweiterungen einschließen. Wenn Sie Vorlagen in Erweiterungen einschließen, können Sie die Versionskontrolle in den Quelldateien implementieren und eine Gruppe von Vorlagen Projekten in einem VSIX-Paket erstellen.

Bei der Erstellung einfacher Vorlagen sollten Sie den Assistenten **Vorlage exportieren** verwenden, der eine komprimierte Datei generiert. Weitere Informationen zum Erstellen von grundlegenden Vorlagen finden Sie unter [Erstellen von Projekt-und Element Vorlagen](../ide/creating-project-and-item-templates.md).

Ab Visual Studio 2017 wird das Scannen von benutzerdefinierten Projekt-und Element Vorlagen nicht mehr durchgeführt. Die Erweiterung muss nun Vorlagenmanifestdateien mit dem Installationspfad dieser Vorlagen enthalten. Sie können die Preview 2-Installation verwenden, um Ihre VSIX-Erweiterungen zu aktualisieren. Wenn Sie eine Erweiterung über eine MSI-Datei bereitstellen, müssen Sie die Vorlagenmanifestdateien manuell generieren. Weitere Informationen finden Sie unter [Upgrade Custom Projekt-und Elementvorlagen für Visual Studio 2017](/visualstudio/extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017?view=vs-2015). Das Vorlagen Manifest-Schema ist in der [Schema Referenz für den Visual Studio-Vorlagen Manifest](/visualstudio/extensibility/visual-studio-template-manifest-schema-reference)dokumentiert.

## <a name="create-a-project-template"></a>Erstellen einer Projektvorlage

1. Erstellen Sie ein Projektvorlagenprojekt. Sie finden die Projektvorlage im Dialogfeld " **Neues Projekt** " im Visual Basic-oder Visual c#- **Erweiterbarkeits** Ordner.

     Die Vorlage generiert eine Klassendatei, ein Symbol, eine VSTEMPLATE-Datei, eine bearbeitbare Projektdatei namens ProjectTemplate.vbproj oder ProjectTemplate.csproj und einige Dateien, die üblicherweise von anderen Projekttypen generiert werden, z. B. eine resources.resx-Datei, eine AssemblyInfo-Datei und eine SETTINGS-Datei. Jede Codedatei enthält die benötigten gängigen Parameterersetzungen.

2. Fügen Sie nach Bedarf Elemente zum Projekt hinzu, oder löschen Sie Elemente aus dem Projekt. Entfernen Sie die bearbeitbare Datei, die AssemblyInfo-Datei und die VSTEMPLATE-Datei nicht.

3. Aktualisieren Sie die VSTEMPLATE-Datei den hinzugefügten und entfernten Elementen entsprechend. Das [Project](../extensibility/project-element-visual-studio-templates.md)-Element muss ein [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)-Element für jede Datei enthalten, die der Vorlage hinzugefügt wird.

4. Bearbeiten Sie Codedateien und andere Inhalte für Benutzer, und fügen Sie die entsprechenden Parameterersetzungen hinzu.

5. Bearbeiten Sie den generierten Inhalt nach Bedarf.

6. Erstellen Sie das Projekt.

     Visual Studio erstellt eine ZIP-Datei, die Ihre Vorlage enthält. Diese wird nicht bereitgestellt und ist nicht in der experimentellen Instanz verfügbar.

## <a name="create-an-item-template"></a>Erstellen einer Element Vorlage

1. Erstellen Sie ein Elementvorlagenprojekt.

     Diese Vorlage erstellt eine Klassendatei, ein Symbol, eine VSTEMPLATE-Datei und eine AssemblyInfo-Datei. Die Klassendatei enthält einige gängige Parameterersetzungen.

2. Fügen Sie nach Bedarf Elemente zum Projekt hinzu, oder löschen Sie Elemente aus dem Projekt.

3. Aktualisieren Sie die VSTEMPLATE-Datei den hinzugefügten und entfernten Elementen entsprechend. Das [Project](../extensibility/project-element-visual-studio-templates.md)-Element muss ein [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)-Element für jede Datei enthalten, die der Vorlage hinzugefügt wird.

4. Bearbeiten Sie Codedateien und andere Inhalte für Benutzer, und fügen Sie die entsprechenden Parameterersetzungen hinzu.

5. Bearbeiten Sie den generierten Inhalt nach Bedarf.

6. Erstellen Sie das Projekt.

     Visual Studio erstellt eine komprimierte Datei, die Ihre Vorlage enthält. Diese wird nicht bereitgestellt und ist nicht in der experimentellen Instanz verfügbar.

## <a name="deploy-the-project-or-item-template"></a>Bereitstellen der Projekt-oder Element Vorlage

1. Erstellen eines VSIX-Projekts Weitere Informationen finden Sie unter [VSIX-Projektvorlage](../extensibility/vsix-project-template.md).

2. Legen Sie das VSIX-Projekt als Startprojekt fest. Klicken Sie im **Projektmappen-Explorer** auf den VSIX-Projektknoten, klicken Sie mit der rechten Maustaste, und wählen Sie **Als Startprojekt festlegen** aus.

3. Legen Sie das Projektvorlagenprojekt als Objekt des VSIX-Projekts fest. Öffnen Sie die VSIXMANIFEST-Datei. Wechseln Sie zur Registerkarte **Objekte** , und klicken Sie auf **neu**.

    1. Legen Sie das Feld **Typ** auf **Microsoft.VisualStudio.ProjectTemplate** oder **Microsoft.VisualStudio.ItemTemplate** fest.

    2. Wählen Sie für die Quelle die Option **Ein Projekt in der aktuellen Projektmappe** und dann das Projekt aus, das Ihre Vorlage enthält.

4. Drücken Sie F5, um die Projektmappe zu kompilieren. Die experimentelle Instanz wird geöffnet.

5. Für ein Projektvorlagen Projekt sollte die Projektvorlage im Dialogfeld **Neues Projekt** (Datei >**neu**> Projekt) im Visual c#-oder Visual Basic-Knoten aufgeführt werden. Für ein Element Vorlagen Projekt sollte die Element Vorlage im Dialogfeld Neues Element hinzufügen aufgelistet werden (Klicken Sie im **Projektmappen-Explorer**auf den Projekt Knoten, und klicken Sie auf **Hinzufügen/Neues Element**).

## <a name="see-also"></a>Weitere Informationen

- [Referenz zu Visual Studio-Vorlagen](../ide/visual-studio-template-reference.md)
---
title: Erstellen von benutzerdefinierten Projekt- und Elementvorlagen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d8864c7b3e5bd43de58032daf88a947cd4082c0e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53822332"
---
# <a name="create-custom-project-and-item-templates"></a>Erstellen von benutzerdefinierten Projekt- und Elementvorlagen

Visual Studio SDK umfasst Projektvorlagen, die eine benutzerdefinierte Projektvorlage und eine benutzerdefinierte Elementvorlage zu erstellen. Diese Vorlagen enthalten einige allgemeine Ersetzen von Parametern, und erstellen als Zip-Dateien. Sie werden nicht automatisch bereitgestellt, und sie sind nicht verfügbar, in der experimentellen Instanz. Sie müssen die generierten Zip-Datei in das Verzeichnis mit Benutzervorlagen kopieren.

Die Vorlage erstellen Vorlagen können Sie die Vorlagen in größeren Erweiterungen enthalten. Dadurch können Sie die Versionskontrolle für die Quelldateien implementieren, und erstellen eine Gruppe von Vorlagenprojekten in einem VSIX-Paket.

Sie können auch eine Vorlage zum Installieren von NuGet-Pakete konfigurieren. Weitere Informationen finden Sie unter [NuGet-Pakete in Visual Studio-Vorlagen](/nuget/visual-studio-extensibility/visual-studio-templates).

Für Szenarien für einfache Vorlage erstellen, sollten Sie verwenden die **Vorlage exportieren** -Assistenten, der in eine komprimierte Datei ausgibt. Weitere Informationen zum Erstellen von grundlegenden Vorlage finden Sie unter [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md).

> [!NOTE]
> Ab Visual Studio 2017, Überprüfung von benutzerdefinierten Projekt- und Elementvorlagen nicht mehr erfolgt. Stattdessen muss die Erweiterung vorlagenmanifestdateien bereitstellen, die den Installationsspeicherort der diese Vorlagen zu beschreiben. Sie können Visual Studio 2017 verwenden, um Ihre VSIX-Erweiterungen zu aktualisieren. Wenn Sie die Erweiterung, die mit MSI bereitstellen, müssen Sie die vorlagenmanifestdateien manuell generieren. Weitere Informationen finden Sie unter [Aktualisieren von benutzerdefinierten Projekt- und Elementvorlagen für Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Das manifest Vorlagenschema finden Sie unter [manifest Visual Studio-Schemareferenz](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="create-a-project-template"></a>Erstellen einer Projektvorlage

1.  Erstellen Sie ein Projekt für die Projektvorlage aus. Finden Sie die Projektvorlage in das **neues Projekt** Dialogfeld in Visual Basic oder Visual C#- *Erweiterbarkeit* Ordner.

     Die Vorlage generiert eine Klassendatei, ein Symbol, ein *VSTEMPLATE* -Datei, eine bearbeitbaren-Projektdatei namens *ProjectTemplate.vbproj* oder *ProjectTemplate.csproj*, und einige Dateien, die von anderen Projekttypen in der Regel generiert werden solche eine *"Resources.resx"* -Datei ein *"AssemblyInfo"* -Datei, und ein *Settings* Datei. Jede Codedatei enthält allgemeine Ersetzen von Parametern an, falls zutreffend.

2.  Hinzufügen und Entfernen von Elementen aus dem Projekt als für Ihr Projekt erforderlich. Entfernen Sie die Projektdatei bearbeitet werden, nicht die *"AssemblyInfo"* -Datei oder das *VSTEMPLATE* Datei.

3.  Update der *VSTEMPLATE* Datei entsprechend alle Hinzufügungen und löschungen. Die [Projekt](../extensibility/project-element-visual-studio-templates.md) -Element muss enthalten eine [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) -Element für jede Datei, die in der Vorlage enthalten sein.

4.  Ändern Sie Ihre Codedateien und anderem benutzerseitigen Inhalt, und fügen Sie entsprechende parameterersetzungen.

5.  Ändern Sie den generierten Inhalt nach Bedarf.

6.  Erstellen Sie das Projekt.

     Visual Studio erstellt eine *ZIP* -Datei, die Ihre Vorlage enthält. Es wird nicht bereitgestellt, und es ist nicht verfügbar, in der experimentellen Instanz.

## <a name="create-an-item-template"></a>Erstellen Sie eine Elementvorlage

1.  Erstellen Sie eine Elementvorlage-Projekt.

     Die Vorlage generiert eine Klassendatei, ein Symbol, ein *VSTEMPLATE* -Datei, und ein *"AssemblyInfo"* Datei. Die Klassendatei enthält einige allgemeine Ersetzen von Parametern.

2.  Hinzufügen und Entfernen von Elementen aus dem Projekt als für Ihr Projekt erforderlich.

3.  Update der *VSTEMPLATE* Datei entsprechend alle Hinzufügungen und löschungen. Die [Projekt](../extensibility/project-element-visual-studio-templates.md) -Element muss enthalten eine [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) -Element für jede Datei, die in der Vorlage enthalten sein.

4.  Ändern Sie Ihre Codedateien und anderem benutzerseitigen Inhalt, und fügen Sie entsprechende parameterersetzungen.

5.  Generierten Inhalt nach Bedarf zu ändern.

6.  Erstellen Sie das Projekt.

     Visual Studio erstellt eine komprimierte Datei, die Ihre Vorlage enthält. Es wird nicht bereitgestellt, und es ist nicht verfügbar, in der experimentellen Instanz.

## <a name="deployment"></a>Bereitstellung

### <a name="to-deploy-the-project-or-item-template"></a>Zum Bereitstellen der Vorlage für Projekt oder Element

1.  Erstellen eines VSIX-Projekts Weitere Informationen finden Sie unter [VSIX-Projektvorlage](../extensibility/vsix-project-template.md).

2.  Festlegen Sie das VSIX-Projekt als Startprojekt. In der **Projektmappen-Explorer**, wählen Sie die VSIX-Projektknoten, mit der rechten Maustaste und wählen Sie **als Startprojekt festlegen**.

3.  Legen Sie das Projektvorlagenprojekt als Medienobjekt des VSIX-Projekts. Öffnen der *vsixmanifest* Datei. Wechseln Sie zu der **Assets** Registerkarte, und klicken Sie auf **neu**.

    1.  Legen Sie die **Typ** Feld **Microsoft.VisualStudio.ProjectTemplate** oder **Microsoft.VisualStudio.ItemTemplate**.

    2.  Wählen Sie für Quelle und das **ein Projekt in der aktuellen Projektmappe** aus, und wählen Sie dann auf das Projekt, das die Vorlage enthält.

4.  Die Projektmappe erstellen, und drücken Sie **F5**. Die experimentelle Instanz angezeigt wird.

5.  Für ein Projektvorlagenprojekt, sollte Ihre Projektvorlage aufgeführt, die der **neues Projekt** Dialogfeld (**Datei** > **neu**  >  **Projekt**) in den Visual c# oder Visual Basic-Knoten. Für ein Elementvorlagenprojekt, sollte die Elementvorlage aufgeführt, die der **neues Element hinzufügen** Dialogfeld. Anzeigen der **neues Element hinzufügen** Dialogfeld aus der **Projektmappen-Explorer**, wählen Sie den Projektknoten, und klicken Sie auf **hinzufügen** > **neues Element**).

## <a name="see-also"></a>Siehe auch

[Referenz zu Visual Studio-Vorlagen](../ide/creating-project-and-item-templates.md)
[NuGet-Pakete in Visual Studio-Vorlagen](/nuget/visual-studio-extensibility/visual-studio-templates)

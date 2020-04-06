---
title: Erstellen benutzerdefinierter Projekt- und Elementvorlagen | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae404004f2660048ef7581a661d8f785495ed95a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739449"
---
# <a name="create-custom-project-and-item-templates"></a>Erstellen benutzerdefinierter Projekt- und Elementvorlagen

Das Visual Studio SDK enthält Projektvorlagen, die eine benutzerdefinierte Projektvorlage und eine benutzerdefinierte Elementvorlage erstellen. Diese Vorlagen enthalten einige häufige Parameterersetzungen und werden als ZIP-Dateien erstellt. Sie werden nicht automatisch bereitgestellt und sind in der experimentellen Instanz nicht verfügbar. Sie müssen die generierte ZIP-Datei in das Benutzervorlagenverzeichnis kopieren.

Mit den Vorlagenerstellungsvorlagen können Sie Vorlagen in größere Erweiterungen einschließen. Auf diese Weise können Sie die Versionskontrolle für die Quelldateien implementieren und eine Gruppe von Vorlagenprojekten in einem VSIX-Paket erstellen.

Sie können auch eine Vorlage für die Installation von NuGet-Paketen konfigurieren. Weitere Informationen finden Sie unter [NuGet-Pakete in Visual Studio-Vorlagen](/nuget/visual-studio-extensibility/visual-studio-templates).

Für grundlegende Vorlagenerstellungsszenarien sollten Sie den **Assistenten zum Exportieren** von Vorlagen verwenden, der in einer komprimierten Datei ausgegeben wird. Weitere Informationen zur Erstellung grundlegender Vorlagen finden Sie unter [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md).

> [!NOTE]
> Ab Visual Studio 2017 wird das Scannen nach benutzerdefinierten Projekt- und Elementvorlagen nicht mehr ausgeführt. Stattdessen muss die Erweiterung Vorlagenmanifestdateien bereitstellen, die den Installationsspeicherort dieser Vorlagen beschreiben. Sie können Visual Studio 2017 verwenden, um Ihre VSIX-Erweiterungen zu aktualisieren. Wenn Sie ihre Erweiterung mit einer MSI bereitstellen, müssen Sie die Vorlagenmanifestdateien von Hand generieren. Weitere Informationen finden Sie unter [Aktualisieren benutzerdefinierter Projekt- und Elementvorlagen für Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Das Vorlagenmanifestschema wird in [Visual Studio-Vorlagenmanifestschemareferenz](../extensibility/visual-studio-template-manifest-schema-reference.md)dokumentiert.

## <a name="create-a-project-template"></a>Erstellen einer Projektvorlage

1. Erstellen Sie ein Projektvorlagenprojekt. Sie können die Projektvorlage im Dialogfeld **"Neues Projekt"** finden, indem Sie nach "Projektvorlage" suchen und entweder die Version "C" oder "Visual Basic" auswählen.

     Die Vorlage generiert eine Klassendatei, ein Symbol, eine *.vstemplate-Datei,* eine bearbeitbare Projektdatei namens *ProjectTemplate.vbproj* oder *ProjectTemplate.csproj*und einige Dateien, die normalerweise von anderen Projekttypen generiert werden, z. B. einer *Datei resources.resx,* einer *AssemblyInfo-Datei* und einer *.settings-Datei.* Jede Codedatei enthält ggf. allgemeine Parameterersetzungen.

![Projektvorlagenprojektauswahl](media/project-template-selection.png)

2. Fügen Sie Elemente nach Bedarf für Ihr Projekt hinzu und entfernen Sie sie aus dem Projekt. Entfernen Sie nicht die bearbeitbare Projektdatei, die *AssemblyInfo-Datei* oder die *.vstemplate-Datei.*

3. Aktualisieren Sie die *.vstemplate-Datei,* um alle Hinzufügungen und Löschungen widerzuspiegeln. Das [Project-Element](../extensibility/project-element-visual-studio-templates.md) muss ein [ProjectItem-Element](../extensibility/projectitem-element-visual-studio-item-templates.md) für jede Datei enthalten, die in die Vorlage aufgenommen werden soll.

4. Ändern Sie Ihre Codedateien und andere benutzerbezogene Inhalte, und fügen Sie entsprechende Parameterersetzungen hinzu.

5. Ändern Sie den generierten Inhalt nach Bedarf.

6. Erstellen Sie das Projekt.

     Visual Studio *.zip* erstellt eine ZIP-Datei, die Ihre Vorlage enthält. Sie wird nicht bereitgestellt und ist in der experimentellen Instanz nicht verfügbar.

## <a name="create-an-item-template"></a>Erstellen einer Elementvorlage

1. Erstellen Sie ein Elementvorlagenprojekt.

     Die Vorlage generiert eine Klassendatei, ein Symbol, eine *.vstemplate-Datei* und eine *AssemblyInfo-Datei.* Die Klassendatei enthält einige häufige Parameterersetzungen.

2. Fügen Sie Elemente nach Bedarf für Ihr Projekt hinzu und entfernen Sie sie aus dem Projekt.

3. Aktualisieren Sie die *.vstemplate-Datei,* um alle Hinzufügungen und Löschungen widerzuspiegeln. Das [Project-Element](../extensibility/project-element-visual-studio-templates.md) muss ein [ProjectItem-Element](../extensibility/projectitem-element-visual-studio-item-templates.md) für jede Datei enthalten, die in die Vorlage aufgenommen werden soll.

4. Ändern Sie Ihre Codedateien und andere benutzerbezogene Inhalte, und fügen Sie entsprechende Parameterersetzungen hinzu.

5. Ändern Sie generierte Inhalte nach Bedarf.

6. Erstellen Sie das Projekt.

     Visual Studio erstellt eine komprimierte Datei, die Ihre Vorlage enthält. Sie wird nicht bereitgestellt und ist in der experimentellen Instanz nicht verfügbar.

## <a name="deployment"></a>Bereitstellung

### <a name="to-deploy-the-project-or-item-template"></a>So stellen Sie das Projekt oder die Elementvorlage bereit

1. Erstellen eines VSIX-Projekts Weitere Informationen finden Sie unter [VSIX-Projektvorlage](../extensibility/vsix-project-template.md).

2. Legen Sie das VSIX-Projekt als Startprojekt fest. Wählen Sie im **Projektmappen-Explorer**den VSIX-Projektknoten aus, klicken Sie mit der rechten Maustaste, und wählen Sie **Als Startprojekt festlegen**aus.

3. Legen Sie das Projektvorlagenprojekt als Asset des VSIX-Projekts fest. Öffnen Sie die *.vsixmanifest-Datei.* Wechseln Sie zur Registerkarte **Assets,** und klicken Sie auf **Neu**.

    1. Legen Sie das **Feld Typ** auf **Microsoft.VisualStudio.ProjectTemplate** oder **Microsoft.VisualStudio.ItemTemplate**fest.

    2. Wählen Sie für Quelle die Option **Ein Projekt in der aktuellen Projektmappe** aus, und wählen Sie dann das Projekt aus, das die Vorlage enthält.

4. Erstellen Sie die Lösung, und drücken Sie **F5**. Die experimentelle Instanz wird angezeigt.

5. Bei einem Projektvorlagenprojekt sollte die Projektvorlage im Dialogfeld **Neues Projekt** ( Neues**New** > **Projekt****datei)** > im Knoten Visual C oder Visual Basic aufgeführt sein. Bei einem Elementvorlagenprojekt sollte die Elementvorlage im Dialogfeld **Neues Element** hinzufügen aufgeführt angezeigt werden. Um das Dialogfeld **Neues Element hinzufügen** anzuzeigen, wählen Sie im **Projektmappen-Explorer**den Projektknoten aus, und klicken Sie auf**Neues Element** **hinzufügen** > .

## <a name="see-also"></a>Weitere Informationen

- [Visual Studio-Vorlagenreferenz](../ide/creating-project-and-item-templates.md)
- [NuGet-Pakete in Visual Studio-Vorlagen](/nuget/visual-studio-extensibility/visual-studio-templates)

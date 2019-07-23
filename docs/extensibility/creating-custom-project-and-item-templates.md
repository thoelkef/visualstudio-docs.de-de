---
title: Erstellen von benutzerdefinierten Projekt-und Element Vorlagen | Microsoft-Dokumentation
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 586da5dc-f678-402b-afd0-0332959fd7a6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8fbe1a4decebd68b80e6cbe8728c5de84a44c641
ms.sourcegitcommit: 485881e6ba872c7b28a7b17ceaede845e5bea4fe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2019
ms.locfileid: "68377750"
---
# <a name="create-custom-project-and-item-templates"></a>Erstellen von benutzerdefinierten Projekt-und Element Vorlagen

Das Visual Studio SDK enthält Projektvorlagen, die eine benutzerdefinierte Projektvorlage und eine benutzerdefinierte Element Vorlage erstellen. Diese Vorlagen enthalten einige allgemeine Parameter Ersetzungen und erstellen als ZIP-Dateien. Sie werden nicht automatisch bereitgestellt und sind in der experimentellen Instanz nicht verfügbar. Sie müssen die generierte ZIP-Datei in das Verzeichnis der Benutzer Vorlage kopieren.

Mit Vorlagen Erstellungs Vorlagen können Sie Vorlagen in größeren Erweiterungen einschließen. Auf diese Weise können Sie die Versionskontrolle für die Quelldateien implementieren und eine Gruppe von Vorlagen Projekten in einem VSIX-Paket erstellen.

Sie können auch eine Vorlage für die Installation von nuget-Paketen konfigurieren. Weitere Informationen finden Sie unter [nuget-Pakete in Visual Studio-Vorlagen](/nuget/visual-studio-extensibility/visual-studio-templates).

Für grundlegende Vorlagen Erstellungs Szenarien sollten Sie den Assistenten zum **Exportieren von Vorlagen** verwenden, der in eine komprimierte Datei ausgibt. Weitere Informationen zum Erstellen von grundlegenden Vorlagen finden Sie unter [Erstellen von Projekt-und Element Vorlagen](../ide/creating-project-and-item-templates.md).

> [!NOTE]
> Ab Visual Studio 2017 wird das Scannen von benutzerdefinierten Projekt-und Element Vorlagen nicht mehr durchgeführt. Stattdessen muss die Erweiterung Vorlagen Manifest-Dateien bereitstellen, die den Installationsort dieser Vorlagen beschreiben. Sie können Visual Studio 2017 zum Aktualisieren der VSIX-Erweiterungen verwenden. Wenn Sie Ihre Erweiterung mithilfe einer MSI-Datei bereitstellen, müssen Sie die Vorlagen Manifest-Dateien per Hand generieren. Weitere Informationen finden Sie unter [Aktualisieren von benutzerdefinierten Projekt-und Element Vorlagen für Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Das Vorlagen Manifest-Schema ist in der [Schema Referenz für den Visual Studio-Vorlagen Manifest](../extensibility/visual-studio-template-manifest-schema-reference.md)dokumentiert.

## <a name="create-a-project-template"></a>Erstellen einer Projektvorlage

1. Erstellen Sie ein Projektvorlagen Projekt. Sie finden die Projektvorlage im Dialogfeld " **Neues Projekt** ", indem Sie nach "Projektvorlage" suchen und entweder C# die-oder die-Visual Basic Version auswählen.

     Die Vorlage generiert eine Klassendatei, ein Symbol, eine *VSTEMPLATE* -Datei, eine bearbeitbare Projektdatei namens " *ProjectTemplate. vbproj* " oder " *ProjectTemplate. csproj*" sowie einige Dateien, die in der Regel von anderen Projekttypen generiert werden, z *. b. die Datei Resources. resx* , eine *AssemblyInfo* -Datei und eine *. Settings* -Datei. Jede Codedatei enthält ggf. allgemeine Parameter Ersetzungen.

![Projektvorlagen Projektauswahl](media/project-template-selection.png)


2. Fügen Sie dem Projekt, wie für Ihr Projekt erforderlich, Elemente hinzu, und entfernen Sie Sie. Entfernen Sie die bearbeitbare Projektdatei, die *AssemblyInfo* -Datei oder die *VSTEMPLATE* -Datei nicht.

3. Aktualisieren Sie die *VSTEMPLATE* -Datei, um Ergänzungen und Löschvorgänge widerzuspiegeln. Das [Project](../extensibility/project-element-visual-studio-templates.md) -Element muss ein [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) -Element für jede Datei enthalten, die in der Vorlage enthalten sein soll.

4. Ändern Sie die Code Dateien und anderen Benutzer seitigen Inhalt, und fügen Sie entsprechende Parameter Ersetzungen hinzu.

5. Ändern Sie den generierten Inhalt nach Bedarf.

6. Erstellen Sie das Projekt.

     Visual Studio erstellt eine *ZIP* -Datei, die Ihre Vorlage enthält. Sie wurde nicht bereitgestellt und ist in der experimentellen Instanz nicht verfügbar.

## <a name="create-an-item-template"></a>Erstellen einer Element Vorlage

1. Erstellen Sie ein Element Vorlagen Projekt.

     Die Vorlage generiert eine Klassendatei, ein Symbol, eine *VSTEMPLATE* -Datei und eine *AssemblyInfo* -Datei. Die Klassendatei enthält einige allgemeine Parameter Ersetzungen.

2. Fügen Sie dem Projekt, wie für Ihr Projekt erforderlich, Elemente hinzu, und entfernen Sie Sie.

3. Aktualisieren Sie die *VSTEMPLATE* -Datei, um Ergänzungen und Löschvorgänge widerzuspiegeln. Das [Project](../extensibility/project-element-visual-studio-templates.md) -Element muss ein [ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md) -Element für jede Datei enthalten, die in der Vorlage enthalten sein soll.

4. Ändern Sie die Code Dateien und anderen Benutzer seitigen Inhalt, und fügen Sie entsprechende Parameter Ersetzungen hinzu.

5. Ändern Sie den generierten Inhalt nach Bedarf.

6. Erstellen Sie das Projekt.

     Visual Studio erstellt eine komprimierte Datei, die Ihre Vorlage enthält. Sie wurde nicht bereitgestellt und ist in der experimentellen Instanz nicht verfügbar.

## <a name="deployment"></a>Bereitstellung

### <a name="to-deploy-the-project-or-item-template"></a>So stellen Sie das Projekt oder die Element Vorlage bereit

1. Erstellen eines VSIX-Projekts Weitere Informationen finden Sie unter [VSIX-Projektvorlage](../extensibility/vsix-project-template.md).

2. Legen Sie das VSIX-Projekt als Startprojekt fest. Wählen Sie im **Projektmappen-Explorer**den Knoten VSIX-Projekt aus, klicken Sie mit der rechten Maustaste, und wählen Sie **als Startprojekt festlegen**aus.

3. Legen Sie das Projektvorlagen Projekt als Medienobjekt des VSIX-Projekts fest. Öffnen Sie die *vsixmanifest* -Datei. Wechseln Sie zur Registerkarte **Objekte** , und klicken Sie auf **neu**.

    1. Legen Sie das **Typenfeld** auf **Microsoft. VisualStudio. ProjectTemplate** oder **Microsoft. VisualStudio. ItemTemplate**fest.

    2. Wählen Sie für Quelle die Option **ein Projekt in der aktuellen Projekt** Mappe aus, und wählen Sie dann das Projekt aus, das Ihre Vorlage enthält.

4. Erstellen Sie die Projekt Mappe, und drücken Sie **F5**. Die experimentelle Instanz wird angezeigt.

5. Für ein Projektvorlagen Projekt sollten Sie sehen, dass die Projektvorlage im Dialogfeld " **Neues Projekt** " (**Datei** > "**Neues** > **Projekt**") C# im Knoten "Visual" oder Visual Basic aufgeführt ist. Für ein Element Vorlagen Projekt sollte die Element Vorlage im Dialogfeld **Neues Element hinzufügen** aufgelistet werden. Um das Dialogfeld **Neues Element hinzufügen** anzuzeigen, wählen Sie auf der **Projektmappen-Explorer**den Projekt Knoten aus, und klicken Sie auf**Neues Element** **Hinzufügen** > .)

## <a name="see-also"></a>Siehe auch

- [Referenz zu Visual Studio-Vorlagen](../ide/creating-project-and-item-templates.md)
- [NuGet-Pakete in Visual Studio-Vorlagen](/nuget/visual-studio-extensibility/visual-studio-templates)

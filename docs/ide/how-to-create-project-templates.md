---
title: Erstellen von Projektvorlagen
ms.date: 01/02/2018
ms.topic: conceptual
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- project templates [Visual Studio], creating
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7cd5bd20d5840b560d5954d62e5d158eb1f6c6e6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62430509"
---
# <a name="how-to-create-project-templates"></a>Vorgehensweise: Erstellen von Projektvorlagen

In diesem Artikel wird das Erstellen einer Vorlage mithilfe des **Assistenten zum Exportieren von Vorlagen** erläutert, bei dem Ihre Vorlage in eine *ZIP*-Datei gepackt wird.

## <a name="use-the-export-template-wizard"></a>Verwenden des Assistenten zum Exportieren von Vorlagen

1. Erstellen eines Projekts.

    > [!NOTE]
    > Verwenden Sie nur gültige Bezeichnerzeichen beim Benennen eines Projekts, das als Quelle für eine Vorlage verwendet wird. Andernfalls können Kompilierungsfehler in Projekten auftreten, die anhand der Vorlage erstellt werden. Weitere Informationen zu gültigen Bezeichnerzeichen finden Sie unter [Declared Element Names (Deklarierte Elementnamen)](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names) oder [Identifiers (C++) (Bezeichner (C++))](/cpp/cpp/identifiers-cpp). Stattdessen können Sie auch [Vorlagenparameter](../ide/template-parameters.md) verwenden, damit die Namen Ihrer Klassen und Namespaces „sicher“ sind.

2. Bearbeiten Sie das Projekt solange, bis es als Vorlage exportiert werden kann. Ändern Sie beispielsweise die Codedateien, um anzugeben, an welcher Stelle Parameter ersetzt werden sollen. Weitere Informationen finden Sie unter [Vorgehensweise: Ersetzen von Parametern in einer Vorlage](../ide/how-to-substitute-parameters-in-a-template.md).

3. Klicken Sie im Menü **Projekt** auf **Vorlage exportieren**.

   Der **Assistent zum Exportieren von Vorlagen** wird geöffnet.

4. Wählen Sie auf der Seite **Vorlagentyp auswählen** die Option **Projektvorlage** aus. Wählen Sie das Projekt aus, das Sie in eine Vorlage exportieren möchten, und klicken Sie anschließend auf **Weiter**.

::: moniker range="vs-2017"

5. Geben Sie auf der Seite **Vorlagenoptionen auswählen** einen Namen, ggf. eine Beschreibung sowie ein Symbol für Ihre Vorlage ein, und fügen Sie ein Vorschaubild hinzu. Diese Elemente werden im Dialogfeld **Neues Projekt** angezeigt. Klicken Sie auf **Fertig stellen**.

   Das Projekt wird als *ZIP*-Datei exportiert und am angegebenen Speicherort platziert. Außerdem wird es in Visual Studio importiert, wenn diese Option ausgewählt wurde.

Sie finden Ihre Vorlage im Dialogfeld **Neues Projekt**, indem Sie zunächst **Installiert** und anschließend die Kategorie erweitern, die dem `ProjectType`-Element in der *VSTEMPLATE*-Datei entspricht. Beispielsweise wird eine *VSTEMPLATE*-Datei, die `<ProjectType>CSharp</ProjectType>` enthält, standardmäßig unter **Installiert** > **Visual C#** angezeigt. Sie können Ihre Vorlage in ein Unterverzeichnis des Projekttyps speichern, indem Sie in diesem Verzeichnis einen Ordner erstellen und die *ZIP*-Datei Ihrer Vorlage darin ablegen. Weitere Informationen finden Sie unter [Vorgehensweise: Suchen und Organisieren von Vorlagen](../ide/how-to-locate-and-organize-project-and-item-templates.md).

::: moniker-end

::: moniker range=">=vs-2019"

5. Geben Sie auf der Seite **Vorlagenoptionen auswählen** einen Namen, ggf. eine Beschreibung sowie ein Symbol für Ihre Vorlage ein, und fügen Sie ein Vorschaubild hinzu. Diese Elemente werden in dem Dialogfeld angezeigt, in dem Sie ein neues Projekt erstellen. Klicken Sie auf **Fertig stellen**.

   Das Projekt wird als *ZIP*-Datei exportiert und am angegebenen Speicherort platziert. Außerdem wird es in Visual Studio importiert, wenn diese Option ausgewählt wurde.

Um Ihre Vorlage in dem Dialogfeld zu finden, in dem Sie ein neues Projekt erstellen, suchen Sie anhand des Namens nach ihr, oder scrollen Sie in der Liste. (Das Filtern nach Sprache oder Projekttyp ist für Benutzervorlagen zurzeit nicht möglich.)

::: moniker-end

## <a name="other-ways-to-create-project-templates"></a>Andere Möglichkeiten zum Erstellen von Projektvorlagen

Sie können manuell Projektvorlagen erstellen, indem Sie die Dateien erfassen, die die Grundlage für ein Projekt in einem Ordner darstellen, und eine *VSTEMPLATE*-XML-Datei mit den entsprechenden Metadaten erstellen. Weitere Informationen finden Sie unter [Vorgehensweise: Manuelles Erstellen von Webvorlagen](../ide/how-to-manually-create-web-templates.md).

Wenn das Visual Studio SDK installiert ist, können Sie die fertige Vorlage für die Bereitstellung in einer VSIX-Datei umschließen, indem Sie die Vorlage **VSIX-Projekt** verwenden. Weitere Informationen finden Sie unter [Erste Schritte mit der VSIX-Projektvorlage](../extensibility/getting-started-with-the-vsix-project-template.md).

## <a name="see-also"></a>Siehe auch

- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
- [Vorgehensweise: Erstellen von Elementvorlagen](../ide/how-to-create-item-templates.md)
- [Erste Schritte mit der VSIX-Projektvorlage](../extensibility/getting-started-with-the-vsix-project-template.md)
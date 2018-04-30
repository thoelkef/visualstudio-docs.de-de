---
title: Erstellen einer Projektvorlage für Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/02/2018
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- project templates [Visual Studio], creating
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: a18b756b38a810915ea49e9f3208e9349afda7ef
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-create-project-templates"></a>Vorgehensweise: Erstellen von Projektvorlagen

In diesem Artikel wird das Erstellen einer Vorlage mithilfe des **Assistenten zum Exportieren von Vorlagen** erläutert, bei dem Ihre Vorlage in eine *ZIP*-Datei gepackt wird.

## <a name="to-create-a-user-project-template-by-using-the-export-template-wizard"></a>Erstellen einer Benutzerprojektvorlage mithilfe des Assistenten zum Exportieren von Vorlagen

1. Erstellen eines Projekts.

    > [!NOTE]
    > Verwenden Sie nur gültige Bezeichnerzeichen beim Benennen eines Projekts, das als Quelle für eine Vorlage verwendet wird. Andernfalls können Kompilierungsfehler in Projekten auftreten, die anhand der Vorlage erstellt werden. Weitere Informationen zu gültigen Bezeichnerzeichen finden Sie unter [Declared Element Names (Deklarierte Elementnamen)](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names) oder [Identifiers (C++) (Bezeichner (C++))](/cpp/cpp/identifiers-cpp). Stattdessen können Sie auch [Vorlagenparameter](../ide/template-parameters.md) verwenden, damit die Namen Ihrer Klassen und Namespaces „sicher“ sind.

1. Bearbeiten Sie das Projekt solange, bis es als Vorlage exportiert werden kann. Ändern Sie beispielsweise die Codedateien, um anzugeben, an welcher Stelle Parameter ersetzt werden sollen. Weitere Informationen finden Sie unter [Vorgehensweise: Ersetzen von Parametern in einer Vorlage](../ide/how-to-substitute-parameters-in-a-template.md).

1. Klicken Sie im Menü **Projekt** auf **Vorlage exportieren**.

   Der **Assistent zum Exportieren von Vorlagen** wird geöffnet.

1. Wählen Sie auf der Seite **Vorlagentyp auswählen** die Option **Projektvorlage** aus. Wählen Sie das Projekt aus, das Sie in eine Vorlage exportieren möchten, und klicken Sie anschließend auf **Weiter**.

1. Geben Sie auf der Seite **Vorlagenoptionen auswählen** einen Namen, ggf. eine Beschreibung sowie ein Symbol für Ihre Vorlage ein, und fügen Sie ein Vorschaubild hinzu. Diese Elemente werden im Dialogfeld **Neues Projekt** angezeigt. Klicken Sie auf **Fertig stellen**.

  Das Projekt wird als *ZIP*-Datei exportiert und am angegebenen Speicherort platziert. Außerdem wird es in Visual Studio importiert, wenn diese Option ausgewählt wurde.

>[!NOTE]
> Sie finden Ihre Vorlage im Dialogfeld **Neues Projekt**, indem Sie zunächst **Installiert** und anschließend die Kategorie erweitern, die dem `ProjectType`-Element in der *VSTEMPLATE*-Datei entspricht. Beispielsweise wird eine *VSTEMPLATE*-Datei, die `<ProjectType>CSharp</ProjectType>` enthält, standardmäßig unter **Installiert** > **Visual C#** angezeigt. Sie können Ihre Vorlage in ein Unterverzeichnis des Projekttyps speichern, indem Sie in diesem Verzeichnis einen Ordner erstellen und die *ZIP*-Datei Ihrer Vorlage darin ablegen. Weitere Informationen finden Sie unter [Vorgehensweise: Suchen und Organisieren von Vorlagen](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="other-ways-to-create-project-templates"></a>Andere Möglichkeiten zum Erstellen von Projektvorlagen

Sie können manuell Projektvorlagen erstellen, indem Sie die Dateien erfassen, die die Grundlage für ein Projekt in einem Ordner darstellen, und anschließend eine *VSTEMPLATE*-XML-Datei mit den entsprechenden Metadaten erstellen. Weitere Informationen finden Sie unter [Vorgehensweise: Manuelles Erstellen von Projektvorlagen](../ide/how-to-manually-create-web-templates.md).

Wenn das Visual Studio SDK installiert ist, können Sie die fertige Vorlage für die Bereitstellung in einer VSIX-Datei umschließen, indem Sie die Vorlage **VSIX-Projekt** verwenden. Weitere Informationen finden Sie unter [Erste Schritte mit der VSIX-Projektvorlage](../extensibility/getting-started-with-the-vsix-project-template.md).

## <a name="see-also"></a>Siehe auch

[Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)  
[Vorgehensweise: Erstellen von Elementvorlagen](../ide/how-to-create-item-templates.md)  
[Erste Schritte mit der VSIX-Projektvorlage](../extensibility/getting-started-with-the-vsix-project-template.md)

---
title: Organisieren von Vorlagen in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project templates [Visual Studio], locations
- item templates [Visual Studio], locations
- template locations [Visual Studio]
- Visual Studio templates, organizing
- templates [Visual Studio], organizing
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 167ffa269ea8051a4791000d96a86cb5788af60d
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Vorgehensweise: Suchen und Organisieren von Projekt- und Elementvorlagen

Vorlagendateien müssen an einem Speicherort abgelegt werden, an dem Visual Studio sie findet, damit sie in den Dialogfeldern **Neues Projekt** und **Neues Element hinzufügen** angezeigt werden können. Sie können benutzerdefinierte Unterkategorien für Vorlagen erstellen, die ebenfalls in den Dialogfeldern angezeigt werden.

## <a name="locating-templates"></a>Suchen nach Vorlagen

Installierte Vorlagen und Benutzervorlagen werden an unterschiedlichen Orten gespeichert. Wenn eine komprimierte Datei, die eine VSTEMPLATE-Datei enthält, sich an einem dieser Speicherorte befindet, wird in den Dialogfeldern **Neues Projekt** bzw. **Neues Element hinzufügen** eine Vorlage angezeigt.

> [!TIP]
> Sie können den Speicherort für Benutzervorlagen unter **Extras** > **Optionen** > **Projekte und Projektmappen** > **Speicherorte** festlegen.

### <a name="installed-templates"></a>Installierte Vorlagen

Standardmäßig werden Vorlagen, die gemeinsam mit Visual Studio installiert werden, in folgendem Verzeichnis gespeichert:

- \\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\\*Programmiersprache*\\*Gebietsschema-ID*

- \\*VisualStudioInstallationDirectory*\Common7\IDE\ProjectTemplates\\*Programmiersprache*\\*Gebietsschema-ID*

Das folgende Verzeichnis enthält beispielsweise die Elementvorlagen für Visual Basic für Englisch (LCID 1033):

   C:\\*VisualStudioInstallationDirectory*\Common7\IDE\ItemTemplates\VisualBasic\1033\

### <a name="user-templates"></a>Benutzervorlagen

Benutzervorlagen werden standardmäßig in folgenden Verzeichnissen gespeichert:

- „%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ProjectTemplates“

- „%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates“

Das folgende Verzeichnis enthält beispielsweise die Benutzerprojektvorlagen für C#:

   „C:\Users\UserName\Documents\Visual Studio 2017\Templates\ProjectTemplates\Visual C#\“

> [!NOTE]
> Der Speicherort der Benutzervorlage umfasst keine Unterverzeichnisse des Gebietsschemas für lokalisierte Vorlagen.

Sie können das Standardverzeichnis für Benutzervorlagen im Dialogfeld **Optionen** unter **Projekte und Projektmappen** > **Speicherorte** ändern.

## <a name="organizing-templates"></a>Organisieren von Vorlagen

Die Kategorien in den Dialogfeldern **Neues Projekt** und **Neues Element hinzufügen** spiegeln die Verzeichnisstrukturen wider, so wie sie an den Speicherorten für installierte Vorlagen und Benutzervorlagen angelegt sind. Sie können diese Verzeichnisstrukturen ändern, um Ihre Vorlagen in einer sinnvollen Weise zu organisieren.

> [!NOTE]
> Auf Programmiersprachenebene können keine neuen Kategorien erstellt werden. Neue Kategorien können nur innerhalb der einzelnen Programmiersprachen erstellt werden.

> [!NOTE]
> Wenn die Verzeichnisstrukturen für installierte Vorlagen und Benutzervorlagen für eine bestimmte Sprache nicht übereinstimmen (d.h. in einem Ordner sind Verzeichnisse vorhanden, in einem anderen allerdings nicht), werden sämtliche Kategorien im Dialogfeld **Neues Projekt** angezeigt.

### <a name="organizing-user-templates"></a>Organisieren von Benutzervorlagen

Benutzervorlagen können in eigenen Kategorien organisiert werden, indem dem Speicherort für Benutzervorlagen neue Ordner hinzugefügt werden. Im Dialogfeld **Neues Projekt** werden alle Änderungen angezeigt, die Sie an den Vorlagenkategorien vornehmen.

#### <a name="to-create-new-user-project-template-categories"></a>Erstellen von neuen Kategorien für Benutzerprojektvorlagen

1. Erstellen Sie im Verzeichnis für Benutzerprojektvorlagen einen Ordner im jeweiligen Programmiersprachenordner. Um z.B. die Kategorie **HelloWorld** für C#-Vorlagen einzurichten, erstellen Sie das folgende Verzeichnis:

    „\%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ProjectTemplates\Visual C#\HelloWorld\“

1. Fügen Sie alle Vorlagen für diese Kategorie in den neuen Ordner ein.

1. Wählen Sie im Menü **Datei** die Optionsfolge **Neu** > **Projekt** aus.

   Die Kategorie **HelloWorld** wird im Dialogfeld **Neues Projekt** unter **Installiert** > **Visual C#** angezeigt.

#### <a name="to-create-new-user-item-template-categories"></a>Erstellen neuer Kategorien für Benutzerelementvorlagen

1. Erstellen Sie im Verzeichnis für Benutzerelementvorlagen einen Ordner im jeweiligen Programmiersprachenordner. Um z.B. die Kategorie **HelloWorld** für C#-Elementvorlagen einzurichten, erstellen Sie das folgende Verzeichnis:

    „\%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates\Visual C#\HelloWorld\“

1. Fügen Sie alle Vorlagen für diese Kategorie in den neuen Ordner ein.

1. Erstellen Sie ein Projekt, oder öffnen Sie ein vorhandenes Projekt. Klicken Sie dann im Menü **Projekt** auf **Neues Element hinzufügen**.

   Die Kategorie **HelloWorld** wird im Dialogfeld **Neues Element hinzufügen** unter **Installiert** > **Visual C#-Elemente** angezeigt.

### <a name="displaying-templates-in-parent-categories"></a>Anzeigen von Vorlagen in übergeordneten Kategorien

Sie können in Unterkategorien enthaltene Vorlagen in den übergeordneten Kategorien anzeigen lassen, indem Sie das `NumberOfParentCategoriesToRollUp`-Element in der VSTEMPLATE-Datei verwenden. Diese Schritte sind für Projektvorlagen und Elementvorlagen identisch.

#### <a name="to-display-templates-in-parent-categories"></a>So zeigen Sie Vorlagen in übergeordneten Kategorien an

1. Suchen Sie die ZIP-Datei, die die Vorlage enthält.

1. Extrahieren Sie die ZIP-Datei.

1. Öffnen Sie die VSTEMPLATE-Datei in Visual Studio.

1. Fügen Sie im `TemplateData`-Element ein `NumberOfParentCategoriesToRollUp`-Element hinzu. Durch den folgenden Code wird die Vorlage beispielsweise in der unmittelbar übergeordneten Kategorie, nicht jedoch in höheren Kategorien angezeigt.

    ```xml
    <TemplateData>
        ...
        <NumberOfParentCategoriesToRollUp>
            1
        </NumberOfParentCategoriesToRollUp>
        ...
    </TemplateData>
    ```

1. Speichern und schließen Sie die VSTEMPLATE-Datei.

1. Klicken Sie mit der rechten Maustaste auf die Dateien in der Vorlage, die Sie auswählen möchten, und klicken Sie anschließend auf **Senden an** > **ZIP-komprimierter Ordner**.

   Die Dateien werden in eine ZIP-Datei komprimiert.

1. Löschen Sie die extrahierten Vorlagendateien und die alte ZIP-Datei der Vorlage.

1. Fügen Sie die neue ZIP-Datei in das Verzeichnis ein, in dem sich die gelöschte ZIP-Datei befunden hat.

## <a name="see-also"></a>Siehe auch

[Anpassen von Vorlagen](../ide/customizing-project-and-item-templates.md)  
[Visual Studio Template Schema Reference (Extensibility) (Schemareferenz zu Vorlagen für Visual Studio (Erweiterbarkeit))](../extensibility/visual-studio-template-schema-reference.md)  
[NumberOfParentCategoriesToRollUp (Visual Studio-Vorlagen)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)  
[Gewusst wie: Erstellen von Projektvorlagen](../ide/how-to-create-project-templates.md)  
[Gewusst wie: Erstellen von Elementvorlagen](../ide/how-to-create-item-templates.md)

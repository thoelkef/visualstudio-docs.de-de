---
title: Organisieren von Vorlagen
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project templates [Visual Studio], locations
- item templates [Visual Studio], locations
- template locations [Visual Studio]
- Visual Studio templates, organizing
- templates [Visual Studio], organizing
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: c6bca61dd88b164fcae2b2ccb7e2a98086bf102b
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066287"
---
# <a name="how-to-locate-and-organize-project-and-item-templates"></a>Vorgehensweise: Suchen und Organisieren von Projekt- und Elementvorlagen

Vorlagendateien müssen an einem Speicherort abgelegt werden, an dem Visual Studio sie findet, damit sie in den Dialogfeldern **Neues Projekt** und **Neues Element hinzufügen** angezeigt werden können. Sie können auch benutzerdefinierte Unterkategorien im Ordner für Benutzervorlagen erstellen, diese werden ebenfalls in den Dialogfeldern **Neues Projekt** und **Neues Element hinzufügen** angezeigt.

## <a name="locate-templates"></a>Auffinden von Vorlagen

Installierte Vorlagen und Benutzervorlagen werden an unterschiedlichen Orten gespeichert.

### <a name="user-templates"></a>Benutzervorlagen

Wenn Sie eine komprimierte Datei (*ZIP*), die eine *VSTEMPLATE*-Datei enthält, zum Verzeichnis mit Benutzervorlagen hinzufügen, wird die Vorlage in den Dialogfeldern **Neues Projekt** bzw. **Neues Element hinzufügen** angezeigt. Benutzervorlagen werden standardmäßig in folgenden Verzeichnissen gespeichert:

- *%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ProjectTemplates*

- *%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates*

Das folgende Verzeichnis enthält beispielsweise die Benutzerprojektvorlagen für C#:

- *C:\Users\UserName\Documents\Visual Studio 2017\Templates\ProjectTemplates\Visual C#*

> [!TIP]
> Sie können den Speicherort für Benutzervorlagen unter **Extras** > **Optionen** > **Projekte und Projektmappen** > **Speicherorte** festlegen.

### <a name="installed-templates"></a>Installierte Vorlagen

Standardmäßig werden Vorlagen, die gemeinsam mit Visual Studio installiert werden, in folgendem Verzeichnis gespeichert:

- *\\<VisualStudioInstallationDirectory\>\Common7\IDE\ItemTemplates\\<Programming Language\>\\<Locale ID>*

- *\\<VisualStudioInstallationDirectory\>\Common7\IDE\ProjectTemplates\\<Programming Language\>\\<Locale ID>*

Das folgende Verzeichnis enthält beispielsweise die Elementvorlagen für Visual Basic für Englisch (LCID 1033):

- *C:\\<VisualStudioInstallationDirectory\>\Common7\IDE\ItemTemplates\VisualBasic\1033*

## <a name="organize-templates"></a>Organisieren von Vorlagen

Die Kategorien in den Dialogfeldern **Neues Projekt** und **Neues Element hinzufügen** spiegeln die Verzeichnisstrukturen wider, so wie sie an den Speicherorten für installierte Vorlagen und Benutzervorlagen angelegt sind. Benutzervorlagen können in eigenen Kategorien organisiert werden, indem dem Verzeichnis für Benutzervorlagen neue Ordner hinzugefügt werden. In den Dialogfeldern **Neues Projekt** und **Neues Element hinzufügen** werden alle Änderungen angezeigt, die Sie an den Benutzervorlagenkategorien vornehmen.

> [!NOTE]
> Auf Programmiersprachenebene können keine neuen Kategorien erstellt werden. Neue Kategorien können nur innerhalb der einzelnen Programmiersprachen erstellt werden.

### <a name="to-create-new-user-project-template-categories"></a>Erstellen von neuen Kategorien für Benutzerprojektvorlagen

1. Erstellen Sie im Verzeichnis für Benutzerprojektvorlagen einen Ordner im jeweiligen Programmiersprachenordner. Um z.B. die Kategorie **HelloWorld** für C#-Vorlagen einzurichten, erstellen Sie das folgende Verzeichnis:

    - *\%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ProjectTemplates\Visual C#\HelloWorld*

1. Fügen Sie alle Vorlagen für diese Kategorie in den neuen Ordner ein.

1. Wählen Sie im Menü **Datei** die Optionsfolge **Neu** > **Projekt** aus.

   Die Kategorie **HelloWorld** wird im Dialogfeld **Neues Projekt** unter **Installiert** > **Visual C#** angezeigt.

### <a name="to-create-new-user-item-template-categories"></a>Erstellen neuer Kategorien für Benutzerelementvorlagen

1. Erstellen Sie im Verzeichnis für Benutzerelementvorlagen einen Ordner im jeweiligen Programmiersprachenordner. Um z.B. die Kategorie **HelloWorld** für C#-Elementvorlagen einzurichten, erstellen Sie das folgende Verzeichnis:

    - *\%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ItemTemplates\Visual C#\HelloWorld*

1. Fügen Sie alle Vorlagen für diese Kategorie in den neuen Ordner ein.

1. Erstellen Sie ein Projekt, oder öffnen Sie ein vorhandenes Projekt. Klicken Sie dann im Menü **Projekt** auf **Neues Element hinzufügen**.

   Die Kategorie **HelloWorld** wird im Dialogfeld **Neues Element hinzufügen** unter **Installiert** > **Visual C#-Elemente** angezeigt.

### <a name="display-templates-in-parent-categories"></a>Anzeigen von Vorlagen in übergeordneten Kategorien

Sie können in Unterkategorien enthaltene Vorlagen in den übergeordneten Kategorien anzeigen lassen, indem Sie das `NumberOfParentCategoriesToRollUp`-Element in der *VSTEMPLATE*-Datei verwenden. Diese Schritte sind für Projektvorlagen und Elementvorlagen identisch.

#### <a name="to-display-templates-in-parent-categories"></a>So zeigen Sie Vorlagen in übergeordneten Kategorien an

1. Suchen Sie die *ZIP*-Datei, die die Vorlage enthält.

1. Extrahieren Sie die *ZIP*-Datei.

1. Öffnen Sie die *VSTEMPLATE*-Datei in Visual Studio.

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

1. Speichern und schließen Sie die *VSTEMPLATE*-Datei.

1. Klicken Sie mit der rechten Maustaste auf die Dateien in der Vorlage, die Sie auswählen möchten, und klicken Sie anschließend auf **Senden an** > **ZIP-komprimierter Ordner**.

   Die Dateien werden in eine *ZIP*-Datei komprimiert.

1. Löschen Sie die extrahierten Vorlagendateien und die alte *ZIP*-Datei der Vorlage.

1. Fügen Sie die neue *ZIP*-Datei in das Verzeichnis ein, in dem sich die gelöschte *ZIP*-Datei befunden hat.

## <a name="see-also"></a>Siehe auch

- [Anpassen von Projekt- und Elementvorlagen](../ide/customizing-project-and-item-templates.md)
- [Visual Studio Template Schema Reference (Extensibility) (Schemareferenz zu Vorlagen für Visual Studio (Erweiterbarkeit))](../extensibility/visual-studio-template-schema-reference.md)
- [NumberOfParentCategoriesToRollUp (Visual Studio-Vorlagen)](../extensibility/numberofparentcategoriestorollup-visual-studio-templates.md)
- [Vorgehensweise: Erstellen von Projektvorlagen](../ide/how-to-create-project-templates.md)
- [Vorgehensweise: Erstellen von Elementvorlagen](../ide/how-to-create-item-templates.md)
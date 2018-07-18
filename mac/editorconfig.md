---
title: EditorConfig
description: Verwendung einer EditorConfig-Datei zum Aktivieren konsistenter Codierungskonventionen für Projekte in Visual Studio für Mac.
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 26A0DE31-2FBF-4E1B-99FB-083111AA1680
ms.openlocfilehash: 336ec5ef0779bcd67302bea7b51851dced531a7d
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "33957388"
---
# <a name="creating-and-editing-a-custom-editorconfig-file"></a>Erstellen und Bearbeiten einer benutzerdefinierten EditorConfig-Datei

In Visual Studio für Mac können Sie Ihrem Projekt oder der Codebasis eine [EditorConfig](http://editorconfig.org/)-Datei hinzufügen, um einheitliche Codierungskonventionen für alle Benutzer durchzusetzen, die an der Codebasis arbeiten. Die in der EditorConfig-Datei deklarierten Einstellungen haben Vorrang vor den globalen Einstellungen des Visual Studio-Text-Editors. Die Verwendung einer EditorConfig-Datei in Ihrem Projekt oder Ihrer Codebase ermöglicht Ihnen, Codierungskonventionen, Einstellungen und Warnungen für Ihr Projekt festzulegen. Dies erleichtert allen Benutzern von Visual Studio für Mac, die Codierungspraktiken eines Projekts einzuhalten.

[EditorConfig](http://editorconfig.org/)-Dateien werden von vielen IDEs und Code-Editoren unterstützt, einschließlich Visual Studio 2017. 

## <a name="supported-settings"></a>Unterstützte Einstellungen

Der Editor in Visual Studio unterstützt die gebräuchlichsten [EditorConfig-Eigenschaften](http://editorconfig.org/#supported-properties):

- `indent_style`
- `indent_size`
- `tab_width`
- `end_of_line`
- `charset`
- `trim_trailing_whitespace`
- `insert_final_newline`
- `root`

EditorConfig unterstützt auch die [Formatierung von Codierungskonventionen](https://docs.microsoft.com/visualstudio/ide/editorconfig-code-style-settings-reference) in C#.

## <a name="add-an-editorconfig-file-to-a-project"></a>Hinzufügen einer EditorConfig-Datei zu einem Projekt

### <a name="adding-a-new-editorconfig-file"></a>Hinzufügen einer neuen EditorConfig-Datei

1. Öffnen Sie Ihr Projekt in Visual Studio für Mac. Wählen Sie den Projektknoten aus, dem Sie Dateien hinzufügen möchten.

2. Navigieren Sie mit dem ausgewählten Projektknoten in der Menüleiste zu **Datei > Neue Datei**, um das Dialogfeld **Neue Datei** zu öffnen.

3. Wählen Sie **Misc > Empty Text File** (Sonstiges > Leere Textdatei) aus, und geben Sie ihr den **Namen** `.editorconfig`. Klicken Sie auf **Neu**, um die Datei zu erstellen und im Editor zu öffnen:

    ![Dialogfeld „Neue Datei“](media/editorconfig-image1.png)

4. Bearbeiten Sie die Datei. Zum Beispiel:

    ```EditorConfig
    # This file is the top-most EditorConfig file
    root = true

    # All Files
    [*]
    indent_style = space
    indent_size = 8
    insert_final_newline = false
    trim_trailing_whitespace = false

    [*.cs]
    csharp_new_line_before_open_brace = none
    ```

4. Das Hinzufügen der Datei aktualisiert Ihre Einstellungen nicht automatisch. Wählen Sie den Projektknoten aus, und klicken Sie in der Menüleiste auf **Bearbeiten > Formatieren > Dokument formatieren**, um die Einstellungen der `.editorconfig`-Datei anzuzeigen:

    ![Menüelement „Dokument formatieren“](media/editorconfig-image2.png)

### <a name="adding-an-existing-editorconfig-file"></a>Hinzufügen einer vorhandenen EditorConfig-Datei

Wenn Sie mit einem Projekt oder einer Projektmappe arbeiten, die bereits eine `.editorconfig`-Datei enthält, müssen Sie nichts tun, um diese Einstellungen anzuwenden. Neue Codezeilen werden gemäß den EditorConfig-Einstellungen formatiert. Beachten Sie, dass Visual Studio für Mac `.editorconfig`-Dateien auf Projektmappenebene berücksichtigt. Sie werden möglicherweise nicht im Lösungspad angezeigt, da mit `.` beginnende Dateien in MacOS ausgeblendete Dateien sind.

Sie sollten eine vorhandene `.editorconfig`-Datei in Ihrem Projekt wiederverwenden. Zum Hinzufügen einer vorhandenen Datei müssen Sie zuerst die ausgeblendeten Dateien im Finder anzeigen, indem Sie den folgenden Befehl im **Terminal** eingeben:

```bash
$ defaults write com.apple.Finder AppleShowAllFiles true
$ killall Finder
```

Ziehen Sie die `.editorconfig`-Datei in Ihren Projektknoten, sobald sie sichtbar ist. Wenn das folgende Dialogfeld angezeigt wird, wählen Sie die Option **Datei in das Verzeichnis kopieren** aus, und klicken Sie auf **OK**:

![Menüelement „Dokument formatieren“](media/editorconfig-image3.png)

Wählen Sie den Projektknoten aus, und klicken Sie in der Menüleiste auf **Bearbeiten > Formatieren > Dokument formatieren**, um die Einstellungen der `.editorconfig`-Datei anzuzeigen:

## <a name="editing-an-editorconfig-file"></a>Bearbeiten von EditorConfig-Dateien

EditorConfig-Dateien verwenden ein einfaches Dateilayout zum Angeben von Einstellungen, was im Folgenden unter Verwendung eines vorherigen Beispiels erläutert wird:


```EditorConfig
# This file is the top-most EditorConfig file
root = true

# All Files
[*]
indent_style = space
indent_size = 4
insert_final_newline = false
trim_trailing_whitespace = false

[*.cs]
csharp_new_line_before_open_brace = none
```

Das Festlegen von `root` auf `true` markiert diese Datei als die oberste Datei der Codebase, und alle höheren `.editorconfig`-Dateien im Projekt werden ignoriert, wie im Abschnitt [Überschreiben der EditorConfig-Einstellungen](#override-editorconfig-settings) erläutert wird.

Jeder Abschnitt wird durch ein Quadrat (**[ ]**) gekennzeichnet und gibt Informationen zu den Arten von Dateien an, auf die die folgenden Eigenschaften sich beziehen.

Im obigen Beispiel werden einige Einstellungen auf alle Dateien im Projekt angewendet. Andere werden nur C#-Dateien hinzugefügt. Die folgenden Screenshots zeigen den Code vor und nach der Anwendung der `.editorconfig`-Einstellung:

**Vorher**:

![Bevor die EditorConfig-Einstellungen angewendet wurden](media/editorconfig-image4.png)

**Nachher**:

![Nachdem die EditorConfig-Einstellungen angewendet wurden](media/editorconfig-image5.png)

Weitere Informationen über die verfügbaren EditorConfig-Einstellungen finden Sie im Artikel [Einstellungen für die .NET-Codierungskonventionen für „EditorConfig“](https://docs.microsoft.com/visualstudio/ide/editorconfig-code-style-settings-reference) und im Abschnitt [Supported Properties (Unterstützte Eigenschaften)](http://editorconfig.org/#supported-properties) der offiziellen Dokumentation.

## <a name="override-editorconfig-settings"></a>Überschreiben von EditorConfig-Einstellungen

Es ist möglich, dass mehr als eine `.editorconfig`-Datei in einer Projektmappe enthalten ist. Visual Studio für Mac liest `.editorconfig`-Dateien in der Projektmappe von oben nach unten und fügt dabei Einstellungen hinzu oder überschreibt sie. Das bedeutet, dass die Einstellungen der `.editorconfig`-Datei Vorrang haben, die der Datei _am nächsten liegen_, die Sie bearbeiten. 

Wenn Sie sicherstellen möchten, dass _keine_ Einstellungen von übergeordneten `.editorconfig`-Dateien auf diesen Teil der Codebase angewendet werden, fügen Sie die `root=true`-Eigenschaft oben in der untergeordneten `.editorconfig`-Datei ein:

```EditorConfig
# top-most EditorConfig file
root = true
```
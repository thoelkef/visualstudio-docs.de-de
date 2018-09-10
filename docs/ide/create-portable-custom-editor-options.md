---
title: Verwenden von EditorConfig-Einstellungen in Visual Studio
ms.date: 08/01/2018
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.openlocfilehash: 8e2118564cb6e0a3eb4811cb69283256cd48a489
ms.sourcegitcommit: 4c60bcfa2281bcc1a28def6a8e02433d2c905be6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/14/2018
ms.locfileid: "42626704"
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Erstellen von portablen, benutzerdefinierten Editor-Einstellungen mit „EditorConfig“

In Visual Studio 2017 können Sie Ihrem Projekt oder der Codebasis eine [EditorConfig](http://editorconfig.org/)-Datei hinzufügen, um einheitliche Codierungsstile für alle Benutzer durchzusetzen, die an der Codebasis arbeiten. EditorConfig Einstellungen haben Vorrang vor den globalen Einstellungen des Visual Studio-Text-Editors. Das bedeutet, dass Sie jede Codebasis für die Verwendung von Text-Editor-Einstellungen anpassen können, die für dieses Projekt spezifisch sind. Ihre persönlichen Einstellungen können Sie im Visual Studio-Dialogfeld **Optionen** festlegen. Diese Einstellungen gelten immer dann, wenn Sie ohne eine *EDITORCONFIG*-Datei an einer Codebasis arbeiten oder wenn die *EDITORCONFIG*-Datei eine bestimmte Einstellung nicht außer Kraft setzt. Ein Beispiel ist das Format von Einzügen, also Tabulatoren oder Leerzeichen.

EditorConfig-Einstellungen werden von zahlreichen Code-Editoren und IDEs einschließlich Visual Studio unterstützt. Außerdem ist es eine portable Komponente, die mit dem Code geliefert wird und Codierungsstile auch außerhalb von Visual Studio erzwingen kann.

> [!NOTE]
> Wenn Sie Ihrem Projekt in Visual Studio eine EditorConfig-Datei hinzufügen, wird die Formatierung von vorhandenem Code nicht geändert, es sei denn, Sie formatieren das Dokument (**Bearbeiten** > **Erweitert** > **Dokument formatieren** oder **STRG**+**K**, **STRG**+**D** im Standardprofil). Neue Codezeilen werden jedoch gemäß den Einstellungen aus EditorConfig formatiert. Sie können festlegen, welche EditorConfig-Einstellungen von **Dokument formatieren** auf die [**Seite Formatierungsoptionen**](reference/options-text-editor-csharp-formatting.md#format-document-settings) angewendet werden sollen.

## <a name="coding-consistency"></a>Programmierkonsistenz

Durch die Einstellungen in EDITORCONFIG-Dateien können Sie einen einheitlichen Programmierstil und einheitliche Programmiereinstellungen in einer Codebasis erzielen. Dies betrifft beispielsweise die Einzugsgröße, die Tabulatorbreite, Zeilenendzeichen, die Codierung usw. und ist unabhängig vom verwendeten Editor oder der verwendeten IDE. Wenn Sie beispielsweise in C# programmieren und für Ihre Codebasis eine Konvention gilt, dass Einzüge immer aus fünf Leerzeichen bestehen, für Dokumente UTF-8-Codierung verwendet wird und jede Zeile mit CR/LF endet, können Sie eine *EDITORCONFIG*-Datei entsprechend konfigurieren.

Programmierkonventionen, die Sie für Ihre eigenen Projekte verwenden, unterscheiden sich möglicherweise von denen, die für Ihre Teamprojekte verwendet werden. Z.B. kann es sein, dass Sie es vorziehen, dass beim Programmieren bei einem Einzug ein Tabstoppzeichen hinzugefügt wird. Ihrem Team ist es aber möglicherweise lieber, dass bei einem Einzug vier Leerzeichen anstelle eines Tabstoppzeichens hinzugefügt werden. EditorConfig-Dateien lösen dieses Problem, indem sie Ihnen ermöglichen, für jedes Szenario eine Konfiguration zu verwenden.

Da sich die Einstellungen in einer Datei innerhalb der Codebasis befinden, bilden sie eine Transporteinheit mit der Codebasis. Sofern Sie die Codedatei in einem mit EditorConfig kompatiblen Editor öffnen, werden die Text-Editor-Einstellungen implementiert. Weitere Informationen zu EditorConfig-Dateien finden Sie auf der Website von [EditorConfig.org](http://editorconfig.org/).

## <a name="supported-settings"></a>Unterstützte Einstellungen

Der Editor in Visual Studio unterstützt die gebräuchlichsten [EditorConfig-Eigenschaften](http://editorconfig.org/#supported-properties):

- indent_style
- indent_size
- tab_width
- end\_of_line
- charset
- trim\_trailing_whitespace
- insert\_final_newline
- Stamm

Die Einstellungen des EDITORCONFIG-Editors werden in allen von Visual Studio unterstützten Sprachen mit Ausnahme von XML unterstützt. Zusätzlich unterstützt EditorConfig Konventionen für [Programmierstile](../ide/editorconfig-code-style-settings-reference.md) und [Namenskonventionen](../ide/editorconfig-naming-conventions.md) für C# und Visual Basic.

## <a name="adding-and-removing-editorconfig-files"></a>Hinzufügen und Entfernen von EDITORCONFIG-Dateien

Durch das Hinzufügen einer EDITORCONFIG-Datei zu Ihrem Projekt oder Ihrer Codebasis werden vorhandene Formate nicht in die neuen umgewandelt. Wenn in Ihrer Datei beispielsweise Einzüge vorhanden sind, die mit Tabstopps formatiert sind, und Sie eine EDITORCONFIG-Datei hinzufügen, bei der die Einzüge mit Leerräumen formatiert sind, werden die Einzugszeichen nicht automatisch in Leerräume konvertiert. Neue Codezeilen werden jedoch gemäß den Einstellungen aus der EDITORCONFIG-Datei formatiert. Darüber hinaus werden beim Formatieren des Dokuments (**Bearbeiten** > **Erweitert** > **Dokument formatieren** oder **Strg**+**K**, **Strg**+**D**) die Einstellungen in der EDITORCONFIG-Datei auf vorhandene Codezeilen angewendet.

Wenn Sie eine EDITORCONFIG-Datei aus Ihrem Projekt oder Ihrer Codebasis entfernen, müssen Sie alle geöffneten Codedateien schließen und erneut öffnen, um die globalen Editor-Einstellungen für neue Codezeilen wiederherzustellen.

### <a name="to-add-an-editorconfig-file-to-a-project-or-solution"></a>Hinzufügen einer EditorConfig-Datei zu einem Projekt oder einer Projektmappe

1. Öffnen Sie ein Projekt oder eine Projektmappe in Visual Studio. Wählen Sie den Knoten „Projekt“ oder „Projektmappe“ aus, je nachdem, ob Ihre Einstellungen für die *EDITORCONFIG*-Datei für alle Projekte in der Projektmappe oder nur für ein Projekt gelten sollen. Sie können ebenfalls einen Ordner in Ihrem Projekt oder in Ihrer Projektmappe auswählen, zu dem die *EDITORCONFIG*-Datei hinzugefügt werden soll.

1. Klicken Sie in der Menüleiste auf **Projekt** > **Neues Element hinzufügen**, oder drücken Sie **STRG**+**UMSCHALTTASTE**+**A**.

   Das Dialogfeld **Neues Element hinzufügen** wird angezeigt.

1. Klicken Sie in den Kategorien auf der linken Seite auf **Allgemein**, und wählen Sie die Vorlage **Textdatei** aus. Geben Sie `.editorconfig` im Textfeld **Name** ein, und klicken Sie dann auf **Hinzufügen**.

   Anschließend wird eine *EDITORCONFIG*-Datei in Projektmappen-Explorer angezeigt und im Editor geöffnet.

   ![EDITORCONFIG-Datei in Projektmappen-Explorer](media/editorconfig-in-solution-explorer.png)

1. Bearbeiten Sie die Datei wie gewünscht, zum Beispiel folgendermaßen:

   ```EditorConfig
   root = true

   [*.{cs,vb}]
   indent_size = 4
   trim_trailing_whitespace = true

   [*.cs]
   csharp_new_line_before_open_brace = methods
   ```

### <a name="other-ways-to-add-an-editorconfig-file"></a>Weitere Möglichkeiten zum Hinzufügen einer EditorConfig-Datei

Es gibt mehrere Möglichkeiten, wie Sie Ihrem Projekt eine EditorConfig-Datei hinzufügen können:

- Installieren Sie die [EditorConfig-Sprachdiensterweiterung](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig), die das Hinzufügen einer leeren *.editorconfig*-Datei zu Projekten vereinfacht. Klicken Sie nach der Installation dieser Erweiterung im Knoten „Projektmappe“, „Projekt“ oder in einem beliebigen Ordner im **Projektmappen-Explorer** im Kontextmenü oder in dem Menü, das sich durch Rechtsklick öffnet, auf **Hinzufügen** > **.editorconfig-Datei**. Diese Erweiterung verbessert auch die Bearbeitungsfunktionen für die *.editorconfig* Datei.

   ![Hinzufügen der EDITORCONFIG-Datei mit Erweiterung](media/editorconfig-extension-add.png)

- Testen Sie die [IntelliCode-Erweiterung](/visualstudio/intellicode/intellicode-visual-studio). Diese experimentelle Erweiterung leitet Ihre Codeformate aus vorhandenem Code ab und erstellt dann eine nicht leere *.editorconfig*-Datei, in der Ihre Einstellungen für das Codeformat bereits definiert sind.

## <a name="override-editorconfig-settings"></a>Außer Kraft setzen von EditorConfig-Einstellungen

Wenn Sie einem Ordner in Ihrer Dateihierarchie eine *EDITORCONFIG*-Datei hinzufügen, gelten deren Einstellungen für alle geeigneten Dateien auf der betreffenden Ebene und den Ebenen darunter. Sie können die EditorConfig-Einstellungen ebenfalls für ein bestimmtes Projekt, eine bestimmte Codebasis oder für einen Teil einer Codebasis außer Kraft setzen, sodass dieser andere Konventionen als die anderen Teile der Codebasis verwendet. Dies kann nützlich sein, wenn Sie Code von einer anderen Stelle integrieren und dessen Konventionen nicht ändern möchten.

Fügen Sie zur Außerkraftsetzung einiger oder aller EditorConfig-Einstellungen eine *EDITORCONFIG*-Datei zu der Ebene der Dateihierarchie hinzu, für die die Einstellungen außer Kraft gesetzt werden sollen. Die neuen EDITORCONFIG-Dateieinstellungen gelten für alle Dateien auf der gleichen Ebene sowie für alle Dateien in Unterverzeichnissen.

![EditorConfig-Hierarchie](../ide/media/vside_editorconfig_hierarchy.png)

Wenn einige, aber nicht alle Einstellungen außer Kraft gesetzt werden sollen, geben Sie nur diese Einstellungen in der *EDITORCONFIG*-Datei an. Nur die Eigenschaften, die Sie explizit in der Datei auf der niedrigsten Ebene auflisten, werden außer Kraft gesetzt. Andere Einstellungen aus *EDITORCONFIG*-Dateien auf höheren Ebenen werden weiterhin angewendet. Wenn Sie sicherstellen möchten, dass die _Nein_-Einstellungen von _beliebigen_ *EDITORCONFIG*-Dateien auf höheren Ebenen auf diesen Teil der Codebasis angewendet werden, fügen Sie die ```root=true```-Eigenschaft zu der *EDITORCONFIG*-Datei auf niedrigerer Ebene hinzu:

```EditorConfig
# top-most EditorConfig file
root = true
```

EDITORCONFIG-Dateien werden von unten nach oben gelesen, und die nächstgelegenen EDITORCONFIG-Dateien werden als letztes gelesen. Konventionen aus übereinstimmenden EDITORCONFIG-Abschnitten werden in der Reihenfolge angewendet, in der sie gelesen werden, damit näher gelegenen Dateien der Vorrang gegeben wird.

## <a name="editing-editorconfig-files"></a>Bearbeiten von EDITORCONFIG-Dateien

Mit Visual Studio können Sie *EDITORCONFIG*-Dateien bearbeiten, indem Sie IntelliSense-Vervollständigungslisten bereitstellen.

![IntelliSense in einer EDITORCONFIG-Datei](media/editorconfig-intellisense-no-extension.png)

Nachdem Sie Ihre EDITORCONFIG-Datei bearbeitet haben, müssen Sie Ihre Codedateien erneut laden, damit die neuen Einstellungen wirksam werden.

Wenn Sie mehrere *EDITORCONFIG*-Dateien bearbeiten, kann die Erweiterung [EditorConfig Language Service](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig) nützlich sein. Zu den Features dieser Erweiterung zählen die Syntaxhervorhebung sowie eine Verbesserung der Überprüfung, Codeformatierung und von IntelliSense.

![IntelliSense in der Erweiterung „EditorConfig Language Service“](media/editorconfig-intellisense.png)

## <a name="example"></a>Beispiel

Im folgenden Beispiel werden die Einzüge eines C#-Codeausschnitts vor und nach dem Hinzufügen einer *EDITORCONFIG*-Datei zum Projekt gezeigt. Die Einstellung **Tabstopps** im Dialogfeld **Optionen** für den Visual Studio-Text-Editor ist auf das Einfügen von Leerräumen festgelegt, wenn Sie die **TAB**-TASTE drücken.

![Text-Editor-Tabstoppeinstellung](../ide/media/vside_editorconfig_tabsetting.png)

Wie erwartet erfolgt der Einzug beim Drücken der **TAB-TASTE** in der nächsten Zeile durch Hinzufügen von vier zusätzlichen Leerzeichen.

![Code vor der Verwendung von EditorConfig](../ide/media/vside_editorconfig_before.png)

Fügen Sie dem Projekt eine neue Datei mit dem Namen *EDITORCONFIG* mit folgenden Inhalten hinzu. Die Einstellung `[*.cs]` bewirkt, dass sich diese Änderung nur auf C#-Codedateien in diesem Projekt auswirkt.

```EditorConfig
# Top-most EditorConfig file
root = true

# Tab indentation
[*.cs]
indent_style = tab
```

Wenn Sie jetzt die **TAB-TASTE** drücken, werden Tabstoppzeichen anstelle von Leerzeichen eingefügt.

![Die TAB-TASTE fügt Tabstoppzeichen hinzu](../ide/media/vside_editorconfig_tab.png)

## <a name="troubleshooting-editorconfig-settings"></a>Behandeln von Problemen mit den EditorConfig-Einstellungen

Wenn irgendwo in der Verzeichnisstruktur entweder am Speicherort Ihres Projekts oder darüber eine EditorConfig-Datei vorhanden ist, wendet Visual Studio die Editoreinstellungen in dieser Datei auf Ihren Editor an. In diesem Fall wird Ihnen die folgende Meldung in der Statusleiste angezeigt:

   **User preferences for this file type are overridden by this project's coding conventions** („Benutzereinstellungen für diesen Dateityp werden durch die Codekonventionen dieses Projekts außer Kraft gesetzt“).

Das bedeutet, dass die Konventionen der EDITORCONFIG-Dateien die Einstellungen in **Optionen** überschreiben, wenn Editor-Einstellungen (z.B. Einzugsgröße und Stil, Tabstoppgröße oder Codierungskonventionen) in **Extras** > **Optionen** > **Text-Editor** in einer EDITORCONFIG-Datei auf Projektebene oder höher in der Verzeichnisstruktur festgelegt sind. Dieses Verhalten können Sie steuern, indem Sie die Option **Codierungskonventionen des Projekts befolgen** unter **Extras** > **Optionen** > **Text-Editor** verändern. Wenn Sie diese Option deaktivieren, wird auch die EditorConfig-Unterstützung für Visual Studio deaktiviert.

![Tooloptionen: Codierungskonventionen des Projekts befolgen](media/coding_conventions_option.png)

Sie können *EDITORCONFIG*-Dateien in übergeordneten Verzeichnissen finden, indem Sie eine Eingabeaufforderung öffnen und den folgenden Befehl vom Stamm des Datenträgers ausführen, der Ihr Projekt enthält:

```Shell
dir .editorconfig /s
```

Sie können den Bereich Ihrer EDITORCONFIG-Konventionen steuern, indem Sie die ```root=true```-Eigenschaft in *EDITORCONFIG*-Dateien am Stamm Ihres Repositorys oder an dem Verzeichnis, in dem sich Ihr Projekt befindet, festlegen. Visual Studio sucht in dem Verzeichnis der geöffneten Datei oder in allen übergeordneten Verzeichnissen nach einer Datei mit der Dateiendung *EDITORCONFIG*. Die Suche wird beendet, wenn es den Stammdateipfad erreicht oder wenn eine *EDITORCONFIG*-Datei mit ```root=true``` gefunden wird.

## <a name="see-also"></a>Siehe auch

- [.NET-Codeformatkonventionen](../ide/editorconfig-code-style-settings-reference.md)
- [.NET-Benennungskonventionen](../ide/editorconfig-naming-conventions.md)
- [Supporting EditorConfig for a language service (Unterstützen von EditorConfig für einen Sprachdienst)](../extensibility/supporting-editorconfig.md)
- [EditorConfig.org](http://editorconfig.org/)
- [Features des Code-Editors](writing-code-in-the-code-and-text-editor.md)
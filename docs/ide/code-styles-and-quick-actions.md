---
title: Codeformateinstellungen
ms.date: 03/12/2019
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 689bdb62d5a4bc9aea21da67e8e5e844660756d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62975316"
---
# <a name="code-style-preferences"></a>Codeformateinstellungen

Codeformateinstellungen können für Ihre C#- und Visual Basic-Projekte festgelegt werden, indem Sie das Dialogfeld **Optionen** im Menü **Extras** öffnen. Klicken Sie im Dialogfeld **Optionen** auf **Text-Editor** > [**C#** oder **Basic**] > **Codeformat** > **Allgemein**.

Jedes Element auf der Liste zeigt eine Vorschau der Einstellung an, wenn es ausgewählt wird:

::: moniker range="vs-2017"

![Codeformatoptionen](media/code-style-quick-actions-dialog.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Codeformatoptionen](media/vs-2019/code-style-quick-actions-dialog.png)

::: moniker-end

In diesem Fenster festgelegte Optionen gelten für Ihr Visual Studio-Personalisierungskonto und sind keinem bestimmten Projekt bzw. keiner bestimmten Codebasis zugeordnet. Darüber hinaus werden sie nicht zur Buildzeit erzwungen. Das gilt auch für CI-Builds (Continuous Integration). Wenn Sie Codeformateinstellungen mit Ihrem Projekt verknüpfen möchten und die Formate während des Buildvorgangs erzwungen werden, geben Sie die Einstellungen in einer Datei vom Typ [.editorconfig](#editorconfig-files) an.

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Editorverhalten in Visual Studio für Mac](/visualstudio/mac/editor-behavior).

## <a name="editorconfig-files"></a>EDITORCONFIG-Dateien

Sie können Codeformateinstellungen für .NET auch angeben, indem Sie Ihrem Projekt eine [EditorConfig](../ide/editorconfig-code-style-settings-reference.md)-Datei hinzufügen.

::: moniker range=">=vs-2019"

Klicken Sie auf **Generate .editorconfig file from setting** (.editorconfig-Datei aus Einstellungen generieren), um automatisch eine .editorconfig-Codeformatdatei auf Grundlage der Optionen zu erstellen, die Sie auf dieser **Optionenseite** festgelegt haben.

![Screenshot: Generieren einer .editorconfig-Datei aus den Einstellungen in VS 2019](media/vs-2019/generate-editorconfig-file-small.png)

::: moniker-end

Diese .editorconfig-Dateien sind nicht mit einem Visual Studio-Personalisierungskonto, sondern mit einer Codebasis verknüpft. Die Einstellungen in der .editorconfig-Datei haben Vorrang gegenüber den im Dialogfeld **Optionen** ausgewählten Optionen. Verwenden Sie eine EditorConfig-Datei, wenn Sie Codierungsstile für alle Mitwirkenden an Ihrem Repository oder Projekt erzwingen möchten.

## <a name="preference-and-severity"></a>Einstellung und Schweregrad

Sie können für jede dieser Codeformateinstellungen auf dieser Seite über die Dropdownfelder jeder Zeile die Werte für **Preference** (Präferenz)und **Schweregrad** festlegen. Der Schweregrad kann auf **Kein**, **Vorschlag**, **Warnung** oder **Fehler** festgelegt werden. Wenn Sie für ein Codeformat [Schnellaktionen](../ide/quick-actions.md) aktivieren möchten, stellen Sie sicher, dass die Einstellung für den **Schweregrad** auf einen anderen Wert als **Kein** festgelegt ist. Das Glühbirnensymbol für **Schnellaktionen** ![Glühbirnensymbol](media/light-bulb-dropdown.png), das Fehlerglühbirnensymbol ![Fehlerglühbirnensymbol](media/error-bulb.png) oder das Schraubendrehersymbol ![Schraubendrehersymbol](media/screwdriver.png) wird angezeigt, wenn ein nicht bevorzugtes Format verwendet wird, und Sie können eine Option aus der Liste der **Schnellaktionen** auswählen, um den Code automatisch im bevorzugten Format neu zu schreiben.

## <a name="format-document-command"></a>Befehl „Dokument formatieren“

Sie können den Befehl **Dokument formatieren** konfigurieren (**Bearbeiten** > **Erweitert** > **Dokument formatieren**), um in einer Datei zusätzliche Codebereinigung anzuwenden, wie z.B. das Entfernen und Sortieren von Using-Direktiven oder das Anwenden von Codeformateinstellungen. Sie können festlegen, welche Einstellungen von **Dokument formatieren** auf die Seite [Formatierungsoptionen](reference/options-text-editor-csharp-formatting.md#format-document-settings) angewendet werden sollen.

Bei der Codebereinigung werden die in einer *.editorconfig*-Datei konfigurierten Einstellungen beachtet. Wenn die Regel oder die Datei fehlen, werden die Einstellungen respektiert, die in **Tools** > **Optionen** > **Text-Editor** > **C#** > [**Codeformat** oder **Formatierung**] festgelegt sind.

Beim ersten Auslösen des Befehls **Dokument formatieren** in Visual Studio werden Sie über eine gelbe Infoleiste aufgefordert, Ihre Codebereinigungseinstellungen zu konfigurieren.

> [!TIP]
> Regeln, die mit dem Schweregrad **Kein** konfiguriert sind, nehmen nicht an der Codebereinigung teil, können aber einzeln über das Menü **Schnellaktionen und Refactorings** angewendet werden.

## <a name="see-also"></a>Siehe auch

- [Schnelle Aktionen](../ide/quick-actions.md)
- [Einstellungen für die .NET-Codierungskonventionen für EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
- [Editorverhalten (Visual Studio für Mac)](/visualstudio/mac/editor-behavior)
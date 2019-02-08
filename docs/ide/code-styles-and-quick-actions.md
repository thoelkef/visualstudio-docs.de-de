---
title: Codeformateinstellungen
ms.date: 03/10/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: f33c1edec4b4093e9157a59618befa2e1175be49
ms.sourcegitcommit: e3d96b20381916bf4772f9db52b22275763bb603
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/31/2019
ms.locfileid: "55483990"
---
# <a name="code-style-preferences"></a>Codeformateinstellungen

Codeformateinstellungen können für Ihre C#- und Visual Basic-Projekte festgelegt werden, indem Sie das Dialogfeld **Optionen** im Menü **Extras** öffnen. Klicken Sie im Dialogfeld **Optionen** auf **Text-Editor** > [**C#** oder **Basic**] > **Codeformat** > **Allgemein**. Die Optionen, die in diesem Fenster vorgenommen werden, werden nur auf den lokalen Computer angewendet.

Jedes Element auf der Liste zeigt eine Vorschau der Einstellung an, wenn es ausgewählt wird:

![Codeformatoptionen](media/code-style-quick-actions-dialog.png)

> [!NOTE]
> Dieses Thema gilt für Visual Studio unter Windows. Informationen zu Visual Studio für Mac finden Sie unter [Editorverhalten in Visual Studio für Mac](/visualstudio/mac/editor-behavior).

## <a name="preference-and-severity"></a>Einstellung und Schweregrad

Sie können für jedes Element über die Dropdownfelder jeder Zeile die Werte für **Präferenz** und **Sicherheit** festlegen. Der Schweregrad kann auf **Kein**, **Vorschlag**, **Warnung** oder **Fehler** festgelegt werden. Wenn Sie für ein Codeformat [Schnellaktionen](../ide/quick-actions.md) aktivieren möchten, stellen Sie sicher, dass die Einstellung für den **Schweregrad** auf einen anderen Wert als **Kein** festgelegt ist. Das Glühbirnensymbol für **Schnellaktionen** ![Glühbirnensymbol](media/vs2015_lightbulbsmall.png), das Fehlerglühbirnensymbol ![Fehlerglühbirnensymbol](media/error-bulb.png) oder das Schraubendrehersymbol ![Schraubendrehersymbol](media/screwdriver.png) wird angezeigt, wenn ein nicht bevorzugtes Format verwendet wird, und Sie können eine Option aus der Liste der **Schnellaktionen** auswählen, um den Code automatisch im bevorzugten Format neu zu schreiben.

## <a name="editorconfig-files"></a>EDITORCONFIG-Dateien

Codeformateinstellungen für .NET können auch mithilfe einer [EditorConfig](../ide/editorconfig-code-style-settings-reference.md)-Datei verwaltet werden. Die Einstellungen in der EDITORCONFIG-Datei haben Vorrang gegenüber den im Dialogfeld **Optionen** ausgewählten Optionen. Sie können eine EDITORCONFIG-Datei verwenden, um ein Codierungsformat für Ihr gesamtes Repository oder Ihr gesamtes Projekt zu erzwingen oder zu konfigurieren.

## <a name="format-document-command"></a>Befehl „Dokument formatieren“

In Visual Studio 2017 Version 15.8 und höher können Sie den Befehl **Dokument formatieren** konfigurieren (**Bearbeiten** > **Erweitert** > **Dokument formatieren**), um in einer Datei zusätzliche Codebereinigung anzuwenden, wie z.B. das Entfernen und Sortieren von Using-Direktiven oder das Anwenden von Codeformateinstellungen. Sie können festlegen, welche Einstellungen von **Dokument formatieren** auf die Seite [Formatierungsoptionen](reference/options-text-editor-csharp-formatting.md#format-document-settings) angewendet werden sollen.

Bei der Codebereinigung werden die in einer *.editorconfig*-Datei konfigurierten Einstellungen beachtet. Wenn die Regel oder die Datei fehlen, werden die Einstellungen respektiert, die in **Tools** > **Optionen** > **Text-Editor** > **C#** > [**Codeformat** oder **Formatierung**] festgelegt sind.

Beim ersten Auslösen des Befehls **Dokument formatieren** in Visual Studio 2017 werden Sie über eine gelbe Infoleiste aufgefordert, Ihre Codebereinigungseinstellungen zu konfigurieren.

> [!TIP]
> Regeln, die in einer *.editorconfig*-Datei als **Kein** konfiguriert sind, nehmen nicht an der Codebereinigung teil, können aber einzeln über das Menü **Schnellaktionen und Refactorings** angewendet werden.

## <a name="see-also"></a>Siehe auch

- [Schnelle Aktionen](../ide/quick-actions.md)
- [Einstellungen für die .NET-Codierungskonventionen für EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
- [Editorverhalten (Visual Studio für Mac)](/visualstudio/mac/editor-behavior)
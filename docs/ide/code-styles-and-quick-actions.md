---
title: "Codeformateinstellungen für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 03/10/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload: multiple
ms.openlocfilehash: 741df95afdd7c7e8b6f0ba2de75c1465cd35cc97
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2018
---
# <a name="code-style-preferences"></a>Codeformateinstellungen

Codeformateinstellungen können für Ihre C#- und Visual Basic-Projekte festgelegt werden, indem Sie das Dialogfeld **Optionen** im Menü **Extras** öffnen. Wählen Sie **Text-Editor** > **C#** oder  **Basic** > **Codeformat** > **Allgemein** aus. Die Optionen, die in diesem Fenster vorgenommen werden, werden auf den lokalen Computer angewendet. Jedes Element auf der Liste zeigt eine Vorschau der Einstellung an, wenn es ausgewählt wird, so wie unten abgebildet.

![Codeformatoptionen](media/code-style-quick-actions-dialog.png)

Sie können für jedes Element über die Dropdownfelder jeder Zeile die Werte für **Präferenz** und **Sicherheit** festlegen. Der Schweregrad kann auf **Kein**, **Vorschlag**, **Warnung** oder **Fehler** festgelegt werden. Wenn Sie für ein Codeformat [Schnellaktionen](../ide/quick-actions.md) aktivieren möchten, stellen Sie sicher, dass die Einstellung für den **Schweregrad** auf einen anderen Wert als **Kein** festgelegt ist. Das Glühbirnensymbol für Schnellaktionen ![Kleines Glühbirnensymbol](media/vs2015_lightbulbsmall.png) wird angezeigt, wenn ein nicht bevorzugtes Format verwendet wird, und Sie können eine Option aus der Liste der Schnellaktionen auswählen, um den Code automatisch im bevorzugten Format neu zu schreiben.

Codeformateinstellungen für .NET können auch mithilfe einer [EditorConfig](../ide/editorconfig-code-style-settings-reference.md)-Datei verwaltet werden. In diesem Fall haben die Einstellungen in der EDITORCONFIG-Datei Vorrang gegenüber den im Dialogfeld **Optionen** ausgewählten Optionen. Sie können eine EDITORCONFIG-Datei verwenden, um ein Codierungsformat für Ihr gesamtes Repository oder Ihr gesamtes Projekt zu erzwingen oder zu konfigurieren.

## <a name="see-also"></a>Siehe auch

[Schnellaktionen](../ide/quick-actions.md)  
[Einstellungen für die .NET-Codierungskonventionen für EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
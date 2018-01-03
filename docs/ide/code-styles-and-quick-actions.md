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
ms.openlocfilehash: 80b7260296f1f57448ae94147a59dbb29160be40
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="code-style-preferences"></a>Codeformateinstellungen

Codeformateinstellungen können für Ihre C#- und Visual Basic-Projekte festgelegt werden, indem Sie das Dialogfeld **Optionen** im Menü **Extras** öffnen. Klicken Sie auf **Text-Editor** > **C#** oder **Basic** > **Codeformat** > **Allgemein**. Die Optionen, die in diesem Fenster vorgenommen werden, werden auf den lokalen Computer angewendet. Jedes Element auf der Liste zeigt eine Vorschau der Einstellung an, wenn es ausgewählt wird, so wie unten abgebildet.

![Codeformatoptionen](media/code-style-quick-actions-dialog.png)

Sie können für jedes Element **Preference** (Präferenz) und **Security** (Sicherheit) über die Dropdownfelder jeder Zeile festlegen. Der Schweregrad kann auf **None** (Keiner), **Suggestion** (Vorschlag), **Warning** (Warnung) oder **Fehler** festgelegt werden, und das Verhalten von Visual Studio wird dementsprechend angepasst. Wenn Sie [schnelle Aktionen](quick-actions.md) für diese Codeformate verwenden möchten, um automatisch Code in ein bevorzugtes Format umzuschreiben, stellen Sie sicher, dass die Einstellung nicht auf **None** (Keiner) eingestellt ist, damit das Glühbirnensymbol ![Small Light Bulb Icon](media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall") erscheint, wenn ein nicht bevorzugten Format verwendet wird. Sie können diese Einstellungen anwenden, indem auf das Glühbirnensymbol klicken oder **STRG+.** drücken, wenn sich Ihr Cursor in der entsprechenden Codezeile befindet.

Codeformateinstellungen für .NET können auch mithilfe einer [EditorConfig](../ide/editorconfig-code-style-settings-reference.md)-Datei verwaltet werden. In diesem Fall haben die Einstellungen in der EDITORCONFIG-Datei Vorrang gegenüber den im Dialogfeld **Optionen** ausgewählten Optionen. Sie können eine EDITORCONFIG-Datei verwenden, um ein Codierungsformat für Ihr gesamtes Repository oder Ihr gesamtes Projekt zu erzwingen oder zu konfigurieren.

## <a name="see-also"></a>Siehe auch

[Schnelle Aktionen](quick-actions.md)  
[Einstellungen für die .NET-Codierungskonventionen für EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
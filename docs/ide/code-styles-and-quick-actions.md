---
title: Codeformate und schnelle Aktionen | Microsoft-Dokumentation
ms.custom: 
ms.date: 03/10/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: 25bb9d99-aeff-4053-925d-2177f5e79574
author: BrianPeek
ms.author: brpeek
manager: ghogen
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 46846db26bee30841e6cb35913d533b512d01ba0
ms.openlocfilehash: acc01617fffd7465cee01267482112aac5e352fc
ms.lasthandoff: 03/27/2017

---

# <a name="code-styles-and-quick-actions"></a>Codeformate und schnelle Aktionen
Für Ihre C#- und Visual Basic-Projekte können Sie Codeformateinstellungen vornehmen, indem Sie das Fenster **Tools > Options** (Tools > Optionen) öffnen und anschließend **Text Editor > C# / Basic > Code Style > General** (Text-Editor > C#/Basic > Codeformat > Allgemein) auswählen.  Die Optionen, die in diesem Fenster vorgenommen werden, werden auf den lokalen Computer angewendet.  Jedes Element auf der Liste zeigt eine Vorschau der Einstellung an, wenn es ausgewählt wird, so wie unten abgebildet.

![Codeformatoptionen](~/ide/media/code-style-quick-actions-dialog.png)

Sie können für jedes Element **Preference** (Präferenz) und **Security** (Sicherheit) über die Dropdownfelder jeder Zeile festlegen.  Der Schweregrad kann auf **None** (Keiner), **Suggestion** (Vorschlag), **Warning** (Warnung) oder **Fehler** festgelegt werden, und das Verhalten von Visual Studio wird dementsprechend angepasst.  Wenn Sie [schnelle Aktionen](quick-actions.md) für diese Codeformate verwenden möchten, um automatisch Code in ein bevorzugtes Format umzuschreiben, stellen Sie sicher, dass die Einstellung nicht auf **None** (Keiner) eingestellt ist, damit das Glühbirnensymbol ![Small Light Bulb Icon](~/ide/media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall") erscheint, wenn ein nicht bevorzugten Format verwendet wird.  Sie können diese Einstellungen anwenden, indem Sie auf das Glühbirnensymbol klicken oder **STRG + .** drücken , wenn sich Ihr Cursor auf der entsprechenden Codezeile befindet.

Codeformateinstellungen für .NET können auch mithilfe einer [EditorConfig](editorconfig-code-style-settings-reference.md)-Datei verwaltet werden.  In diesem Fall sind die Einstellungen, die Sie im Fenster „Optionen“ vorgenommen haben, die Alternativeinstellungen, mit der „EditorConfig“-Datei an erster Stelle.  Sie können diese Datei verwenden, um ein Codierungsformat für Ihr gesamtes Repository oder Ihr gesamtes Team zu erzwingen oder zu konfigurieren.

# <a name="see-also"></a>Siehe auch
* [Schnelle Aktionen](quick-actions.md)

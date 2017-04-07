---
title: "Erstellen von portablen, benutzerdefinierten Editor-Einstellungen mit „EditorConfig“ | Microsoft-Dokumentation"
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- editor
ms.assetid: 
caps.latest.revision: 29
author: kempb
ms.author: kempb
manager: ghogen
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
ms.openlocfilehash: f377ada139d9c0e8b01b640cf603cf349dc1c3c3
ms.lasthandoff: 03/27/2017

---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Erstellen von portablen, benutzerdefinierten Editor-Einstellungen mit „EditorConfig“
Text-Editor-Einstellungen in Visual Studio gelten für alle Projekte eines bestimmten Typs. Wenn Sie also beispielsweise eine Text-Editor-Einstellung für C# ändern, betrifft diese Einstellung *alle* C#-Projekte in Visual Studio. Es kann jedoch in einigen Fällen erforderlich sein, Konventionen zu verwenden, die von Ihren eigenen persönlichen Editor-Einstellungen abweichen. [EditorConfig](http://editorconfig.org/)-Dateien ermöglichen Ihnen dies, indem sie gemeinsame Text-Editor-Optionen auf Projektbasis bereitstellen. EditorConfig-Einstellungen, die in einer EDITORCONFIG-Datei enthalten sind, die Ihrer Codebasis hinzugefügt wurde, haben Vorrang vor globalen Visual Studio-Text-Editor-Einstellungen. Das bedeutet, dass Sie jede Codebasis für die Verwendung der von Ihnen bevorzugten Text-Editor-Einstellungen anpassen können. Zur Nutzung dieser Funktionalität in Visual Studio sind keine Plug-Ins erforderlich.

## <a name="coding-consistency"></a>Programmierkonsistenz
Mithilfe der Einstellungen in EditorConfig-Dateien können Sie beim Programmieren für eine Sprache konsistente Formate und Einstellungen in einer Codebasis erzielen, etwa hinsichtlich Einzugstil, Tabstoppbreite, Zeilenendezeichen, Codierung und mehr, unabhängig vom verwendeten Editor oder der verwendeten IDE. Wenn Sie beispielsweise in C# programmieren und für Ihre Codebasis eine Konvention gilt, dass Einzüge immer aus fünf Leerzeichen bestehen, für Dokumente UTF-8-Codierung verwendet wird und jede Zeile mit CR/LF endet, können Sie eine EDITORCONFIG-Datei entsprechend konfigurieren.

Programmierkonventionen, die Sie für Ihre eigenen Projekte verwenden, unterscheiden sich möglicherweise von denen, die für Ihre Teamprojekte verwendet werden. So ziehen Sie es möglicherweise vor, dass ein Drücken der TAB-TASTE beim Programmieren das Hinzufügen eines Tabstoppzeichens bewirkt. Ihrem Team ist es aber vielleicht lieber, dass bei einem Einzug vier Leerzeichen anstelle eines Tabstoppzeichens hinzugefügt werden. EditorConfig-Dateien lösen dieses Problem, indem sie Ihnen ermöglichen, für jedes Szenario eine Konfiguration zu verwenden.

Da sich die Einstellungen in einer Datei innerhalb der Codebasis befinden, bilden sie eine Transporteinheit mit der Codebasis. Sofern Sie die Codedatei in einem mit EditorConfig kompatiblen Editor öffnen, werden die Text-Editor-Einstellungen implementiert. Weitere Informationen zu EditorConfig-Dateien finden Sie auf der Website von [EditorConfig.org](http://editorconfig.org/). Wenn Sie viele EDITORCONFIG-Dateien bearbeiten, finden Sie die [EditorConfig-Sprachdienst](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig)-Erweiterung möglicherweise nützlich.

## <a name="override-editorconfig-settings"></a>Außer Kraft setzen von EditorConfig-Einstellungen
Wenn Sie einem Ordner in Ihrer Dateihierarchie eine EDITORCONFIG-Datei hinzufügen, gelten ihre Einstellungen für alle geeigneten Dateien auf der betreffenden Ebene und den Ebenen darunter. Um EditorConfig-Einstellungen für ein bestimmtes Projekt oder eine bestimmte Codebasis außer Kraft zu setzen und andere oder vorrangige Werte zu verwenden, als sie in der EDITORCONFIG-Datei der obersten Ebene festgelegt sind, fügen Sie einfach auf der Ebene, die Sie ändern möchten, eine EDITORCONFIG-Datei hinzu.

![EditorConfig-Hierarchie](../ide/media/vside_editorconfig_hierarchy.png)

Die Einstellungen der neuen EDITORCONFIG-Datei gelten für die Ebene, auf der sie sich befindet und alle Ebenen darunter.

## <a name="supported-settings"></a>Unterstützte Einstellungen
Der Editor in Visual Studio unterstützt die folgenden Werte aus der Kernmenge der EditorConfig-Optionen.
- indent_style
- indent_size
- tab_width
- end_of_line
- charset
- Stamm
- [code style conventions](../ide/editorconfig-code-style-settings-reference.md)

EditorConfig-Einstellungen werden in allen von Visual Studio unterstützten Sprachen mit Ausnahme von XML unterstützt.

## <a name="example"></a>Beispiel
Hier finden Sie ein Beispiel, das den Einzugstatus eines C#-Codeausschnitts vor und nach dem Hinzufügen einer EDITORCONFIG-Datei zum Projekt zeigt. Die Einstellung **Tabstopps** im Dialogfeld **Optionen** für den Visual Studio-Text-Editor ist auf das Einfügen von Leerzeichen festgelegt, wenn Sie in Ihrem Code die TAB-TASTE drücken.

![Text-Editor-Tabstoppeinstellung](../ide/media/vside_editorconfig_tabsetting.png)

Wie erwartet erfolgt der Einzug beim Drücken der TAB-TASTE in der nächsten Zeile durch Hinzufügen von vier zusätzlichen Leerzeichen.

![Code vor der Verwendung von EditorConfig](../ide/media/vside_editorconfig_before.png)

Wir fügen einer neuen Datei mit dem Namen EDITORCONFIG Folgendes und die Datei dann zum Projekt hinzu. (Die Einstellung `[*.cs]` bewirkt, dass sich diese Änderung nur auf CS-Dateien im Projekt auswirkt.)

![Projekt mit hinzugefügter EDITORCONFIG-Datei](../ide/media/vside_editorconfig_addconfig.png)

Wenn Sie jetzt die TAB-TASTE drücken, erhalten Sie Tabstoppzeichen anstelle von Leerzeichen.

![Die TAB-TASTE fügt Tabstoppzeichen hinzu](../ide/media/vside_editorconfig_tab.png)

> [!NOTE]
>  Das Hinzufügen einer EDITORCONFIG-Datei zu Ihrem Projekt oder Ihrer Codebasis bewirkt keine Umwandlung der vorhandenen Formate in die neuen, sondern wirkt sich nur auf neu hinzugefügte Zeilen aus. Wenn Sie eine EDITORCONFIG-Datei aus Ihrem Projekt oder Ihrer Codebasis entfernen, müssen Sie die Codedateien neu laden, damit die Editor-Einstellungen wieder auf die globalen Einstellungen zurückgesetzt werden. Alle Fehler in EDITORCONFIG-Dateien werden im Fehlerfenster in Visual Studio gemeldet.

## <a name="support-editorconfig-for-your-language-service"></a>Support von EditorConfig für Ihren Sprachdienst

In den meisten Fällen ist bei der Implementierung eines Visual Studio-Sprachdiensts keine zusätzliche Arbeit erforderlich, um universelle EditorConfig-Eigenschaften zu unterstützen. Der Haupteditor ermittelt und liest die .editorconfig-Datei automatisch, wenn Benutzer Dateien öffnen, und er legt den entsprechenden Textpuffer und die Ansichtsoptionen fest. Jedoch verwenden einige Sprachdienste lieber eine entsprechende kontextbezogene Ansichtsoption, statt globale Einstellungen für Elemente, wie z.B. Registerkarten und Leerzeichen, wenn ein Benutzer einen Text bearbeitet oder formatiert. In diesen Fällen muss der Sprachdienst aktualisiert werden, um EditorConfig-Dateien zu unterstützen.

Die folgende Tabelle enthält die erforderlichen Änderungen, um einen Sprachdienst für den Support von EditorConfig-Dateien zu aktualisieren.

| Veraltete globale sprachspezifische Option | Ersetzen der kontextbezogenen Option |
| :------------- | :------------- |
| Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs oder Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs | !textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId) oder !textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId) |
| Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize oder Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize | textBufferOptions.GetOptionValue(DefaultOptions. IndentSizeOptionId) oder textView.Options.GetOptionValue(DefaultOptions. IndentSizeOptionId) |
| Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize oder Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize | textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId) oder textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId) |

# <a name="see-also"></a>Siehe auch
[Erstellen von portablen, benutzerdefinierten Editor-Optionen mit „EditorConfig“](create-portable-custom-editor-options.md)

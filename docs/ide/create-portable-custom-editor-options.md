---
title: "Erstellen von portablen, benutzerdefinierten Editor-Einstellungen mit „EditorConfig“ | Microsoft-Dokumentation"
ms.custom: 
ms.date: 10/27/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editor
ms.assetid: 
caps.latest.revision: "29"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-general
ms.openlocfilehash: 2c1df6f8e34d2b8e72486dd804ba57f0dcf2406b
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/07/2017
---
# <a name="create-portable-custom-editor-settings-with-editorconfig"></a>Erstellen von portablen, benutzerdefinierten Editor-Einstellungen mit „EditorConfig“
Text-Editor-Einstellungen in Visual Studio gelten für alle Projekte eines bestimmten Typs. Wenn Sie also beispielsweise eine Text-Editor-Einstellung für C# ändern, betrifft diese Einstellung *alle* C#-Projekte in Visual Studio. Es kann jedoch in einigen Fällen erforderlich sein, Konventionen zu verwenden, die von Ihren eigenen persönlichen Editor-Einstellungen abweichen. [EditorConfig](http://editorconfig.org/)-Dateien ermöglichen Ihnen dies, indem sie gemeinsame Text-Editor-Optionen auf Projektbasis bereitstellen. EditorConfig-Einstellungen, die in einer EDITORCONFIG-Datei enthalten sind, die Ihrer Codebasis hinzugefügt wurde, haben Vorrang vor globalen Visual Studio-Text-Editor-Einstellungen. Das bedeutet, dass Sie jede Codebasis für die Verwendung der von Ihnen bevorzugten Text-Editor-Einstellungen anpassen können. Zur Nutzung dieser Funktionalität in Visual Studio sind keine Plug-Ins erforderlich.

## <a name="coding-consistency"></a>Programmierkonsistenz
Mithilfe der Einstellungen in EditorConfig-Dateien können Sie beim Programmieren für eine Sprache konsistente Formate und Einstellungen in einer Codebasis erzielen, etwa hinsichtlich Einzugstil, Tabstoppbreite, Zeilenendezeichen, Codierung und mehr, unabhängig vom verwendeten Editor oder der verwendeten IDE. Wenn Sie beispielsweise in C# programmieren und für Ihre Codebasis eine Konvention gilt, dass Einzüge immer aus fünf Leerzeichen bestehen, für Dokumente UTF-8-Codierung verwendet wird und jede Zeile mit CR/LF endet, können Sie eine EDITORCONFIG-Datei entsprechend konfigurieren.

Programmierkonventionen, die Sie für Ihre eigenen Projekte verwenden, unterscheiden sich möglicherweise von denen, die für Ihre Teamprojekte verwendet werden. So ziehen Sie es möglicherweise vor, dass ein Drücken der TAB-TASTE beim Programmieren das Hinzufügen eines Tabstoppzeichens bewirkt. Ihrem Team ist es aber vielleicht lieber, dass bei einem Einzug vier Leerzeichen anstelle eines Tabstoppzeichens hinzugefügt werden. EditorConfig-Dateien lösen dieses Problem, indem sie Ihnen ermöglichen, für jedes Szenario eine Konfiguration zu verwenden.

Da sich die Einstellungen in einer Datei innerhalb der Codebasis befinden, bilden sie eine Transporteinheit mit der Codebasis. Sofern Sie die Codedatei in einem mit EditorConfig kompatiblen Editor öffnen, werden die Text-Editor-Einstellungen implementiert. Weitere Informationen zu EditorConfig-Dateien finden Sie auf der Website von [EditorConfig.org](http://editorconfig.org/).

## <a name="override-editorconfig-settings"></a>Außer Kraft setzen von EditorConfig-Einstellungen
Wenn Sie einem Ordner in Ihrer Dateihierarchie eine EDITORCONFIG-Datei hinzufügen, gelten ihre Einstellungen für alle geeigneten Dateien auf der betreffenden Ebene und den Ebenen darunter. Fügen Sie dem Stamm des Repositorys der Codebasis oder dem Projektverzeichnis eine EDITORCONFIG-Datei hinzu, um EditorConfig-Einstellungen für ein bestimmtes Projekt oder eine bestimmte Codebasis außer Kraft zu setzen. Stellen Sie sicher, dass Sie der Datei eine ```root=true```-Eigenschaft hinzufügen, damit Visual Studio nicht weiter oben in der Verzeichnisstruktur nach EDITORCONFIG-Dateien sucht. Die Einstellungen der neuen EDITORCONFIG-Datei gelten für die Ebene, auf der sie sich befindet sowie für Dateien in Unterverzeichnissen.

```
# top-most EditorConfig file
root = true
```

![EditorConfig-Hierarchie](../ide/media/vside_editorconfig_hierarchy.png)

EDITORCONFIG-Dateien werden von unten nach oben gelesen, und die nächstgelegenen EDITORCONFIG-Dateien werden als letztes gelesen. Konventionen aus übereinstimmenden EDITORCONFIG-Abschnitten werden in der Reihenfolge angewendet, in der sie gelesen werden, damit näher gelegenen Dateien der Vorrang gegeben wird.

## <a name="supported-settings"></a>Unterstützte Einstellungen
Der Editor in Visual Studio unterstützt die folgenden Werte aus den gebräuchlichsten [EditorConfig-Eigenschaften](http://editorconfig.org/#supported-properties):  

- indent_style
- indent_size
- tab_width
- end_of_line
- charset
- Stamm

Außerdem unterstützt er die [.NET-Codierungsstilkonventionen](../ide/editorconfig-code-style-settings-reference.md).  

EditorConfig-Einstellungen werden in allen von Visual Studio unterstützten Sprachen mit Ausnahme von XML unterstützt.

## <a name="intellisense"></a>IntelliSense
Visual Studio stellt eingeschränkten Zugriff auf IntelliSense zur Bearbeitung von EDITORCONFIG-Dateien zur Verfügung. Wenn Sie viele EDITORCONFIG-Dateien bearbeiten, finden Sie die [EditorConfig-Sprachdienst](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.EditorConfig)-Erweiterung möglicherweise nützlich.

## <a name="example"></a>Beispiel
Hier finden Sie ein Beispiel, das den Einzugstatus eines C#-Codeausschnitts vor und nach dem Hinzufügen einer EDITORCONFIG-Datei zum Projekt zeigt. Die Einstellung **Tabs** im Dialogfeld **Optionen** für den Visual Studio-Text-Editor ist auf das Einfügen von Leerzeichen festgelegt, wenn Sie in Ihrem Code die **TAB-TASTE** drücken.

![Text-Editor-Tabstoppeinstellung](../ide/media/vside_editorconfig_tabsetting.png)

Wie erwartet erfolgt der Einzug beim Drücken der **TAB-TASTE** in der nächsten Zeile durch Hinzufügen von vier zusätzlichen Leerzeichen.

![Code vor der Verwendung von EditorConfig](../ide/media/vside_editorconfig_before.png)

Fügen Sie dem Projekt eine neue Datei mit dem Namen EDITORCONFIG mit folgenden Inhalten hinzu. Die Einstellung `[*.cs]` bewirkt, dass sich diese Änderung nur auf CS-Dateien im Projekt auswirkt.  

![Projekt mit hinzugefügter EDITORCONFIG-Datei](../ide/media/vside_editorconfig_addconfig.png)

Wenn Sie jetzt die **TAB-TASTE** drücken, werden Tabstoppzeichen anstelle von Leerzeichen eingefügt.

![Die TAB-TASTE fügt Tabstoppzeichen hinzu](../ide/media/vside_editorconfig_tab.png)

> [!NOTE]
>  Das Hinzufügen einer EDITORCONFIG-Datei zu Ihrem Projekt oder Ihrer Codebasis bewirkt keine Umwandlung der vorhandenen Formate in die neuen, sondern wirkt sich nur auf neu hinzugefügte Zeilen aus. Wenn Sie eine EDITORCONFIG-Datei aus Ihrem Projekt oder Ihrer Codebasis entfernen, müssen Sie die Codedateien neu laden, damit die Editor-Einstellungen wieder auf die globalen Einstellungen zurückgesetzt werden. Alle Fehler in EDITORCONFIG-Dateien werden im Fenster „Fehlerliste“ in Visual Studio gemeldet.

## <a name="troubleshooting-editorconfig-settings"></a>Behandeln von Problemen mit den EditorConfig-Einstellungen
Wenn irgendwo in der EDITORCONFIG-Datei eine Verzeichnisstruktur am Speicherort Ihres Projekts oder darüber vorhanden ist, wendet Visual Studio die Editoreinstellungen für den Editor in Ihrer Datei an. In diesem Fall wird Ihnen die folgende Meldung in der Statusleiste angezeigt:

**User preferences for this file type are overridden by this project's coding conventions** („Benutzereinstellungen für diesen Dateityp werden durch die Codekonventionen dieses Projekts außer Kraft gesetzt“).

Das bedeutet, dass die Konventionen in der EDITORCONFIG-Datei die Einstellungen unter „Optionen“ außer Kraft setzen, wenn andere Einstellungen unter **Extras** > **Optionen** > **Text-Editor** (wie die Einzugsgröße, Tabulatorgröße, Standardeinzugstabs &mdash; oder Leerzeichen oder Codekonventionen wie die Verwendung von `var`) in einer EDITORCONFIG-Datei bei oder über dem Projekt in der Verzeichnisstruktur angegeben sind. Dieses Verhalten können Sie steuern, indem Sie die Option **Codierungskonventionen des Projekts befolgen** unter **Extras** > **Optionen** > **Text-Editor** verändern. Wenn Sie diese Option deaktivieren, wird auch die EditorConfig-Unterstützung für Visual Studio deaktiviert.

![Tooloptionen: Codierungskonventionen des Projekts befolgen](media/coding_conventions_option.png)

Sie können die EDITORCONFIG-Dateien in übergeordneten Verzeichnissen finden, indem Sie eine Eingabeaufforderung öffnen und den folgenden Befehl vom Stamm des Datenträgers ausführen, der Ihr Projekt enthält:

```
dir .editorconfig /s
```

Sie können den Bereich Ihrer EDITORCONFIG-Konventionen steuern, indem Sie die ```root=true```-Eigenschaft in EDITORCONFIG-Dateien am Stamm Ihres Repositorys oder an dem Verzeichnis, in dem sich Ihr Projekt befindet, festlegen. Visual Studio sucht in dem Verzeichnis der geöffneten Datei oder in allen übergeordneten Verzeichnissen nach einer Datei mit der Dateiendung „.editorconfig“. Visual Studio beendet die Suche, wenn der Stammdateipfad erreicht wird oder die EDITORCONFIG-Datei mit ```root=true``` gefunden wird.

## <a name="support-editorconfig-for-your-language-service"></a>Support von EditorConfig für Ihren Sprachdienst
In den meisten Fällen ist bei der Implementierung eines Visual Studio-Sprachdiensts keine zusätzliche Arbeit erforderlich, um universelle EditorConfig-Eigenschaften zu unterstützen. Der Haupteditor ermittelt und liest die .editorconfig-Datei automatisch, wenn Benutzer Dateien öffnen, und er legt den entsprechenden Textpuffer und die Ansichtsoptionen fest. Jedoch verwenden einige Sprachdienste lieber eine entsprechende kontextbezogene Ansichtsoption, statt globale Einstellungen für Elemente, wie z.B. Registerkarten und Leerzeichen, wenn ein Benutzer einen Text bearbeitet oder formatiert. In diesen Fällen muss der Sprachdienst aktualisiert werden, um EditorConfig-Dateien zu unterstützen.

Die folgenden Änderungen sind erforderlich, um den Sprachdienst zu aktualisieren, damit dieser EDITORCONFIG-Dateien unterstützt. Dafür müssen Sie eine globale _sprachspezifische_ Option durch eine _kontextbezogene_ Option ersetzen:  

### <a name="indent-style"></a>Einzugsgröße
Ersetzen:  

Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs  
 _oder_   
Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs  

Durch:  

!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)  
 _oder_   
!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)  

### <a name="indent-size"></a>Einzugsgröße
Ersetzen:  

Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize  
 _oder_   
Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize  

Durch:  

textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)  
 _oder_   
textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)  

### <a name="tab-size"></a>Tabulatorgröße
Ersetzen:  

Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize  
 _oder_   
Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize  

Durch:  

textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)  
 _oder_   
textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)  

## <a name="see-also"></a>Siehe auch
[.NET-Codeformatkonventionen](../ide/editorconfig-code-style-settings-reference.md)  
[EditorConfig.org](http://editorconfig.org/)  
[Writing code in the editor (Schreiben von Code im Code-Editor)](writing-code-in-the-code-and-text-editor.md)
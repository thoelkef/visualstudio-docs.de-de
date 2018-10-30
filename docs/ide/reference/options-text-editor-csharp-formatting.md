---
title: C# -Editor-Formatierungsoptionen
ms.date: 08/14/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
helpviewer_keywords:
- formatting options [C#]
- Text editor Options dialog box, formatting
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: bcd63e9a155843d715e63fb6514e22f356847d2f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49821382"
---
# <a name="options-text-editor-c-formatting"></a>Optionen, Text-Editor, C#, Formatierung

Auf der Optionsseite **Formatierung** können Sie Optionen zur Formatierung von Code im Code-Editor festlegen. Klicken Sie auf **Extras** > **Optionen**, um die Optionsseite aufzurufen. Klicken Sie im Dialogfeld **Optionen** auf **Text-Editor** > **C#** > **Codeformat** > **Formatierung**.

## <a name="general-page"></a>Seite „Allgemein“

### <a name="general-settings"></a>Allgemeine Einstellungen

Es hängt von den Einstellungen ab, *wann* Formatierungsoptionen für den Code vom Code-Editor übernommen werden.

|Bezeichnung|Beschreibung |
|-----------|-----------------|
|**Automatisch während der Eingabe formatieren**|Wenn diese Bezeichnung deaktiviert ist, sind auch die Optionen **Beim Eingeben von ; Anweisung formatieren** und **Bei Eingabe von } Block formatieren** deaktiviert.|
|**Bei Eingabe von ; Anweisung automatisch formatieren**|Bei Auswahl dieser Option werden Anweisungen nach der Fertigstellung entsprechend den für den Editor ausgewählten Formatierungsoptionen formatiert.|
|**Bei Eingabe von } Block automatisch formatieren**|Bei Auswahl dieser Option werden Codeblöcke entsprechend den für den Editor ausgewählten Formatierungsoptionen formatiert, sobald der Codeblock abgeschlossen ist.|
|**Bei Verwendung der EINGABETASTE automatisch formatieren**|Bei Auswahl dieser Option wird Text formatiert, wenn Sie die **EINGABETASTE** drücken, damit dieser den für den Editor aktivierten Formatierungsoptionen entspricht.|
|**Beim Einfügen automatisch formatieren**|Bei Auswahl dieser Option wird in den Editor eingefügter Text entsprechend den für den Editor ausgewählten Formatierungsoptionen formatiert.|

### <a name="format-document-settings"></a>Einstellungen für Befehl „Dokument formatieren“

Mit den folgenden Einstellungen wird der Befehl **Dokument formatieren** so konfiguriert, dass zusätzliche Bereinigungsvorgänge für eine Datei ausgeführt werden. Weitere Informationen darüber, wie diese Einstellungen übernommen werden, finden Sie unter [Befehl „Dokument formatieren“](../code-styles-and-quick-actions.md#format-document-command).

|Bezeichnung|Beschreibung |Entsprechende EditorConfig-Optionen und Regeln unter „Extras“ > „Optionen“|
|-----------|-----------------|-----------------|-----------------|
|**Alle C#-Formatierungsregeln anwenden (Einzug, Umbruch, Abstände)**|Durch den Befehl **Dokument formatieren** werden alle Formatierungsprobleme behoben. Diese Einstellung kann nicht angepasst werden.| [Grundlegende EditorConfig-Optionen](../../ide/create-portable-custom-editor-options.md)<br/>[.NET EditorConfig-Formatierungsoptionen](../../ide/editorconfig-code-style-settings-reference.md#formatting-conventions)<br/><br/>**Extras** > **Optionen** > **Text-Editor** > **C#** > **Formatierung** > [**Einzug**, **Neue Zeilen**, **Abstand** oder **Umbruch**]|
|**Zusätzliche Codebereinigung während der Formatierung durchführen**|Bei Auswahl dieser Option werden die Korrekturen angewendet, die in den Regeln für den **Edit.FormatDocument**-Befehl angegeben wurden.| Nicht zutreffend |
|**Remove unnecessary usings** (Nicht erforderliche using-Anweisungen entfernen)|Bei Auswahl dieser Option werden unnötige `using`-Anweisungen entfernt, sobald **Edit.FormatDocument** ausgelöst wird.| Nicht zutreffend |
|**Sort usings** (using-Anweisungen sortieren)|Bei Auswahl dieser Option werden `using`-Anweisungen sortiert, sobald **Edit.FormatDocument** ausgelöst wird.| dotnet_sort_system_directives_first<br/><br/>**Extras** > **Optionen** > **Text-Editor** > **C#** > **Erweitert** > **Place 'System' directives first when sorting usings („System“-Anweisungen beim Sortieren von using-Anweisungen oben anzeigen)** |
|**Geschweifte Klammern für einzeilige Steuerungsanweisungen hinzufügen/entfernen**|Bei Auswahl dieser Option werden einzeiligen Steuerungsanweisungen geschweifte Klammern hinzugefügt bzw. aus diesen entfernt, sobald **Edit.FormatDocument** ausgelöst wird.| csharp_prefer_braces<br/><br/>**Extras** > **Optionen** > **Text-Editor** > **C#** > **Codeformat** > **Codeblockeinstellungen** > **Geschweifte Klammern bevorzugen** |
|**Zugriffsmodifizierer hinzufügen**|Bei Auswahl dieser Option werden Zugriffsmodifizierer hinzugefügt, sobald **Edit.FormatDocument** ausgelöst wird.| dotnet_style_require_accessibility_modifiers |
|**Zugriffsmodifizierer sortieren**|Bei Auswahl dieser Option werden Zugriffsmodifizierer sortiert, sobald **Edit.FormatDocument** ausgelöst wird.| csharp_preferred_modifier_order<br/>visual_basic_preferred_modifier_order |
|**Ausdrucks-/Blocktexteinstellungen anwenden**|Bei Auswahl dieser Option werden Ausdruckskörpermember in Blocktexte konvertiert (oder die umgekehrte Aktion wird ausgeführt), sobald **Edit.FormatDocument** ausgelöst wird.| [EditorConfig-Optionen für Ausdruckskörpermember](../../ide/editorconfig-code-style-settings-reference.md#expression_bodied_members)<br/><br/>**Extras** > **Optionen** > **Text-Editor** > **C#** > **Codeformat** > **Ausdruckseinstellungen** > **Use expression body for methods, constructors, etc. (Ausdruckskörper für Methoden, Konstruktoren usw. verwenden)** |
|**Apply implicit/explicit type preferences** (Einstellungen für implizite/explizite Typen anwenden)|Bei Auswahl dieser Option wird `var` in den expliziten Typ konvertiert (oder die umgekehrte Aktion wird ausgeführt), sobald **Edit.FormatDocument** ausgelöst wird.| [EditorConfig-Optionen für explizite Typen](../../ide/editorconfig-code-style-settings-reference.md#implicit-and-explicit-types)<br/><br/>**Extras** > **Optionen** > **Text-Editor** > **C#** > **Codeformat** > **var-Einstellungen** |
|**Einstellungen für out-Inlinevariablen anwenden**|Bei Auswahl dieser Option werden `out`-Inlinevariablen nach Möglichkeit verwendet, sobald **Edit.FormatDocument** ausgelöst wird.| csharp_style_inlined_variable_declaration<br/><br/>**Extras** > **Optionen** > **Text-Editor** > **C#** > **Codeformat** > **Variableneinstellungen** > **Inlinevariablendeklaration vorziehen** |
|**Typeinstellungen für Sprache/Framework anwenden**|Bei Auswahl dieser Option werden Sprachtypen in Frameworktypen konvertiert (oder die umgekehrte Aktion wird ausgeführt), sobald **Edit.FormatDocument** ausgelöst wird.| dotnet_style_predefined_type_for_locals_parameters_members<br/>dotnet_style_predefined_type_for_member_access<br/><br/>**Extras** > **Optionen** > **Text-Editor** > **C#** > **Codeformat** > **Vordefinierte Typeinstellungen** |
|**Einstellungen für Objekt-/Sammlungsinitialisierung anwenden**|Bei Auswahl dieser werden nach Möglichkeit Objekt- und Elementinitialisierer verwendet, sobald **Edit.FormatDocument** ausgelöst wird.| dotnet_style_object_initializer<br/>dotnet_style_collection_initializer<br/><br/>**Extras** > **Optionen** > **Text-Editor** > **C#** > **Codeformat** > **Ausdruckseinstellungen** > **Objektinitialisierer vorziehen** oder **Prefer collection initializer** (Elementinitialisierer vorziehen) |
|**this.-Qualifizierungseinstellungen anwenden**|Bei Auswahl dieser Option werden die `this.`-Einstellungen angewendet, sobald **Edit.FormatDocument** ausgelöst wird.| [EditorConfig-Optionen für this.-Qualifizierung](../../ide/editorconfig-code-style-settings-reference.md#this_and_me)<br/><br/>**Extras** > **Optionen** > **Text-Editor** > **C#** > **Codeformat** > **this.-Einstellungen** |
|**Private Felder nach Möglichkeit als schreibgeschützt festlegen**|Bei Auswahl dieser Option wird für private Felder nach Möglichkeit `readonly` festgelegt, sobald **Edit.FormatDocument** ausgelöst wird.| dotnet_style_readonly_field<br/><br/>**Extras** > **Optionen** > **Text-Editor** > **C#** > **Codeformat** > **Voreinstellungen für Feld** > **Readonly bevorzugen** |
|**Unnötige Umwandlungen entfernen**|Bei Auswahl dieser Option werden nach Möglichkeit unnötige Umwandlungen entfernt, sobald **Edit.FormatDocument** ausgelöst wird.| Nicht zutreffend |
|**Nicht verwendete Variablen entfernen**|Bei Auswahl dieser Option werden nicht verwendete Variablen entfernt, sobald **Edit.FormatDocument** ausgelöst wird.| Nicht zutreffend |

![Codebereinigungseinstellungen für C# in Visual Studio](media/format-document-settings.png)

## <a name="preview-windows"></a>Vorschaufenster

Auf den Unterseiten **Einzug**, **Neue Zeilen**, **Abstand** und **Umbruch** wird jeweils ein Vorschaufenster im unteren Bereich angezeigt. Im Vorschaufenster wird die Auswirkung der einzelnen Optionen angezeigt. Wählen Sie zur Verwendung des Vorschaufensters eine Formatierungsoption aus. Im Vorschaufenster wird ein Beispiel der ausgewählten Option angezeigt. Wenn Sie eine Einstellung ändern, indem Sie z.B. ein Optionsfeld oder ein Kontrollkästchen aktivieren oder deaktivieren, wird das Vorschaufenster in Anpassung an diese neue Einstellung aktualisiert.

## <a name="indentation-remarks"></a>Hinweise zu Einzügen

Durch die Einzugsoptionen auf den Seiten **Tabstopps** für die jeweiligen Programmiersprachen wird lediglich festgelegt, an welche Position der Cursor im Code-Editor gesetzt wird, wenn Sie am Ende einer Zeile die **EINGABETASTE** drücken. Die Einzugsoptionen unter **Formatierung** werden bei der automatischen Codeformatierung übernommen, beispielsweise wenn Sie Code bei aktivierter Option **Beim Einfügen automatisch formatieren** in die Datei einfügen, und wenn der zu formatierende Block manuell eingegeben wird.

## <a name="see-also"></a>Siehe auch

- [Allgemein, Umgebung, Dialogfeld „Optionen“](../../ide/reference/general-environment-options-dialog-box.md)
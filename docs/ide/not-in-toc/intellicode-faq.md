---
title: Fragen und Antworten zu IntelliCode
ms.date: 07/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
manager: douge
author: markw-t
ms.author: mwthomas
ms.openlocfilehash: 79e18778eae231d16cf32c0fa68bcb6f5564b09d
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079310"
---
# Visual Studio IntelliCode: Häufig gestellte Fragen

Vielen Dank für Ihr Interesse an Visual Studio IntelliCode. Dieses kurze FAQ beantwortet einige Fragen, die Sie sich möglicherweise stellen.

## F. Was ist Visual Studio IntelliCode?

Visual Studio IntelliCode ist eine neue Funktion, die bei der Entwicklerkonferenz Build 2018 von Microsoft angekündigt wurde und die Softwareentwicklung mithilfe von künstlicher Intelligenz verbessert. IntelliCode hilft Entwicklern und Teams dabei, zuverlässig zu codieren, Probleme schneller zu ermitteln und sich auf Code Reviews zu konzentrieren.

In einer frühen Veranschaulichung wurde gezeigt, wie IntelliCode den Softwareentwicklungsprozess auf folgende Weise verbessert:

- Übermittelt kontextabhängige Codevervollständigungen
- Hilft Entwicklern dabei, sich an die Muster und Konventionen ihres Teams zu halten
- Sucht nach schwer auffindbaren Codeproblemen
- Legt den Schwerpunkt auf Code Reviews, indem die Aufmerksamkeit auf die wichtigen Bereiche gerichtet wird.

Unter [https://aka.ms/intellicode](https://aka.ms/intellicode) können Sie weitere Informationen finden und sich für Neuigkeiten und private Vorschauen anmelden.

## F. Was ermöglicht Visual Studio IntelliCode den Kunden?

Visual Studio IntelliCode verfügt über eine Reihe von Funktionen, die mithilfe von künstlicher Intelligenz (KI) neue Produktivitätserweiterungen anbieten.

Entwickler können für Visual Studio 2017 Version 15.7 und höher [eine experimentelle Erweiterung herunterladen](https://go.microsoft.com/fwlink/?linkid=872707). Die Erweiterung bietet derzeit Folgendes:

- IntelliSense mit verbesserter künstlicher Intelligenz, die für den Entwickler die API vorhersieht, die wahrscheinlich am besten zur Verwendung geeignet ist, anstatt nur eine alphabetische Liste der Member darzustellen. Sie verwendet den aktuellen Codekontext und Muster des Entwicklers, um diese dynamische Liste bereitzustellen.

- Den Rückschluss von Codestil- und Formatierungskonventionen, durch den Sie Ihren Code konsistent halten können, indem Sie über Ihre Codebasis eine [EditorConfig-Datei](../create-portable-custom-editor-options.md) zum Definieren von Codierungsstilen und -formaten erstellen. Durch diese Konventionen kann Visual Studio automatische Korrekturen von Stil und Format zur Bereinigung Ihres Dokuments anbieten.

Die Erweiterung wird in den nächsten Monaten mit weiteren Funktionen ausgestattet.

## F. Weshalb stellt der EditorConfig-Rückschluss dem Dateinamen eine 1 voran?

Ein bekanntes Problem in Visual Studio besteht darin, dass dem Dateinamen „.editorconfig“ eine 1 vorangestellt wird, wenn Sie diese durch einen Rechtsklick und durch Auswahl der Option **Hinzufügen > Neues Element** erstellen. Dateien, die auf diese Weise benannt werden, erkennt der Prozessor „editorconfig“ in Visual Studio nicht. Dieses Problem wurde in Visual Studio 2017, Version 15.8, Vorschauversion 4, behoben. Bis dahin können Sie das Problem umgehen, indem Sie die 1 im Dialogfeld **Neues Element hinzufügen** entfernen.

## F. Warum kann ich sehen, ob meine EditorConfig-Konventionen in Kraft getreten sind?
Für dieses Problem gibt es verschiedene häufige Ursachen:

- In Versionen von Visual Studio 2017, die älter als Version 15.8, Vorschauversion 3, sind, müssen Sie alle Dokumente schließen und erneut öffnen, um anzeigen zu können, ob die von Ihnen in der EditorConfig-Datei erstellten Konventionen in Kraft getreten sind. Dieses Problem wurde in Release 15.8, Vorschauversion 3, behoben.
- Formatierungskonventionen werden nie in der **Fehlerliste** oder als „Wellenlinien“ in Ihrem Code angezeigt. Sie können jedoch durch die neue Erweiterung „Format Document“ (STRG + K, STRG + D) in Visual Studio 2017, ab Version 15.8, Vorschauversion 3, korrigiert werden

## F. Weshalb werden meine Stilkonventionen durch die Erweiterung „Format Document“ nicht korrigiert?
Für dieses Problem gibt es verschiedene häufige Ursachen:

- Möglicherweise verwenden Sie nicht Visual Studio 2017, ab Version 15.8, Vorschauversion 3. Sie benötigen diese Version, um den erweiterten Befehl „Format Document“ für die zusätzliche Codebereinigung im aktuellen Dokument verwenden zu können.
- Möglicherweise haben Sie Stilkorrekturen nicht aktiviert. Die erweiterte Möglichkeit zur Korrektur der konventionsbasierten Probleme in „Format Document“ deckt nur bestimmte Probleme ab. Sie können in **Tools > Optionen** unter **Texteditor > C# > Codestil > Formatierung > Allgemein > Einstellungen für „Format Document“ (Experiment)** ändern, welche Probleme behoben werden sollen. Beachten Sie, dass die Standardeinstellungen nicht die Korrektur von Stilkonventionen beinhalten. Sie können diese über **Tools > Optionen** aktivieren. Die Option „Apply implicit/explicit type preferences“ (Implizite/explizite Typeinstellungen anwenden) führt beispielsweise Stilregeln zur Verwendung von `var` aus.

## F. Welche EditorConfig-Konventionen kann Visual Studio IntelliCode ableiten?

Diese Funktion ist derzeit experimentell. Daher wird noch nicht für alle Konventionen, die im [Verweis auf Einstellungen für den Codestil](../editorconfig-code-style-settings-reference.md) dokumentiert sind, Unterstützung geboten.

IntelliCode kann derzeit folgende Konventionen ableiten:

Formatierungskonventionen:

-   csharp_space_between_method_declaration_parameter_list_parentheses
-   csharp_space_between_method_declaration_empty_parameter_list_parentheses
-   csharp_space_between_method_call_name_and_opening_parenthesis
-   csharp_space_between_method_call_parameter_list_parentheses
-   csharp_space_between_method_call_empty_parameter_list_parentheses
-   csharp_space_after_keywords_in_control_flow_statements
-   csharp_space_between_parentheses
-   csharp_space_after_cast
-   csharp_space_after_colon_in_inheritance_clause
-   csharp_space_before_colon_in_inheritance_clause
-   csharp_space_around_binary_operators
-   csharp_indent_switch_labels
-   csharp_indent_case_contents
-   csharp_indent_case_contents_when_block
-   csharp_indent_labels
-   csharp_preserve_single_line_blocks
-   csharp_preserve_single_line_statements
-   csharp_new_line_before_open_brace
-   csharp_new_line_before_else
-   csharp_new_line_before_catch
-   csharp_new_line_before_finally
-   csharp_new_line_before_members_in_object_initializers
-   csharp_new_line_before_members_in_anonymous_types
-   csharp_new_line_between_query_expression_clauses

Stilkonventionen
-   csharp__new_line_before_catch
-   csharp_new_line_before_else
-   csharp_new_line_before_members_in_anonymous_types
-   csharp_new_line_before_members_in_object_initializers
-   csharp_new_line_before_finally_style
-   csharp_new_line_between_query_expression_clauses
-   csharp_prefer_braces_style
-   csharp_preferred_modifier_order_style
-   csharp_prefer_simple_default_expression
-   csharp_preserve_single_line_blocks
-   csharp_space_after_cast
-   csharp_space_after_keywords_in_control_flow_statements
-   csharp_space_between_method_call_parameter_list_parentheses
-   csharp_space_between_method_declaration_parameter_list_parentheses
-   csharp_space_between_parentheses
-   csharp_style_expression_bodied_accessors
-   csharp_style_expression_bodied_constructors
-   csharp_style_expression_bodied_indexers
-   csharp_style_expression_bodied_methods
-   csharp_style_expression_bodied_operators
-   csharp_style_expression_bodied_properties
-   csharp_style_inlined_variable_declaration
-   csharp_style_pattern_local_over_anonymous_function
-   csharp_style_pattern_matching_over_as_with_null_check
-   csharp_style_var_for_built_in_types
-   csharp_style_var_when_type_is_apparent
-   dotnet_sort_system_directives_first
-   dotnet_style_explicit_tuple_names
-   dotnet_style_object_initializer
-   dotnet_style_predefined_type_for_locals_parameters_members
-   dotnet_style_predefined_type_for_member_access
-   dotnet_style_prefer_inferred_anonymous_type_member_names
-   dotnet_style_qualification_for_event
-   dotnet_style_qualification_for_field
-   dotnet_style_qualification_for_method
-   dotnet_style_qualification_for_property
-   dotnet_style_require_accessibility_modifiers

## F. Werden weitere Features für die IntelliCode-Erweiterung für Visual Studio veröffentlicht?

Es wird aktiv an einer Reihe von Funktionen gearbeitet, die bekannt gegeben werden, wenn sie verfügbar sind. Unter [https://aka.ms/intellicode](https://aka.ms/intellicode) können Sie sich für Neuigkeiten und Updates anmelden, um zu den Ersten zu gehören, die über neu verfügbare Funktionen informiert sind.

## F: Was macht „KI-unterstütztes IntelliSense“, das von IntelliCode unterstützt wird, besser als reguläres IntelliSense?

Mit IntelliCode schlägt die Vervollständigungsliste das wahrscheinlich richtige API für einen Entwickler vor, anstatt eine einfache alphabetische Liste der Member anzuzeigen. Es verwendet den aktuellen Codekontext des Entwicklers und Muster, die auf 2000 qualitativ hochwertigen Open-Source-Projekten auf GitHub mit jeweils über 100 Sternen basieren, um diese dynamische Liste bereitzustellen. Die Ergebnisse bilden ein Modell, das die wahrscheinlichsten und relevantesten API-Aufrufe vorhersagt.

## F: Wie gut sind die automatischen Vorschläge für IntelliCode?

Die Vorschläge von IntelliCode werden schon seit einiger Zeit intern von Microsoft verwendet. Wir sind der Meinung, dass die Vorschläge nützlich sind. Letztendlich müssen Sie aber selbst beim Codieren testen, wie nützlich die Vorschläge für Sie sind. Probieren Sie die [IntelliCode-Erweiterung](https://go.microsoft.com/fwlink/?linkid=872707) für Visual Studio doch einmal aus. Sie können uns dann gerne Ihre Meinung dazu mitteilen. Wir trainieren auch unser Modell auf der Grundlage davon, welche Vorschläge Sie auswählen. Wir aktualisieren die Erweiterung, wenn sich das Modell verbessert.

> [!NOTE]
> Ihr benutzerdefinierter Code wird nicht erfasst. Weitere Informationen dazu erhalten Sie in der Frage zum [Datenschutz](#privacy).

## F. Was ist die Zukunft von IntelliCode?

Eine Vielzahl von Möglichkeiten zur Verbesserung der Produktivität von Entwicklern mithilfe von KI und anderen fortgeschrittenen Verfahren. Bei der Entwicklerkonferenz Microsoft Build 2018 wurde eine frühe Übersicht zu einigen Szenarios veranschaulicht, bei denen die künstliche Intelligenz Entwicklern helfen kann, aber es gibt noch viele mehr. Wir sind daran interessiert, von Entwicklern zu lernen, die damit experimentieren, melden Sie sich also für Neuigkeiten und Updates unter [https://aka.ms/intellicode](https://aka.ms/intellicode) an.

## F. Wie viel kostet es?

Es gibt derzeit noch keine Ankündigungen zu den Preisen.

## F. Wann wird IntelliCode veröffentlicht?

Das KI-unterstützte IntelliSense von IntelliCode befindet sich derzeit in der ersten experimentellen Vorschauversion. Die experimentelle Erweiterung wird weiterhin aktualisiert, und weitere Funktionen werden hinzugefügt. Es gibt keinen Zeitplan für eine endgültige Veröffentlichung, aber wir freuen uns über Feedback von Entwicklern, damit die bestmöglichen Features geboten werden können. Unter [https://aka.ms/intellicode](https://aka.ms/intellicode) können Sie sich für Neuigkeiten und Updates anmelden.

## F. Ist dieses Feature nur in Visual Studio und für C# verfügbar?

Das Feature wurde bei der Entwicklerkonferenz Build 2018 in Visual Studio 2017 auf einer C#-Codebase gezeigt. Allerdings freuen wir uns darauf, IntelliCode für weitere Sprachen und Tools in der Visual Studio-Familie zu erweitern.

## F. <a name="whynointellisense"/> Es werden keine Vorschläge von IntelliCode auf der C#-Benutzeroberfläche angezeigt, wo liegt das Problem?

IntelliCode-Vorschläge werden auf der standardmäßigen Benutzeroberfläche für C# von Visual Studio IntelliSense angezeigt. Erweiterungen, die die Benutzeroberfläche überschreiben, verhindern, dass die mit Sternen bewerteten IntelliCode-Vorschläge ganz oben in der Liste angezeigt werden. Sie können überprüfen, ob Erweiterungen dieses Verhalten verursachen, indem Sie sie deaktivieren und IntelliSense erneut öffnen.

Wenn Ihr Problem dadurch nicht behoben wird, melden Sie das Problem über das Visual Studio-Feature zum [Melden eines Problems](https://docs.microsoft.com/en-us/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017), und merken Sie IntelliCode in Ihrem Bericht an.

## F. Für welche Visual Studio-Version muss ich diese Erweiterung ausführen?

Die IntelliCode-Erweiterung für Visual Studio wird in Visual Studio 2017 Version 15.7 Vorschauversion 5 und höher (alle SKUs) unterstützt. Die Installation dieser Erweiterung wird unterbrochen und die Meldung "This extension is not installable on any currently installed products." (Diese Erweiterung kann für die derzeit installierten Produkte nicht installiert werden.) wird angezeigt, wenn Sie nicht die mindestens erforderliche Version installiert haben.

## F. Ist dieses Feature nur auf Englisch verfügbar?

IntelliCode ist derzeit nur die Vorschauversion einer Erweiterung und wir möchten gerne wissen, wie nützlich diese Funktionen für die verschiedenen Kunden sind. Wenn IntelliCode die Phase der Vorschau abgeschlossen hat, werden wir anhand Ihres Feedbacks prüfen, welche Gebiete oder Sprachen zuerst unterstützt und wie diese Unterstützung aussehen sollte.

## <a name="privacy"/> F: Wie sieht es mit dem Datenschutz aus? Senden Sie meinen Code an die Cloud? Welche Kundendaten werden an Microsoft gesendet?

Entwickler sind dazu eingeladen, Visual Studio IntelliCode noch heute als experimentelle Vorschauerweiterung kennenzulernen. Der Zweck dieser Erweiterung ist es, den Entwicklern zu ermöglichen, die Funktionen von IntelliCode zu testen und Feedback an das Produktteam zu senden.

Wir erfassen einige anonymisierte Daten zur Verwendung und Fehlerberichtserstattung der Erweiterung, um das Produkt zu verbessern. Es wird kein benutzerdefinierter Code an Microsoft gesendet, aber wir sammeln Informationen über Ihre Verwendung der IntelliCode-Ergebnisse. Die Daten enthalten nur die Open-Source- und .NET-Typen und -Members, die Sie aus der Liste der vorgeschlagenen Ergebnisse von IntelliCode ausgewählt haben. Entwickler können das [Programm zur Verbesserung der Benutzerfreundlichkeit von Visual Studio](../../ide/visual-studio-experience-improvement-program.md) deaktivieren, wodurch auch die Datensammlung für die IntelliCode-Erweiterung deaktiviert wird. Klicken Sie dazu in der Menüleiste auf **Hilfe** > **Feedback senden** > **Einstellungen**. Wählen Sie im Dialogfeld **Programm zur Verbesserung der Benutzerfreundlichkeit von Visual Studio** **Nein, ich möchte nicht teilnehmen** aus, und klicken Sie dann auf **OK**.

Die IntelliCode-Erweiterung fragt möglicherweise regelmäßig nach, ob der Entwickler an einer anonymen Umfrage teilnehmen möchte. Benutzer können sich für Neuigkeiten und eine zukünftige private Vorschau anmelden, derzeit ist dies jedoch keine Voraussetzung, um die experimentelle Erweiterung verwenden zu können.

Zukünftige Features erfordern möglicherweise den Zugriff auf einen Dienst, der eine Anmeldung erfordert. Weitere Informationen werden veröffentlicht, wenn diese Features bereit für die private Vorschauversion sind.

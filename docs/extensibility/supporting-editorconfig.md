---
title: Erweitern des Sprachdienstes zur Unterstützung von EditorConfig
ms.date: 11/22/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ddfe0e30904d000b4fd70c85371d29a2ee486932
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699586"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Unterstützung von EditorConfig für Ihren Sprachdienst

[EditorConfig-Dateien](https://editorconfig.org/) ermöglichen es Ihnen, allgemeine Texteditor-Optionen, z. B. Einzugsgröße, pro Projekt zu beschreiben. Weitere Informationen zur Unterstützung von EditorConfig-Dateien durch Visual Studio finden Sie unter [Erstellen von einstellungen für tragbare Editormitungen mit EditorConfig](../ide/create-portable-custom-editor-options.md).

In den meisten Fällen ist bei der Implementierung eines Visual Studio-Sprachdiensts keine zusätzliche Arbeit erforderlich, um universelle EditorConfig-Eigenschaften zu unterstützen. Der Haupteditor ermittelt und liest die .editorconfig-Datei automatisch, wenn Benutzer Dateien öffnen, und er legt den entsprechenden Textpuffer und die Ansichtsoptionen fest. Bei Bearbeitungen wie Registerkarten und Leerzeichen entscheiden sich einige Sprachdienste jedoch dafür, eine geeignete kontextbezogene Textansichtsoption zu verwenden, anstatt globale Einstellungen zu verwenden. In diesen Fällen muss der Sprachdienst aktualisiert werden, um EditorConfig-Dateien zu unterstützen.

Im Folgenden sind die Änderungen zu finden, die zum Aktualisieren eines Sprachdienstes zur Unterstützung von EditorConfig-Dateien erforderlich sind, indem eine globale _sprachspezifische_ Option durch eine _kontextbezogene_ Option ersetzt wird:

## <a name="indent-style"></a>Einzugsgröße

Sprachspezifische Optionen | Kontextbezogene Optionen
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>Einzugsgröße

Sprachspezifische Optionen | Kontextbezogene Optionen
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>Tabulatorgröße

Sprachspezifische Optionen | Kontextbezogene Optionen
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>Weitere Informationen

- [Erstellen von portablen Editor-Einstellungen mit EditorConfig](../ide/create-portable-custom-editor-options.md)
- [Erweiterung der Editor- und Sprachdienste](../extensibility/extending-the-editor-and-language-services.md)

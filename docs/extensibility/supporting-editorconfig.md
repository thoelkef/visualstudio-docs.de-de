---
title: Erweitern Sie zur Unterstützung von EditorConfig-Sprachdienst
ms.date: 11/22/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c6974c7943a751f50cafb0b141ba9c1dfc85677
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353496"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Unterstützung von EditorConfig für Ihren Sprachdienst

["Editorconfig"](http://editorconfig.org/) Dateien ermöglichen es Ihnen, allgemeine Text-Editor--Optionen, z.B. die Einzugsgröße, auf einer Basis pro Projekt zu beschreiben. Weitere Informationen zu Visual Studio Unterstützung für EditorConfig-Dateien finden Sie unter [Erstellen von portablen editoreinstellungen, die mit "editorconfig"](../ide/create-portable-custom-editor-options.md).

In den meisten Fällen ist bei der Implementierung eines Visual Studio-Sprachdiensts keine zusätzliche Arbeit erforderlich, um universelle EditorConfig-Eigenschaften zu unterstützen. Der Haupteditor ermittelt und liest die .editorconfig-Datei automatisch, wenn Benutzer Dateien öffnen, und er legt den entsprechenden Textpuffer und die Ansichtsoptionen fest. Jedoch, sich für Bearbeitungen wie z.B. Registerkarten und Leerzeichen, um eine entsprechende kontextbezogene Ansichtsoption, statt globale Einstellungen verwenden einige Sprachdienste entscheiden. In diesen Fällen muss der Sprachdienst aktualisiert werden, um EditorConfig-Dateien zu unterstützen.

Folgendes sind die Änderungen, die erforderlich sind, zum Aktualisieren eines Sprachdiensts zur Unterstützung von EditorConfig-Dateien durch Ersetzen einer globalen _sprachspezifische_ -Option mit einer _kontextbezogene_ Option:

## <a name="indent-style"></a>Einzugsgröße

Language-spezifische Optionen | Kontextbezogene Optionen
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>Einzugsgröße

Language-spezifische Optionen | Kontextbezogene Optionen
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>Tabulatorgröße

Language-spezifische Optionen | Kontextbezogene Optionen
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>Siehe auch

- [Erstellen von portablen editoreinstellungen, die mit "editorconfig"](../ide/create-portable-custom-editor-options.md)
- [Erweitern Sie die Dienste, Editoren und Sprachen](../extensibility/extending-the-editor-and-language-services.md)
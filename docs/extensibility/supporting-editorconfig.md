---
title: "Erweitern einen Sprachdienst zur Unterstützung von EditorConfig in Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 9b38601953fd5b1c80e5eeffd75c2fdc2608fc73
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Unterstützung von EditorConfig für Ihre-Sprachdienst

[EditorConfig](http://editorconfig.org/) Dateien ermöglichen es Ihnen, allgemeine Text-Editor-Optionen, z. B. Einzugsgröße, regelmäßig pro Projekt beschreiben. Weitere Informationen zu Visual Studio-Unterstützung für EditorConfig-Dateien finden Sie unter [erstellen Sie portable editoreinstellungen mit EditorConfig](../ide/create-portable-custom-editor-options.md).

In den meisten Fällen ist bei der Implementierung eines Visual Studio-Sprachdiensts keine zusätzliche Arbeit erforderlich, um universelle EditorConfig-Eigenschaften zu unterstützen. Der Haupteditor ermittelt und liest die .editorconfig-Datei automatisch, wenn Benutzer Dateien öffnen, und er legt den entsprechenden Textpuffer und die Ansichtsoptionen fest. Jedoch wahlweise für die Bearbeitung z. B. Tabstoppzeichen und Leerzeichen, Dienste für einige Sprachen eine Ansichtsoption entsprechenden kontextabhängige Text statt globale Einstellungen verwenden. In diesen Fällen muss der Sprachdienst aktualisiert werden, um EditorConfig-Dateien zu unterstützen.

Folgendes sind die Änderungen, die erforderlich sind, zum Aktualisieren eines Sprachdiensts zur Unterstützung von EditorConfig-Dateien durch einen globalen ersetzen _sprachspezifische_ -Option mit einer _kontextabhängige_ Option:

## <a name="indent-style"></a>Einzugsgröße

Sprachspezifische-Optionen | Kontextabhängige Optionen
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>Einzugsgröße

Sprachspezifische-Optionen | Kontextabhängige Optionen
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>Tabulatorgröße

Sprachspezifische-Optionen | Kontextabhängige Optionen
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>Siehe auch

[Erstellen Sie portable editoreinstellungen EditorConfig verwenden](../ide/create-portable-custom-editor-options.md)  
[Erweitern Sie die Dienste-Editor und Sprache](../extensibility/extending-the-editor-and-language-services.md)
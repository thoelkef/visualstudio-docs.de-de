---
title: Erweiterung des Editors und der Sprachdienste | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 239c638ec32cc0dc2b2e275a5dbe0c4213a3423e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711716"
---
# <a name="extend-the-editor-and-language-services"></a>Erweitern der Editor- und Sprachdienste
Sie können Ihrem eigenen Editor Sprachdienstfeatures (z. B. IntelliSense) hinzufügen und die meisten Features des Visual Studio-Code-Editors erweitern.  Eine vollständige Liste der [Erweiterungspunkte sprachfürdiens und editor](../extensibility/language-service-and-editor-extension-points.md).

 Sie erweitern die meisten Editorfunktionen mithilfe des Managed Extensibility Framework (MEF). Wenn das Editor-Feature, das Sie erweitern möchten, z. B. Syntaxfarben ist, können Sie ein *MEF-Komponententeil* schreiben, das die Klassifizierungen definiert, für die Sie eine andere Färbung wünschen und wie sie behandelt werden sollen. Der Editor unterstützt auch mehrere Erweiterungen desselben Features.

 Die Editorpräsentationsebene basiert auf dem Windows Presentation Framework (WPF). WPF bietet eine Grafikbibliothek für flexible Textformatierung und auch Visualisierungen wie Grafiken und Animationen.

 Das Visual Studio SDK stellt Adapter bereit, die als *Shims* bezeichnet werden, um VSPackages zu unterstützen, die für frühere Versionen geschrieben wurden. Wenn Sie jedoch über ein vorhandenes VSPackage verfügen, empfehlen wir Ihnen, es auf die neue Technologie zu aktualisieren, um eine bessere Leistung und Zuverlässigkeit zu erzielen.

## <a name="related-topics"></a>Verwandte Themen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[Erste Schritte mit Sprachdienst- und Editorerweiterungen](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Erläutert, wie eine Erweiterung für den Editor erstellt wird.|
|[Innerhalb des Editors](../extensibility/inside-the-editor.md)|Beschreibt die allgemeine Struktur des Editors und listet einige seiner Features auf.|
|[Managed Extensibility Framework im Editor](../extensibility/managed-extensibility-framework-in-the-editor.md)|Erläutert die Verwendung des Managed Extensibility Framework (MEF) mit dem Editor.|
|[Sprachdienst- und Editorerweiterungspunkte](../extensibility/language-service-and-editor-extension-points.md)|Listet die Erweiterungspunkte des Editors auf. Erweiterungspunkte stellen die Editor-Features dar, die erweitert werden können.|
|[Exemplarische Vorgehensweise: Erstellen einer Ansichtsverzierung, Befehle und Einstellungen (Spaltenführungslinien)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Durchläuft und erklärt das Erstellen einer Ansichtsverzierung, die Spaltenführungslinien zeichnet, damit Sie Code auf eine bestimmte Anzeigebreite halten können.  Zeigt auch Lese- und Schreibeinstellungen sowie deklarierende und implementierende Befehle an, die Sie über das Befehlsfenster aufrufen können.|
|[Editor-Importe](../extensibility/editor-imports.md)|Listet die Dienste auf, die eine Erweiterung importieren kann.|
|[Anpassen von Legacy-Code an den Editor](/visualstudio/extensibility/adapting-legacy-code-to-the-editor?view=vs-2015)|Erläutert verschiedene Möglichkeiten zum Anpassen von Legacycode (pre-Visual Studio 2010), um den Editor zu erweitern.|
|[Migrieren eines älteren Sprachdienstes](../extensibility/internals/migrating-a-legacy-language-service.md)|Erläutert, wie ein VSPackage-basierter Sprachdienst migriert wird.|
|[Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Zeigt, wie ein Inhaltstyp mit einer Dateinamenerweiterung verknüpft wird.|
|[Exemplarische Vorgehensweise: Erstellen einer Rand-Glyphe](../extensibility/walkthrough-creating-a-margin-glyph.md)|Zeigt, wie einem Rand ein Symbol hinzugefügt wird.|
|[Exemplarische Vorgehensweise: Text hervorheben](../extensibility/walkthrough-highlighting-text.md)|Zeigt, wie *Tags* zum Hervorheben von Text verwendet werden.|
|[Exemplarische Vorgehensweise: Hinzufügen von Gliederung](../extensibility/walkthrough-outlining.md)|Zeigt, wie Diegliederung für bestimmte Arten von geschweiften Klammern hinzugefügt wird.|
|[Exemplarische Vorgehensweise: Passende geschweifte Klammern anzeigen](../extensibility/walkthrough-displaying-matching-braces.md)|Zeigt, wie übereinstimmende geschweifte Geschweifungen hervorgehoben werden.|
|[Exemplarische Vorgehensweise: QuickInfo-Tooltips anzeigen](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Zeigt, wie QuickInfo-Popups angezeigt werden, die Elemente von Code wie Eigenschaften, Methoden und Ereignisse beschreiben.|
|[Exemplarische Vorgehensweise: Signaturhilfe anzeigen](../extensibility/walkthrough-displaying-signature-help.md)|Zeigt, wie Popups angezeigt werden, die Informationen über die Anzahl und die Typen von Parametern in einer Signatur enthalten.|
|[Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung](../extensibility/walkthrough-displaying-statement-completion.md)|Zeigt, wie die Anweisungsvervollständigung implementiert wird.|
|[Exemplarische Vorgehensweise: Implementieren von Codeausschnitten](../extensibility/walkthrough-implementing-code-snippets.md)|Zeigt, wie die Codeausschnitterweiterung implementiert wird.|
|[Walkthrough: Anzeigen von Glühbirnenvorschlägen](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Zeigt, wie Glühbirnen für Codevorschläge angezeigt werden.|
|[Exemplarische Vorgehensweise: Verwenden eines Shellbefehls mit einer Editorerweiterung](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Zeigt, wie ein Menübefehl in einem VSPackage einer MEF-Komponente zugeordnet wird.|
|[Exemplarische Vorgehensweise: Verwenden einer Tastenkombination mit einer Editorerweiterung](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Zeigt, wie eine Menüverknüpfung in einem VSPackage einer MEF-Komponente zugeordnet wird.|
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Enthält Informationen zum Managed Extensibility Framework (MEF).|
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Enthält Informationen zur Windows Presentation Foundation (WPF).|

## <a name="reference"></a>Referenz
 Der Visual Studio-Editor enthält die folgenden Namespaces.

 <xref:Microsoft.VisualStudio.Language.Intellisense>

 <xref:Microsoft.VisualStudio.Language.StandardClassification>

 <xref:Microsoft.VisualStudio.Editor>

 <xref:Microsoft.VisualStudio.Text>

 <xref:Microsoft.VisualStudio.Text.Adornments>

 <xref:Microsoft.VisualStudio.Text.Classification>

 <xref:Microsoft.VisualStudio.Text.Differencing>

 <xref:Microsoft.VisualStudio.Text.Document>

 <xref:Microsoft.VisualStudio.Text.Editor>

 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>

 <xref:Microsoft.VisualStudio.Text.Formatting>

 <xref:Microsoft.VisualStudio.Text.IncrementalSearch>

 <xref:Microsoft.VisualStudio.Text.Operations>

 <xref:Microsoft.VisualStudio.Text.Outlining>

 <xref:Microsoft.VisualStudio.Text.Projection>

 <xref:Microsoft.VisualStudio.Text.Tagging>

 <xref:Microsoft.VisualStudio.Utilities>

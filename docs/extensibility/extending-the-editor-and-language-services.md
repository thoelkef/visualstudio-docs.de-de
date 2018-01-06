---
title: Erweitern des Editors und des Sprachdienste | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4e81409f8ac93c80bf16b5040c6f388b64ffabbe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="extending-the-editor-and-language-services"></a>Erweitern des Editors und des Language-Dienste
Sie können Ihren eigenen Editor Dienst Sprachfunktionen (z. B. IntelliSense) hinzu, und Sie können die meisten Features von Visual Studio Code-Editor erweitern.  Eine vollständige Liste von was Sie erweitern können, finden Sie unter [Sprachdienst und Erweiterungspunkten Editor](../extensibility/language-service-and-editor-extension-points.md).  
  
 Mit Managed Extensibility Framework (MEF) erweitern Sie die meisten Features im Editor. Beispielsweise ist die Editor-Funktion, die Sie erweitern möchten, Syntaxfarben, Sie können schreiben, eine MEF *Komponententeil* , definiert die Klassifizierungen für die unterschiedliche Farben und wie Sie diese als behandelt werden sollen. Der Editor unterstützt auch mehrere Erweiterungen der gleichen Funktion.  
  
 Die Editor Darstellungsschicht basiert Windows Presentation Framework (WPF). WPF enthält eine Grafikbibliothek für flexible textformatierung und bietet außerdem Visualisierungen, z. B. Grafiken und Animationen.  
  
 Das Visual Studio SDK stellt Adapter, die als bekannte *Shims* VSPackages zu unterstützen, die für frühere Versionen geschrieben wurden. Wenn Sie ein VSPackage vorhandene verfügen, empfehlen wir trotzdem, dass Sie sie, um die neue Technologie aktualisieren, die eine bessere Leistung und Zuverlässigkeit zu erhalten.  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Erste Schritte mit Erweiterungen des Sprachdiensts und des Editors](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Erläutert, wie eine Erweiterung in den Editor zu erstellen.|  
|[Im Editor](../extensibility/inside-the-editor.md)|Beschreibt die allgemeine Struktur des Editors und listet einige der Features.|  
|[Managed Extensibility Framework im Editor](../extensibility/managed-extensibility-framework-in-the-editor.md)|Erläutert das Managed Extensibility Framework (MEF) in einem Editor zu verwenden.|  
|[Erweiterungspunkte für den Sprachdienst und den Editor](../extensibility/language-service-and-editor-extension-points.md)|Listet die Erweiterungspunkte des Editors an. Erweiterungspunkte darstellen, die Editorfunktionen, die erweitert werden können.|  
|[Exemplarische Vorgehensweise: Erstellen von Randsteuerelementen für eine Ansicht, Befehlen und Einstellungen (Satzspiegel)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Führt Sie durch, und erstellen eine Ansicht Zusatzelement (adornment), die Spalte Gudie Zeilen ein, um Code beibehalten wird, um eine bestimmte Anzeigebreite Hilfe zeichnet erläutert.  Zeigt auch, lesen und Schreiben von Einstellungen sowie deklarieren und Implementieren von Befehlen, die Sie über das Befehlsfenster aufrufen können.|  
|[Editor-Importe](../extensibility/editor-imports.md)|Listet die Dienste, die eine Erweiterung importieren können.|  
|[Anpassen von Legacycode auf den Editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Erläutert verschiedene Arten Legacycode (vor Visual Studio 2010) zum Erweitern des Editors angepasst werden kann.|  
|[Migrieren eines Legacysprachdiensts](../extensibility/internals/migrating-a-legacy-language-service.md)|Erläutert, wie einen VSPackage basiert-Sprachdienst zu migrieren.|  
|[Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Zeigt, wie Sie einen Inhaltstyp mit einer Dateinamenerweiterung zu verknüpfen.|  
|[Exemplarische Vorgehensweise: Erstellen einer Randglyphe](../extensibility/walkthrough-creating-a-margin-glyph.md)|Zeigt, wie ein Rand ein Symbol hinzu.|  
|[Exemplarische Vorgehensweise: Markieren von Text](../extensibility/walkthrough-highlighting-text.md)|Zeigt, wie *Tags* Hervorheben von Text.|  
|[Exemplarische Vorgehensweise: Gliedern](../extensibility/walkthrough-outlining.md)|Zeigt, wie eine Gliederung für bestimmte Arten von geschweiften Klammern hinzufügen.|  
|[Exemplarische Vorgehensweise: Anzeigen von übereinstimmenden Klammern](../extensibility/walkthrough-displaying-matching-braces.md)|Veranschaulicht die übereinstimmende Klammern hervorgehoben.|  
|[Exemplarische Vorgehensweise: Anzeigen von QuickInfos](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Zeigt, wie QuickInfo-Popups angezeigt, die Elemente des Codes z. B. Eigenschaften, Methoden und Ereignisse zu beschreiben.|  
|[Exemplarische Vorgehensweise: Anzeigen der Signaturhilfe](../extensibility/walkthrough-displaying-signature-help.md)|Zeigt, wie Popups angezeigt, mit die Informationen über die Anzahl und Typen der Parameter in einer Signatur zu erhalten.|  
|[Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung](../extensibility/walkthrough-displaying-statement-completion.md)|Anweisungsvervollständigung Implementierung veranschaulicht.|  
|[Exemplarische Vorgehensweise: Implementieren von Codeausschnitten](../extensibility/walkthrough-implementing-code-snippets.md)|Zeigt, wie Codeausschnitt Erweiterung zu implementieren.|  
|[Exemplarische Vorgehensweise: Anzeigen von mit einer Glühbirne gekennzeichneten Vorschlägen](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Zeigt, wie Glühbirnen Code Vorschläge anzuzeigen.|  
|[Exemplarische Vorgehensweise: Verwenden eines Shellbefehls mit einer Editor-Erweiterung](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Veranschaulicht das Zuordnen eines Menübefehls in einem VSPackage MEF-Komponente.|  
|[Exemplarische Vorgehensweise: Verwenden einer Tastenkombination mit einer Editor-Erweiterung](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Zeigt, wie eine Verknüpfung im Menü in einem VSPackage MEF-Komponente zugeordnet werden soll.|  
|[Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)|Enthält Informationen über das Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](/dotnet/framework/wpf/index)|Enthält Informationen über Windows Presentation Foundation (WPF).|  
  
## <a name="reference"></a>Verweis  
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
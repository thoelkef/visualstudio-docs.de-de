---
title: Erweitern der-Editor und Sprachdienste | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 4d04f4588b1005e9b5ccb42c6042d01aacb45710
ms.lasthandoff: 02/22/2017

---
# <a name="extending-the-editor-and-language-services"></a>Erweitern der-Editor und Sprachdienste
Sie können einen eigenen Editor Language Service-Funktionen (z. B. IntelliSense) hinzu, und Sie können die meisten Funktionen des Code-Editor von Visual Studio zu erweitern.  Eine vollständige Liste von was Sie erweitern können, finden Sie unter [Sprachdienst und Erweiterungspunkte Editor](../extensibility/language-service-and-editor-extension-points.md).  
  
 Erweitern Sie die meisten-Editor-Funktionen mithilfe von Managed Extensibility Framework (MEF). Zum Beispiel wenn die Editor-Funktion, die Sie erweitern möchten Syntaxfarben ist, können Sie schreiben eine MEF *Komponente* , definiert die Klassifikationen aus, für die unterschiedliche Farben und wie Sie diese als behandelt werden sollen. Der Editor unterstützt auch mehrere Erweiterungen der gleichen Funktion.  
  
 Die Darstellungsschicht Editor basiert Windows Presentation Framework (WPF). WPF enthält eine Grafikbibliothek für flexibles Textformat, sowie auch Visualisierungen wie Grafiken und Animationen.  
  
 Das Visual Studio SDK stellt Adapter, die genannte *Shims* VSPackages zu unterstützen, die für frühere Versionen geschrieben wurden. Dennoch, wenn Sie eine vorhandene VSPackage haben, wird empfohlen, dass die Aktualisierung auf die neue Technologie, um eine bessere Leistung und Zuverlässigkeit zu erhalten.  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Erste Schritte mit Sprachdienst und Editor-Erweiterungen](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Erläutert, wie eine Erweiterung in den Editor zu erstellen.|  
|[Im Editor](../extensibility/inside-the-editor.md)|Beschreibt die allgemeine Struktur des Editors, und führt einige seiner Funktionen.|  
|[Managed Extensibility Framework im Editor](../extensibility/managed-extensibility-framework-in-the-editor.md)|Erläutert, wie das Managed Extensibility Framework (MEF) in einem Editor.|  
|[Language Service und Erweiterungspunkte-Editor](../extensibility/language-service-and-editor-extension-points.md)|Listet die Erweiterungspunkte des Editors an. Erweiterungspunkte darstellen, die Editorfunktionen, die erweitert werden können.|  
|[Exemplarische Vorgehensweise: Erstellen einer Ansicht Adornment, Befehle und Einstellungen (Spaltenhilfslinien)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Durchläuft, und erstellen eine Ansicht Adornment, die Spalte Gudie Zeilen, sodass Sie Code auf eine bestimmte Anzeigebreite Geschäftsprojekte zeichnet erläutert.  Außerdem erfahren Sie, lesen und Schreiben von Einstellungen als auch deklarieren und Implementieren von Befehlen, die Sie im Befehlsfenster aufrufen können.|  
|[Imports-Editor](../extensibility/editor-imports.md)|Listet die Dienste, die eine Erweiterung importieren können.|  
|[Anpassen von Legacycode in den Editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Erläutert verschiedene Methoden zum Anpassen von Legacycode (vor Visual Studio 2010), erweitern den Editor.|  
|[Migration von Legacy-Language-Dienst](../extensibility/internals/migrating-a-legacy-language-service.md)|Erläutert, wie ein VSPackage-Basis-Sprachdienst zu migrieren.|  
|[Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit Erweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Zeigt, wie Sie einen Inhaltstyp mit der Erweiterung zu verknüpfen.|  
|[Exemplarische Vorgehensweise: Erstellen einer Randglyphe](../extensibility/walkthrough-creating-a-margin-glyph.md)|Zeigt, wie ein Symbol mit einem Rand hinzuzufügen.|  
|[Exemplarische Vorgehensweise: Markieren von Text](../extensibility/walkthrough-highlighting-text.md)|Zeigt, wie *Tags* Hervorheben von Text.|  
|[Exemplarische Vorgehensweise: Gliedern](../extensibility/walkthrough-outlining.md)|Zeigt, wie eine Gliederung für bestimmte Arten von geschweiften Klammern hinzufügen.|  
|[Exemplarische Vorgehensweise: Anzeigen von übereinstimmenden geschweiften Klammern](../extensibility/walkthrough-displaying-matching-braces.md)|Veranschaulicht, wie übereinstimmende Klammern hervorgehoben.|  
|[Exemplarische Vorgehensweise: Anzeigen von QuickInfos](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Zeigt, wie QuickInfo-Popups angezeigt, die Beschreibung der Code z. B. Eigenschaften, Methoden und Ereignisse.|  
|[Exemplarische Vorgehensweise: Anzeigen von Signaturhilfe](../extensibility/walkthrough-displaying-signature-help.md)|Zeigt, wie Popups angezeigt, die Informationen zur Anzahl und Typen der Parameter in einer Signatur enthält.|  
|[Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung](../extensibility/walkthrough-displaying-statement-completion.md)|Anweisungsabschluss Implementierung veranschaulicht.|  
|[Exemplarische Vorgehensweise: Implementieren von Codeausschnitten](../extensibility/walkthrough-implementing-code-snippets.md)|Zeigt, wie der Codeausschnitt Erweiterung zu implementieren.|  
|[Exemplarische Vorgehensweise: Anzeigen von Glühbirne Vorschläge](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Zeigt, wie Glühbirnen Code Vorschläge angezeigt.|  
|[Exemplarische Vorgehensweise: Verwenden eines Shell-Befehls mit der Erweiterung-Editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Zeigt, wie einen Menübefehl in einem VSPackage MEF-Komponente zugeordnet.|  
|[Exemplarische Vorgehensweise: Verwenden einer Tastenkombination, mit der Erweiterung-Editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Zeigt, wie MEF-Komponente in einem VSPackage Tastenkombination zugeordnet.|  
|[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Enthält Informationen über das Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/Library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Enthält Informationen zu Windows Presentation Foundation (WPF).|  
  
## <a name="reference"></a>Verweis  
 Der Visual Studio-Editor enthält die folgenden Namespaces.  
  
 <xref:Microsoft.VisualStudio.Language.Intellisense></xref:Microsoft.VisualStudio.Language.Intellisense>  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification></xref:Microsoft.VisualStudio.Language.StandardClassification>  
  
 <xref:Microsoft.VisualStudio.Editor></xref:Microsoft.VisualStudio.Editor>  
  
 <xref:Microsoft.VisualStudio.Text></xref:Microsoft.VisualStudio.Text>  
  
 <xref:Microsoft.VisualStudio.Text.Adornments></xref:Microsoft.VisualStudio.Text.Adornments>  
  
 <xref:Microsoft.VisualStudio.Text.Classification></xref:Microsoft.VisualStudio.Text.Classification>  
  
 <xref:Microsoft.VisualStudio.Text.Differencing></xref:Microsoft.VisualStudio.Text.Differencing>  
  
 <xref:Microsoft.VisualStudio.Text.Document></xref:Microsoft.VisualStudio.Text.Document>  
  
 <xref:Microsoft.VisualStudio.Text.Editor></xref:Microsoft.VisualStudio.Text.Editor>  
  
 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods></xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>  
  
 <xref:Microsoft.VisualStudio.Text.Formatting></xref:Microsoft.VisualStudio.Text.Formatting>  
  
 <xref:Microsoft.VisualStudio.Text.IncrementalSearch></xref:Microsoft.VisualStudio.Text.IncrementalSearch>  
  
 <xref:Microsoft.VisualStudio.Text.Operations></xref:Microsoft.VisualStudio.Text.Operations>  
  
 <xref:Microsoft.VisualStudio.Text.Outlining></xref:Microsoft.VisualStudio.Text.Outlining>  
  
 <xref:Microsoft.VisualStudio.Text.Projection></xref:Microsoft.VisualStudio.Text.Projection>  
  
 <xref:Microsoft.VisualStudio.Text.Tagging></xref:Microsoft.VisualStudio.Text.Tagging>  
  
 <xref:Microsoft.VisualStudio.Utilities></xref:Microsoft.VisualStudio.Utilities>

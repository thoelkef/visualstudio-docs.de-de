---
title: Erweitern des Editors und Sprachdienste | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8a7233a89dbda0ebd333979de752296df45bf712
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259193"
---
# <a name="extending-the-editor-and-language-services"></a>Erweitern des Editors und der Sprachdienste
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können Ihren eigenen Editor Language Service-Features (z. B. IntelliSense) hinzu, und Sie können die meisten Features von Visual Studio Code-Editor zu erweitern.  Eine vollständige Liste von was Sie erweitern können, finden Sie unter [Sprachdienst und Erweiterungspunkte Editor](../extensibility/language-service-and-editor-extension-points.md).  
  
 Erweitern Sie die meisten-Editor-Funktionen mit dem Managed Extensibility Framework (MEF). Z. B. wenn die Editor-Funktion, die Sie erweitern möchten, farbige syntaxmarkierung ist, können Sie schreiben eine MEF *Komponente* , definiert die Klassifizierungen, die für die Sie möchten andere Farben und wie sie behandelt werden sollen. Der Editor unterstützt auch mehrere Erweiterungen der gleichen Funktion.  
  
 Die Darstellungsschicht Editor basiert die Windows Presentation Framework (WPF). WPF bietet eine Grafikbibliothek für flexible textformatierung und bietet außerdem Visualisierungen wie Grafiken und Animationen.  
  
 Visual Studio SDK stellt Adapter, die als bekannt *Shims* VSPackages zu unterstützen, die für frühere Versionen geschrieben wurden. Wenn Sie einen vorhandenen VSPackage verfügen, empfehlen wir dennoch, dass Sie es, um die neue Technologie aktualisieren, um eine bessere Leistung und Zuverlässigkeit zu erhalten.  
  
## <a name="related-topics"></a>Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|-----------------|  
|[Erste Schritte mit Erweiterungen des Sprachdiensts und des Editors](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Erläutert, wie eine Erweiterung für den Editor zu erstellen.|  
|[Im Editor](../extensibility/inside-the-editor.md)|Beschreibt die allgemeine Struktur des Editors und führt einige der Features.|  
|[Managed Extensibility Framework im Editor](../extensibility/managed-extensibility-framework-in-the-editor.md)|Erläutert, wie das Managed Extensibility Framework (MEF) mit dem Editor.|  
|[Erweiterungspunkte für den Sprachdienst und den Editor](../extensibility/language-service-and-editor-extension-points.md)|Listet die Erweiterungspunkte im Editor. Erweiterungspunkte darstellen, die Editor-Funktionen, die erweitert werden können.|  
|[Exemplarische Vorgehensweise: Erstellen von Randsteuerelementen für eine Ansicht, Befehlen und Einstellungen (Satzspiegel)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Erläutert, und erläutert, erstellen eine Ansicht Zusatzelement, das zeichnet Spalte Gudie Zeilen aus, um Sie Code auf eine bestimmte Anzeigebreite halten können.  Zeigt auch, lesen und Schreiben von Einstellungen sowie deklarieren und Implementieren von Befehlen, die Sie aus dem Befehlsfenster aufrufen können.|  
|[Editor-Importe](../extensibility/editor-imports.md)|Listet die Dienste, die eine Erweiterung importieren können.|  
|[Anpassen des Legacycodes an den Editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Erläutert verschiedene Möglichkeiten zum Anpassen von Legacycode (vor Visual Studio 2010) um den Editor zu erweitern.|  
|[Migrieren eines Legacysprachdiensts](../extensibility/internals/migrating-a-legacy-language-service.md)|Erläutert, wie einen VSPackage-basierten Sprachdienst zu migrieren.|  
|[Exemplarische Vorgehensweise: Verknüpfen eines Inhaltstyps mit einer Dateinamenerweiterung](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Zeigt, wie Sie einen Inhaltstyp mit einer Dateinamenerweiterung verknüpfen.|  
|[Exemplarische Vorgehensweise: Erstellen einer Randglyphe](../extensibility/walkthrough-creating-a-margin-glyph.md)|Zeigt, wie ein Symbol mit einem Rand hinzufügen.|  
|[Exemplarische Vorgehensweise: Markieren von Text](../extensibility/walkthrough-highlighting-text.md)|Zeigt, wie *Tags* um Text zu markieren.|  
|[Exemplarische Vorgehensweise: Gliedern](../extensibility/walkthrough-outlining.md)|Veranschaulicht, wie eine Gliederung für bestimmte Arten von geschweiften Klammern hinzufügen.|  
|[Exemplarische Vorgehensweise: Anzeigen von übereinstimmenden Klammern](../extensibility/walkthrough-displaying-matching-braces.md)|Zeigt, wie zum Hervorheben von übereinstimmenden geschweiften Klammern.|  
|[Exemplarische Vorgehensweise: Anzeigen von QuickInfos](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|QuickInfo-Popups anzuzeigen, die Beschreibung der Code z. B. Eigenschaften, Methoden und Ereignisse veranschaulicht.|  
|[Exemplarische Vorgehensweise: Anzeigen der Signaturhilfe](../extensibility/walkthrough-displaying-signature-help.md)|Zeigt, wie Popups angezeigt, die Informationen zur Anzahl und Typen der Parameter in einer Signatur.|  
|[Exemplarische Vorgehensweise: Anzeigen von Anweisungsvervollständigung](../extensibility/walkthrough-displaying-statement-completion.md)|Zeigt, wie Anweisungsvervollständigung zu implementieren.|  
|[Exemplarische Vorgehensweise: Implementieren von Codeausschnitten](../extensibility/walkthrough-implementing-code-snippets.md)|Zeigt, wie Code-Snippet-Erweiterung zu implementieren.|  
|[Exemplarische Vorgehensweise: Anzeigen von mit einer Glühbirne gekennzeichneten Vorschlägen](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Zeigt, wie Glühbirnen für Vorschläge für Code angezeigt.|  
|[Exemplarische Vorgehensweise: Verwenden eines Shellbefehls mit einer Editor-Erweiterung](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Veranschaulicht das Zuordnen ein Menübefehls in einem VSPackage mit MEF-Komponente.|  
|[Exemplarische Vorgehensweise: Verwenden einer Tastenkombination mit einer Editor-Erweiterung](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Zeigt, wie MEF-Komponente eine Verknüpfung im Startmenü in einem VSPackage zugeordnet werden soll.|  
|[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Enthält Informationen über das Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Stellt Informationen über die Windows Presentation Foundation (WPF) bereit.|  
  
## <a name="reference"></a>Referenz  
 Visual Studio-Editor enthält die folgenden Namespaces.  
  
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


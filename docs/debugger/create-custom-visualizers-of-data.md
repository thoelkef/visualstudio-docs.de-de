---
title: Erstellen Sie benutzerdefinierte Schnellansichten Datenmenge | Microsoft Docs
ms.custom: ''
ms.date: 06/19/2017
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.visualizer.troubleshoot
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers
ms.assetid: c24c006f-f2ac-429f-89db-677fc0c6e1ea
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dac2fd507936ffc3b305e8d1339000def3e00e2a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="create-custom-visualizers-of-data"></a>Erstellen Sie benutzerdefinierte Schnellansichten von Daten
 Schnellansichten sind Komponenten der [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] Debugger-Benutzeroberfläche. Ein *Schnellansicht* erstellt ein Dialogfeld oder eine andere Schnittstelle, um eine Variable oder ein Objekt in einer Weise anzeigen, die für den Datentyp geeignet ist. So interpretiert zum Beispiel eine HTML-Schnellansicht eine HTML-Zeichenfolge und stellt das Ergebnis so dar, wie es in einem Browserfenster angezeigt würde, eine Bitmapschnellansicht interpretiert eine Bitmapstruktur und zeigt die in der Bitmapdatei enthaltene Grafik an. Bei einigen Schnellansichten können Sie die Daten nicht nur anzeigen lassen, sondern auch bearbeiten.

 Der [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]-Debugger beinhaltet sechs Standardschnellansichten. Dies sind die für Text, HTML, XML und JSON Schnellansichten, wobei alle auf Zeichenfolgenobjekten; die WPF-Strukturschnellansicht zum Anzeigen der visuellen Struktur eines WPF-Objekts; sowie die Datasetschnellansicht, die für DataView DataSet und DataTable-Objekte verwendet. Weitere Schnellansichten stehen möglicherweise in Zukunft zum Download von der Microsoft Corporation zur Verfügung und werden von Dritten und der Community zur Verfügung. Außerdem können Sie eigene Schnellansichten schreiben und sie im [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]-Debugger installieren.

 > [!NOTE]
 > Um eine benutzerdefinierte Schnellansicht für systemeigenen Code zu erstellen, finden Sie unter der [native Debuggerschnellansicht SQLite](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) Beispiel. Benutzerdefinierte Schnellansichten werden in UWP und Windows 8.x-apps nicht unterstützt.

 Schnellansichten werden im Debugger durch ein Lupensymbol dargestellt ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Schnellansicht Symbol"). Wenn angezeigt wird, das Lupensymbol in einer **DataTip**, in einem Debuggerfenster, z. B. die **Überwachen** Fenster oder in der **Schnellüberwachung** (Dialogfeld), klicken Sie auf das Lupensymbol, um Wählen Sie eine Schnellansicht in den Datentyp des entsprechenden Objekts.

## <a name="overview-of-custom-visualizers"></a>Übersicht über benutzerdefinierte Schnellansichten

Sie können für ein Objekt einer beliebigen verwalteten Klasse eine benutzerdefinierte Schnellansicht schreiben. Ausnahmen stellen <xref:System.Object> und <xref:System.Array> dar.  
  
 Die Architektur einer Debuggerschnellansicht besteht aus zwei Teilen:  
  
-   Die *Debuggerseite* innerhalb der Visual Studio-Debugger ausgeführt wird. Im debuggerseitigen Code wird die Benutzeroberfläche für die Schnellansicht erstellt und angezeigt.  
  
-   Die *zu debuggende Seite* ausgeführt wird, innerhalb des Prozesses, der Visual Studio debuggt (die *zu debuggende Komponente*).  
  
 Das Datenobjekt, das Sie visuell darstellen möchten (z. B. ein Zeichenfolgenobjekt), ist im zu debuggenden Prozess vorhanden. Die zu debuggende Seite muss dieses Datenobjekt zur Debuggerseite senden, die dieses Objekt dann über die erstellte Benutzeroberfläche anzeigen kann.  
  
 Die Debuggerseite empfängt dieses Datenobjekt, das von visualisiert werden ein *Objektanbieter* , implementiert die <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> Schnittstelle. Die zu debuggende Seite sendet das Datenobjekt mithilfe der *Objektquelle*, abgeleitet aus <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>. Der Objektanbieter kann auch Daten an die Objektquelle zurücksenden. Dadurch können Sie eine Schnellansicht schreiben, die Daten bearbeitet und anzeigt. Der Objektanbieter kann überschrieben werden, um mit der Ausdrucksauswertung und somit der Objektquelle zu kommunizieren.  
  
 Die zu debuggende Seite und die Debuggerseite kommunizieren durch <xref:System.IO.Stream> miteinander. Es werden Methoden bereitgestellt für die Serialisierung eines Datenobjekts in einen <xref:System.IO.Stream> und für die Deserialisierung eines <xref:System.IO.Stream> zurück in ein Datenobjekt.  
  
 Der Code der zu debuggenden Seite wird mit dem DebuggerVisualizer-Attribut (<xref:System.Diagnostics.DebuggerVisualizerAttribute>) angegeben.  
  
 Um die Benutzeroberfläche der Schnellansicht auf Debuggerseite zu erstellen, müssen Sie eine Klasse erstellen, die von <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> erbt und die <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName>-Methode zum Anzeigen der Oberfläche überschreibt.  
  
 Sie können mit <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> Windows Forms, Dialogfelder und Steuerelemente über die Schnellansicht anzeigen lassen.  
  
 Die Unterstützung für generische Typen ist eingeschränkt. Sie können für ein Zielobjekt eines generischen Typs nur dann eine Schnellansicht schreiben, wenn es sich bei dem generischen Typ um einen offenen Typ handelt. Diese Einschränkung entspricht der Einschränkung bei Verwendung des `DebuggerTypeProxy`-Attributs. Weitere Informationen finden Sie unter [Verwenden des DebuggerTypeProxy-Attributs](../debugger/using-debuggertypeproxy-attribute.md).  
  
 In benutzerdefinierten Schnellansichten treten möglicherweise Sicherheitsprobleme auf. Finden Sie unter [Sicherheitsüberlegungen zu Schnellansichten](../debugger/visualizer-security-considerations.md).  
  
 Die folgenden Verfahren vermitteln Ihnen einen allgemeinen Überblick darüber, welche Schritte zum Erstellen einer Schnellansicht erforderlich sind. Eine ausführlichere Erläuterung finden Sie unter [Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in c#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
### <a name="to-create-the-debugger-side"></a>So erstellen Sie die Debuggerseite  
  
1.  Verwenden Sie <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>-Methoden, damit das visuell dargestellte Objekt auf der Debuggerseite ist.  
  
2.  Erstellen Sie eine Klasse, die von <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> erbt.  
  
3.  Überschreiben Sie die <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName>-Methode, um die Oberfläche anzuzeigen. Mit <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService>-Methoden können Sie Windows Forms, Dialogfelder und Steuerelemente als Teil der Oberfläche anzeigen.  
  
4.  Übernehmen Sie <xref:System.Diagnostics.DebuggerVisualizerAttribute>, indem Sie diesem Attribut eine Schnellansicht (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) zuweisen.  
  
### <a name="to-create-the-debuggee-side"></a>So erstellen Sie die gedebuggte Seite  
  
1.  Übernehmen Sie <xref:System.Diagnostics.DebuggerVisualizerAttribute>, indem Sie diesem Attribut eine Schnellansicht (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) und eine Objektquelle (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>) zuweisen. Wenn Sie die Objektquelle weglassen, wird eine Standardobjektquelle verwendet.  
  
2.  Wenn Sie möchten, dass die Schnellansicht Datenobjekte sowohl bearbeiten als auch anzeigen kann, müssen Sie die `TransferData`-Methode oder die `CreateReplacementObject`-Methode aus <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> überschreiben.   
  
## <a name="in-this-section"></a>In diesem Abschnitt
  
 [Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)  

 [Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)  
  
 [Gewusst wie: Installieren einer Schnellansicht](../debugger/how-to-install-a-visualizer.md)  
  
 [Gewusst wie: Testen und Debuggen einer Schnellansicht](../debugger/how-to-test-and-debug-a-visualizer.md)  
  
 [Referenz zur Schnellansicht-API](../debugger/visualizer-api-reference.md)  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)
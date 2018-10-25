---
title: Erstellen benutzerdefinierter Schnellansichten von Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/19/2017
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 859bf6493a06663a8977898ffa07d600b826d458
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49854311"
---
# <a name="create-custom-visualizers-of-data"></a>Erstellen Sie benutzerdefinierter Schnellansichten von Daten
 Schnellansichten sind Komponenten der [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] Debugger-Benutzeroberfläche. Ein *Schnellansicht* erstellt ein Dialogfeld oder eine andere Schnittstelle für eine Variable oder ein Objekt in einer Weise anzeigen, die für den Datentyp geeignet ist. So interpretiert zum Beispiel eine HTML-Schnellansicht eine HTML-Zeichenfolge und stellt das Ergebnis so dar, wie es in einem Browserfenster angezeigt würde, eine Bitmapschnellansicht interpretiert eine Bitmapstruktur und zeigt die in der Bitmapdatei enthaltene Grafik an. Bei einigen Schnellansichten können Sie die Daten nicht nur anzeigen lassen, sondern auch bearbeiten.

 Der [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]-Debugger beinhaltet sechs Standardschnellansichten. Dies sind der Text, HTML, XML und JSON-Schnellansichten, die alle auf Zeichenfolgenobjekten arbeiten. die WPF-Strukturschnellansicht zum Anzeigen der visuellen Struktur eines WPF-Objekt; sowie die Datasetschnellansicht, die für die DataView-DataSet und DataTable-Objekten funktioniert. Weitere Schnellansichten stehen möglicherweise in Zukunft zum Download von der Microsoft Corporation zur Verfügung und werden von Dritten und der Community zur Verfügung. Außerdem können Sie eigene Schnellansichten schreiben und sie im [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]-Debugger installieren.

 > [!NOTE]
 > Um eine benutzerdefinierte Schnellansicht für nativen Code zu erstellen, finden Sie unter den [nativen SQLite-Debuggerschnellansicht](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) Beispiel. Benutzerdefinierte Schnellansichten in UWP und Windows 8.x-apps nicht unterstützt.

 Im Debugger-Schnellansichten werden durch ein Lupensymbol dargestellt ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Schnellansicht Symbol"). Wenn angezeigt wird, das Lupensymbol in einer **DataTip**, in einem Debuggerfenster wie die **sehen Sie sich** Fenster oder in der **Schnellüberwachung** Dialogfeld klicken Sie auf das Lupensymbol, um Wählen Sie eine Schnellansicht in den Datentyp des entsprechenden Objekts.

## <a name="overview-of-custom-visualizers"></a>Übersicht über benutzerdefinierte Schnellansichten

Sie können für ein Objekt einer beliebigen verwalteten Klasse eine benutzerdefinierte Schnellansicht schreiben. Ausnahmen stellen <xref:System.Object> und <xref:System.Array> dar.  
  
 Die Architektur einer Debuggerschnellansicht besteht aus zwei Teilen:  
  
- Die *Debuggerseite* in Visual Studio-Debugger ausgeführt wird. Im debuggerseitigen Code wird die Benutzeroberfläche für die Schnellansicht erstellt und angezeigt.  
  
- Die *zu debuggende Seite* ausgeführt wird, innerhalb des Prozesses, die Visual Studio debuggt (die *zu debuggende Komponente*).  
  
  Das Datenobjekt, das Sie visuell darstellen möchten (z. B. ein Zeichenfolgenobjekt), ist im zu debuggenden Prozess vorhanden. Die zu debuggende Seite muss dieses Datenobjekt zur Debuggerseite senden, die dieses Objekt dann über die erstellte Benutzeroberfläche anzeigen kann.  
  
  Die Debuggerseite empfängt dieses Datenobjekt, das von visualisiert werden ein *Objektanbieter* , implementiert die <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> Schnittstelle. Die zu debuggende Seite sendet das Datenobjekt mithilfe der *Objektquelle*, ergibt sich aus <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>. Der Objektanbieter kann auch Daten an die Objektquelle zurücksenden. Dadurch können Sie eine Schnellansicht schreiben, die Daten bearbeitet und anzeigt. Der Objektanbieter kann überschrieben werden, um mit der Ausdrucksauswertung und somit der Objektquelle zu kommunizieren.  
  
  Die zu debuggende Seite und die Debuggerseite kommunizieren durch <xref:System.IO.Stream> miteinander. Es werden Methoden bereitgestellt für die Serialisierung eines Datenobjekts in einen <xref:System.IO.Stream> und für die Deserialisierung eines <xref:System.IO.Stream> zurück in ein Datenobjekt.  
  
  Der Code der zu debuggenden Seite wird mit dem DebuggerVisualizer-Attribut (<xref:System.Diagnostics.DebuggerVisualizerAttribute>) angegeben.  
  
  Um die Benutzeroberfläche der Schnellansicht auf Debuggerseite zu erstellen, müssen Sie eine Klasse erstellen, die von <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> erbt und die <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName>-Methode zum Anzeigen der Oberfläche überschreibt.  
  
  Sie können mit <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> Windows Forms, Dialogfelder und Steuerelemente über die Schnellansicht anzeigen lassen.  
  
  Die Unterstützung für generische Typen ist eingeschränkt. Sie können für ein Zielobjekt eines generischen Typs nur dann eine Schnellansicht schreiben, wenn es sich bei dem generischen Typ um einen offenen Typ handelt. Diese Einschränkung entspricht der Einschränkung bei Verwendung des `DebuggerTypeProxy`-Attributs. Weitere Informationen finden Sie unter [Verwenden des DebuggerTypeProxy-Attributs](../debugger/using-debuggertypeproxy-attribute.md).  
  
  In benutzerdefinierten Schnellansichten treten möglicherweise Sicherheitsprobleme auf. Finden Sie unter [Sicherheitsüberlegungen zu Schnellansichten](../debugger/visualizer-security-considerations.md).  
  
  Die folgenden Verfahren vermitteln Ihnen einen allgemeinen Überblick darüber, welche Schritte zum Erstellen einer Schnellansicht erforderlich sind. Eine ausführlichere Erklärung finden Sie unter [Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in c#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
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
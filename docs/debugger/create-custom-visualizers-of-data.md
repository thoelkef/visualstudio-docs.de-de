---
title: Erstellen von benutzerdefinierten Daten-Schnellansichten | Microsoft-Dokumentation
ms.date: 11/07/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64f44379c98808cb93fbe51498234a34a695c3d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62564722"
---
# <a name="create-custom-data-visualizers"></a>Erstellen von benutzerdefinierten Daten-Schnellansichten
 Ein *Schnellansicht* ist Teil der [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] Debugger-Benutzeroberfläche, die eine Variable oder ein Objekt in einer entsprechend seinem Datentyp angezeigt. Beispielsweise wird eine HTML-Schnellansicht eine HTML-Zeichenfolge interpretiert und das Ergebnis zeigt, wie es in einem Browserfenster angezeigt wird. Eine Bitmapschnellansicht interpretiert eine Bitmapstruktur und zeigt die Grafik aus, die es darstellt. Einige Schnellansichten können Sie sowie das Anzeigen der Daten ändern.

 Der [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]-Debugger beinhaltet sechs Standardschnellansichten. Der Text, HTML, XML und JSON-Schnellansichten für String-Objekten zu arbeiten. Der WPF Tree Visualizer zeigt die Eigenschaften der visuellen Struktur eines WPF-Objekts. Die Dataset-Schnellansicht funktioniert für DataView DataSet und DataTable-Objekten.

Weitere Schnellansichten möglicherweise zum Herunterladen von Microsoft, Drittanbietern und der Community zur Verfügung. Sie können auch eigene Schnellansichten schreiben und installieren Sie sie in der [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] Debugger.

Im Debugger wird eine Schnellansicht durch ein Lupensymbol dargestellt ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Schnellansicht Symbol"). Sie können auswählen, das Symbol in einer **DataTip**, Debugger **sehen Sie sich** Fenster oder **Schnellüberwachung** (Dialogfeld), und wählen Sie dann die entsprechende Schnellansicht für das entsprechende Objekt.

## <a name="write-custom-visualizers"></a>Benutzerdefinierte Schnellansichten schreiben

 > [!NOTE]
 > Um eine benutzerdefinierte Schnellansicht für nativen Code zu erstellen, finden Sie unter den [nativen SQLite-Debuggerschnellansicht](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/SqliteVisualizer) Beispiel. Benutzerdefinierte Schnellansichten werden nicht für UWP und Windows 8.x-apps unterstützt.

Sie können für ein Objekt einer beliebigen verwalteten Klasse eine benutzerdefinierte Schnellansicht schreiben. Ausnahmen stellen <xref:System.Object> und <xref:System.Array> dar.

Die Architektur einer Debuggerschnellansicht besteht aus zwei Teilen:

- Die *Debuggerseite* innerhalb der Visual Studio-Debugger ausgeführt wird, erstellt und zeigt die Benutzeroberfläche der Schnellansicht.

- Die *zu debuggende Seite* wird innerhalb des Prozesses ausgeführt, den Visual Studio debuggt (die *zu debuggende Komponente*). Das Datenobjekt zu visualisieren (z. B. ein Zeichenfolgenobjekt), die in der zu debuggenden Prozess vorhanden ist. Die zu debuggende Seite sendet das Objekt auf der Seite des Debuggers, die sie in der Benutzeroberfläche anzeigt, die Sie erstellen.

Die Debuggerseite empfängt das Datenobjekt aus einer *Objektanbieter* , implementiert die <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> Schnittstelle. Die zu debuggende Seite sendet das Objekt über die *Objektquelle*, ergibt sich aus <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.

Der Objektanbieter kann auch Daten zurücksenden zur Objektquelle, können Sie eine Schnellansicht schreiben, die Daten bearbeiten können. Sie Überschreiben der Objektanbieter die ausdrucksauswertung und die Objektquelle zu kommunizieren.

Die zu debuggende Seite und die Debuggerseite kommunizieren miteinander über <xref:System.IO.Stream> Methoden, die eine serialisieren-Objekt in ein <xref:System.IO.Stream> und Deserialisieren der <xref:System.IO.Stream> zurück in ein Datenobjekt.

Sie können eine Schnellansicht für einen generischen Typ erstellen, nur dann, wenn der Typ ein offener Typ ist. Diese Einschränkung entspricht der Einschränkung bei Verwendung des `DebuggerTypeProxy`-Attributs. Weitere Informationen finden Sie unter [Verwenden des DebuggerTypeProxy-Attributs](../debugger/using-debuggertypeproxy-attribute.md).

In benutzerdefinierten Schnellansichten treten möglicherweise Sicherheitsprobleme auf. Finden Sie unter [sicherheitsüberlegungen zu Schnellansichten](../debugger/visualizer-security-considerations.md).

Die folgenden Schritte bieten einen allgemeinen Überblick über die Schnellansicht erstellen. Ausführliche Anweisungen finden Sie unter [Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in C# ](../debugger/walkthrough-writing-a-visualizer-in-csharp.md) oder [Exemplarische Vorgehensweise: Schreiben eine Schnellansicht in Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md).

### <a name="to-create-the-debugger-side"></a>So erstellen Sie die Debuggerseite

Um die Benutzeroberfläche der Schnellansicht auf Debuggerseite zu erstellen, erstellen Sie eine Klasse, die von erbt <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>, und überschreiben die <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> Methode, um die Benutzeroberfläche anzuzeigen. Sie können <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> Windows Forms, Dialogfelder und Steuerelemente in der Schnellansicht angezeigt.

1. Verwenden Sie <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>-Methoden, damit das visuell dargestellte Objekt auf der Debuggerseite ist.

1. Erstellen Sie eine Klasse, die von <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> erbt.

1. Überschreiben Sie die <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName>-Methode, um die Oberfläche anzuzeigen. Verwendung <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> Methoden für die Anzeige von Windows Forms, Dialogfelder und Steuerelemente in der Schnittstelle.

4. Anwenden <xref:System.Diagnostics.DebuggerVisualizerAttribute>, indem sie die Schnellansicht anzuzeigende (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>).

### <a name="to-create-the-debuggee-side"></a>So erstellen Sie die zu debuggende Seite

Sie geben zu debuggende Code mit der <xref:System.Diagnostics.DebuggerVisualizerAttribute>.

1. Übernehmen Sie <xref:System.Diagnostics.DebuggerVisualizerAttribute>, indem Sie diesem Attribut eine Schnellansicht (<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>) und eine Objektquelle (<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>) zuweisen. Wenn Sie die Objektquelle weglassen, wird die Schnellansicht eine Standardobjektquelle verwenden.

1. Damit können die Schnellansicht, bearbeiten und Anzeigen von Datenobjekten, überschreiben die `TransferData` oder `CreateReplacementObject` Methoden aus <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.

## <a name="see-also"></a>Siehe auch

- [Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)
- [Vorgehensweise: Installieren einer Schnellansicht](../debugger/how-to-install-a-visualizer.md)
- [Vorgehensweise: Testen und Debuggen einer Schnellansicht](../debugger/how-to-test-and-debug-a-visualizer.md)
- [Referenz zur Schnellansicht-API](../debugger/visualizer-api-reference.md)
- [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)
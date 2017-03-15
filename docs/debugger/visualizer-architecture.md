---
title: "Schnellansichtarchitektur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 6aad395f-7170-4d9e-b2b8-a5faf453380e
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Schnellansichtarchitektur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Architektur einer Debuggerschnellansicht besteht aus zwei Teilen:  
  
-   Die *Debuggerseite* wird innerhalb des Visual Studio\-Debuggers ausgeführt.  Im debuggerseitigen Code wird die Benutzeroberfläche für die Schnellansicht erstellt und angezeigt.  
  
-   Die *zu debuggende Seite* wird innerhalb des Prozesses ausgeführt, den Visual Studio debuggt \(die *zu debuggende Komponente*\).  
  
 Eine Schnellansicht ist eine Debuggerkomponente, mit der der Debugger die Inhalte eines Datenobjekts in aussagekräftiger, verständlicher Form anzeigen \(*visualisieren*\) kann.  Einige Schnellansichten unterstützen auch die Bearbeitung des Datenobjekts.  Sie können den Debugger erweitern, um eigene benutzerdefinierte Datentypen zu behandeln, indem Sie benutzerdefinierte Schnellansichten schreiben.  
  
 Das Datenobjekt, das visualisiert werden soll, befindet sich innerhalb des Prozesses, den Sie debuggen \(der *zu debuggende*  Prozess\).  Die Benutzeroberfläche, die die Daten anzeigt, wird innerhalb des Visual Studio\-Debuggerprozesses erstellt:  
  
|Debuggerprozess|Zu debuggender Prozess|  
|---------------------|----------------------------|  
|Debuggerbenutzeroberfläche \(DataTips, Überwachenfenster, Schnellüberwachung\)|Zu visualisierendes Datenobjekt|  
  
 Um das Datenobjekt innerhalb der Debuggerschnittstelle zu visualisieren, benötigen Sie Code zur Kommunikation zwischen den beiden Prozessen.  Infolgedessen besteht die Schnellansichtarchitektur aus zwei Teilen: aus *debuggerseitigem* Code und aus Code der *zu debuggenden Seite*.  
  
 Der debuggerseitige Code erstellt eine eigene Benutzeroberfläche, die von der Debuggerschnittstelle aufgerufen werden kann, zum Beispiel DataTip, das Überwachungsfenster oder die Schnellüberwachung.  Die Schnellansichtschnittstelle wird mithilfe der <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>\-Klasse und der <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService>\-Schnittstelle erstellt.  Wie alle Schnellansicht\-APIs befinden sich DialogDebuggerVisualizer und IDialogVisualizerService im <xref:Microsoft.VisualStudio.DebuggerVisualizers>\-Namespace.  
  
|Debuggerseite|Zu debuggende Seite|  
|-------------------|-------------------------|  
|DialogDebuggerVisualizer\-Klasse<br /><br /> IDialogVisualizerService\-Schnittstelle|Datenobjekt|  
  
 Die Benutzeroberfläche ruft die zu visualisierenden Daten von einem Objektanbieter auf Debuggerseite ab.  
  
|Debuggerseite|Zu debuggende Seite|  
|-------------------|-------------------------|  
|DialogDebuggerVisualizer\-Klasse<br /><br /> IDialogVisualizerService\-Schnittstelle|Datenobjekt|  
|Objektanbieter \(implementiert <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>\)||  
  
 Auf der zu debuggenden Seite ist ein entsprechendes Objekt vorhanden, das als Objektquelle bezeichnet wird:  
  
|Debuggerseite|Zu debuggende Seite|  
|-------------------|-------------------------|  
|DialogDebuggerVisualizer\-Klasse<br /><br /> IDialogVisualizerService\-Schnittstelle|Datenobjekt|  
|Objektanbieter \(implementiert <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>\)|Objektquelle \(abgeleitet von <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>\)|  
  
 Der Objektanbieter stellt der Schnellansicht\-Benutzeroberfläche die zu visualisierenden Objektdaten bereit.  Der Objektanbieter ruft die Objektdaten von der Objektquelle ab.  Der Objektanbieter und die Objektquelle stellen APIs bereit, um Objektdaten zwischen der Debuggerseite und der zu debuggenden Seite zu übertragen.  
  
 Jede Schnellansicht muss das zu visualisierende Datenobjekt abrufen.  Die folgende Tabelle zeigt die entsprechenden APIs, die der Objektanbieter und die Objektquelle zu diesem Zweck verwenden:  
  
|Objektanbieter|Objektquelle|  
|--------------------|------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A><br /><br /> – oder –<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A>|  
  
 Beachten Sie, dass der Objektanbieter <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> oder <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A> verwenden kann.  Jede API führt zu einem Anruf von <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A> in der Objektquelle.  Durch einen Aufruf von <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.GetData%2A?displayProperty=fullName> wird ein [System.IO.Stream](assetId:///System.IO.Stream?qualifyHint=False&autoUpgrade=True) eingefügt, der eine serialisierte Form des visualisierten Objekts darstellt.  
  
 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> deserialisiert die Daten wieder in ein Objekt, das Sie anschließend in der Benutzeroberfläche anzeigen können, die Sie mit <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> erstellen.  <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> füllt mit Daten als unformatiertem assetId:///System.IO.Stream?qualifyHint=False&autoUpgrade=True auf, den Sie selbst deserialisieren müssen.  <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A?displayProperty=fullName> ruft <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName> auf, um den serialisierten assetId:///System.IO.Stream?qualifyHint=False&autoUpgrade=True abzurufen und deserialisiert dann die Daten.  Verwenden Sie <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A?displayProperty=fullName>, wenn das Objekt von .NET nicht serialisiert werden kann und benutzerdefiniert serialisiert werden muss.  In diesem Fall müssen Sie auch die <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.Serialize%2A?displayProperty=fullName>\-Methode überschreiben.  
  
 Wenn Sie eine schreibgeschützte Schnellansicht erstellen, genügt eine unidirektionale Kommunikation mit <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetData%2A> oder <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.GetObject%2A>.  Wenn Sie eine Schnellansicht erstellen, die die Bearbeitung von Datenobjekten unterstützt, müssen Sie weitere Schritte durchführen.  Sie müssen ein Datenobjekt auch vom Objektanbieter zurück zur Objektquelle senden können.  Die folgende Tabelle zeigt den Objektanbieter und die Objektquellen\-APIs, die für diesen Zweck verwendet werden:  
  
|Objektanbieter|Objektquelle|  
|--------------------|------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A><br /><br /> – oder –<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A>|  
  
 Beachten Sie wieder, dass es zwei APIs gibt, die der Objektanbieter verwenden kann.  Daten werden vom Objektanbieter zur Objektquelle immer als assetId:///System.IO.Stream?qualifyHint=False&autoUpgrade=True gesendet, aber durch <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> müssen Sie das Objekt selbst in einen assetId:///System.IO.Stream?qualifyHint=False&autoUpgrade=True serialisieren.  
  
 <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceObject%2A> akzeptiert ein von Ihnen bereitgestelltes Objekt, serialisiert es in einen assetId:///System.IO.Stream?qualifyHint=False&autoUpgrade=True und ruft dann <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.ReplaceData%2A> auf, um den assetId:///System.IO.Stream?qualifyHint=False&autoUpgrade=True an <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.CreateReplacementObject%2A> zu senden.  
  
 Durch Verwendung einer der Methoden zum Ersetzen wird in der zu debuggenden Komponente ein neues Datenobjekt erstellt, das das visualisierte Objekt ersetzt.  Wenn Sie den Inhalt des ursprünglichen Objekts ändern möchten, ohne es zu ersetzen, verwenden Sie eine der Übertragungsmethoden aus der folgenden Tabelle.  Diese APIs übertragen Daten gleichzeitig in beide Richtungen, ohne das Objekt zu ersetzen, das visualisiert wird:  
  
|Objektanbieter|Objektquelle|  
|--------------------|------------------|  
|<xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferData%2A><br /><br /> – oder –<br /><br /> <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider.TransferObject%2A>|<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource.TransferData%2A>|  
  
## Siehe auch  
 [Gewusst wie: Schreiben einer Schnellansicht](../debugger/how-to-write-a-visualizer.md)   
 [Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in C\#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)   
 [Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in Visual Basic](../debugger/walkthrough-writing-a-visualizer-in-visual-basic.md)   
 [Sicherheitsüberlegungen zu Schnellansichten](../debugger/visualizer-security-considerations.md)
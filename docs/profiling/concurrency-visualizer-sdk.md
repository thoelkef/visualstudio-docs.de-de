---
title: "Parallelit&#228;tsschnellansichts-SDK | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.sdk.about"
ms.assetid: 4b22cdf9-59b1-4c88-a6d8-1644a4a11e08
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Parallelit&#228;tsschnellansichts-SDK
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können Ihren Quellcode instrumentieren, indem Sie das SDK Parallelitätsschnellansicht verwenden, um zusätzliche Informationen in der Parallelitätsschnellansicht angezeigt.  Sie können die weiteren Daten mit Phasen und Ereignisse im Code zu.  Diese zusätzlichen Visualisierungen bekannt als *Markierung*.  Eine dieser einführenden exemplarischen Vorgehensweise finden Sie unter [Addition der Parallelitätsschnellansicht SDK](http://go.microsoft.com/fwlink/?LinkId=235405).  
  
## Eigenschaften  
 Flags, Spannen und Meldungen ist jeweils zwei Eigenschaften: Kategorie und Bedeutung.  Im Dialogfeld [Erweiterte Einstellungen](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) können Sie diese Eigenschaften verwenden, um den Satz von Markern zu filtern, die angezeigt werden.  Darüber hinaus auswirken diese Eigenschaften die visuelle Darstellung von Markern.  Beispielsweise wird die Größe aus Flags, die Bedeutung darzustellen.  Darüber hinaus wird Farbe verwendet, um Kategorie anzugeben.  
  
## Grundlegende Verwendung  
 Die Parallelitätsschnellansicht macht einen Standardanbieter verfügbar den Sie verwenden können, um Markierungen zu generieren.  Der Anbieter wurde bereits mit der Parallelitätsschnellansicht registriert und Sie müssen noch etwas nicht ausführen, um die Markierung zu erstellen, in der Benutzeroberfläche angezeigt wird.  
  
### C\# und Visual Basic  
 In C\# verwenden Visual Basic und anderer verwalteter Code, den Standardanbieter, indem <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers> aufrufen.  Es macht vier Funktionen zum Generieren von Markern verfügbar: <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteFlag%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.EnterSpan%2A>, <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteMessage%2A> und <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.WriteAlert%2A>.  Es gibt mehrere Überladungen für diese Funktionen, je nachdem, ob Sie Standardwerte für die Eigenschaften verwenden möchten.  Die einfachste Überladung akzeptiert nur einen Zeichenfolgenparameter, der Beschreibung des Ereignisses angibt.  Die Beschreibung wird in den Nebenläufigkeitsschnellansichtsberichten angezeigt.  
  
##### So SDK\-Unterstützung einem C\#\- oder einem Visual Basic\-Projekt hinzufügen  
  
1.  Klicken Sie auf der Menüleiste **Nebenläufigkeitsschnellansicht**, **SDK zum Projekt hinzufügen**, **Analysieren** aus.  
  
2.  Wählen Sie das Projekt, in dem auf das SDK zugreifen möchten und dann die Schaltfläche **SDK zum ausgewählten Projekt hinzufügen** auswählen.  
  
3.  Hinzufügen von Importen oder Using\-Anweisung dem Code hinzu.  
  
    ```c#  
    using Microsoft.ConcurrencyVisualizer.Instrumentation;  
    ```  
  
    ```vb  
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation  
    ```  
  
### C\+\+  
 In C\+\+ erstellen Sie ein [marker\_series\-Klasse](../profiling/marker-series-class.md)\-Objekt und verwenden Sie es, um Funktionen aufzurufen.  Die `marker_series`\-Klasse macht drei Funktionen zum Generieren von Markern, [marker\_series::write\_flag\-Methode](../profiling/marker-series-write-flag-method.md), [marker\_series::write\_message\-Methode](../profiling/marker-series-write-message-method.md) und [marker\_series::write\_alert\-Methode](../profiling/marker-series-write-alert-method.md) verfügbar.  
  
##### Um SDK\-Unterstützung eine C\+\+\-Datei C oder fügen Sie  
  
1.  Klicken Sie auf der Menüleiste **Nebenläufigkeitsschnellansicht**, **SDK zum Projekt hinzufügen**, **Analysieren** aus.  
  
2.  Wählen Sie das Projekt, in dem auf das SDK zugreifen möchten und dann die Schaltfläche **SDK zum ausgewählten Projekt hinzufügen** auswählen.  
  
3.  In C\+\+ schließen Sie `cvmarkersobj.h` ein.  In C schließen Sie `cvmarkers.h` ein.  
  
4.  Fügen Sie einer using\-Anweisung dem Code hinzu.  
  
    ```  
    using namespace Concurrency::diagnostic;  
    ```  
  
5.  Erstellen Sie ein `marker_series`\-Objekt und übergeben Sie es an das `span`\-Konstruktor.  
  
    ```cpp  
  
    marker_series mySeries;  
    span s(mySeries, _T("Span description"));  
  
    ```  
  
## Benutzerdefinierte Verwendung  
 Für erweiterte Szenarios macht das Parallelitätsschnellansicht SDK mehr Steuerelement verfügbar.  Zwei Hauptkonzepte werden um mit komplexeren Szenarien zugeordnet: Markeranbieter und Marker\-Reihe.  Markeranbieter sind verschiedene ETW\-Anbieter \(jeder enthält eine andere GUID\).  Marker\-Reihe ist serielle Kanal von Ereignissen, die durch einen Anbieter generiert werden.  Sie können es verwenden, um die Ereignisse zu organisieren, die durch einen Markeranbieter generiert werden.  
  
#### Um einen neuen Markeranbieter in einem C\#\- oder Visual Basic\-Projekt verwenden  
  
1.  Erstellen eines <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter>\-Objekts  Der Konstruktor akzeptiert eine GUID.  
  
2.  Um den Anbieter registriert, öffnen Sie das Dialogfeld Nebenläufigkeitsschnellansichts [Erweiterte Einstellungen](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md).  Wählen Sie die Registerkarte **Marker** und wählen Sie dann die Schaltfläche **Neuen Anbieter hinzufügen** aus.  Im [Erweiterte Einstellungen](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md) Dialogfeld geben Sie die GUID ein, die verwendet wurde, um den Anbieter und eine Beschreibung des Anbieters zu erstellen.  
  
#### Um einen neuen Markeranbieter in eine C\+\+\-Datei oder C zu verwenden Sie  
  
1.  Verwenden Sie die `CvInitProvider`\-Funktion, um ein PCV\_PROVIDER zu initialisieren.  Der Konstruktor akzeptiert ein GUID\* und ein PCV\_PROVIDER\*.  
  
2.  Um den Anbieter registriert, öffnen Sie das Dialogfeld [Erweiterte Einstellungen](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md).  Wählen Sie die Registerkarte **Marker** und wählen Sie dann die Schaltfläche **Neuen Anbieter hinzufügen** aus.  In diesem Dialogfeld geben Sie die GUID ein, die verwendet wurde, um den Anbieter und eine Beschreibung des Anbieters zu erstellen.  
  
#### So Reihe einer Markierung in einem C\#\- oder Visual Basic\-Projekt verwenden  
  
1.  Um ein neues <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerSeries> zu verwenden, erstellen Sie es zuerst indem Sie ein <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerWriter>\-Objekt verwenden, und generieren Sie dann Markerereignisse direkt von der neue Serie.  
  
    ```c#  
    MarkerSeries series1 = myMarkerWriter.CreateMarkerSeries(″Series 1″);  
    series1.WriteFlag(″My flag″);  
    ```  
  
    ```vb  
    Dim series1 As New myMarkerWriter.CreateMarkerSeries(″Series 1″)  
    series1.WriteFlag(″My flag″)  
    ```  
  
#### Um Reihe einer Markierung in eine C\+\+\-Datei zu verwenden Sie  
  
1.  Erstellen eines `marker_series`\-Objekts  Sie können Ereignisse aus dieser neue Serie generieren.  
  
    ```scr  
    marker_series series;  
    series.write_flag(_T("Hello world!"));  
    ```  
  
#### Um einer Markierung in eine Reihe zu verwenden Sie  
  
1.  Verwenden Sie die `CvCreateMarkerSeries`\-Funktion, um ein PCV\_MARKERSERIES zu erstellen.  
  
    ```cpp  
    PCV_MARKERSERIES series;  
    CvCreatemarkerSeries(myProvider, _T("My Series"), &series);  
    CvWriteFlag(series, _T("Writing a flag"));  
    ```  
  
## Verwandte Themen  
  
|Titel|**Beschreibung**|  
|-----------|----------------------|  
|[C\+\+\-Bibliotheksreferenz](../profiling/cpp-library-reference.md)|Beschreibt die API der Parallelitätsschnellansicht für C\+\+.|  
|[C Bibliotheksverweis](../profiling/c-library-reference.md)|Beschreibt die API der Parallelitätsschnellansicht für C.|  
|<xref:Microsoft.ConcurrencyVisualizer.Instrumentation>|Beschreibt die API der Parallelitätsschnellansicht für verwalteten Code.|  
|[Parallelitätsschnellansicht](../profiling/concurrency-visualizer.md)|Referenzinformationen zu den Ansichten und Berichten für Profilerstellungs\-Datendateien, die mit der Parallelitätsmethode generiert werden und Daten zur Threadausführung enthalten.|
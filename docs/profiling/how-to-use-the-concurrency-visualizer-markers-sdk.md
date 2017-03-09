---
title: "Gewusst wie: Verwenden der SDK-Parallelit&#228;tsschnellansichtsmarker | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19a45032-f8a7-4137-890e-2ceeec938b8d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Verwenden der SDK-Parallelit&#228;tsschnellansichtsmarker
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema veranschaulicht, wie mit der Concurrency Visualizer SDK Spannen erstellen und Schreiben von Flags, Nachrichten und Warnungen.  
  
### <a name="to-use-c"></a>Verwendung von C++  
  
1.  Concurrency Visualizer SDK-Unterstützung für Ihre Anwendung hinzufügen. Weitere Informationen finden Sie unter [Concurrency Visualizer SDK](../profiling/concurrency-visualizer-sdk.md).  
  
2.  Hinzufügen einer `include` Anweisung und einer `using` -Anweisung für das SDK.  
  
    ```cpp  
  
    #include <cvmarkersobj.h>  
    using namespace Concurrency::diagnostic;  
  
    ```  
  
3.  Fügen Sie Code zum Erstellen von drei Bereichen in der Standard-Marker-Serien und ein Kennzeichen, eine Nachricht und eine Warnung, eine für jeden Textabschnitt zu schreiben. Die Methoden zum Schreiben von Flags, Nachrichten und Warnungen sind Mitglieder der [Marker_series](../profiling/marker-series-class.md) Klasse. Der Konstruktor für die [umfassen](../profiling/span-class.md) Klasse erfordert ein `marker_series` Objekt, sodass jeder Bereich eine bestimmte Marker-Serien zugeordnet ist. Ein `span` endet, wenn er gelöscht wird.  
  
    ```cpp  
  
    marker_series series;  
    span *flagSpan = new span(series, 1, _T("flag span"));  
    series.write_flag(_T("Here is the flag."));  
    delete flagSpan;  
  
    span *messageSpan = new span(series, 2, _T("message span"));  
    series.write_flag(_T("Here is the message."));  
    delete messageSpan;  
  
    span *alertSpan = new span(series, 3, _T("alert span"));  
    series.write_flag(_T("Here is the alert."));  
    delete alertSpan;  
  
    ```  
  
4.  Wählen Sie auf der Menüleiste **Analysieren**, **Concurrency Visualizer**, **beginnen mit dem aktuellen Projekt** zum Ausführen der Anwendung und der Concurrency Visualizer anzeigen. Die folgende Abbildung zeigt die drei Spannen und drei Marker in der Parallelitätsschnellansicht.  
  
     ![Parallelitätsschnellansicht mit drei Markern und Warnungen](../profiling/media/cvmarkersnative.png "CvMarkersNative")  
  
5.  Fügen Sie Code zum Aufrufen des Konstruktors für zusätzliche, benutzerdefinierte Marker-Serien erstellen `marker_series` ein Name für die Marker-Serien akzeptiert.  
  
    ```cpp  
  
    marker_series flagSeries(_T("flag series"));  
    span *flagSeriesSpan = new span(flagSeries, 1, _T("flag span"));  
    flagSeries.write_flag(1, _T("flag"));  
    // Sleep to even out the display in the Concurrency Visualizer.  
    Sleep(50);  
    delete flagSeriesSpan;  
  
    marker_series messageSeries(_T("message series"));  
    span *messageSeriesSpan = new span(messageSeries, 1, _T("message span"));  
    messageSeries.write_message(1, _T("message"));  
    // Sleep to even out the display in the Concurrency Visualizer.  
    Sleep(50);  
    delete messageSeriesSpan;  
  
    ```  
  
6.  Starten Sie das aktuelle Projekt Concurrency Visualizer anzeigen. Die zwei Marker-Serien werden in ihre eigenen Spuren in der Threadansicht angezeigt. Die folgende Abbildung zeigt die beiden neuen Spannen.  
  
     ![Parallelitätsschnellansicht mit drei benutzerdefinierten Marker-Serien](../profiling/media/cvmarkerseriesnative.png "CvMarkerSeriesNative")  
  
### <a name="to-use-visual-basic-or-c"></a>Visual Basic oder C# verwenden.#  
  
1.  Concurrency Visualizer SDK-Unterstützung für Ihre Anwendung hinzufügen. Weitere Informationen finden Sie unter [Concurrency Visualizer SDK](../profiling/concurrency-visualizer-sdk.md).  
  
2.  Hinzufügen einer `using` oder `Imports` -Anweisung für das SDK.  
  
    ```vb  
    Imports Microsoft.ConcurrencyVisualizer.Instrumentation  
  
    ```  
  
    ```c#  
    using Microsoft.ConcurrencyVisualizer.Instrumentation;  
    ```  
  
3.  Fügen Sie Code zum Erstellen von drei Bereichen auf die Standard-Marker-Serien und ein Flag, eine Nachricht und eine Warnung, eine für jeden Textabschnitt zu schreiben. Sie erstellen eine <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Span> Objekt durch Aufrufen der statischen [EnterSpan](assetId:///EnterSpan?qualifyHint=False&autoUpgrade=True) Methode. Zum Schreiben in die Standard-Serie, die Sie verwenden die statische Write-Methoden von der <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers> Klasse.  
  
    ```vb  
  
    Dim flagSpan As Span = Markers.EnterSpan("flag span")  
    Markers.WriteFlag("Here is the flag.")  
    flagSpan.Leave()  
  
    Dim messageSpan As Span = Markers.EnterSpan("message span")  
    ' Sleep for a millisecond to even out the display in the Concurrency Visualizer.  
    System.Threading.Thread.Sleep(1)  
    Markers.WriteMessage("Here is a message")  
    messageSpan.Leave()  
  
    Dim alertSpan As Span = Markers.EnterSpan("alert span")  
    ' Sleep for a millisecond to even out the display in the Concurrency Visualizer.  
    System.Threading.Thread.Sleep(1)  
    Markers.WriteAlert("Here is an alert")  
    alertSpan.Leave()  
  
    ```  
  
    ```c#  
  
    Span flagSpan = Markers.EnterSpan("flag span");  
    Markers.WriteFlag("Here is the flag.");  
    flagSpan.Leave();  
  
    Span messageSpan = Markers.EnterSpan("message span");  
    // Sleep for a millisecond to even out the display in the Concurrency Visualizer.  
    System.Threading.Thread.Sleep(1);  
    Markers.WriteMessage("Here is a message");  
    messageSpan.Leave();  
  
    Span alertSpan = Markers.EnterSpan("alert span");  
    // Sleep for a millisecond to even out the display in the Concurrency Visualizer.  
    System.Threading.Thread.Sleep(1);  
    Markers.WriteAlert("Here is an alert");  
    alertSpan.Leave();  
    ```  
  
4.  Wählen Sie auf der Menüleiste **Analysieren**, **Concurrency Visualizer**, **beginnen mit dem aktuellen Projekt** zum Ausführen der Anwendung und der Concurrency Visualizer anzeigen. Die folgende Abbildung zeigt die drei Spannen und drei Marker in der Ansicht "Threads" der Concurrency Visualizer.  
  
     ![Parallelitätsschnellansicht mit Markern und Warnungen](../profiling/media/cvmarkersmanaged.png "CvMarkersManaged")  
  
5.  Fügen Sie Code zum Erstellen von Customer-Marker-Serien mithilfe der statischen <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.Markers.CreateMarkerSeries%2A> Methode. Die <xref:Microsoft.ConcurrencyVisualizer.Instrumentation.MarkerSeries> -Klasse enthält Methoden zum Erstellen von Bereichen und das Schreiben von Flags, Nachrichten und Warnungen.  
  
    ```vb  
  
    Dim flagSeries As MarkerSeries = Markers.DefaultWriter.CreateMarkerSeries("flag series")  
    Dim flagSeriesSpan As Span = flagSeries.EnterSpan("flag span")  
    System.Threading.Thread.Sleep(1)  
    flagSeries.WriteFlag(1, "flag")  
    System.Threading.Thread.Sleep(1)  
    flagSeriesSpan.Leave()  
  
    Dim messageSeries As MarkerSeries = Markers.DefaultWriter.CreateMarkerSeries("message series")  
    Dim messageSeriesSpan As Span = messageSeries.EnterSpan("message span")  
    messageSeries.WriteMessage("message")  
    System.Threading.Thread.Sleep(1)  
    messageSeriesSpan.Leave()  
    ```  
  
    ```c#  
  
    MarkerSeries flagSeries = Markers.DefaultWriter.CreateMarkerSeries("flag series");  
    Span flagSeriesSpan = flagSeries.EnterSpan("flag span");  
    System.Threading.Thread.Sleep(1);  
    flagSeries.WriteFlag(1, "flag");  
    System.Threading.Thread.Sleep(1);  
    flagSeriesSpan.Leave();  
  
    MarkerSeries messageSeries = Markers.DefaultWriter.CreateMarkerSeries("message series");  
    Span messageSeriesSpan = messageSeries.EnterSpan("message span");  
    messageSeries.WriteMessage("message");  
    System.Threading.Thread.Sleep(1);  
    messageSeriesSpan.Leave();  
    ```  
  
6.  Starten Sie das aktuelle Projekt Concurrency Visualizer anzeigen. Die drei Marker-Serien werden in ihre eigenen Spuren in der Threadansicht angezeigt. Die folgende Abbildung zeigt die drei neuen Spannen.  
  
     ![Parallelitätsschnellansicht mit drei benutzerdefinierten Marker-Serien](../profiling/media/cvmarkerseriesmanaged.png "CvMarkerSeriesManaged")  
  
## <a name="see-also"></a>Siehe auch  
 [Parallelitätsschnellansichts-SDK](../profiling/concurrency-visualizer-sdk.md)
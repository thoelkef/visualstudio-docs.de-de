---
title: Debuggen zur Entwurfszeit - Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 452b4045357db12c4b4cff1a5b6e27035cf85d82
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257198"
---
# <a name="debug-at-design-time-in-visual-studio-c-c-visual-basic-f"></a>Debuggen zur Entwurfszeit in Visual Studio (C#, C++, Visual Basic F#)

In einigen Szenarios sollten Sie so Debuggen Sie Code zur Entwurfszeit anstelle von Zeit, während die Anwendung ausgeführt wird. Hierzu können Sie mithilfe der **direkt** Fenster. Sollten Sie das Debuggen von XAML-Code, mit der interagiert mit anderen Code, z. B. Code für die Datenbindung, können Sie **Debuggen** > **an den Prozess anhängen** dafür.
  
### <a name="debug-at-design-time-using-the-immediate-window"></a>Debuggen Sie zur Entwurfszeit über das "Direktfenster"  

Sie können Visual Studio **direkt** Fenster aus, um eine Funktion oder Unterroutine ausführen, während die Anwendung nicht ausgeführt wird. Wenn die Funktion oder die Unterroutine einen Haltepunkt enthält, unterbricht Visual Studio die Ausführung an der entsprechenden Stelle. Sie können dann die Debuggerfenster verwenden, um den Programmzustand zu überprüfen. Diese Funktion wird „Debuggen zur Entwurfszeit“ genannt.  

Im folgende Beispiel wird in Visual Basic. Verwenden der **direkt** Fenster zur Entwurfszeit wird auch in unterstützt C#, C++ und F# Anwendungen.
  
1.  Fügen Sie den folgenden Code in eine Visual Basic-Konsolenanwendung ein:  
  
    ```vb  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2.  Legen Sie einen Haltepunkt an der Zeile `s="Add BreakPoint Here"` fest.  
  
3.  Öffnen der **direkt** Fenster (**Debuggen** > **Windows** > **direkt**), und geben Sie Folgendes in die Fenster: `?MyFunction<enter>`  
  
4.  Stellen Sie sicher, dass der Haltepunkt erreicht wurde und dass die Aufrufliste korrekt ist.  
  
5.  Auf der **Debuggen** Menü klicken Sie auf **Weiter**, und stellen Sie sicher, dass Sie immer noch im Entwurfsmodus sind.  
  
6.  Geben Sie Folgendes in die **direkt** Fenster: `?MyFunction<enter>`  
  
7.  Geben Sie Folgendes in die **direkt** Fenster: `?MySub<enter>`  
  
8.  Stellen Sie sicher, dass Sie den Haltepunkt, und überprüfen Sie den Wert der statischen Variablen `i` in die **"lokal"** Fenster. Sie sollte den Wert 3 haben.  
  
9. Überprüfen Sie, dass die Aufrufliste korrekt ist.  
  
10. Auf der **Debuggen** Menü klicken Sie auf **Weiter**, und stellen Sie sicher, dass Sie immer noch im Entwurfsmodus sind.  

## <a name="debug-at-design-time-from-the-xaml-designer"></a>Debuggen Sie zur Entwurfszeit aus dem XAML-designer

Es kann hilfreich sein, das Debuggen von Code hinter aus dem XAML-Designer in einige deklarative Datenbindungsszenarios sein.

1. Fügen Sie in Ihrem Projekt eine neue XAML-Seite ein, z. B. *temp.xaml*. Lassen Sie die neue XAML-Seite leer. 

1. Kompilieren Sie Ihre Lösung.

1. Open *temp.xaml*, die den Designer lädt (*UwpSurface.exe* in einer UWP-app oder *XDesProc.exe*), damit Sie in späteren Schritten anfügen können. 

1. Öffnen Sie eine Instanz von Visual Studio. Öffnen Sie in die neue Instanz der **an den Prozess anhängen** (Dialogfeld) (**Debuggen** > **an den Prozess anhängen**), legen die **Anfügen an** Feld in den richtigen Code-Typ, z. B. **Managed Code (CoreCLR)** oder der richtigen Code-Typ basierend auf Ihre Version von .NET. Wählen des richtigen Prozesses für die Designer aus der Liste aus, und wählen Sie **Anfügen**.

    Für UWP-Projekte für build 16299 oder höher, die der Designer-Prozess ist *UwpSurface.exe*. Für WPF oder uwp-Versionen vor 16299, wird der Designer-Prozess *XDesProc.exe*.

1. Während an den Prozess angefügt wird, wechseln Sie zu Ihrem Projekt, öffnen Sie den Code hinter der, in dem Sie debuggen möchten, und legen Sie einen Haltepunkt.

1. Öffnen Sie schließlich die Seite, die den XAML-Code enthält, der die Datenbindung enthält.

    Beispielsweise können Sie einen Haltepunkt in der Code für den Konverter für das folgende XAML, festlegen Bindung ein TextBlock-Element zur Entwurfszeit.

    ```xaml
    <TextBlock Text="{Binding title, ConverterParameter=lower, Converter={StaticResource StringFormatConverter}, Mode=TwoWay}"  />
    ```
   Wenn die Seite geladen wird, wird der Haltepunkt erreicht.
  
## <a name="see-also"></a>Siehe auch  
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Debugger – Grundlagen](../debugger/getting-started-with-the-debugger.md)

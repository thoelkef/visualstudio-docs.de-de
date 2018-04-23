---
title: Debuggen zur Entwurfszeit - Visual Studio | Microsoft Docs
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
ms.openlocfilehash: c569ba018cfaa65cf2fec3edcf0676ef374db225
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="debug-at-design-time-in-visual-studio"></a>Debuggen Sie in Visual Studio zur Entwurfszeit

In einigen Szenarien müssen Sie eventuell ein Debuggen von Code zur Entwurfszeit anstelle der Zeit, während die Anwendung ausgeführt wird. Hierzu können Sie mithilfe der **Direktfenster** Fenster. Wenn Sie XAML-Code, der Interaktion mit anderen Code, z. B. Code für die Datenbindung debuggen möchten, können Sie mithilfe **Debuggen** > **an den Prozess anhängen** nachholen.
  
### <a name="debug-at-design-time-using-the-immediate-window"></a>Debuggen Sie zur Entwurfszeit über das "Direktfenster"  

Sie können die Visual Studio **Direktfenster** eine Funktion oder Unterroutine ausführen, während die Anwendung nicht ausgeführt wird. Wenn die Funktion oder die Unterroutine einen Haltepunkt enthält, unterbricht Visual Studio die Ausführung an der entsprechenden Stelle. Sie können dann die Debuggerfenster verwenden, um den Programmzustand zu überprüfen. Diese Funktion wird „Debuggen zur Entwurfszeit“ genannt.  

Im folgende Beispiel wird in Visual Basic, aber die **Direktfenster** Fenster wird auch in c# und C++-Anwendungen unterstützt.
  
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
  
3.  Öffnen der **Direktfenster** Fenster (**Debuggen** > **Windows** > **Direktfenster**), und geben Sie Folgendes in die Fenster: `?MyFunction<enter>`  
  
4.  Stellen Sie sicher, dass der Haltepunkt erreicht wurde und dass die Aufrufliste korrekt ist.  
  
5.  Auf der **Debuggen** Menü klicken Sie auf **Fortfahren**, und stellen Sie sicher, dass Sie immer noch im Entwurfsmodus befinden.  
  
6.  Geben Sie Folgendes in die **Direktfenster** Fenster: `?MyFunction<enter>`  
  
7.  Geben Sie Folgendes in die **Direktfenster** Fenster: `?MySub<enter>`  
  
8.  Stellen Sie sicher, dass Sie den Haltepunkt, und überprüfen Sie den Wert der statischen Variablen `i` in der **"lokal"** Fenster. Sie sollte den Wert 3 haben.  
  
9. Überprüfen Sie, dass die Aufrufliste korrekt ist.  
  
10. Auf der **Debuggen** Menü klicken Sie auf **Fortfahren**, und stellen Sie sicher, dass Sie immer noch im Entwurfsmodus befinden.  

## <a name="debug-at-design-time-from-the-xaml-designer"></a>Debuggen Sie zur Entwurfszeit aus der XAML-designer

Es kann zum Debuggen von XAML-Designer in einigen deklarative Datenbindungsszenarien CodeBehind hilfreich sein.

1. Fügen Sie in Ihrem Projekt eine neue XAML-Seite ein, z. B. *temp.xaml*. Die neue XAML-Seite leer sein. 

1. Kompilieren Sie die Projektmappe.

1. Open *temp.xaml*, die den Designer lädt (*UwpSurface.exe* in einer UWP-app oder *XDesProc.exe*), damit Sie in späteren Schritten anfügen können. 

1. Öffnen Sie eine Instanz von Visual Studio. Öffnen Sie in der neuen Instanz der **an den Prozess anhängen** (Dialogfeld) (**Debuggen** > **an den Prozess anhängen**), legen die **zuordnen** Datumsfeld in den richtigen Codetyp aus, wie z. B. **verwaltetem Code (CoreCLR)** oder der richtigen Codetyp aus. entsprechend der Version .NET. Wählen Sie den richtigen-Designer-Prozess, aus der Liste aus, und wählen Sie **Anfügen**.

    Für UWP-Projekte für 16299 erstellen oder höher, die Designer-Prozess ist *UwpSurface.exe*. Für WPF- oder universelle Windows-Plattform-Versionen, die vor 16299, ist der Designer Vorgang *XDesProc.exe*.

1. Während an den Prozess angefügt wird, wechseln Sie zu Ihrem Projekt, öffnen Sie den Code hinter der, in dem Sie debuggen möchten, und legen Sie einen Haltepunkt.

1. Öffnen Sie schließlich die Seite, die den XAML-Code enthält, der die Datenbindung enthält.

    Beispielsweise konnte einen Haltepunkt im Code Typ-Konverter für das folgende XAML festlegen TextBlock-Steuerelement zur Entwurfszeit gebunden.

    ```xaml
    <TextBlock Text="{Binding title, ConverterParameter=lower, Converter={StaticResource StringFormatConverter}, Mode=TwoWay}"  />
    ```
   Wenn die Seite geladen wird, wird der Haltepunkt erreicht.
  
## <a name="see-also"></a>Siehe auch  
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Debugger – Grundlagen](../debugger/debugger-basics.md)

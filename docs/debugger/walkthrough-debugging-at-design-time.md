---
title: Debuggen zur Entwurfszeit | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/21/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf4a781bee0d0ccb1acd7d9c6b035acac603aea3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696700"
---
# <a name="debug-at-design-time-in-visual-studio-c-c-visual-basic-f"></a>Debuggen zur Entwurfszeit in Visual Studio (C#, C++, Visual Basic F#)

So debuggen Sie Code zur Entwurfszeit anstelle von während einer app ausgeführt werden, können Sie mit der **direkt** Fenster.

So debuggen Sie XAML-Code hinter einer app aus dem XAML-Designer, z. B. Code für die Datenbindung, können Sie **Debuggen** > **an den Prozess anhängen**.

## <a name="use-the-immediate-window"></a>Verwenden Sie das "Direktfenster"

Sie können Visual Studio **direkt** Fenster aus, um eine Funktion oder Unterroutine ausführen, ohne die app ausgeführt wird. Wenn die Funktion oder Unterroutine einen Haltepunkt enthält, wird Visual Studio die Ausführung am Haltepunkt unterbrochen. Sie können dann die Debuggerfenster verwenden, um den Programmzustand zu überprüfen. Dieses Feature wird *Debuggen zur Entwurfszeit* genannt.

Im folgende Beispiel wird in Visual Basic. Sie können auch die **direkt** Fenster zur Entwurfszeit im C#, F#, und C++-apps.

1. Fügen Sie den folgenden Code in eine leere Visual Basic-Konsolen-app ein:

   ```vb
   Module Module1

       Sub Main()
           MySub()
       End Sub

       Function MyFunction() As Decimal
           Static i As Integer
           i = i + 1
           Return i
       End Function

       Sub MySub()
           MyFunction()

       End Sub
   End Module
   ```

1. Legen Sie einen Haltepunkt in der Zeile **End Function**.

1. Öffnen der **direkt** Fenster durch Auswahl **Debuggen** > **Windows** > **direkt**. Typ `?MyFunction` in das Fenster, und drücken Sie dann die **EINGABETASTE**.

   Der Haltepunkt wird erreicht, und der Wert des **MyFunction** in die **"lokal"** Fenster **1**. Sie können die Aufrufliste und andere debugging-Fenster überprüfen, während die app im Unterbrechungsmodus befindet.

1. Wählen Sie **Weiter** auf der Symbolleiste von Visual Studio. Die app beendet wird, und **1** wird zurückgegeben, der **direkt** Fenster. Stellen Sie sicher, dass Sie immer noch im Entwurfsmodus befinden.

1. Typ `?MyFunction` in die **direkt** erneut aus, und drücken Sie **EINGABETASTE**. Der Haltepunkt wird erreicht, und der Wert des **MyFunction** in die **"lokal"** Fenster **2**.

1. Ohne eine Auswahl **Weiter**, Typ `?MySub()` in die **direkt** Fenster, und drücken Sie dann die **EINGABETASTE**. Der Haltepunkt wird erreicht, und der Wert des **MyFunction** in die **"lokal"** Fenster **3**. Sie können app-Status überprüfen, während die app im Unterbrechungsmodus befindet.

1. Wählen Sie **weiterhin**. Der Haltepunkt wird erneut drücken, und der Wert des **MyFunction** in die **"lokal"** Fenster wird jetzt **2**. Die **direkt** Fenster gibt **Ausdruck wurde ausgewertet und hat keinen Wert**.

1. Wählen Sie **Weiter** erneut aus. Die app beendet wird, und **2** wird zurückgegeben, der **direkt** Fenster. Stellen Sie sicher, dass Sie immer noch im Entwurfsmodus sind.

1. Um den Inhalt löschen der **direkt** , mit der rechten Maustaste im Fenster, und wählen Sie im Fenster **deaktivieren Sie alle**.

## <a name="attach-to-an-app-from-the-xaml-designer"></a>Fügen Sie an eine app aus dem XAML-Designer an

In einigen Szenarien deklarative Datenbindung ist es hilfreich, Debuggen von Code hinter der XAML-Designer.

1. Fügen Sie in der Visual Studio-Projekt eine neue XAML-Seite ein, z. B. *temp.xaml*. Lassen Sie die neue XAML-Seite leer.

1. Erstellen Sie die Projektmappe.

1. Open *temp.xaml*, die im XAML-Designer lädt *XDesProc.exe*, oder *UwpSurface.exe* in einer UWP-app.

1. Öffnen Sie eine Instanz von Visual Studio. Wählen Sie in der neuen Instanz **Debuggen** > **an den Prozess anhängen**.

1. In der **an den Prozess anhängen** wählen Sie im Dialogfeld aus kann vom Designer verarbeitet die **verfügbare Prozesse** Liste.

   Für UWP-Projekte für Windows build 16299 oder höher, die der Designer-Prozess ist *UwpSurface.exe*. Für WPF oder UWP-Versionen vor 16299, wird der Designer-Prozess *XDesProc.exe*.

1. Stellen Sie sicher, dass die **Anfügen an** Feld ist in den Typ der korrekten Code für Ihre Version von .NET festgelegt, wie z. B. **Managed Code (CoreCLR)**.

1. Wählen Sie **Anfügen**.

1. Während an den Prozess angefügt wird, wechseln Sie zu anderen Visual Studio-Instanz, und legen Sie Haltepunkte fest, wo Sie möchten den Code hinter Ihrer app zu debuggen.

   Beispielsweise können Sie einen Haltepunkt in der Code für den Konverter für das folgende XAML, festlegen Bindung ein TextBlock-Element zur Entwurfszeit.

    ```xaml
    <TextBlock Text="{Binding title, ConverterParameter=lower, Converter={StaticResource StringFormatConverter}, Mode=TwoWay}"  />
    ```
   Wenn die Seite geladen wird, wird der Haltepunkt erreicht.

## <a name="see-also"></a>Siehe auch
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
- [Debuggersicherheit](../debugger/debugger-security.md)
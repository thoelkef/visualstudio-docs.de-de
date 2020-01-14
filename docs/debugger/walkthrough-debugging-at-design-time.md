---
title: Debuggen zur Entwurfszeit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/10/2019
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
ms.openlocfilehash: beb16ae52f880e31bd19a185d47b13c02026752f
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916143"
---
# <a name="debug-at-design-time-in-visual-studio-c-ccli-visual-basic-f"></a>Debuggen zur Entwurfszeit in VisualC#Studio C++(,/CLI, F#Visual Basic,)

Zum Debuggen von Code zur Entwurfszeit anstelle der Ausführung einer App können Sie das **direkt** Fenster verwenden.

Zum Debuggen von XAML-Code hinter einer App aus dem XAML-Designer (z. b. in deklarativen Daten Bindungs Szenarien) können Sie **Debuggen** , > **an den Prozess anhängen**.

## <a name="use-the-immediate-window"></a>Direkt Fenster verwenden

Sie können das **direkt** Fenster in Visual Studio verwenden, um eine Funktion oder Unterroutine auszuführen, ohne Ihre APP auszuführen. Wenn die Funktion oder die Unterroutine einen Haltepunkt enthält, unterbricht Visual Studio am Breakpoint. Sie können dann die Debuggerfenster verwenden, um den Programmzustand zu überprüfen. Dieses Feature wird *Debuggen zur Entwurfszeit* genannt.

Das folgende Beispiel befindet sich in Visual Basic. Sie können das **direkt** Fenster zur Entwurfszeit auch in C#-, F#-und C++/CLI-Apps verwenden.

1. Fügen Sie den folgenden Code in eine leere Visual Basic Konsolen-App ein:

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

1. Legen Sie einen Haltepunkt für die Zeilen **Ende Funktion**fest.

1. Öffnen Sie das Fenster **direkt** , indem Sie **Debuggen** > **Fenster** > **direkt**auswählen. Geben Sie im-Fenster `?MyFunction` ein, und drücken Sie dann die **Eingabe**Taste.

   Der Breakpoint wird getroffen, und der Wert von **MyFunction** **im Fenster Lokal** ist **1**. Sie können die-Aufrufe und andere Debuggingfenster überprüfen, während sich die APP im unterbrechen Modus befindet.

1. Wählen Sie auf der Visual Studio-Symbolleiste **weiter** aus. Die APP wird beendet, und **1** wird im **direkt** Fenster zurückgegeben. Stellen Sie sicher, dass Sie sich noch im Entwurfs Modus befinden.

1. Geben Sie `?MyFunction` erneut im **direkt** Fenster ein, und drücken **Sie die Eingabe**Taste. Der Breakpoint wird getroffen, und der Wert von **MyFunction** **im Fenster Lokal** ist **2**.

1. Geben Sie `?MySub()` im **direkt** Fenster ein, und drücken Sie dann die **Eingabe**Taste, ohne " **Continue**" auszuwählen. Der Breakpoint wird getroffen, und der Wert von **MyFunction** **im Fenster Lokal** ist **3**. Sie können den App-Status überprüfen, während sich die APP im unterbrechen Modus befindet.

1. Wählen Sie **weiterhin**. Der Breakpoint wird wiederholt, und der Wert von **MyFunction** **im Fenster Lokal** ist jetzt **2**. Der **direkt** Fenster Rückgabe **Ausdruck wurde ausgewertet und weist keinen Wert**auf.

1. Klicken Sie erneut auf **weiter** . Die APP wird beendet, und **2** wird im **direkt** Fenster zurückgegeben. Stellen Sie sicher, dass Sie sich noch im Entwurfs Modus befinden.

1. Um den Inhalt des **direkt Fensters zu** löschen, klicken Sie mit der rechten Maustaste in das Fenster, und wählen Sie **Alle löschen**aus.

## <a name="debug-a-custom-xaml-control-at-design-time-by-attaching-to-xaml-designer"></a>Debuggen eines benutzerdefinierten XAML-Steuer Elements zur Entwurfszeit durch Anhängen an den XAML-Designer

1. Öffnen Sie die Projekt Mappe oder das Projekt in Visual Studio.

1. Erstellen Sie die Projekt Mappe/das Projekt.

1. Öffnen Sie die XAML-Seite mit dem benutzerdefinierten Steuerelement, das Sie debuggen möchten.

   Bei UWP-Projekten, die auf Windows Build 16299 oder höher ausgerichtet sind, wird mit diesem Schritt der *uwpsurface. exe* -Prozess gestartet. Bei WPF-oder UWP-Versionen vor Windows Build 16299 wird mit diesem Schritt der *xdesproc. exe* -Prozess gestartet.

1. Öffnen Sie eine zweite Instanz von Visual Studio. Öffnen Sie keine Projekt Mappe oder ein Projekt in der zweiten Instanz.

1. Öffnen Sie in der zweiten Instanz von Visual Studio das Menü **Debuggen** , und wählen Sie **an den Prozess anhängen...** aus.

1. Wählen Sie je nach Projekttyp (siehe vorherige Schritte) in der Liste der verfügbaren Prozesse entweder den Prozess " *uwpsurface. exe* " oder den *xdesproc. exe* -Prozess aus.

1. Wählen Sie im **Dialogfeld an** den **Prozess anhängen** an den richtigen Codetyp für das benutzerdefinierte Steuerelement aus, das Sie debuggen möchten.

   Wenn Ihr benutzerdefiniertes Steuerelement in einer .NET-Sprache geschrieben wurde, wählen Sie den entsprechenden .net-Codetyp aus, z. b. **Managed (CoreCLR)** . Wenn Ihr benutzerdefiniertes Steuerelement in C++geschrieben wurde, wählen Sie **native**aus.

1. Fügen Sie die zweite Instanz von Visual Studio durch Klicken auf die Schaltfläche **Anfügen** an.

1. Öffnen Sie in der zweiten Instanz von Visual Studio die Code Dateien, die dem benutzerdefinierten Steuerelement zugeordnet sind, das Sie debuggen möchten. Stellen Sie sicher, dass Sie nur die Dateien öffnen, nicht die gesamte Projekt Mappe oder das gesamte Projekt.

1. Platzieren Sie die erforderlichen Breakpoints in den zuvor geöffneten Dateien.

1. Schließen Sie in der ersten Instanz von Visual Studio die XAML-Seite, die das benutzerdefinierte Steuerelement enthält, das Sie debuggen möchten (dieselbe Seite, die Sie in den vorherigen Schritten geöffnet haben).

1. Öffnen Sie in der ersten Instanz von Visual Studio die XAML-Seite, die Sie im vorherigen Schritt geschlossen haben. Dies bewirkt, dass der Debugger am ersten Haltepunkt angehalten wird, den Sie in der zweiten Instanz von Visual Studio festgelegt haben.

1. Debuggen Sie den Code in der zweiten Instanz von Visual Studio.

## <a name="see-also"></a>Siehe auch
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
- [Debuggersicherheit](../debugger/debugger-security.md)
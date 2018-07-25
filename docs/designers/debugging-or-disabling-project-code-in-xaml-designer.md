---
title: Debuggen oder Deaktivieren von Projektcode im XAML-Designer
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: ac600581-8fc8-49e3-abdf-1569a3483d74
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 4764df436a7adeb3ac65c574812c8f7d334d497b
ms.sourcegitcommit: 522ba712c0d625e51352506146b0556414681964
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37890564"
---
# <a name="debug-or-disable-project-code-in-xaml-designer"></a>Debuggen oder Deaktivieren von Projektcode im XAML-Designer

In vielen Fällen können Ausnahmefehler im **XAML**-Designer durch Projektcode verursacht werden, der versucht, auf Eigenschaften oder Methoden zuzugreifen, die verschiedene Werte zurückgeben oder auf verschiedene Weise funktionieren, wenn die Anwendung im Designer ausgeführt wird. Sie können diese Ausnahmen auflösen, indem Sie den Projektcode in einer anderen Instanz von Visual Studio debuggen. Sie können Ausnahmen vorübergehend verhindern, indem Sie Projektcode im Designer deaktivieren.

Der Projektcode umfasst Folgendes:

-   Benutzerdefinierte Steuerelemente und Benutzersteuerelemente

-   Klassenbibliotheken

-   Wertkonverter

-   Bindungen für Entwurfszeitdaten, die aus Projektcode generiert werden

Wenn Projektcode deaktiviert ist, zeigt Visual Studio Platzhalter an. Visual Studio zeigt beispielsweise den Namen der Eigenschaft für eine Bindung an, in der keine Daten mehr verfügbar sind, oder einen Platzhalter für ein Steuerelement, das nicht mehr ausgeführt wird.

![Dialogfeld für nicht behandelte Ausnahmen](../designers/media/xaml_unhandledexception.png)

## <a name="to-determine-if-project-code-is-causing-an-exception"></a>So ermitteln Sie, ob das Projektcode eine Ausnahme verursacht

1.  Wählen Sie im Dialogfeld des Ausnahmefehlers den Link **Klicken Sie hier, um den Designer neu zu laden** aus.

2.  Klicken Sie auf der Menüleiste auf **Debuggen** > **Debuggen starten**, um die Anwendung zu erstellen und auszuführen.

     Wenn die Anwendung erfolgreich erstellt wurde und ausgeführt wird, wird die Ausnahme zur Entwurfszeit ggf. durch Projektcode verursacht, der im Designer ausgeführt wird.

## <a name="to-debug-project-code-running-in-the-designer"></a>So debuggen Sie Projektcode, der im Designer ausgeführt wird

1.  Wählen Sie im Dialogfeld des Ausnahmefehlers den Link **Klicken Sie hier, um das Ausführen von Projektcode zu deaktivieren und den Designer erneut zu laden** aus.

2.  Wählen Sie im Windows Task-Manager die Schaltfläche **Task beenden** aus, um alle Instanzen des XAML-Designers von Visual Studio zu schließen, die zurzeit ausgeführt werden.

     ![XAML-Designer-Instanzen im Task-Manager](../designers/media/xaml_taskmanager.png)

3.  Öffnen Sie in Visual Studio die XAML-Seite, die den Code oder das Steuerelement enthält, den bzw. das Sie debuggen möchten.

4.  Öffnen Sie eine neue Instanz von Visual Studio, und öffnen Sie dann eine zweite Instanz Ihres Projekts.

5.  Legen Sie einen Haltepunkt in Ihrem Projektcode fest.

6.  Klicken Sie in der neuen Instanz von Visual Studio auf der Menüleiste auf **Debuggen** > **An den Prozess anhängen**.

7.  Wählen Sie im Dialogfeld **An den Prozess anhängen** in der Liste **Verfügbare Prozesse** die Datei **XDesProc.exe**aus, und wählen Sie dann die Schaltfläche **Anfügen** aus.

     ![Der XAML-Designer-Prozess](../designers/media/xaml_attach.png)

     Dies ist der Prozess für den XAML-Designer in der ersten Instanz von Visual Studio.

8.  Klicken Sie in der ersten Instanz von Visual Studio auf der Menüleiste auf **Debuggen** > **Debugging starten**.

     Sie können den Code nun schrittweise durchlaufen, der im Designer ausgeführt wird.

## <a name="to-disable-project-code-in-the-designer"></a>So deaktivieren Sie Projektcode im Designer

-   Wählen Sie im Dialogfeld des Ausnahmefehlers den Link **Klicken Sie hier, um das Ausführen von Projektcode zu deaktivieren und den Designer erneut zu laden** aus.

-   Alternativ können Sie auf der Symbolleiste im **XAML-Designer** die Schaltfläche **Projektcode deaktivieren** auswählen.

     ![Schaltfläche "Projektcode deaktivieren"](../designers/media/xaml_disablecode.png)

     Sie können die Schaltfläche erneut umschalten, um Projektcode erneut zu aktivieren.

    > [!NOTE]
    > Für Projekte für ARM- oder X64-Prozessoren kann Visual Studio keinen Projektcode im Designer ausführen. Die Schaltfläche **Projektcode deaktivieren** ist daher im Designer deaktiviert.

-   Jede dieser Optionen bewirkt, dass der Designer erneut geladen und anschließend der gesamte Code für das zugehörige Projekt deaktiviert wird.

    > [!NOTE]
    > Das Deaktivieren von Projektcode kann zu einem Verlust von Entwurfszeitdaten führen. Eine Alternative besteht darin, den im Designer ausgeführten Code zu debuggen.

## <a name="see-also"></a>Siehe auch

- [Designing XAML in Visual Studio and Blend for Visual Studio (Entwerfen mithilfe von XAML in Visual Studio und Blend für Visual Studio)](../designers/designing-xaml-in-visual-studio.md)
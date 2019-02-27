---
title: Debuggen eines Windows Forms | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- debugging managed code, Windows Forms
- debugging [Visual Studio], Windows Forms
- Attach to Process dialog box
- debugger, attaching to programs
- Attach to Process dialog box, walkthroughs
- Windows Forms, debugging
- debugging Windows Forms, walkthroughs
ms.assetid: 529db1e2-d9ea-482a-b6a0-7c543d17f114
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df8a099470661545666149e32cf02f4481487e54
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56696141"
---
# <a name="walkthrough-debugging-a-windows-form"></a>Exemplarische Vorgehensweise: Debuggen eines Windows Forms
Ein Windows Form ist eine der am häufigsten vorkommenden verwalteten Anwendungen. Ein solches Formular erstellt eine Windows-Standardanwendung. Sie können diese exemplarische Vorgehensweise mit Visual Basic, C# oder C++ ausführen.

 Zuerst müssen Sie alle geöffneten Projektmappen schließen.

### <a name="to-prepare-for-this-walkthrough"></a>So bereiten Sie diese exemplarische Vorgehensweise vor

-   Wenn Sie bereits eine Projektmappe geöffnet haben, schließen Sie diese. (Klicken Sie im Menü **Datei** auf **Projektmappe schließen**.)

## <a name="create-a-new-windows-form"></a>Erstellen eines neuen Windows Form
 Als Nächstes erstellen Sie ein neues Windows Form.

#### <a name="to-create-the-windows-form-for-this-walkthrough"></a>So erstellen Sie das Windows Form für diese exemplarische Vorgehensweise

1.  Klicken Sie im Menü **Datei** auf **Neu** und auf **Projekt**.

     Das Dialogfeld **Neues Projekt** wird angezeigt.

2.  Öffnen Sie im Bereich „Projekttypen“ den Knoten **Visual Basic**, **Visual C#** oder **Visual C++**. Gehen Sie anschließend wie folgt vor:

    1.  Für Visual Basic oder Visual C#Option **Windows Desktop** > **Windows-Formular-App**.

    2.  Wählen Sie für Visual C++, **Windows-Desktopanwendung**.

3.  Geben Sie im Feld **Name** einen eindeutigen Namen für das Projekt ein (z. B. „Walkthrough_SimpleDebug“).

4.  Klicken Sie auf **OK**.

     Visual Studio erstellt ein neues Projekt und zeigt ein neues Formular im Windows Forms-Designer an. Weitere Informationen finden Sie unter [Windows Forms-Designer](/previous-versions/visualstudio/visual-studio-2010/e06hs424\(v\=vs.100\)).

5.  Wählen Sie im Menü **Ansicht** die Option **Toolbox** aus.

     Die Toolbox wird geöffnet. Weitere Informationen finden Sie unter [Toolbox](../ide/reference/toolbox.md).

6.  Klicken Sie in der Toolbox auf das **Button**-Steuerelement, und ziehen Sie es auf die Formularentwurfsoberfläche. Legen Sie das Steuerelement im Formular ab.

7.  Klicken Sie in der Toolbox auf das **TextBox**-Steuerelement, und ziehen Sie es auf die Formularentwurfsoberfläche. Legen Sie das **TextBox**-Steuerelement im Formular ab.

8. Doppelklicken Sie auf der Formularentwurfsoberfläche auf die Schaltfläche.

     Dadurch gelangen Sie auf die Codepage. Der Cursor sollte sich nun in der `button1_Click`-Funktion befinden.

10. Fügen Sie folgenden Code in die `button1_Click`-Funktion ein:

    ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

11. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.

     Das Projekt wird fehlerfrei erstellt.

## <a name="debug-your-form"></a>Debuggen des Formulars
 Jetzt können Sie mit dem Debuggen beginnen.

#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>So debuggen Sie das Windows Form, das für diese exemplarische Vorgehensweise erstellt wurde

1.  Klicken Sie im Quellcodefenster auf den linken Rand der Zeile, in der sich der hinzugefügte Text befindet:

     ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

     Ein roter Punkt wird angezeigt, und der Text der Zeile wird rot hervorgehoben. Der rote Punkt steht für einen Haltepunkt. Weitere Informationen finden Sie unter [Breakpoints (Haltepunkte)](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583). Wenn Sie die Anwendung unter dem Debugger ausführen, hält dieser die Ausführung an der Stelle mit dem Haltepunkt an. Dadurch erhalten Sie die Möglichkeit, den Status der Anwendung zu überprüfen und diese zu debuggen.

    > [!NOTE]
    >  Sie können auch mit der rechten Maustaste auf jede Codezeile klicken, auf **Haltepunkt** zeigen und anschließend auf **Haltepunkt einfügen** klicken, um einen Breakpoint in dieser Zeile hinzuzufügen.

2.  Wählen Sie im Menü **Debuggen** den Befehl **Starten** aus.

     Das Windows Form wird ausgeführt.

3.  Klicken Sie im Formular auf die hinzugefügte Schaltfläche.

     In Visual Studio gelangen Sie damit in die Zeile, in der Sie auf der Codepage den Haltepunkt festgelegt haben. Diese Zeile sollte gelb markiert sein. Jetzt können Sie die Variablen der Anwendung anzeigen und die Ausführung der Anwendung steuern. Die Ausführung der Anwendung wird angehalten, und der Debugger wartet auf eine Aktion Ihrerseits.

4.  Klicken Sie im Menü **Debuggen** auf **Fenster**, dann auf **Überwachen** und anschließend auf **Überwachen 1**.

5.  Klicken Sie im Fenster **Überwachen 1** auf eine leere Zeile. In der **Namen** Spalte, Typ `textBox1.Text` (Wenn Sie Visual Basic oder Visual verwenden C#) oder `textBox1->Text` (Wenn Sie C++ verwenden), dann die EINGABETASTE drücken.

     Das Fenster **Überwachen 1** zeigt den Wert dieser Variablen in Anführungszeichen an:

    `""`

6.  Wählen Sie im Menü **Debuggen** die Option **Einzelschritt** aus.

     Der Wert von textBox1.Text ändert sich in der **Überwachen 1** Fenster:

    `Button was clicked!`

7.  Klicken Sie im Menü **Debuggen** auf **Weiter**, um das Debuggen des Programms fortzusetzen.

8.  Klicken Sie im Formular erneut auf die Schaltfläche.

     Visual Studio unterbricht die Ausführung erneut.

9. Klicken Sie auf den roten Punkt, der den Haltepunkt darstellt.

     Dadurch wird der Haltpunkt aus dem Code entfernt.

10. Wählen Sie im Menü **Debuggen** die Option **Debuggen beenden** aus.

## <a name="attach-to-your-windows-form-application-for-debugging"></a>Anfügen an die Windows Form-Anwendung zum Debuggen
 In [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] können Sie den Debugger an einen laufenden Prozess anfügen. Wenn Sie eine Express Edition verwenden, wird dieses Feature nicht unterstützt.

#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>So fügen Sie die Windows Form-Anwendung zum Debuggen an

1.  Klicken Sie im soeben erstellen Projekt in den linken Rand der hinzugefügten Zeile, um erneut einen Haltepunkt festzulegen:

     ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";

2.  On the **Debug** menu, select **Start Without Debugging**.

     The Windows Form starts running under Windows, just as if you had double-clicked its executable. The debugger is not attached.

3.  On the **Debug** menu, select **Attach to Process**. (This command is also available on the **Tools** menu.)

     The **Attach to Process** dialog box appears.

4.  In the **Available Processes** pane, find the process name (Walkthrough_SimpleDebug.exe) in the **Process** column and click it.

5.  Click the **Attach** button.

6.  In your Windows Form, click the one and only button.

     The debugger breaks execution of the Windows Form at the breakpoint.

## See Also
- [Debugging Managed Code](../debugger/debugging-managed-code.md)
- [Debugger Security](../debugger/debugger-security.md)
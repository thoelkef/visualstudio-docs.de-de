---
title: 'Exemplarische Vorgehensweise: Debuggen eines Windows Forms | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a21450dda35addae55019545d67ab7f1e4ebe99a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-debugging-a-windows-form"></a>Exemplarische Vorgehensweise: Debuggen eines Windows Forms
Ein Windows Form ist eine der am häufigsten vorkommenden verwalteten Anwendungen. Ein solches Formular erstellt eine Windows-Standardanwendung. Sie können diese exemplarische Vorgehensweise mit Visual Basic, C# oder C++ ausführen.  
  
 Zuerst müssen Sie alle geöffneten Projektmappen schließen.  
  
### <a name="to-prepare-for-this-walkthrough"></a>So bereiten Sie diese exemplarische Vorgehensweise vor  
  
-   Wenn Sie bereits eine Projektmappe geöffnet haben, schließen Sie diese. (Auf der **Datei** klicken Sie im Menü **Projektmappe schließen**.)  
  
## <a name="create-a-new-windows-form"></a>Erstellen eines neuen Windows Form  
 Als Nächstes erstellen Sie ein neues Windows Form.  
  
#### <a name="to-create-the-windows-form-for-this-walkthrough"></a>So erstellen Sie das Windows Form für diese exemplarische Vorgehensweise  
  
1.  Auf der **Datei** Menü wählen **neu** , und klicken Sie auf **Projekt**.  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
2.  Öffnen Sie im Bereich Projekttypen den **Visual Basic**, **Visual C#-**, oder **Visual C++** Knoten, klicken Sie dann  
  
    1.  Wählen Sie für Visual Basic oder Visual c# den **Windows** Knoten, wählen Sie dann **Windows Forms-Anwendung** in der **Vorlagen** Bereich.  
  
    2.  Wählen Sie für Visual C++ die **CLR** Knoten, wählen Sie dann **Windows Forms-Anwendung** in der **Vorlagen** Bereich...  
  
3.  In der **Vorlagen** klicken Sie im Bereich **Windows-Anwendung**.  
  
4.  In der **Namen** gewähren Sie dem Projekt einen eindeutigen Namen (z. B. "Walkthrough_SimpleDebug").  
  
5.  Klicken Sie auf **OK**.  
  
     Visual Studio erstellt ein neues Projekt und zeigt ein neues Formular im Windows Forms-Designer an. Weitere Informationen finden Sie unter [Windows Forms-Designer](http://msdn.microsoft.com/en-us/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  
  
6.  Auf der **Ansicht** klicken Sie im Menü **Toolbox**.  
  
     Die Toolbox wird geöffnet. Weitere Informationen finden Sie unter [Toolbox](../ide/reference/toolbox.md).  
  
7.  Klicken Sie in der Toolbox auf die **Schaltfläche** Steuerelement, und ziehen Sie das Steuerelement auf die Formularentwurfsoberfläche. Legen Sie das Steuerelement im Formular ab.  
  
8.  Klicken Sie in der Toolbox auf die **Textfeld** Steuerelement, und ziehen Sie das Steuerelement auf die Formularentwurfsoberfläche. Löschen der **Textfeld** auf dem Formular.  
  
9. Doppelklicken Sie auf der Formularentwurfsoberfläche auf die Schaltfläche.  
  
     Dadurch gelangen Sie auf die Codepage. Der Cursor sollte sich nun in der `button1_Click`-Funktion befinden.  
  
10. Fügen Sie folgenden Code in die `button1_Click`-Funktion ein:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
11. Auf der **erstellen** klicken Sie im Menü **Projektmappe**.  
  
     Das Projekt wird fehlerfrei erstellt.  
  
## <a name="debug-your-form"></a>Debuggen des Formulars  
 Jetzt können Sie mit dem Debuggen beginnen.  
  
#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>So debuggen Sie das Windows Form, das für diese exemplarische Vorgehensweise erstellt wurde  
  
1.  Klicken Sie im Quellcodefenster auf den linken Rand der Zeile, in der sich der hinzugefügte Text befindet:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!";  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
     Ein roter Punkt wird angezeigt, und der Text der Zeile wird rot hervorgehoben. Der rote Punkt steht für einen Haltepunkt. Weitere Informationen finden Sie unter [Haltepunkte](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583). Wenn Sie die Anwendung unter dem Debugger ausführen, hält dieser die Ausführung an der Stelle mit dem Haltepunkt an. Dadurch erhalten Sie die Möglichkeit, den Status der Anwendung zu überprüfen und diese zu debuggen.  
  
    > [!NOTE]
    >  Sie können auch mit der rechten Maustaste eine beliebige Zeile des Codes, zeigen Sie auf **Haltepunkt**, und klicken Sie dann auf **Haltepunkt einfügen** um einen Haltepunkt in dieser Zeile hinzuzufügen.  
  
2.  AUF der **Debuggen** Menü wählen **starten**.  
  
     Das Windows Form wird ausgeführt.  
  
3.  Klicken Sie im Formular auf die hinzugefügte Schaltfläche.  
  
     In Visual Studio gelangen Sie damit in die Zeile, in der Sie auf der Codepage den Haltepunkt festgelegt haben. Diese Zeile sollte gelb markiert sein. Jetzt können Sie die Variablen der Anwendung anzeigen und die Ausführung der Anwendung steuern. Die Ausführung der Anwendung wird angehalten, und der Debugger wartet auf eine Aktion Ihrerseits.  
  
4.  Auf der **Debuggen** Menü wählen **Windows**, klicken Sie dann **Überwachen**, und klicken Sie auf **Überwachen 1**.  
  
5.  In der **Überwachen 1** Fenster, klicken Sie auf eine leere Zeile. In der **Namen** Geben Sie die Spalte `textBox1.Text` (Wenn Sie Visual Basic, Visual C#- oder j# verwenden) oder `textBox1->Text` (Wenn Sie C++ verwenden), drücken Sie dann die EINGABETASTE.  
  
     Die **Überwachen 1** Fenster zeigt den Wert dieser Variablen in Anführungszeichen:  
  
    ```  
    ""  
    ```  
  
6.  Auf der **Debuggen** Menü wählen **Einzelschritt**.  
  
     Der Wert von textBox1.Text ändert sich in der **Überwachen 1** Fenster angezeigt:  
  
    ```  
    Button was clicked!  
    ```  
  
7.  Auf der **Debuggen** Menü wählen **Fortfahren** zum Debuggen des Programms fortzusetzen.  
  
8.  Klicken Sie im Formular erneut auf die Schaltfläche.  
  
     Visual Studio unterbricht die Ausführung erneut.  
  
9. Klicken Sie auf den roten Punkt, der den Haltepunkt darstellt.  
  
     Dadurch wird der Haltpunkt aus dem Code entfernt.  
  
10. Auf der **Debuggen** Menü wählen **Beenden des Debuggens**.  
  
## <a name="attach-to-your-windows-form-application-for-debugging"></a>Anfügen an die Windows Form-Anwendung zum Debuggen  
 In [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] können Sie den Debugger an einen laufenden Prozess anfügen. Wenn Sie eine Express Edition verwenden, wird dieses Feature nicht unterstützt.  
  
#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>So fügen Sie die Windows Form-Anwendung zum Debuggen an  
  
1.  Klicken Sie im soeben erstellen Projekt in den linken Rand der hinzugefügten Zeile, um erneut einen Haltepunkt festzulegen:  
  
    ```  
    ' Visual Basic  
    textBox1.Text = "Button was clicked!"  
  
    // C#  
    textBox1.Text = "Button was clicked!"  
  
    // C++  
    textBox1->Text = "Button was clicked!";  
    ```  
  
2.  Auf der **Debuggen** klicken Sie im Menü **Starten ohne Debugging**.  
  
     Das Windows Form wird unter Windows ausgeführt, genau wie bei einem Doppelklick auf die ausführbare Datei. Der Debugger wird nicht angehängt.  
  
3.  Auf der **Debuggen** klicken Sie im Menü **an den Prozess anhängen**. (Dieser Befehl steht auch auf die **Tools** Menü.)  
  
     Das Dialogfeld **An den Prozess anhängen** wird angezeigt.  
  
4.  In der **verfügbare Prozesse** Bereich, suchen den Prozessnamen (Walkthrough_SimpleDebug.exe) in der **Prozess** Spalte, und klicken Sie darauf.  
  
5.  Klicken Sie auf die **Anfügen** Schaltfläche.  
  
6.  Klicken Sie im Formular auf die einzige vorhandene Schaltfläche.  
  
     Der Debugger unterbricht die Ausführung des Formulars am Haltepunkt.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)
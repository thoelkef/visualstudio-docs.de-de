---
title: "Erstellen und Verwalten von modalen Dialogfeldern | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Dialogfelder in Visual Studio verwalten"
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Erstellen und Verwalten von modalen Dialogfeldern
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie ein modales Dialogfeld in Visual Studio erstellen, müssen Sie sicherstellen, dass das übergeordnete Fenster des Dialogfelds deaktiviert ist, während das Dialogfeld angezeigt wird und dann das übergeordnete Fenster wieder zu aktivieren, nachdem das Dialogfeld geschlossen wurde. Wenn Sie dies nicht tun, kann die Fehlermeldung: "Microsoft Visual Studio kann nicht heruntergefahren, da ein modales Dialogfeld noch aktiv ist. Schließen Sie das aktive Dialogfeld, und versuchen Sie es erneut."  
  
 Es gibt zwei Möglichkeiten, auf diese Weise. Haben eine WPF\-Dialogfeld wird empfohlen, leiten Sie ihn von <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, und rufen Sie dann <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> um das Dialogfeld anzuzeigen. Wenn Sie dies tun, müssen Sie nicht den modalen Zustand des übergeordneten Fensters zu verwalten.  
  
 Ist das Dialogfeld nicht WPF oder einem anderen Grund, Sie können nicht abgeleitet werden, die im Dialogfeld\-Klasse <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, das übergeordnete Element des Dialogfelds durch Aufrufen von erhalten Sie müssen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> und Verwalten der modalen Zustand selbst, der durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> \-Methode mit einem Parameter von 0 \(falsch\), bevor Sie das Dialogfeld anzuzeigen, und rufen die Methode erneut mit dem Parameter 1 \(True\) nach dem Schließen des Dialogfelds.  
  
## Erstellen eines Dialogfelds DialogWindow abgeleitet  
  
1.  Erstellen Sie ein VSIX\-Projekt namens **OpenDialogTest** und fügen Sie einen Befehl mit dem Namen **Öffnen**. Weitere Informationen hierzu finden Sie unter [Erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Verwenden der <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> \-Klasse, müssen Sie Verweise auf die folgenden Assemblys hinzufügen \(auf der Registerkarte Framework die **Verweis hinzufügen** Dialogfeld\):  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
    -   System.Xaml  
  
3.  Fügen Sie folgende OpenDialog.cs, `using` Anweisung:  
  
    ```c#  
    using Microsoft.VisualStudio.PlatformUI;  
    ```  
  
4.  Deklarieren Sie eine Klasse mit dem Namen **TestDialogWindow** abgeleitet <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>:  
  
    ```c#  
    class TestDialogWindow : DialogWindow  
    {. . .}  
    ```  
  
5.  Legen Sie zum Minimieren und Maximieren das Dialogfeld Lage sein, <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> und <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> auf "true":  
  
    ```c#  
    internal TestDialogWindow()  
    {  
        this.HasMaximizeButton = true;  
        this.HasMinimizeButton = true;  
    }  
    ```  
  
6.  In der **OpenDialog.ShowMessageBox** \-Methode, ersetzen Sie den vorhandenen Code durch Folgendes:  
  
    ```c#  
    TestDialogWindow testDialog = new TestDialogWindow();  
    testDialog.ShowModal();  
    ```  
  
7.  Erstellen Sie die Anwendung, und führen Sie sie aus. Die experimentelle Instanz von Visual Studio sollte angezeigt werden. Auf der **Tools** im Menü der experimentellen Instanz sollte einen Befehl mit dem Namen **aufrufen öffnen**. Wenn Sie diesen Befehl klicken, sollte das Dialogfeld angezeigt werden. Sie sollten in der Lage zu minimieren und Maximieren Sie das Fenster.  
  
## Erstellen und Verwalten von ein Dialogfeld, das nicht von DialogWindow abgeleitet.  
  
1.  Bei diesem Verfahren können Sie die **OpenDialogTest** Lösung, die Sie erstellt, die zuvor mit der gleichen Assemblyverweisen haben.  
  
2.  Fügen Sie die folgenden `using` Deklarationen:  
  
    ```c#  
    using System.Windows;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    ```  
  
3.  Erstellen Sie eine Klasse mit dem Namen **TestDialogWindow2** abgeleitet <xref:System.Windows.Window>:  
  
    ```c#  
    class TestDialogWindow2 : Window  
    {. . .}  
    ```  
  
4.  Fügen Sie einen privaten Verweis auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:  
  
    ```  
    private IVsUIShell shell;  
    ```  
  
5.  Fügen Sie einen Konstruktor, der den Verweis wird auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:  
  
    ```c#  
    public TestDialogWindow2(IVsUIShell uiShell)  
    {  
        shell = uiShell;  
    }  
    ```  
  
6.  In der **OpenDialog.ShowMessageBox** \-Methode, ersetzen Sie den vorhandenen Code durch Folgendes:  
  
    ```c#  
    IVsUIShell uiShell = (IVsUIShell)ServiceProvider.GetService(typeof(SVsUIShell));  
  
    TestDialogWindow2 testDialog2 = new TestDialogWindow2(uiShell);  
    //get the owner of this dialog  
    IntPtr hwnd;  
    uiShell.GetDialogOwnerHwnd(out hwnd);  
    testDialog2.WindowStartupLocation = System.Windows.WindowStartupLocation.CenterOwner;  
    uiShell.EnableModeless(0);  
    try  
    {  
        WindowHelper.ShowModal(testDialog2, hwnd);  
    }  
    finally  
    {  
        // This will take place after the window is closed.  
        uiShell.EnableModeless(1);  
    }  
    ```  
  
7.  Erstellen Sie die Anwendung, und führen Sie sie aus. Auf der **Tools** Menü sollte einen Befehl mit dem Namen **aufrufen öffnen**. Wenn Sie diesen Befehl klicken, sollte das Dialogfeld angezeigt werden.
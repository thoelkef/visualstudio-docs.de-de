---
title: Erstellen und Verwalten von modalen Dialogfeldern | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: dc53145a52d6b902ef1b8d15195df37ee6de0d62
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="creating-and-managing-modal-dialog-boxes"></a>Erstellen und Verwalten von modalen Dialogfeldern
Wenn Sie ein modales Dialogfeld in Visual Studio erstellen, müssen Sie sicherstellen, dass das übergeordnete Fenster des Dialogfelds deaktiviert ist, während das Dialogfeld angezeigt wird und dann das übergeordnete Fenster erneut aktivieren, nachdem Sie das Dialogfeld geschlossen wurde. Wenn Sie dies tun, kann die Fehlermeldung: "Microsoft Visual Studio kann nicht beendet, da ein modales Dialogfeld aktiv ist. Schließen Sie das aktive Dialogfeld, und versuchen Sie es erneut."  
  
 Es gibt zwei Möglichkeiten, dies aus. Die empfohlene Methode ist ein WPF-Dialogfeld wird zum Ableiten von <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, und rufen Sie anschließend <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> um das Dialogfeld anzuzeigen. Wenn Sie so vorgehen, müssen Sie nicht den modalen Zustand des übergeordneten Fensters zu verwalten.  
  
 Wenn das Dialogfeld nicht WPF ist, oder für eine andere Klasse Grund, Sie können nicht abgeleitet werden, die im Dialogfeld aus <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, das übergeordnete Element des Dialogfelds durch den Aufruf erhalten Sie müssen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> und verwalten den modalen Status selbst, der durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> Methode mit einer der Parameter 0 (False) vor dem Anzeigen des Dialogfelds "", und beim Aufrufen der Methode erneut mit einem Parameter 1 (True) nach dem Schließen des Dialogfelds.  
  
## <a name="creating-a-dialog-box-derived-from-dialogwindow"></a>Erstellen eines Dialogfelds DialogWindow abgeleitet  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen **OpenDialogTest** und Hinzufügen eines Menübefehls mit dem Namen **öffnen**. Weitere Informationen hierzu finden Sie unter [erstellen eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Verwenden der <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> -Klasse, müssen Sie Verweise auf die folgenden Assemblys hinzufügen (in der Registerkarte "Framework" die **Verweis hinzufügen** Dialogfeld):  
  
    -   PresentationCore  
  
    -   PresentationFramework  
  
    -   WindowsBase  
  
    -   System.Xaml  
  
3.  In OpenDialog.cs, fügen Sie die folgenden `using` Anweisung:  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    ```  
  
4.  Deklarieren Sie eine Klasse mit dem Namen **TestDialogWindow** abgeleitet, die <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>:  
  
    ```csharp  
    class TestDialogWindow : DialogWindow  
    {. . .}  
    ```  
  
5.  Legen Sie zum Minimieren und Maximieren das Dialogfeld Lage sein, <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> und <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> auf "true":  
  
    ```csharp  
    internal TestDialogWindow()  
    {  
        this.HasMaximizeButton = true;  
        this.HasMinimizeButton = true;  
    }  
    ```  
  
6.  In der **OpenDialog.ShowMessageBox** -Methode, ersetzen Sie den vorhandenen Code durch Folgendes:  
  
    ```csharp  
    TestDialogWindow testDialog = new TestDialogWindow();  
    testDialog.ShowModal();  
    ```  
  
7.  Erstellen Sie die Anwendung, und führen Sie sie aus. Die experimentelle Instanz von Visual Studio sollte angezeigt werden. Auf der **Tools** Menü der experimentellen Instanz daraufhin sollte einen Befehl mit dem Namen **aufrufen öffnen**. Wenn Sie mit diesem Befehl klicken, sehen Sie im Dialogfenster. Sie sollten Lage minimieren und Maximieren des Fensters.  
  
## <a name="creating-and-managing-a-dialog-box-not-derived-from-dialogwindow"></a>Erstellen und verwalten ein Dialogfeld, die nicht von DialogWindow abgeleitet  
  
1.  Bei diesem Verfahren können Sie die **OpenDialogTest** Lösung, die Sie erstellt, in der vorherigen Prozedur, mit der gleichen Assemblyverweisen haben.  
  
2.  Fügen Sie die folgenden `using` Deklarationen:  
  
    ```csharp  
    using System.Windows;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    ```  
  
3.  Erstellen Sie eine Klasse mit dem Namen **TestDialogWindow2** abgeleitet, die <xref:System.Windows.Window>:  
  
    ```csharp  
    class TestDialogWindow2 : Window  
    {. . .}  
    ```  
  
4.  Fügen Sie einen privaten Verweis auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:  
  
    ```  
    private IVsUIShell shell;  
    ```  
  
5.  Fügen Sie einen Konstruktor, die den Verweis in schaltet <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:  
  
    ```csharp  
    public TestDialogWindow2(IVsUIShell uiShell)  
    {  
        shell = uiShell;  
    }  
    ```  
  
6.  In der **OpenDialog.ShowMessageBox** -Methode, ersetzen Sie den vorhandenen Code durch Folgendes:  
  
    ```csharp  
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
  
7.  Erstellen Sie die Anwendung, und führen Sie sie aus. Auf der **Tools** Menü sehen Sie einen Befehl mit dem Namen **aufrufen öffnen**. Wenn Sie mit diesem Befehl klicken, sehen Sie im Dialogfenster.
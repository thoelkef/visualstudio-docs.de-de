---
title: Erstellen und Verwalten von modalen Dialogfeldern | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89c92dad143ab29c34537913335e9b5db31c5be4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54927189"
---
# <a name="create-and-manage-modal-dialog-boxes"></a>Erstellen und Verwalten von modalen Dialogfeldern
Wenn Sie ein modales Dialogfeld in Visual Studio erstellen, müssen Sie sicherstellen, dass das übergeordnete Fenster im Dialogfeld deaktiviert ist, während das Dialogfeld angezeigt wird und anschließend das übergeordnete Fenster erneut aktivieren, nachdem Sie das Dialogfeld geschlossen wurde. Wenn Sie dies nicht tun, können Sie die Fehlermeldung angezeigt: *Microsoft Visual Studio kann nicht heruntergefahren, da ein modales Dialogfeld noch aktiv ist. Schließen Sie das aktive Dialogfeld, und versuchen Sie es erneut.*  
  
 Es gibt zwei Möglichkeiten, dies zu tun. Wenn Sie ein WPF-Dialogfeld, haben wird empfohlen, leiten Sie von <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, und rufen dann <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> um das Dialogfeld anzuzeigen. Wenn Sie dies tun, müssen Sie nicht zum Verwalten des modalen Zustands des übergeordneten Fensters.  
  
 Ist das Dialogfeld nicht WPF oder einem anderen Grund, Sie können nicht abgeleitet werden, das Dialogfeld-Klasse <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>, müssen Sie das übergeordnete Element des Dialogfelds durch den Aufruf erhalten <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> und verwalten den modalen Zustand selbst, der durch den Aufruf der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> -Methode mit einer der Parameter 0 (False), bevor Sie das Dialogfeld anzuzeigen und Aufrufen der Methode erneut mit dem Parameter 1 (True) nach dem Schließen des Dialogfelds.  
  
## <a name="create-a-dialog-box-derived-from-dialogwindow"></a>Erstellen Sie ein Dialogfeld DialogWindow abgeleitet  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen **OpenDialogTest** und Hinzufügen eines Menübefehls mit dem Namen **öffnen (Open)**. Weitere Informationen hierzu finden Sie unter [erstellen Sie eine Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Verwenden der <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> -Klasse, müssen Sie Verweise auf die folgenden Assemblys hinzufügen (in der Registerkarte "Framework" der **Verweis hinzufügen** Dialogfeld):  
  
    -   *PresentationCore*  
  
    -   *PresentationFramework*  
  
    -   *WindowsBase*  
  
    -   *System.Xaml*  
  
3.  In *OpenDialog.cs*, fügen Sie die folgenden `using` Anweisung:  
  
    ```csharp  
    using Microsoft.VisualStudio.PlatformUI;  
    ```  
  
4.  Deklarieren Sie eine Klasse, die mit dem Namen `TestDialogWindow` abgeleitet, die <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>:  
  
    ```csharp  
    class TestDialogWindow : DialogWindow  
    {. . .}  
    ```  
  
5.  Um zu minimieren und Maximieren Sie das Dialogfeld, legen Sie <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> und <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> auf "true":  
  
    ```csharp  
    internal TestDialogWindow()  
    {  
        this.HasMaximizeButton = true;  
        this.HasMinimizeButton = true;  
    }  
    ```  
  
6.  In der `OpenDialog.ShowMessageBox` -Methode, ersetzen Sie den vorhandenen Code durch Folgendes:  
  
    ```csharp  
    TestDialogWindow testDialog = new TestDialogWindow();  
    testDialog.ShowModal();  
    ```  
  
7.  Erstellen Sie die Anwendung, und führen Sie sie aus. Die experimentelle Instanz von Visual Studio sollte angezeigt werden. Auf der **Tools** im Menü der experimentellen Instanz sollte einen Befehl mit dem Namen **aufrufen öffnen (Open)**. Wenn Sie mit diesem Befehl klicken, sollte das Dialogfeld angezeigt werden. Sie sollten in der Lage, zu minimieren und Maximieren Sie das Fenster.  
  
## <a name="create-and-manage-a-dialog-box-not-derived-from-dialogwindow"></a>Erstellen Sie und verwalten Sie ein Dialogfeld, das nicht von DialogWindow abgeleitet  
  
1.  Informationen zu dieser Prozedur können Sie die **OpenDialogTest** Lösung, die Sie erstellt, in der vorherigen Prozedur, mit der gleichen Assemblyverweisen haben.  
  
2.  Fügen Sie die folgenden `using` Deklarationen:  
  
    ```csharp  
    using System.Windows;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    ```  
  
3.  Erstellen Sie eine Klasse, die mit dem Namen `TestDialogWindow2` abgeleitet, die <xref:System.Windows.Window>:  
  
    ```csharp  
    class TestDialogWindow2 : Window  
    {. . .}  
    ```  
  
4.  Fügen Sie einen privaten Verweis um <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:  
  
    ```  
    private IVsUIShell shell;  
    ```  
  
5.  Fügen Sie einen Konstruktor, der den Verweis wird auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>:  
  
    ```csharp  
    public TestDialogWindow2(IVsUIShell uiShell)  
    {  
        shell = uiShell;  
    }  
    ```  
  
6.  In der `OpenDialog.ShowMessageBox` -Methode, ersetzen Sie den vorhandenen Code durch Folgendes:  
  
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
  
7.  Erstellen Sie die Anwendung, und führen Sie sie aus. Auf der **Tools** Menü sollte einen Befehl mit dem Namen **aufrufen öffnen (Open)**. Wenn Sie mit diesem Befehl klicken, sollte das Dialogfeld angezeigt werden.
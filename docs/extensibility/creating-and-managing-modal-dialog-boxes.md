---
title: Erstellen und Verwalten von Modal DialogFeldern | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 786a2fbe2b75c51420668eb1ab6f596213d3da9b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739495"
---
# <a name="create-and-manage-modal-dialog-boxes"></a>Erstellen und Verwalten modaler Dialogfelder
Wenn Sie ein modales Dialogfeld in Visual Studio erstellen, müssen Sie sicherstellen, dass das übergeordnete Fenster des Dialogfelds deaktiviert ist, während das Dialogfeld angezeigt wird, und dann das übergeordnete Fenster nach dem Schließen des Dialogfelds erneut aktivieren. Wenn Sie dies nicht tun, wird möglicherweise die Fehlermeldung angezeigt: Microsoft Visual Studio kann nicht heruntergefahren werden, *da ein modales Dialogfeld aktiv ist. Schließen Sie das aktive Dialogfeld, und versuchen Sie es erneut.*

Es gibt zwei Möglichkeiten, dies zu tun. Wenn Sie über ein WPF-Dialogfeld verfügen, empfiehlt <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>es sich, <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> es von abzuleiten und dann aufzurufen, um das Dialogfeld anzuzeigen. Wenn Sie dies tun, müssen Sie den Modalstatus des übergeordneten Fensters nicht verwalten.

Wenn Ihr Dialogfeld nicht WPF ist, oder aus einem anderen <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>Grund können Sie die Dialogfeldklasse nicht <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> von ableiten, dann müssen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> Sie das übergeordnete Dialogfeld abrufen, indem Sie den Modalstatus selbst aufrufen und verwalten, indem Sie die Methode mit dem Parameter 0 (false) aufrufen, bevor Sie das Dialogfeld anzeigen und die Methode nach dem Schließen des Dialogfelds erneut mit dem Parameter 1 (true) aufrufen.

## <a name="create-a-dialog-box-derived-from-dialogwindow"></a>Erstellen eines aus DialogFenster abgeleiteten Dialogfelds

1. Erstellen Sie ein VSIX-Projekt mit dem Namen **OpenDialogTest,** und fügen Sie einen Menübefehl mit dem Namen **OpenDialog**hinzu. Weitere Informationen hierzu finden Sie unter [Erstellen einer Erweiterung mit einem Menübefehl](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Um die <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> Klasse zu verwenden, müssen Sie Verweise auf die folgenden Assemblys hinzufügen (auf der Registerkarte Framework im Dialogfeld **Referenz hinzufügen):**

    - *PresentationCore*

    - *PresentationFramework*

    - *WindowsBase*

    - *System.Xaml*

3. Fügen *Sie*in `using` OpenDialog.cs die folgende Anweisung hinzu:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    ```

4. Deklarieren `TestDialogWindow` Sie eine Klasse <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>mit dem Namen, die von: ableitet:

    ```csharp
    class TestDialogWindow : DialogWindow
    {. . .}
    ```

5. Um das Dialogfeld zu minimieren und <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> zu maximieren, legen Sie fest und auf true:

    ```csharp
    internal TestDialogWindow()
    {
        this.HasMaximizeButton = true;
        this.HasMinimizeButton = true;
    }
    ```

6. Ersetzen `OpenDialog.ShowMessageBox` Sie in der Methode den vorhandenen Code durch Folgendes:

    ```csharp
    TestDialogWindow testDialog = new TestDialogWindow();
    testDialog.ShowModal();
    ```

7. Erstellen Sie die Anwendung, und führen Sie sie aus. Die experimentelle Instanz von Visual Studio sollte angezeigt werden. Im Menü **Extras** der experimentellen Instanz sollte ein Befehl mit dem Namen **Invoke OpenDialog**angezeigt werden. Wenn Sie auf diesen Befehl klicken, sollte das Dialogfeld angezeigt werden. Sie sollten in der Lage sein, das Fenster zu minimieren und zu maximieren.

## <a name="create-and-manage-a-dialog-box-not-derived-from-dialogwindow"></a>Erstellen und Verwalten eines Dialogfelds, das nicht von DialogWindow abgeleitet ist

1. Für dieses Verfahren können Sie die **OpenDialogTest-Lösung** verwenden, die Sie im vorherigen Verfahren mit denselben Assemblyverweisen erstellt haben.

2. Fügen Sie `using` die folgenden Deklarationen hinzu:

    ```csharp
    using System.Windows;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    ```

3. Erstellen Sie `TestDialogWindow2` eine Klasse mit <xref:System.Windows.Window>dem Namen, die von: ableitet.

    ```csharp
    class TestDialogWindow2 : Window
    {. . .}
    ```

4. Fügen Sie einen <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>privaten Verweis auf:

    ```
    private IVsUIShell shell;
    ```

5. Fügen Sie einen Konstruktor <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>hinzu, der den Verweis auf:

    ```csharp
    public TestDialogWindow2(IVsUIShell uiShell)
    {
        shell = uiShell;
    }
    ```

6. Ersetzen `OpenDialog.ShowMessageBox` Sie in der Methode den vorhandenen Code durch Folgendes:

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

7. Erstellen Sie die Anwendung, und führen Sie sie aus. Im Menü **Extras** sollte ein Befehl mit dem Namen **Invoke OpenDialog**angezeigt werden. Wenn Sie auf diesen Befehl klicken, sollte das Dialogfeld angezeigt werden.

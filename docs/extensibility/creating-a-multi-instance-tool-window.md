---
title: Erstellen eines Toolfensters mit mehreren Instanzen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33585f623f846e16200d430ad2c886fe0874b537
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739626"
---
# <a name="create-a-multi-instance-tool-window"></a>Erstellen eines Toolfensters mit mehreren Instanzen
Sie können ein Toolfenster so programmieren, dass mehrere Instanzen gleichzeitig geöffnet werden können. Standardmäßig kann in Toolfenstern nur eine Instanz geöffnet sein.

Wenn Sie ein Toolfenster mit mehreren Instanzen verwenden, können Sie mehrere verwandte Informationsquellen gleichzeitig anzeigen. Sie können z. B. <xref:System.Windows.Forms.TextBox> ein mehrzeiliges Steuerelement in einem Toolfenster mit mehreren Instanzen speichern, sodass mehrere Codeausschnitte während einer Programmiersitzung gleichzeitig verfügbar sind. Außerdem können Sie z. <xref:System.Windows.Forms.DataGrid> B. ein Steuerelement und ein Dropdown-Listenfeld in einem Toolfenster mit mehreren Instanzen speichern, sodass mehrere Echtzeitdatenquellen gleichzeitig nachverfolgt werden können.

## <a name="create-a-basic-single-instance-tool-window"></a>Erstellen eines einfachen (eininstanzigen) Toolfensters

1. Erstellen Sie ein Projekt mit dem Namen **MultiInstanceToolWindow** mithilfe der VSIX-Vorlage, und fügen Sie eine benutzerdefinierte Vorlagenvorlage für das Toolfenster mit dem Namen **MIToolWindow**hinzu.

    > [!NOTE]
    > Weitere Informationen zum Erstellen einer Erweiterung mit einem Toolfenster finden Sie unter [Erstellen einer Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="make-a-tool-window-multi-instance"></a>Erstellen eines Werkzeugfensters mit mehreren Instanzen

1. Öffnen *MIToolWindowPackage.cs* Sie die MIToolWindowPackage.cs `ProvideToolWindow` Datei, und suchen Sie das Attribut. und `MultiInstances=true` den Parameter, wie im folgenden Beispiel gezeigt:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
        [ProvideMenuResource("Menus.ctmenu", 1)]
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]
        [Guid(MIToolWindowPackage.PackageGuidString)]
        public sealed class MIToolWindowPackage : Package
    {. . .}
    ```

2. Suchen Sie in der `ShowToolWindos()` Datei *MIToolWindowCommand.cs* die Methode. Rufen Sie in <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> dieser Methode `create` die `false` Methode auf, und legen Sie ihr Flag `id` so fest, dass sie durch vorhandene Toolfensterinstanzen iteriert, bis eine verfügbare gefunden wird.

3. Um eine Toolfensterinstanz zu <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> erstellen, `id` rufen Sie die `create` Methode `true`auf, und legen Sie sie auf einen verfügbaren Wert und ihr Flag auf fest.

    Standardmäßig ist `id` `0`der Wert des <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> Parameters der Methode . Dieser Wert macht ein Toolfenster mit einer Instanz. Damit mehr als eine Instanz gehostet werden kann, `id`muss jede Instanz über eine eigene eindeutige Instanz verfügen.

4. Rufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Methode für das <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> Objekt auf, das von der Eigenschaft der Toolfensterinstanz zurückgegeben wird.

5. Standardmäßig erstellt `ShowToolWindow` die Methode, die von der Werkzeugfensterelementvorlage erstellt wird, ein Toolfenster mit einer Instanz. Das folgende Beispiel zeigt, `ShowToolWindow` wie Sie die Methode ändern, um mehrere Instanzen zu erstellen.

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        for (int i = 0; i < 10; i++)
        {
            ToolWindowPane window = this.package.FindToolWindow(typeof(MIToolWindow), i, false);
            if (window == null)
            {
                // Create the window with the first free ID.
                window = (ToolWindowPane)this.package.FindToolWindow(typeof(MIToolWindow), i, true);
                if ((null == window) || (null == window.Frame))
                {
                    throw new NotSupportedException("Cannot create tool window");
                }

            IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());
            break;
            }
        }
    }
    ```

---
title: Erstellen eines Tool Fensters mit mehreren Instanzen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0dcdfe3f6e488514bb2ee1ca950e952b16039b42
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2020
ms.locfileid: "91102525"
---
# <a name="creating-a-multi-instance-tool-window"></a>Erstellen eines Toolfensters mit mehreren Instanzen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können ein Tool Fenster programmieren, sodass mehrere Instanzen von gleichzeitig geöffnet werden können. Standardmäßig kann für Tool Fenster nur eine Instanz geöffnet werden.  
  
 Wenn Sie ein Tool Fenster mit mehreren Instanzen verwenden, können Sie mehrere verwandte Quellen von Informationen gleichzeitig anzeigen. Sie könnten z. b. ein mehrzeilige- <xref:System.Windows.Forms.TextBox> Steuerelement in einem Tool Fenster mit mehreren Instanzen platzieren, damit mehrere Code Ausschnitte gleichzeitig während einer Programmier Sitzung verfügbar sind. Sie können z. b. ein <xref:System.Windows.Forms.DataGrid> -Steuerelement und ein Dropdown-Listenfeld in einem Tool Fenster mit mehreren Instanzen platzieren, damit mehrere Echtzeitdaten Quellen gleichzeitig nachverfolgt werden können.  
  
## <a name="creating-a-basic-single-instance-tool-window"></a>Erstellen eines einfachen Tool Fensters (Einzel Instanz)  
  
1. Erstellen Sie ein Projekt mit dem Namen **multiinstancetoolwindow** mithilfe der VSIX-Vorlage, und fügen Sie eine benutzerdefinierte Tool Fenster-Element Vorlage mit dem Namen **mitoolwindow**hinzu.  
  
    > [!NOTE]
    > Weitere Informationen zum Erstellen einer Erweiterung mit einem Tool Fenster finden Sie unter [Erstellen einer Erweiterung mit einem Tool Fenster](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="making-a-tool-window-multi-instance"></a>Erstellen eines Tool Fensters mit mehreren Instanzen  
  
1. Öffnen Sie die Datei **MIToolWindowPackage.cs** , und suchen Sie nach dem- `ProvideToolWindow` Attribut. und den- `MultiInstances=true` Parameter, wie im folgenden Beispiel gezeigt.  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
        [ProvideMenuResource("Menus.ctmenu", 1)]  
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]  
        [Guid(MIToolWindowPackageGuids.PackageGuidString)]  
        public sealed class MIToolWindowPackage : Package  
    {. . .}  
    ```  
  
2. Suchen Sie in der Datei MIToolWindowCommand.cs die Methode showtoolwindos (). Bei dieser Methode wird die <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> -Methode aufgerufen und das-Flag auf festgelegt, `create` sodass die `false` vorhandenen Tool Fenster Instanzen durchlaufen werden, bis ein verfügbarer `id` gefunden wird.  
  
3. Um eine Tool Fenster Instanz zu erstellen, rufen Sie die <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> -Methode auf, und legen `id` Sie auf einen verfügbaren Wert und dessen- `create` Flag auf fest `true` .  
  
     Standardmäßig ist der Wert des- `id` Parameters der- <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> Methode `0` . Dadurch wird ein Einzel Instanz-Tool Fenster erstellt. Für mehr als eine Instanz, die gehostet werden soll, muss jede Instanz über einen eigenen eindeutigen verfügen `id` .  
  
4. Ruft die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> Methode für das- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Objekt auf, das von der- <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> Eigenschaft der Tool Fenster Instanz zurückgegeben wird.  
  
5. Standardmäßig erstellt die- `ShowToolWindow` Methode, die von der Tool Fenster-Element Vorlage erstellt wird, ein Einzel Instanz-Tool Fenster. Im folgenden Beispiel wird gezeigt, wie Sie die- `ShowToolWindow` Methode ändern, um mehrere-Instanzen zu erstellen.  
  
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

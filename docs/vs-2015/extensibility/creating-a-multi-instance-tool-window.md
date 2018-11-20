---
title: Erstellen eines Toolfensters mit mehreren Instanzen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2dc658024447b433b8bc0b5a8dac59234554509f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51794574"
---
# <a name="creating-a-multi-instance-tool-window"></a>Erstellen eines Toolfensters mit mehreren Instanzen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können ein Toolfenster programmieren, sodass sie mehrere Instanzen gleichzeitig geöffnet sein können. Standardmäßig haben die Toolfenster nur eine Instanz zu öffnen.  
  
 Wenn Sie ein Mehrfachinstanz-Toolfenster verwenden, können Sie mehrere verwandte Informationsquellen zur gleichen Zeit anzeigen. Beispielsweise könnten Sie ein mehrzeiliges einfügen <xref:System.Windows.Forms.TextBox> Steuerelement in einem Toolfenster mit mehreren Instanzen, sodass mehrere Codeausschnitte während einer Sitzung Programmierung gleichzeitig zur Verfügung gestellt werden. Sie könnten auch z. B. Einfügen einer <xref:System.Windows.Forms.DataGrid> Steuerelement und ein Dropdown-Liste im Feld ein Mehrfachinstanz-Toolfenster, damit mehrere Echtzeit-Datenquellen gleichzeitig überwacht werden können.  
  
## <a name="creating-a-basic-single-instance-tool-window"></a>Erstellen eines Toolfensters Basic (Einzelinstanz)  
  
1.  Erstellen Sie ein Projekt mit dem Namen **MultiInstanceToolWindow** mithilfe der VSIX-Projektvorlage aus, und fügen Sie der Elementvorlage ein benutzerdefiniertes Tool-Fenster, der mit dem Namen **MIToolWindow**.  
  
    > [!NOTE]
    >  Weitere Informationen zu eine Erweiterung mit einem Toolfenster erstellen, finden Sie unter [erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="making-a-tool-window-multi-instance"></a>Machen ein Tool-Fenster mit mehreren Instanzen  
  
1.  Öffnen der **MIToolWindowPackage.cs** Datei, und suchen die `ProvideToolWindow` Attribut. und die `MultiInstances=true` Parameter, wie im folgenden Beispiel gezeigt.  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
        [ProvideMenuResource("Menus.ctmenu", 1)]  
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]  
        [Guid(MIToolWindowPackageGuids.PackageGuidString)]  
        public sealed class MIToolWindowPackage : Package  
    {. . .}  
    ```  
  
2.  Suchen Sie in der Datei MIToolWindowCommand.cs die ShowToolWindos()-Methode. Bei dieser Methode rufen die <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> Methode, und legen dessen `create` flag auf `false` , damit sie vorhandene Instanzen der Tool-Fenster erst einen verfügbaren durchlaufen wird `id` gefunden wird.  
  
3.  Rufen Sie zum Erstellen einer Instanz der Tool-Fenster die <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> Methode, und legen seine `id` auf einen verfügbaren Wert und die zugehörige `create` flag auf `true`.  
  
     Standardmäßig wird der Wert des der `id` Parameter der <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> Methode ist `0`. Dadurch wird ein Einzelinstanz-Toolfenster. Für mehr als eine Instanz gehostet werden, jede Instanz müssen eine eigene, eindeutige `id`.  
  
4.  Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> Methode für die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> von zurückgegebene Objekt der <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> Eigenschaft der Tool-Fenster-Instanz.  
  
5.  In der Standardeinstellung die `ShowToolWindow` -Methode, die von der Elementvorlage der Tool-Fenster erstellt wird, erstellt ein Einzelinstanz-Toolfenster. Das folgende Beispiel zeigt die Vorgehensweise beim Ändern der `ShowToolWindow` Methode, um mehrere Instanzen erstellen.  
  
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


---
title: Erstellen ein Toolfenster mit mehreren Instanzen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0cb73a5e5f40d21a5b17faae9602e40f7cd39d48
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-multi-instance-tool-window"></a>Erstellen ein Toolfenster mit mehreren Instanzen
Sie können ein Toolfenster programmieren, sodass mehrere Instanzen gleichzeitig geöffnet sein können. Standardmäßig können Toolfenster nur eine Instanz zu öffnen.  
  
 Wenn Sie ein Toolfenster mit mehreren Instanzen verwenden, können Sie mehrere verwandte Informationsquellen zur gleichen Zeit anzeigen. Sie können z. B. Legen Sie ein mehrzeilige <xref:System.Windows.Forms.TextBox> in einem Toolfenster mit mehreren Instanzen zu steuern, sodass mehrere Codeausschnitte während einer Sitzung Programmierung gleichzeitig zur Verfügung stehen. Sie können auch z. B. einfügen eine <xref:System.Windows.Forms.DataGrid> Steuerung und eine Dropdownliste-Feld in einem Toolfenster mit mehreren Instanzen, damit mehrere Datenquellen in Echtzeit gleichzeitig verfolgt werden können.  
  
## <a name="creating-a-basic-single-instance-tool-window"></a>Erstellen ein Toolfenster Basic (Instanz)  
  
1.  Erstellen Sie ein Projekt mit dem Namen **MultiInstanceToolWindow** die VSIX-Vorlage, und fügen Sie eine Elementvorlage für benutzerdefiniertes Tool-Fenster mit dem Namen **MIToolWindow**.  
  
    > [!NOTE]
    >  Weitere Informationen zum Erstellen von Erweiterung mit einem Toolfenster, finden Sie unter [erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="making-a-tool-window-multi-instance"></a>Erstellen ein Tool-Fenster mit mehreren Instanzen  
  
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
  
2.  Suchen Sie in der Datei MIToolWindowCommand.cs die ShowToolWindos()-Methode. Rufen Sie bei dieser Methode die <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> -Methode, und legen seine `create` flag auf `false` , damit es mit vorhandenen Instanzen von Tool-Fenster erst zur Verfügung durchlaufen wird `id` gefunden wird.  
  
3.  Rufen Sie zum Erstellen einer Instanz des Tool-Fenster die <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> -Methode, und legen seine `id` auf einen verfügbaren Wert und die zugehörige `create` flag auf `true`.  
  
     Wird standardmäßig der Wert von der `id` Parameter von der <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> Methode ist `0`. Dadurch wird ein Einzelinstanz-Toolfenster. Für mehr als eine Instanz gehostet werden, muss jede Instanz eine eigene, eindeutige verfügen `id`.  
  
4.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> Methode auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> von zurückgegebene Objekt der <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> Eigenschaft Tool-Fenster-Instanz.  
  
5.  Wird standardmäßig die `ShowToolWindow` Methode, die von der Elementvorlage des Tool-Fenster erstellt wird, erstellt ein Einzelinstanz-Toolfenster. Das folgende Beispiel zeigt die Vorgehensweise beim Ändern der `ShowToolWindow` Methode, um mehrere Instanzen zu erstellen.  
  
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
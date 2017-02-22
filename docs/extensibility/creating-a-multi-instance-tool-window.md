---
title: "Erstellen eines Toolfensters mit mehreren Instanzen | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "mit mehreren"
  - "Toolfenster"
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Erstellen eines Toolfensters mit mehreren Instanzen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können ein Toolfenster programmieren, so, dass mehrere Instanzen gleichzeitig geöffnet sein können. Standardmäßig können Toolfenster nur einmal geöffnet haben.  
  
 Wenn Sie ein Toolfenster mit mehreren Instanzen verwenden, können Sie mehrere zugehörige Informationsquellen gleichzeitig anzeigen. Sie können beispielsweise eine mehrzeilige einfügen <xref:System.Windows.Forms.TextBox> in einem Toolfenster mit mehreren Instanzen steuern, sodass mehrere Codeausschnitte während einer Sitzung Programmierung gleichzeitig zur Verfügung stehen. Sie können auch z. B. Einfügen einer <xref:System.Windows.Forms.DataGrid> \-Steuerelement und eine Dropdown\-Liste im Feld in einem Toolfenster mit mehreren Instanzen, damit mehrere Datenquellen in Echtzeit gleichzeitig verfolgt werden können.  
  
## Erstellen eines Toolfensters Basic \(Single\-Instance\)  
  
1.  Erstellen Sie ein Projekt mit dem Namen **MultiInstanceToolWindow** mithilfe der VSIX\-Projektvorlage, und fügen Sie eine benutzerdefiniertes Tool Fenster Elementvorlage, die mit dem Namen **MIToolWindow**.  
  
    > [!NOTE]
    >  Weitere Informationen zum Erstellen von einer Erweiterungs mit einem Toolfenster, finden Sie unter [Erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## Erstellen ein Tool\-Fenster mit mehreren Instanzen  
  
1.  Öffnen Sie die **MIToolWindowPackage.cs** Datei, und suchen Sie die `ProvideToolWindow` Attribut. und die `MultiInstances=true` Parameter, wie im folgenden Beispiel gezeigt.  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
        [ProvideMenuResource("Menus.ctmenu", 1)]  
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]  
        [Guid(MIToolWindowPackageGuids.PackageGuidString)]  
        public sealed class MIToolWindowPackage : Package  
    {. . .}  
    ```  
  
2.  Suchen Sie in der Datei MIToolWindowCommand.cs die ShowToolWindos\(\)\-Methode. Rufen Sie in dieser Methode die <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> Methode, und legen seine `create` flag auf `false` damit es vorhandene Instanzen der Tool\-Fenster erst ein verfügbares durchläuft `id` gefunden wird.  
  
3.  Rufen Sie zum Erstellen einer Instanz der Tool\-Fenster die <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> Methode, und legen seine `id` auf einen verfügbaren Wert und die zugehörige `create` flag auf `true`.  
  
     Wird standardmäßig der Wert von der `id` Parameter von der <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> Methode ist `0`. Dadurch wird eine Einzelinstanz\-Toolfenster. Für mehr als eine Instanz gehostet werden, muss jede Instanz eine eigene, eindeutige haben `id`.  
  
4.  Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> Methode auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> \-Objekt, das von zurückgegeben wird die <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> \-Eigenschaft der Tool\-Fenster\-Instanz.  
  
5.  In der Standardeinstellung die `ShowToolWindow` \-Methode, die von der Elementvorlage der Tool\-Fenster erstellt wird eine Einzelinstanz\-Toolfenster erstellt. Das folgende Beispiel zeigt die Vorgehensweise beim Ändern der `ShowToolWindow` Methode zum Erstellen mehrerer Instanzen.  
  
    ```c#  
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
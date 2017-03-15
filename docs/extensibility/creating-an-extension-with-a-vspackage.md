---
title: "Erstellen eine Erweiterung mit einem VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# Erstellen eine Erweiterung mit einem VSPackage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise erfahren Sie, wie erstellen Sie ein VSIX\-Projekt, und fügen ein VSPackage\-Projektelement. Wir verwenden das VSPackage den UI\-Shell\-Dienst abrufen, um ein Meldungsfeld anzuzeigen.  
  
## Erforderliche Komponenten  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Erstellen ein VSPackage  
  
1.  Erstellen Sie ein VSIX\-Projekt namens **FirstPackage**. Sie finden die VSIX\-Projektvorlage in die **Neues Projekt** Dialogfeld unter **Visual c\# \/ Erweiterbarkeit**.  
  
2.  Wenn das Projekt geöffnet wird, fügen Sie Elementvorlage ein Visual Studio\-Paket mit dem Namen **FirstPackage**. In der **Projektmappen\-Explorer**, mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Hinzufügen \/ neues Element**. In der **Neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual c\# \/ Erweiterbarkeit** und wählen Sie **Visual Studio\-Paket**. In den **Namen** Feld am unteren Rand des Fensters, das Ändern der Name der Befehlsdatei an **FirstPackage.cs**.  
  
3.  Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
     Die experimentelle Instanz von Visual Studio wird angezeigt. Weitere Informationen über die experimentelle Instanz finden Sie unter [Die experimentelle Instanz](../extensibility/the-experimental-instance.md).  
  
4.  Öffnen Sie in der experimentellen Instanz den **Extras \/ Erweiterungen und Updates** Fenster. Daraufhin sollte die **FirstPackage** Erweiterung. \(Wenn Sie öffnen **Erweiterungen und Updates** in Ihrer Arbeitsinstanz von Visual Studio, nicht angezeigt **FirstPackage**\).  
  
## Laden das VSPackage  
 Die Erweiterung wird zu diesem Zeitpunkt nicht geladen, da es keine Möglichkeit, die geladen wird. Im Allgemeinen können Sie eine Erweiterung laden, wenn Ihnen die Interaktion mit der Benutzeroberfläche \(durch Klicken auf einen Menübefehl, öffnen ein Toolfenster\) oder durch Angabe, dass das VSPackage in einem bestimmten UI\-Kontext geladen werden soll. Weitere Informationen zum Laden von VSPackages und UI\-Kontexte, finden Sie unter [Laden von VSPackages](../extensibility/loading-vspackages.md). Für diese Vorgehensweise erfahren Sie, wie ein VSPackage geladen, wenn eine Projektmappe geöffnet ist.  
  
1.  Öffnen Sie die Datei FirstPackage.cs. Suchen Sie nach der Deklaration der FirstPackage\-Klasse. Ersetzen Sie die vorhandenen Attribute durch folgenden Code:  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackageGuids.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2.  Fügen Sie eine Nachricht, die ermöglicht es uns wissen, dass das VSPackage geladen wurde. Wir verwenden die Initialize\(\)\-Methode des VSPackage dazu, da Visual Studio\-Dienste erhalten Sie, wenn das VSPackage positioniert wurde. \(Weitere Informationen zum Abrufen von Diensten finden Sie unter [Gewusst wie: Abrufen eines Diensts](../extensibility/how-to-get-a-service.md).\) Ersetzen Sie die Initialize\(\)\-Methode des FirstPackage durch Code, der Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> service, ruft der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> \-Schnittstelle ab und ruft seine <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> Methode.  
  
    ```c#  
    protected override void Initialize()  
    {  
        base.Initialize();  
  
        IVsUIShell uiShell = (IVsUIShell)GetService(typeof(SVsUIShell));  
        Guid clsid = Guid.Empty;  
        int result;  
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(uiShell.ShowMessageBox(  
            0,  
            ref clsid,  
            "FirstPackage",  
             string.Format(CultureInfo.CurrentCulture, "Inside {0}.Initialize()", this.GetType().FullName),  
            string.Empty,  
            0,  
            OLEMSGBUTTON.OLEMSGBUTTON_OK,  
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
            OLEMSGICON.OLEMSGICON_INFO,  
            0,  
            out result));  
    }  
    ```  
  
3.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz angezeigt wird.  
  
4.  Öffnen Sie eine Projektmappe in der experimentellen Instanz ein. Daraufhin sollte ein Meldungsfeld mit der Meldung **erste Paket in Initialize\(\)**.
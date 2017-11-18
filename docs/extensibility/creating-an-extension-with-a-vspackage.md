---
title: Erstellen eine Erweiterung mit einem VSPackage | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cb4ed4767146a07db6a4567768ee9a49fec97667
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="creating-an-extension-with-a-vspackage"></a>Erstellen eine Erweiterung mit einem VSPackage
In dieser exemplarischen Vorgehensweise wird gezeigt, wie ein VSIX-Projekt erstellen, und fügen Sie ein VSPackage-Projektelement hinzu. Den UI-Shell-Dienst abrufen, um ein Meldungsfeld anzuzeigen, verwenden Sie das VSPackage.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-vspackage"></a>Erstellen eines VSPackage  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen **FirstPackage**. Sie finden die VSIX-Projektvorlage in die **neues Projekt** Dialogfeld unter **Visual c# / Erweiterbarkeit**.  
  
2.  Wenn das Projekt geöffnet wird, fügen Sie der Elementvorlage eine Visual Studio-Paket, der mit dem Namen **FirstPackage**. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen / neues Element**. In der **neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual c# / Erweiterbarkeit** , und wählen Sie **Visual Studio-Paket**. In der **Namen** Feld am unteren Rand des Fensters, ändern Sie den Namen der Befehlsdatei an **FirstPackage.cs**.  
  
3.  Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
     Die experimentelle Instanz von Visual Studio wird angezeigt. Weitere Informationen über die experimentelle Instanz finden Sie unter [die experimentelle Instanz](../extensibility/the-experimental-instance.md).  
  
4.  Öffnen Sie in der experimentellen Instanz den **Extras / Erweiterungen und Updates** Fenster. Daraufhin sollte die **FirstPackage** hier Erweiterung. (Wenn Sie öffnen **Erweiterungen und Updates** in Ihrer Arbeit Instanz von Visual Studio, werden Sie nicht angezeigt **FirstPackage**).  
  
## <a name="loading-the-vspackage"></a>Laden das VSPackage  
 Die Erweiterung wird zu diesem Zeitpunkt nicht geladen, da es keine Möglichkeit, die bewirkt, sie zum Laden dass. Sie können eine Erweiterung in der Regel laden, wenn Sie interagieren mit der Benutzeroberfläche (durch Klicken auf einen Menübefehl Öffnen eines Toolfensters) oder aber angeben, dass das VSPackage in einem bestimmten UI-Kontext geladen werden soll. Weitere Informationen über das Laden von VSPackages und UI-Kontexten finden Sie unter [Laden von VSPackages](../extensibility/loading-vspackages.md). Für dieses Verfahren erfahren Sie, wie eine VSPackage geladen, wenn eine Projektmappe geöffnet ist.  
  
1.  Öffnen Sie die FirstPackage.cs-Datei. Suchen Sie nach der Deklaration der FirstPackage-Klasse. Ersetzen Sie die vorhandenen Attribute durch Folgendes:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackageGuids.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2.  Fügen Sie eine Nachricht, mit dem uns wissen, dass das VSPackage geladen wurde. Wir verwenden Initialize()-Methode des VSPackage dazu, da Sie Visual Studio-Dienste abrufen können, erst nach das VSPackage positioniert wurde. (Weitere Informationen zum Abrufen von Diensten finden Sie unter [Vorgehensweise: Abrufen eines Diensts](../extensibility/how-to-get-a-service.md).) Ersetzen Sie die Initialize()-Methode des FirstPackage durch Code, der Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> service, ruft der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> -Schnittstelle, und ruft seine <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> Methode.  
  
    ```csharp  
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
  
4.  Öffnen Sie eine Projektmappe, in der experimentellen Instanz. Daraufhin sollte ein Dialogfeld mit der Meldung **erste Paket innerhalb Initialize()**.
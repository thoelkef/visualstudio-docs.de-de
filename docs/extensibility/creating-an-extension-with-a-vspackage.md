---
title: Erstellen einer Erweiterung mit einem VSPackage | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04a31171b2aca3de8284bb93257c106b80780242
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55040810"
---
# <a name="create-an-extension-with-a-vspackage"></a>Erstellen Sie eine Erweiterung mit einem VSPackage
Diese exemplarische Vorgehensweise erstellen Sie ein VSIX-Projekt, und fügen Sie ein VSPackage-Projekt-Element. Wir verwenden das VSPackage, um der UI-Shell-Dienst zu erhalten, um ein Meldungsfeld anzuzeigen.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [installieren Sie Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-vspackage"></a>Erstellen Sie ein VSPackage  
  
1.  Erstellen Sie ein VSIX-Projekt mit dem Namen **FirstPackage**. Sie finden die VSIX-Projektvorlage in das **neues Projekt** Dialogfeld unter **Visual C#-** > **Erweiterbarkeit**.  
  
2.  Wenn das Projekt geöffnet wird, fügen Sie der Elementvorlage eine Visual Studio-Paket, der mit dem Namen **FirstPackage**. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen** > **neues Element**. In der **neues Element hinzufügen** wechseln Sie zum Dialogfeld **Visual C#-** > **Erweiterbarkeit** , und wählen Sie **Visual Studio-Paket**. In der **Namen** Feld am unteren Rand des Fensters, ändern Sie den Namen der Befehlsdatei an *FirstPackage.cs*.  
  
3.  Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
     Die experimentelle Instanz von Visual Studio wird angezeigt. Weitere Informationen zur experimentellen Instanz finden Sie unter [der experimentellen Instanz](../extensibility/the-experimental-instance.md).  
  
4.  Öffnen Sie in der experimentellen Instanz den **Tools** > **Erweiterungen und Updates** Fenster. Daraufhin sollte die **FirstPackage** Erweiterung. (Wenn Sie öffnen **Erweiterungen und Updates** in Ihrer Arbeitsinstanz von Visual Studio, nicht angezeigt **FirstPackage**).  
  
## <a name="load-the-vspackage"></a>Laden Sie das VSPackage  
 Die Erweiterung wird an diesem Punkt nicht geladen, da es keine Möglichkeit, die geladen wird. Im Allgemeinen können Sie eine Erweiterung laden, wenn Sie interagieren mit der Benutzeroberfläche (durch Klicken auf einen Menübefehl Öffnen eines Toolfensters) oder aber angeben, dass das VSPackage in einem bestimmten UI-Kontext geladen werden soll. Weitere Informationen zum Laden von VSPackages und UI-Kontext finden Sie unter [Laden von VSPackages](../extensibility/loading-vspackages.md). Für dieses Verfahren erfahren Sie, wie Sie eine VSPackage zu laden, wenn eine Projektmappe geöffnet ist.  
  
1.  Öffnen der *FirstPackage.cs* Datei. Suchen Sie nach der Deklaration der `FirstPackage` Klasse. Ersetzen Sie die vorhandenen Attribute durch Folgendes:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackage.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2.  Fügen Sie eine Nachricht, die ermöglicht es uns wissen, dass das VSPackage geladen wurde. Wir verwenden der VSPackages `Initialize()` Methode zu diesem Zweck werden, da Sie mit Visual Studio bekommen Dienste enthält, wenn das VSPackage positioniert wurde. (Weitere Informationen zum Abrufen von Diensten finden Sie unter [Vorgehensweise: Abrufen eines Diensts](../extensibility/how-to-get-a-service.md).) Ersetzen der `Initialize()` -Methode der `FirstPackage` mit Code, der Ruft die <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> Dienst, ruft der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> -Schnittstelle ab und ruft seine <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> Methode.  
  
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
  
4.  Öffnen Sie eine Projektmappe in der experimentellen Instanz ein. Daraufhin sollte ein Dialogfeld mit der Meldung **erste Paket im Initialize()**.
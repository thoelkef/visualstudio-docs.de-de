---
title: Erstellen einer Erweiterung mit einem VSPackage | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ddad7149db75aa662f9427a301c04eaf925146f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197424"
---
# <a name="creating-an-extension-with-a-vspackage"></a>Erstellen einer Erweiterung mit einem VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie ein VSIX-Projekt erstellen und ein VSPackage-Projekt Element hinzufügen. Wir verwenden das VSPackage, um den UI-shelldienst zu erhalten, um ein Meldungs Feld anzuzeigen.  
  
## <a name="prerequisites"></a>Voraussetzungen  
 Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Download Center. Sie ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das vs SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-vspackage"></a>Erstellen eines VSPackages  
  
1. Erstellen Sie ein VSIX-Projekt mit dem Namen **firstpackage**. Sie finden die VSIX-Projektvorlage im Dialogfeld " **Neues Projekt** " unter **Visual c#/Erweiterbarkeit**.  
  
2. Wenn das Projekt geöffnet wird, fügen Sie eine Visual Studio-Paket Element Vorlage mit dem Namen **firstpackage**hinzu. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **Hinzufügen/Neues Element**aus. Navigieren Sie im Dialogfeld **Neues Element hinzufügen** zu **Visual c#/Erweiterbarkeit** , und wählen Sie dann **Visual Studio-Paket**aus. Ändern Sie im Feld **Name** am unteren Rand des Fensters den Namen der Befehlsdatei in **FirstPackage.cs**.  
  
3. Erstellen Sie das Projekt, und starten Sie das Debugging.  
  
     Die experimentelle Instanz von Visual Studio wird angezeigt. Weitere Informationen über die experimentelle Instanz finden Sie in [der experimentellen Instanz](../extensibility/the-experimental-instance.md).  
  
4. Öffnen Sie in der experimentellen Instanz das Fenster Extras **/Erweiterungen und Updates** . Die **firstpackage** -Erweiterung sollte hier angezeigt werden. (Wenn Sie **Erweiterungen und Updates** in ihrer funktionierenden Instanz von Visual Studio öffnen, wird **firstpackage**nicht angezeigt.)  
  
## <a name="loading-the-vspackage"></a>VSPackage wird geladen.  
 An diesem Punkt wird die Erweiterung nicht geladen, da Sie nichts bewirkt, das Sie lädt. Im Allgemeinen können Sie eine Erweiterung laden, wenn Sie mit der Benutzeroberfläche interagieren (Klicken Sie auf einen Menübefehl, öffnen Sie ein Tool Fenster), oder indem Sie angeben, dass das VSPackage in einem bestimmten UI-Kontext geladen werden soll. Weitere Informationen zum Laden von VSPackages und UI-Kontexten finden Sie unter [Laden von VSPackages](../extensibility/loading-vspackages.md). In diesem Verfahren erfahren Sie, wie Sie ein VSPackage laden, wenn eine Projekt Mappe geöffnet ist.  
  
1. Öffnen Sie die Datei FirstPackage.cs. Suchen Sie nach der Deklaration der firstpackage-Klasse. Ersetzen Sie die vorhandenen Attribute durch Folgendes:  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid(FirstPackageGuids.PackageGuidString)]  
    public sealed class FirstPackage : Package  
    ```  
  
2. Fügen wir eine Nachricht hinzu, die uns darüber informiert, dass das VSPackage geladen wurde. Hierfür verwenden wir die Initialize ()-Methode des VSPackages, da Sie Visual Studio-Dienste erst dann erhalten können, nachdem das VSPackage positioniert wurde. (Weitere Informationen zum erhalten von Diensten finden Sie unter Gewusst [wie: erhalten eines Diensts](../extensibility/how-to-get-a-service.md).) Ersetzen Sie die Initialize ()-Methode von firstpackage durch Code, der den Dienst abruft <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> , die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> -Schnittstelle abruft und die zugehörige- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> Methode aufruft.  
  
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
  
3. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz wird geöffnet.  
  
4. Öffnen Sie eine Projekt Mappe in der experimentellen Instanz. Es sollte ein Meldungs Feld mit dem **ersten Paket in Initialize ()** angezeigt werden.

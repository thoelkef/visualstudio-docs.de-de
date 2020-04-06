---
title: Erstellen einer Erweiterung mit einem VSPackage | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: c0cc5e08-4897-44f2-8309-e3478f1f999e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1037ebcc58cc4183e6f02119bc7b46abfc132f52
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739526"
---
# <a name="create-an-extension-with-a-vspackage"></a>Erstellen einer Erweiterung mit einem VSPackage

In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie ein VSIX-Projekt erstellen und ein VSPackage-Projektelement hinzufügen. Wir verwenden das VSPackage, um den UI-Shell-Dienst abzubekommen, um ein Meldungsfeld anzuzeigen.

## <a name="prerequisites"></a>Voraussetzungen

Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-vspackage"></a>Erstellen eines VSPackage

1. Erstellen Sie ein VSIX-Projekt mit dem Namen **FirstPackage**. Die VSIX-Projektvorlage finden Sie im Dialogfeld **Neues Projekt,** indem Sie nach "vsix" suchen.

2. Wenn das Projekt geöffnet wird, fügen Sie eine Visual Studio-Paketelementvorlage mit dem Namen **FirstPackage**hinzu. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie**Neues Element** **hinzufügen** > aus. Wechseln Sie im Dialogfeld **Neues Element hinzufügen** zu Visual **C-Extensibility,** > **Extensibility** und wählen Sie **Visual Studio-Paket aus.** Ändern Sie im Feld **Name** am unteren Rand des Fensters den Befehlsdateinamen in *FirstPackage.cs*.

3. Erstellen Sie das Projekt, und starten Sie das Debugging.

    Die experimentelle Instanz von Visual Studio wird angezeigt. Weitere Informationen zur experimentellen Instanz finden Sie unter [Die experimentelle Instanz](../extensibility/the-experimental-instance.md).

4. Öffnen Sie in der experimentellen Instanz das Fenster **Tools** > **Extensions and Updates.** Sie sollten die **FirstPackage-Erweiterung** hier sehen. (Wenn Sie **Erweiterungen und Updates** in Ihrer Arbeitsinstanz von Visual Studio öffnen, wird **FirstPackage**nicht angezeigt.

## <a name="load-the-vspackage"></a>VSPackage laden

An diesem Punkt wird die Erweiterung nicht geladen, da nichts vorhanden ist, was dazu führt, dass sie geladen wird. Sie können eine Erweiterung im Allgemeinen laden, wenn Sie mit der Benutzeroberfläche interagieren (klicken Sie auf einen Menübefehl, öffnen Eines Toolfensters), oder indem Sie angeben, dass das VSPackage in einem bestimmten UI-Kontext geladen werden soll. Weitere Informationen zum Laden von VSPackages und UI-Kontexten finden Sie unter [Laden von VSPackages](../extensibility/loading-vspackages.md). Für dieses Verfahren zeigen wir Ihnen, wie Sie ein VSPackage laden, wenn eine Lösung geöffnet ist.

1. Öffnen Sie die *FirstPackage.cs* Datei. Suchen Sie nach `FirstPackage` der Deklaration der Klasse. Ersetzen Sie die vorhandenen Attribute durch die folgenden Attribute:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid(FirstPackage.PackageGuidString)]
    public sealed class FirstPackage : Package
    ```

2. Fügen wir eine Nachricht hinzu, die uns mitteilt, dass das VSPackage geladen wurde. Dazu verwenden wir die `Initialize()` VSPackage-Methode, da Sie Visual Studio-Dienste erst abrufen können, nachdem das VSPackage sited erstellt wurde. (Weitere Informationen zum Abrufen von Diensten finden Sie unter [Gewusst wie: Abrufen eines Dienstes](../extensibility/how-to-get-a-service.md).) Ersetzen `Initialize()` Sie `FirstPackage` die Methode von <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> durch Code, der den Dienst abruft, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> Schnittstelle abruft und seine <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ShowMessageBox%2A> Methode aufruft.

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

3. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz wird angezeigt.

4. Öffnen Sie eine Lösung in der experimentellen Instanz. Es sollte ein Meldungsfeld mit der Meldung **First Package Inside Initialize()** angezeigt werden.

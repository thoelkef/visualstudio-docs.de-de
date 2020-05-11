---
title: 'Gewusst wie: Verwenden von AsyncPackage zum Laden von VSPackages im Hintergrund | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: 77690a1947f82f97c4aa12809a80ea61335d216d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710616"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Gewusst wie: Verwenden von AsyncPackage zum Laden von VSPackages im Hintergrund
Das Laden und Initialisieren eines VS-Pakets kann zu Datenträger-E/A führen. Wenn solche E/A-Aktivitäten im UI-Thread auftreten, kann dies zu Reaktionsproblemen führen. Um diesem Problem zu begegnen, hat <xref:Microsoft.VisualStudio.Shell.AsyncPackage> Visual Studio 2015 die Klasse eingeführt, die das Laden von Paketen in einem Hintergrundthread ermöglicht.

## <a name="create-an-asyncpackage"></a>Erstellen eines AsyncPackage
 Sie können zunächst ein VSIX-Projekt erstellen (**Datei** > **neues** > **Project** > **Visual C-Extensibility** > **Extensibility** > **VSIX Project**) und dem Projekt ein VSPackage hinzufügen (Rechtsklick auf das Projekt und **Hinzufügen** > **eines neuen Elements** > **C-Element** > **Extensibility** > Visual Studio**Package**). Anschließend können Sie Ihre Dienste erstellen und diese Dienste zu Ihrem Paket hinzufügen.

1. Leiten Sie das <xref:Microsoft.VisualStudio.Shell.AsyncPackage>Paket von ab.

2. Wenn Sie Dienste bereitstellen, deren Abfragen dazu führen können, dass Ihr Paket geladen wird:

    Um Visual Studio anzuzeigen, dass Ihr Paket für das Laden <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> im Hintergrund sicher ist, und um sich für dieses Verhalten zu entscheiden, sollten Sie die **AllowsBackgroundLoading-Eigenschaft** im Attributkonstruktor auf true setzen.

   ```csharp
   [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]

   ```

    Um Visual Studio anzuzeigen, dass es sicher ist, den Dienst in einem <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> Hintergrundthread zu <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> instanziieren, sollten Sie die Eigenschaft im Konstruktor auf true festlegen.

   ```csharp
   [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]

   ```

3. Wenn Sie über UI-Kontexte laden, sollten Sie **PackageAutoLoadFlags.BackgroundLoad** für den <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> ODER den Wert (0x2) in die Flags angeben, die als Wert für den automatischen Ladeeintrag Ihres Pakets geschrieben wurden.

   ```csharp
   [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]

   ```

4. Wenn Sie asynchrone Initialisierungsarbeiten zu erledigen <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>haben, sollten Sie überschreiben. Entfernen `Initialize()` Sie die von der VSIX-Vorlage bereitgestellte Methode. (Die `Initialize()` Methode in **AsyncPackage** ist versiegelt). Sie können eine <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> der Methoden verwenden, um ihrem Paket asynchrone Dienste hinzuzufügen.

    HINWEIS: Um `base.InitializeAsync()`aufzurufen, können Sie Ihren Quellcode in:

   ```csharp
   await base.InitializeAsync(cancellationToken, progress);
   ```

5. Sie müssen darauf achten, KEINE RPCs (Remote Procedure Call) aus Ihrem asynchronen Initialisierungscode (in **InitializeAsync**) zu erstellen. Diese können auftreten, <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> wenn Sie direkt oder indirekt anrufen.  Wenn Synchronisierungslasten erforderlich sind, <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>blockiert der UI-Thread die Verwendung von . Das Standardblockierungsmodell deaktiviert RPCs. Wenn Sie also versuchen, einen RPC aus Ihren async-Tasks zu verwenden, werden Sie blockiert, wenn der UI-Thread selbst auf das Laden des Pakets wartet. Die allgemeine Alternative besteht darin, den Code bei Bedarf in den <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> UI-Thread zu **marshallen,** indem Sie so etwas wie Joinable Task Factory oder einen anderen Mechanismus verwenden, der keine RPC verwendet.  Verwenden Sie NICHT **ThreadHelper.Generic.Invoke** oder blockieren Sie im Allgemeinen den aufrufenden Thread, der darauf wartet, zum UI-Thread zu gelangen.

    HINWEIS: Sie sollten die Verwendung von `InitializeAsync` **GetService** oder **QueryService** in Ihrer Methode vermeiden. Wenn Sie diese verwenden müssen, müssen Sie zuerst zum UI-Thread wechseln. Die Alternative ist, von Ihrem **AsyncPackage** <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>zu verwenden <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> (durch Umwerfen auf .)

   C-Code: Erstellen eines AsyncPackage:

```csharp
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]
public sealed class TestPackage : AsyncPackage
{
    protected override Task InitializeAsync(System.Threading.CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(SMyTestService), CreateService, true);
        return Task.FromResult<object>(null);
    }
}
```

## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Konvertieren eines vorhandenen VSPackage in AsyncPackage
 Der Großteil der Arbeit ist die gleiche wie das Erstellen eines neuen **AsyncPackage**. Folgen Sie den Schritten 1 bis 5 oben. Sie müssen auch mit den folgenden Empfehlungen besonders vorsichtig sein:

1. Denken Sie `Initialize` daran, die Außerkraftsetzung zu entfernen, die Sie in Ihrem Paket hatten.

2. Deadlocks vermeiden: Es könnten versteckte RPCs in Ihrem Code vorhanden sein. die nun auf einem Hintergrundthread auftreten. Stellen Sie sicher, dass Sie beim Erstellen einer RPC (z. B. **GetService**) entweder (1) zum Hauptthread wechseln oder (2) die asynchrone Version der API verwenden müssen, falls vorhanden (z. B. **GetServiceAsync**).

3. Wechseln Sie nicht zu häufig zwischen Threads. Versuchen Sie, die Arbeit zu lokalisieren, die in einem Hintergrundthread geschehen kann, um die Ladezeit zu reduzieren.

## <a name="querying-services-from-asyncpackage"></a>Abfragen von Diensten aus AsyncPackage
 Je nach Aufrufer kann ein **AsyncPackage** asynchron geladen werden. Beispiel:

- Wenn der Aufrufer **GetService** oder **QueryService** (beide synchrone APIs) oder

- Wenn der Aufrufer **iVsShell::LoadPackage** (oder **IVsShell5::LoadPackageWithContext**) oder

- Die Last wird durch einen UI-Kontext ausgelöst, aber Sie haben nicht angegeben, dass der UI-Kontextmechanismus Sie asynchron laden kann.

  dann wird Ihr Paket synchron geladen.

  Ihr Paket hat immer noch die Möglichkeit (in seiner asynchronen Initialisierungsphase), den UI-Thread zu deaktivieren, obwohl der UI-Thread für den Abschluss dieser Arbeit blockiert wird. Wenn der Aufrufer **IAsyncServiceProvider** verwendet, um asynchron nach Ihrem Dienst zu fragen, wird das Laden und Die Initialisierung asynchron durchgeführt, vorausgesetzt, er blockiert nicht sofort das resultierende Taskobjekt.

  C-Code: So wird der Dienst asynchron abgefragt:

```csharp
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.Shell.Interop;

IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;
```

---
title: 'Gewusst wie: Bereitstellen eines asynchronen Visual Studio-Dienstes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65362e465beec5465903083beca069104a48166b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710768"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Gewusst wie: Bereitstellen eines asynchronen Visual Studio-Dienstes
Wenn Sie einen Dienst abrufen möchten, ohne den UI-Thread zu blockieren, sollten Sie einen asynchronen Dienst erstellen und das Paket in einen Hintergrundthread laden. Zu diesem Zweck können <xref:Microsoft.VisualStudio.Shell.AsyncPackage> Sie <xref:Microsoft.VisualStudio.Shell.Package>eine anstelle eines verwenden und den Dienst mit den speziellen asynchronen Methoden des asynchronen Pakets hinzufügen.

 Informationen zum Bereitstellen synchroner Visual Studio-Dienste finden Sie unter [Gewusst wie: Bereitstellen eines Dienstes](../extensibility/how-to-provide-a-service.md).

## <a name="implement-an-asynchronous-service"></a>Implementieren eines asynchronen Dienstes

1. Erstellen sie ein VSIX-Projekt (**Datei** > **Neues** > **Projekt** > Visual**C-Extensiblity** > **Extensiblity** > **VSIX Project**). Benennen Sie das Projekt **TestAsync**.

2. Fügen Sie dem Projekt ein VSPackage hinzu. Wählen Sie den Projektknoten im **Projektmappen-Explorer** aus, und klicken Sie auf**Neues Element** > **Visual C-Elements** > **Extensibility** > **Visual Studio-Paket** **hinzufügen** > . Benennen Sie diese Datei *TestAsyncPackage.cs*.

3. Ändern Sie in *TestAsyncPackage.cs*das Paket, um es `AsyncPackage` zu erben, anstatt: `Package`

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Zum Implementieren eines Dienstes müssen Sie drei Typen erstellen:

    - Eine Schnittstelle, die den Dienst identifiziert. Viele dieser Schnittstellen sind leer, d. h. sie haben keine Methoden, da sie nur zum Abfragen des Dienstes verwendet werden.

    - Eine Schnittstelle, die die Dienstschnittstelle beschreibt. Diese Schnittstelle enthält die zu implementierenden Methoden.

    - Eine Klasse, die sowohl den Dienst als auch die Dienstschnittstelle implementiert.

5. Das folgende Beispiel zeigt eine sehr grundlegende Implementierung der drei Typen. Der Konstruktor der Dienstklasse muss den Dienstanbieter festlegen. In diesem Beispiel fügen wir den Dienst einfach der Paketcodedatei hinzu.

6. Fügen Sie der Paketdatei Folgendes mithilfe von Direktiven hinzu:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```

7. Hier ist die asynchrone Dienstimplementierung. Beachten Sie, dass Sie den asynchronen Dienstanbieter anstelle des synchronen Dienstanbieters im Konstruktor festlegen müssen:

    ```csharp
    public class TextWriterService : STextWriterService, ITextWriterService
    {
        private IAsyncServiceProvider asyncServiceProvider;

        public TextWriterService(IAsyncServiceProvider provider)
        {
            // constructor should only be used for simple initialization
            // any usage of Visual Studio service, expensive background operations should happen in the
            // asynchronous InitializeAsync method for best performance
            asyncServiceProvider = provider;
        }

        public async Task InitializeAsync(CancellationToken cancellationToken)
        {
            await TaskScheduler.Default;
            // do background operations that involve IO or other async methods

            await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
            // query Visual Studio services on main thread unless they are documented as free threaded explicitly.
            // The reason for this is the final cast to service interface (such as IVsShell) may involve COM operations to add/release references.

            IVsShell vsShell = this.asyncServiceProvider.GetServiceAsync(typeof(SVsShell)) as IVsShell;
            // use Visual Studio services to continue initialization
        }

        public async Task WriteLineAsync(string path, string line)
        {
            StreamWriter writer = new StreamWriter(path);
            await writer.WriteLineAsync(line);
            writer.Close();
        }
    }

    public interface STextWriterService
    {
    }

    public interface ITextWriterService
    {
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);
    }
    ```

## <a name="register-a-service"></a>Registrieren eines Dienstes
 Um einen Dienst zu <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> registrieren, fügen Sie die dem Paket hinzu, das den Dienst bereitstellt. Anders als bei der Registrierung eines synchronen Dienstes müssen Sie sicherstellen, dass sowohl Paket als auch Dienst das asynchrone Laden unterstützen:

- Sie müssen das Feld **AllowsBackgroundLoading** <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> = true zum Hinzufügen hinzufügen, um sicherzustellen, dass das Paket asynchron initialisiert werden kann. Weitere Informationen zu PackageRegistrationAttribute finden Sie unter [Registrieren und Aufheben der Registrierung von VSPackages](../extensibility/registering-and-unregistering-vspackages.md).

- Sie müssen das Feld **IsAsyncQueryable** <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> = true zum Hinzufügen hinzufügen, um sicherzustellen, dass die Dienstinstanz asynchron initialisiert werden kann.

  Hier ist ein `AsyncPackage` Beispiel für eine mit einer asynchronen Dienstregistrierung:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>Hinzufügen eines Diensts

1. Entfernen *Sie in TestAsyncPackage.cs*die `Initialize()` `InitializeAsync()` Methode, und überschreiben Sie die Methode. Fügen Sie den Dienst hinzu, und fügen Sie eine Rückrufmethode zum Erstellen der Dienste hinzu. Hier ist ein Beispiel für den asynchronen Initialisierer, der einen Dienst hinzufügt:

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```
    Um diesen Dienst außerhalb dieses Pakets sichtbar zu machen, legen Sie den Wert "promote flag" als letzten Parameter auf *true* fest:`this.AddService(typeof(STextWriterService), CreateTextWriterService, true);`

2. Hinzufügen eines Verweises auf *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll*.

3. Implementieren Sie die Rückrufmethode als asynchrone Methode, die den Dienst erstellt und zurückgibt.

    ```csharp
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        TextWriterService service = new TextWriterService(this);
        await service.InitializeAsync(cancellationToken);
        return service;
    }

    ```

## <a name="use-a-service"></a>Verwenden eines Dienstes
 Jetzt können Sie den Dienst abrufen und seine Methoden verwenden.

1. Wir zeigen dies im Initialisierungsmodul an, aber Sie können den Dienst überall dort abrufen, wo Sie den Dienst nutzen möchten.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
    }

    ```

     Vergessen Sie nicht, `userpath` zu einem Dateinamen und Pfad zu wechseln, der auf Ihrem Computer sinnvoll ist!

2. Erstellen und ausführen Sie den Code. Wenn die experimentelle Instanz von Visual Studio angezeigt wird, öffnen Sie eine Lösung. Dies `AsyncPackage` bewirkt, dass die autoload. Wenn der Initialisierer ausgeführt wurde, sollten Sie eine Datei an dem angegebenen Speicherort finden.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Verwenden eines asynchronen Dienstes in einem Befehlshandler
 Im Folgenden finden Sie ein Beispiel für die Verwendung eines asynchronen Dienstes in einem Menübefehl. Sie können das hier gezeigte Verfahren verwenden, um den Dienst in anderen nicht asynchronen Methoden zu verwenden.

1. Fügen Sie Ihrem Projekt einen Menübefehl hinzu. (Im **Projektmappen-Explorer**den Projektknoten auswählen, mit der rechten Maustaste klicken und **Neue** > **Elementerweiterbarkeit** > **New Item** > **hinzufügen auswählen.)** Benennen Sie die Befehlsdatei *TestAsyncCommand.cs*.

2. Die benutzerdefinierte Befehlsvorlage `Initialize()` fügt die Methode der *TestAsyncPackage.cs-Datei* erneut hinzu, um den Befehl zu initialisieren. Kopieren `Initialize()` Sie in der Methode die Zeile, die den Befehl initialisiert. Diese sollte wie folgt aussehen:

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     Verschieben Sie diese `InitializeAsync()` Zeile in die Methode in der *AsyncPackageForService.cs* Datei. Da sich dies in einer asynchronen Initialisierung befindet, müssen Sie <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>zum Hauptthread wechseln, bevor Sie den Befehl mithilfe von initialisieren. Dies sollte jetzt wie folgt aussehen:

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;
        
        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");

        await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
        TestAsyncCommand.Initialize(this);
    }

    ```

3. Löschen `Initialize()` Sie die Methode.

4. Suchen Sie in der `MenuItemCallback()` Datei *TestAsyncCommand.cs* die Methode. Löschen Sie den Text der Methode.

5. Hinzufügen einer Using-Direktive:

    ```csharp
    using System.IO;
    ```

6. Fügen Sie eine asynchrone Methode mit dem Namen hinzu, `UseTextWriterAsync()`die den Dienst abruft und seine Methoden verwendet:

    ```csharp
    private async System.Threading.Tasks.Task UseTextWriterAsync()
    {
        // Query text writer service asynchronously to avoid a blocking call.
        ITextWriterService textService =
           await AsyncServiceProvider.GlobalProvider.GetServiceAsync(typeof(STextWriterService))
              as ITextWriterService;

        string userpath = @"C:\MyDir\MyFile.txt";
        await textService.WriteLineAsync(userpath, "this is a test");
       }

    ```

7. Rufen Sie diese `MenuItemCallback()` Methode von der Methode auf:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. Erstellen Sie die Projektmappe, und beginnen Sie mit dem Debuggen. Wenn die experimentelle Instanz von Visual Studio angezeigt wird, wechseln Sie zum Menü **Extras,** und suchen Sie nach dem Menüelement **TestAsyncCommand aufrufen.** Wenn Sie darauf klicken, schreibt der TextWriterService in die von Ihnen angegebene Datei. (Sie müssen keine Lösung öffnen, da das Aufrufen des Befehls auch dazu führt, dass das Paket geladen wird.)

## <a name="see-also"></a>Weitere Informationen
- [Nutzung und Bereitstellung von Dienstleistungen](../extensibility/using-and-providing-services.md)

---
title: 'Vorgehensweise: Geben Sie einen asynchronen Visual Studio-Dienst | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a9a03c4282fb7c2719f0f408759be972ead0f866
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62862939"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Vorgehensweise: Geben Sie einen Dienst für die asynchronen Visual Studio
Sie können zum Abrufen eines Diensts, ohne Blockierung im UI-Thread Sie ein asynchrones Diensts erstellen und Laden Sie das Paket in einem Hintergrundthread. Zu diesem Zweck können Sie eine <xref:Microsoft.VisualStudio.Shell.AsyncPackage> anstelle eines <xref:Microsoft.VisualStudio.Shell.Package>, und fügen Sie den Dienst mit asynchroner Pakets spezielle asynchrone Methoden.

 Weitere Informationen zu synchronen Visual Studio-Dienste bereitstellt, finden Sie unter [Vorgehensweise: Geben Sie einen Dienst](../extensibility/how-to-provide-a-service.md).

## <a name="implement-an-asynchronous-service"></a>Implementieren eines asynchronen Diensts

1. Erstellen Sie ein VSIX-Projekt (**Datei** > **neu** > **Projekt** > **Visual C#-**  >  **Erweiterbarkeit** > **VSIX-Projekt**). Nennen Sie das Projekt **TestAsync**.

2. Fügen Sie ein VSPackage zum Projekt hinzu. Wählen Sie den Projektknoten in der **Projektmappen-Explorer** , und klicken Sie auf **hinzufügen** > **neues Element** > **Visual c#-Elemente**  >  **Erweiterbarkeit** > **Visual Studio-Paket**. Nennen Sie diese Datei *TestAsyncPackage.cs*.

3. In *TestAsyncPackage.cs*, ändern Sie das Paket zu vererben `AsyncPackage` statt `Package`:

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Um einen Dienst zu implementieren, müssen Sie drei Arten erstellen:

    - Eine Schnittstelle, die den Dienst identifiziert. Viele dieser Schnittstellen sind leer, d. h. sie keine Methoden haben, wie sie nur für Abfragen an den Dienst verwendet werden.

    - Eine Schnittstelle, die die Dienstschnittstelle beschreibt. Diese Schnittstelle enthält die Methoden implementiert werden.

    - Eine Klasse, die den Dienst und die Dienstschnittstelle implementiert.

5. Das folgende Beispiel zeigt eine sehr grundlegende Implementierung der drei Typen an. Der Konstruktor der Dienstklasse, muss den Dienstanbieter festgelegt. In diesem Beispiel fügen wir einfach den Dienst der Paket-Codedatei.

6. Fügen Sie die folgenden using-Anweisungen zur-Paketdatei:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```

7. Hier ist die Implementierung des asynchronen. Beachten Sie, dass der Dienst für die asynchrone Anbieter anstelle der synchronen Dienstanbieter im Konstruktor festgelegt werden sollen:

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

            await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
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

## <a name="register-a-service"></a>Registrieren von Diensten
 Um einen Dienst zu registrieren, fügen die <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> auf das Paket, das den Dienst bereitstellt. Anders, wenn einen synchronen Dienst registrieren, müssen Sie sicherstellen, dass sowohl Paket auch der Dienst unterstützt asynchrone Laden:

- Müssen Sie hinzufügen, die **AllowsBackgroundLoading = True** Feld der <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> um sicherzustellen, dass Paket kann weitere Informationen zu den PackageRegistrationAttribute asynchron initialisiert werden, finden Sie unter [registrieren und Aufheben der Registrierung von VSPackages](../extensibility/registering-and-unregistering-vspackages.md).

- Müssen Sie hinzufügen, die **IsAsyncQueryable = True** Feld der <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> um sicherzustellen, dass Dienstinstanz kann asynchron initialisiert werden.

  Hier ist ein Beispiel für eine `AsyncPackage` mit einer asynchronen Service-Registrierung:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="add-a-service"></a>Hinzufügen eines Diensts

1. In *TestAsyncPackage.cs*, entfernen Sie die `Initialize()` -Methode und überschreiben die `InitializeAsync()` Methode. Fügen Sie den Dienst, und fügen Sie eine Rückrufmethode, um die Dienste zu erstellen. Hier ist ein Beispiel für die asynchrone Initialisierung Hinzufügen eines Diensts:

    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }

    ```

2. Hinzufügen eines Verweises auf *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll*.

3. Implementieren Sie die Callback-Methode als asynchrone Methode, die erstellt und gibt den Dienst zurück.

    ```csharp
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        TextWriterService service = new TextWriterService(this);
        await service.InitializeAsync(cancellationToken);
        return service;
    }

    ```

## <a name="use-a-service"></a>Verwenden Sie einen Dienst
 Jetzt können Sie den Dienst abrufen und seine Methoden verwenden.

1. Wir zeigen dies im Initialisierer. allerdings erhalten Sie den Dienst an einer beliebigen Stelle, den Sie den Dienst verwenden möchten.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await textService.WriteLineAsync(<userpath>), "this is a test");
    }

    ```

     Vergessen Sie nicht so ändern Sie  *\<Userpath >* , einen Dateinamen und Pfad, der auf Ihrem Computer sinnvoll.

2. Erstellen Sie und führen Sie den Code. Wenn die experimentelle Instanz von Visual Studio angezeigt wird, öffnen Sie eine Projektmappe aus. Dies bewirkt, dass die `AsyncPackage` Automatisches Laden. Wenn der Initialisierer ausgeführt wurde, sollte eine Datei am Speicherort finden Sie, die Sie angegeben haben.

## <a name="use-an-asynchronous-service-in-a-command-handler"></a>Verwenden eines asynchronen Diensts in einem Befehlshandler
 Hier ist ein Beispiel zur Verwendung eines asynchronen Diensts Menübefehl aus. Sie können den Dienst in anderen nicht asynchrone Methoden verwenden hier angezeigten Prozedur verwenden.

1. Fügen Sie dem Projekt einen Menübefehl hinzu. (In der **Projektmappen-Explorer**, wählen Sie den Projektknoten aus, mit der rechten Maustaste und wählen Sie **hinzufügen** > **neues Element**  >   **Erweiterbarkeit** > **benutzerdefinierten Befehl**.) Benennen Sie die Befehlsdatei *TestAsyncCommand.cs*.

2. Die benutzerdefinierten Befehls-Vorlage erneut fügt die `Initialize()` Methode, um die *TestAsyncPackage.cs* Datei, um den Befehl zu initialisieren. In der `Initialize()` -Methode, kopieren Sie die Zeile, die den Befehl initialisiert. Es sollte wie folgt aussehen:

    ```csharp
    TestAsyncCommand.Initialize(this);
    ```

     Verschieben Sie diese Zeile in der `InitializeAsync()` -Methode in der die *AsyncPackageForService.cs* Datei. Da dies eine asynchrone Initialisierung ist, Sie müssen wechseln, an den primären Thread vor dem Initialisieren Sie den Befehl mit <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Es sollte nun wie folgt aussehen:

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await base.InitializeAsync(cancellationToken, progress);
        this.AddService(typeof(STextWriterService), CreateTextWriterService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await textService.WriteLineAsync((<userpath>, "this is a test");

        await this.JoinableTaskFactory.SwitchToMainThreadAsync(cancellationToken);
        TestAsyncCommand.Initialize(this);
    }

    ```

3. Löschen der `Initialize()` Methode.

4. In der *TestAsyncCommand.cs* Datei, suchen die `MenuItemCallback()` Methode. Löschen Sie den Text der Methode.

5. Fügen Sie eine Using-Anweisung hinzu:

    ```csharp
    using System.IO;
    ```

6. Fügen Sie eine asynchrone Methode, die mit dem Namen `UseTextWriterAsync()`, dem ruft des Diensts und seine Methoden verwendet:

    ```csharp
    private async System.Threading.Tasks.Task UseTextWriterAsync()
    {
        // Query text writer service asynchronously to avoid a blocking call.
        ITextWriterService textService =
           await AsyncServiceProvider.GlobalProvider.GetServiceAsync(typeof(STextWriterService))
              as ITextWriterService;

        // don't forget to change <userpath> to a local path
        await textService.WriteLineAsync((<userpath>),"this is a test");
       }

    ```

7. Rufen Sie diese Methode aus der `MenuItemCallback()` Methode:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        UseTextWriterAsync();
    }

    ```

8. Erstellen Sie die Projektmappe, und beginnen Sie mit dem Debuggen. Wenn die experimentelle Instanz von Visual Studio angezeigt wird, wechseln Sie zu der **Tools** Menü, und suchen Sie nach der **aufrufen TestAsyncCommand** Menüelement. Wenn Sie darauf klicken, schreibt den TextWriterService in die Datei, die Sie angegeben haben. (Sie müssen nicht Öffnen einer Projektmappe, weil die zu ladenden Pakets Aufrufen des Befehls auch verursacht werden.)

## <a name="see-also"></a>Siehe auch
- [Verwenden und Dienste bereitstellen](../extensibility/using-and-providing-services.md)

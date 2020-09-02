---
title: 'Vorgehensweise: Bereitstellen eines asynchronen Dienstanbieter | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0c58b0be10bf10a21b783a48d52806bf769381ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204101"
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Gewusst wie: Bereitstellen eines asynchronen Visual Studio-Diensts
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie einen Dienst abrufen möchten, ohne den UI-Thread zu blockieren, sollten Sie einen asynchronen Dienst erstellen und das Paket in einem Hintergrund Thread laden. Zu diesem Zweck können Sie <xref:Microsoft.VisualStudio.Shell.AsyncPackage> anstelle eines verwenden <xref:Microsoft.VisualStudio.Shell.Package> und den Dienst mit den speziellen asynchronen Methoden des asynchronen Pakets hinzufügen.

 Weitere Informationen zum Bereitstellen synchroner Visual Studio-Dienste finden Sie unter Vorgehens [Weise: Bereitstellen eines Diensts](../extensibility/how-to-provide-a-service.md).

## <a name="implementing-an-asynchronous-service"></a>Implementieren eines asynchronen Dienstanbieter

1. Erstellen Sie ein VSIX-Projekt (**Datei/neu/Projekt/Visual c#/extensiblity/VSIX-Projekt**). Nennen Sie das Projekt **testasync**.

2. Fügen Sie dem Projekt ein VSPackage hinzu. Wählen Sie den Projekt Knoten im **Projektmappen-Explorer** aus, und klicken Sie auf **Hinzufügen/Neues Element/Visual c# Elemente/Erweiterbarkeit/Visual Studio-Paket**. Benennen Sie diese Datei **TestAsyncPackage.cs**.

3. Ändern Sie in TestAsyncPackage.cs das Paket so, dass es von asyncpackage und nicht von Package geerbt wird:

    ```csharp
    public sealed class TestAsyncPackage : AsyncPackage
    ```

4. Um einen Dienst zu implementieren, müssen Sie drei Typen erstellen:

    - Eine Schnittstelle, die den Dienst beschreibt. Viele dieser Schnittstellen sind leer, d. h., Sie haben keine Methoden.

    - Eine Schnittstelle, die die Dienst Schnittstelle beschreibt. Diese Schnittstelle schließt die zu implementierenden Methoden ein.

    - Eine Klasse, die sowohl den Dienst als auch die Dienst Schnittstelle implementiert.

5. Das folgende Beispiel zeigt eine grundlegende Implementierung der drei Typen. Der Konstruktor der Dienstklasse muss den Dienstanbieter festlegen. In diesem Beispiel fügen wir den Dienst einfach der Paket Codedatei hinzu.

6. Fügen Sie der Paketdatei die folgenden using-Anweisungen hinzu:

    ```csharp
    using System.Threading;
    using System.Threading.Tasks;
    using System.Runtime.CompilerServices;
    using System.IO;
    ```

7. Hier ist die asynchrone Dienst Implementierung. Beachten Sie, dass Sie den asynchronen Dienstanbieter anstelle des synchronen Dienstanbieters im Konstruktor festlegen müssen:

    ```
    public class TextWriterService : STextWriterService, ITextWriterService
    {
        private Microsoft.VisualStudio.Shell.IAsyncServiceProvider serviceProvider;
        public TextWriterService(Microsoft.VisualStudio.Shell.IAsyncServiceProvider provider)
        {
            serviceProvider = provider;
        }
        public async System.Threading.Tasks.Task WriteLineAsync(string path, string line)
        {
            StreamWriter writer = new StreamWriter(path);
            await writer.WriteLineAsync(line);
            writer.Close();
        }
        public TaskAwaiter GetAwaiter()
        {
            return new TaskAwaiter();
        }
    }
    public interface STextWriterService
    {
    }
    public interface ITextWriterService
    {
        System.Threading.Tasks.Task WriteLineAsync(string path, string line);
        TaskAwaiter GetAwaiter();
    }
    ```

## <a name="registering-a-service"></a>Registrieren eines Dienstanbieter
 Um einen Dienst zu registrieren, fügen Sie dem Paket, das <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> den Dienst bereitstellt, das hinzu. Es gibt zwei Unterschiede beim Registrieren eines synchronen Dienstanbieter:

- Wenn Sie das Paket Automatisches Laden, müssen Sie dem- <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> Attribut den backgroundload-Wert hinzufügen. Weitere Informationen zum Automatisches Laden von VSPackages finden Sie unter [Laden von VSPackages](../extensibility/loading-vspackages.md).

- Sie müssen das Feld **allowsbackgroundload = true** hinzufügen <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> . Weitere Informationen zu packageregistrationattribute finden Sie unter [registrieren und Aufheben der Registrierung von VSPackages](../extensibility/registering-and-unregistering-vspackages.md).

  Im folgenden finden Sie ein Beispiel für ein asyncpackage mit einer asynchronen Dienst Registrierung:

```csharp
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]
[Guid(TestAsyncPackage.PackageGuidString)]
public sealed class TestAsyncPackage : AsyncPackage
{. . . }
```

## <a name="adding-a-service"></a>Hinzufügen eines Dienstes

1. Entfernen Sie in TestAsyncPackage.cs die `Initialize()` -Methode, und überschreiben Sie die- `InitializeAsync()` Methode. Fügen Sie den Dienst hinzu, und fügen Sie eine Rückruf Methode hinzu, um die Dienste zu erstellen. Im folgenden finden Sie ein Beispiel für den asynchronen Initialisierer, der einen Dienst hinzufügt:

    ```
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(STextWriterService), CreateService);

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

2. Fügen Sie einen Verweis auf Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll hinzu.

3. Implementieren Sie die Rückruf Methode als asynchrone Methode, die den Dienst erstellt und zurückgibt.

    ```csharp
    public async System.Threading.Tasks.Task<object> CreateService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)
    {
        STextWriterService service = null;
        await System.Threading.Tasks.Task.Run(() => {
                    service = new TextWriterService(this);
             });

        return service;
    }

    ```

## <a name="using-a-service"></a>Verwenden eines Dienstanbieter
 Nun können Sie den Dienst erhalten und seine Methoden verwenden.

1. Dies wird im Initialisierer gezeigt, aber Sie können den Dienst überall dort aufrufen, wo Sie den Dienst verwenden möchten.

    ```csharp
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        this.AddService(typeof(STextWriterService), CreateService);

        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await writer.WriteLineAsync(<userpath>), "this is a test");

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

     Vergessen Sie nicht, *\<userpath>* zu einem Dateinamen und einem Pfad zu wechseln, der auf Ihrem Computer sinnvoll ist.

2. Erstellen und Ausführen des Codes. Wenn die experimentelle Instanz von Visual Studio angezeigt wird, öffnen Sie eine Projekt Mappe. Dies bewirkt, dass sich das asyncpackage autoload. Wenn der Initialisierer ausgeführt wurde, sollten Sie eine Datei in dem von Ihnen angegebenen Speicherort finden.

## <a name="using-an-asynchronous-service-in-a-command-handler"></a>Verwenden eines asynchronen Dienstanbieter in einem Befehls Handler
 Im folgenden finden Sie ein Beispiel für die Verwendung eines asynchronen Dienstanbieter in einem Menübefehl. Sie können den hier gezeigten Vorgang verwenden, um den Dienst in anderen nicht asynchronen Methoden zu verwenden.

1. Fügen Sie dem Projekt einen Menübefehl hinzu. (Wählen Sie im **Projektmappen-Explorer**den Projekt Knoten aus, klicken Sie mit der rechten Maustaste, und wählen Sie **Hinzufügen/Neues Element/Erweiterbarkeit/benutzerdefinierter Befehl**aus.) Benennen Sie die Befehlsdatei **TestAsyncCommand.cs.**

2. Die benutzerdefinierte Befehls Vorlage fügt die-Methode der TestAsyncPackage.cs-Datei erneut hinzu, `Initialize()` um den Befehl zu initialisieren. Kopieren Sie in der Initialize ()-Methode die Zeile, in der der Befehl initialisiert wird. Diese sollte wie folgt aussehen:

    ```
    TestAsyncCommand.Initialize(this);
    ```

     Verschieben Sie diese Zeile in die- `InitializeAsync()` Methode in der Datei AsyncPackageForService.cs. Da dies in einer asynchronen Initialisierung vorliegt, müssen Sie zum Haupt Thread wechseln, bevor Sie den Befehl mit initialisieren <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> . Dies sollte jetzt wie folgt aussehen:

    ```csharp

    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
    {
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        TestAsyncCommand.Initialize(this);

        this.AddService(typeof(STextWriterService), CreateService);

        ITextWriterService textService =
           await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;

        await writer.WriteLineAsync((<userpath>, "this is a test");

        await base.InitializeAsync(cancellationToken, progress);
    }

    ```

3. Löschen Sie die- `Initialize()` Methode.

4. Suchen Sie in der Datei TestAsyncCommand.cs die- `MenuItemCallback()` Methode. Löschen Sie den Text der-Methode.

5. Fügen Sie eine Using-Anweisung hinzu:

    ```
    using System.IO;
    ```

6. Fügen Sie eine asynchrone Methode mit dem Namen hinzu `GetAsyncService()` , die den Dienst abruft und seine Methoden verwendet:

    ```csharp
    private async System.Threading.Tasks.Task GetAsyncService()
    {
        ITextWriterService textService =
           this.ServiceProvider.GetService(typeof(STextWriterService))
              as ITextWriterService;
        // don’t forget to change <userpath> to a local path
        await writer.WriteLineAsync((<userpath>),"this is a test");
       }

    ```

7. Diese Methode wird von der- `MenuItemCallback()` Methode aufgerufen:

    ```
    private void MenuItemCallback(object sender, EventArgs e)
    {
        GetAsyncService();
    }

    ```

8. Erstellen Sie die Projektmappe, und beginnen Sie mit dem Debuggen. Wenn die experimentelle Instanz von Visual Studio angezeigt wird, navigieren Sie zum Menü "Extras", und suchen Sie nach **dem Menü Element** " **testasynccommand aufrufen** ". Wenn Sie darauf klicken, schreibt der textschreibdienst in die angegebene Datei. (Sie müssen keine Projekt Mappe öffnen, da das Aufrufen des Befehls auch bewirkt, dass das Paket geladen wird.)

## <a name="see-also"></a>Weitere Informationen
 [Verwenden und Bereitstellen von Diensten](../extensibility/using-and-providing-services.md)

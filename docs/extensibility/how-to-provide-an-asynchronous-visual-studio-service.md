---
title: 'Vorgehensweise: Bereitstellen einen asynchronen Visual Studio-Dienst | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8741779cf96cb970f3ebc4907443b85ced5b80c0
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-provide-an-asynchronous-visual-studio-service"></a>Vorgehensweise: Bereitstellen einen asynchronen Visual Studio-Dienst
Wenn Sie einen Dienst zu erhalten, ohne den Benutzeroberflächenthread zu blockieren möchten, sollten Sie asynchrone-Dienst erstellen und Laden Sie das Paket in einem Hintergrundthread auf. Zu diesem Zweck können Sie eine <xref:Microsoft.VisualStudio.Shell.AsyncPackage> anstelle eines <xref:Microsoft.VisualStudio.Shell.Package>, und fügen Sie den Dienst mit speziellen asynchronen Methoden für das asynchrone Paket hinzu.
  
 Weitere Informationen zu synchronen Visual Studio-Dienste bereitstellt, finden Sie unter [Vorgehensweise: Bereitstellen ein Diensts](../extensibility/how-to-provide-a-service.md).  
  
## <a name="implementing-an-asynchronous-service"></a>Implementieren eines asynchronen Dienstes  
  
1.  Erstellen Sie ein VSIX-Projekt (**Datei > Neu > Projekt > c# > Extensiblity > VSIX-Projekt**). Nennen Sie das Projekt **TestAsync**.  
  
2.  Fügen Sie dem Projekt ein VSPackage hinzu. Wählen Sie den Projektknoten in der **Projektmappen-Explorer** , und klicken Sie auf **hinzufügen > Neues Element > Visual C#-Elemente > Erweiterbarkeit > Visual Studio-Paket**. Nennen Sie diese Datei **TestAsyncPackage.cs**.  
  
3.  In TestAsyncPackage.cs ändern Sie das Paket von AsyncPackage statt Paket erben:  
  
    ```csharp  
    public sealed class TestAsyncPackage : AsyncPackage  
    ```  
  
4.  Um einen Dienst zu implementieren, müssen Sie drei Arten erstellen:  
  
    -   Eine Schnittstelle, die den Dienst identifiziert. Viele dieser Schnittstellen sind leer, d. h. sie keine Methoden aufweisen, da sie nur für Abfragen des Diensts verwendet werden.
  
    -   Eine Schnittstelle, die die Dienstschnittstelle beschreibt. Diese Schnittstelle enthält die Methoden implementiert werden.  
  
    -   Eine Klasse, die den Dienst und die Dienstschnittstelle implementiert.  
  
5.  Das folgende Beispiel zeigt eine sehr grundlegende Implementierung der drei Typen an. Der Konstruktor der Dienstklasse, muss den Dienstanbieter festgelegt. In diesem Beispiel fügen wir gerade den Dienst der Paket-Codedatei.  
  
6.  Fügen Sie die folgenden using-Anweisungen zur-Paketdatei:  
  
    ```csharp  
    using System.Threading;  
    using System.Threading.Tasks;  
    using System.Runtime.CompilerServices;  
    using System.IO;
    using Microsoft.VisualStudio.Threading;
    using IAsyncServiceProvider = Microsoft.VisualStudio.Shell.IAsyncServiceProvider;
    using Task = System.Threading.Tasks.Task;
    ```  
  
7.  Hier ist die asynchrone-Implementierung. Beachten Sie, dass der asynchronen Dienstanbieter statt der synchronen Dienstanbieter im Konstruktor festgelegt werden sollen:  
  
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
  
## <a name="registering-a-service"></a>Registrieren eines Diensts  
 Um einen Dienst zu registrieren, fügen die <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> auf das Paket, das den Dienst bereitstellt. Unterscheiden, wenn einen synchronen Dienst registrieren, müssen Sie sicherstellen, dass sowohl Paket als auch Service unterstützt asynchrone Laden:
  
-   Müssen Sie hinzufügen, die **AllowsBackgroundLoading = "true"** -Feld der <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> damit Paket kann weitere Informationen zu den PackageRegistrationAttribute asynchron initialisiert werden, finden Sie unter [registrieren und Aufheben der Registrierung von VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
-   Müssen Sie hinzufügen, die **IsAsyncQueryable = "true"** -Feld der <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> um sicherzustellen, dass Dienstinstanz asynchron initialisiert werden kann.

 Hier ist ein Beispiel für eine AsyncPackage mit einer asynchronen Service-Registrierung:
  
```csharp  
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]  
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]   
[Guid(TestAsyncPackage.PackageGuidString)]  
public sealed class TestAsyncPackage : AsyncPackage  
{. . . }  
```  
  
## <a name="adding-a-service"></a>Hinzufügen eines Diensts  
  
1.  In TestAsyncPackage.cs, entfernen Sie die `Initialize()` -Methode und überschreiben die `InitializeAsync()` Methode. Fügen Sie den Dienst, und fügen Sie eine Rückrufmethode, um die Dienste zu erstellen. Hier ist ein Beispiel für die asynchrone Initialisierung Hinzufügen eines Diensts:  
  
    ```csharp
    protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);
    }  
  
    ```  
  
2.  Fügen Sie einen Verweis auf Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll.  
  
3.  Implementieren Sie die Rückrufmethode als asynchrone Methode, die erstellt und den Dienst gibt.  
  
    ```csharp  
    public async Task<object> CreateTextWriterService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)  
    {  
        TextWriterService service = new TextWriterService(this);  
        await service.InitializeAsync(cancellationToken);
        return service;
    }  
  
    ```  
  
## <a name="using-a-service"></a>Mithilfe eines Diensts  
 Nun können Sie den Dienst und seine Methoden verwenden.  
  
1.  Wir zeigen dies im Initialisierer allerdings erhalten Sie den Dienst an einer beliebigen Stelle, den Sie den Dienst verwenden möchten.  
  
    ```csharp  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        await base.InitializeAsync(cancellationToken, progress);  
        this.AddService(typeof(STextWriterService), CreateTextWriterService);  
  
        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await textService.WriteLineAsync(<userpath>), "this is a test");  
    }  
  
    ```  
  
     Vergessen Sie nicht so ändern Sie  *\<Userpath >* , einen Dateinamen und Pfad, der auf dem Computer sinnvoll.  
  
2.  Erstellen Sie und führen Sie den Code. Wenn die experimentelle Instanz von Visual Studio angezeigt wird, öffnen Sie eine Projektmappe aus. Dies bewirkt, dass die AsyncPackage auf Autoload. Wenn die Initialisierung ausgeführt wurde, sollten Sie eine Datei am Speicherort suchen, die Sie angegeben haben.  
  
## <a name="using-an-asynchronous-service-in-a-command-handler"></a>Verwenden einen Dienst für die asynchronen in Befehlshandler  
 Hier ist ein Beispiel zum Dienst für die asynchronen in einen Menübefehl zu verwenden. Sie können den Dienst in anderen nicht asynchronen Methoden verwenden hier angezeigten Prozedur verwenden.  
  
1.  Fügen Sie dem Projekt einen Menübefehl hinzu. (In der **Projektmappen-Explorer**, wählen Sie den Projektknoten aus, mit der rechten Maustaste und wählen Sie **hinzufügen / neues Element / Erweiterbarkeit / benutzerdefinierte Befehl**.) Benennen Sie die Befehlsdatei **TestAsyncCommand.cs.**  
  
2.  Die benutzerdefinierte Befehlsvorlage erneut fügt die `Initialize()` Methode, um die TestAsyncPackage.cs-Datei, um den Befehl zu initialisieren. Kopieren Sie die Zeile, die der Befehl initialisiert, in die Initialize()-Methode. Es sollte wie folgt aussehen:  
  
    ```csharp
    TestAsyncCommand.Initialize(this);  
    ```  
  
     Verschieben Sie diese Zeile, sodass die `InitializeAsync()` Methode in der Datei AsyncPackageForService.cs. Da dies in einer asynchronen Initialisierung ist, Sie müssen wechseln, auf den Hauptthread bevor Sie die Verwendung des Befehls initialisiert werden <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Es sollte jetzt wie folgt aussehen:  
  
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
  
3.  Löschen Sie die `Initialize()` Methode.  
  
4.  Suchen Sie in der Datei TestAsyncCommand.cs die `MenuItemCallback()` Methode. Löschen Sie den Text der Methode.  
  
5.  Fügen Sie eine Using-Anweisung hinzu:  
  
    ```csharp 
    using System.IO;  
    ```  
  
6.  Fügen Sie eine asynchrone Methode mit dem Namen `UseTextWriterAsync()`, dem ruft des Diensts und seine Methoden verwendet:  
  
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
  
7.  Rufen Sie diese Methode aus der `MenuItemCallback()` Methode:  
  
    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        UseTextWriterAsync();  
    }  
  
    ```  
  
8.  Erstellen Sie die Projektmappe, und beginnen Sie mit dem Debuggen. Wenn die experimentelle Instanz von Visual Studio angezeigt wird, wechseln Sie zu der **Tools** Menü- und suchen Sie nach der **TestAsyncCommand Aufrufen** Menüelement. Wenn Sie darauf klicken, schreibt der TextWriterService zu der Datei, die Sie angegeben haben. (Sie müssen eine Projektmappe öffnen zu ladenden Pakets Aufrufen des Befehls auch verursacht werden.)  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden und Bereitstellen von Diensten](../extensibility/using-and-providing-services.md)

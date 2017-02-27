---
title: "Gewusst wie: Bereitstellen einen asynchronen Visual Studio-Dienst | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Gewusst wie: Bereitstellen einen asynchronen Visual Studio-Dienst
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie einen Dienst abzurufen, ohne den UI\-Thread blockieren möchten, Sie erstellen einen Dienst für die asynchronen, und Laden Sie das Paket in einem Hintergrundthread. Zu diesem Zweck können Sie ein <xref:Microsoft.VisualStudio.Shell.AsyncPackage> anstelle eines <xref:Microsoft.VisualStudio.Shell.Package>, und fügen Sie den Dienst das asynchrone Paket spezielle asynchrone Methoden  
  
 Informationen zu synchronen Visual Studio\-Dienste bereitstellt, finden Sie unter [Gewusst wie: Bereitstellen ein Diensts](../extensibility/how-to-provide-a-service.md).  
  
## Implementieren eines asynchronen Dienstes  
  
1.  Erstellen Sie ein VSIX\-Projekt \(**Datei auf neu \/ Projekt \/ Visual C\#\-\/ Extensiblity \/ VSIX\-Projekt**\). Nennen Sie das Projekt **TestAsync**.  
  
2.  Fügen Sie ein VSPackage zum Projekt hinzu. Wählen Sie den Projektknoten in der **Projektmappen\-Explorer** und klicken Sie auf **Hinzufügen \/ neues Element \/ Visual C\#\-Elemente \/ Erweiterbarkeit \/ Visual Studio\-Paket**. Nennen Sie diese Datei **TestAsyncPackage.cs**.  
  
3.  In TestAsyncPackage.cs ändern Sie das Paket das Paket, sondern AsyncPackage erben:  
  
    ```c#  
    public sealed class TestAsyncPackage : AsyncPackage  
    ```  
  
4.  Um einen Dienst zu implementieren, müssen Sie drei Arten erstellen:  
  
    -   Eine Schnittstelle, die den Dienst beschreibt. Viele dieser Schnittstellen sind leer, d. h. sie haben keine Methoden.  
  
    -   Eine Schnittstelle, die die Dienstschnittstelle beschreibt. Diese Schnittstelle enthält die Methoden implementiert werden.  
  
    -   Eine Klasse, die den Dienst und die Dienstschnittstelle implementiert.  
  
5.  Das folgende Beispiel zeigt eine einfache Implementierung der drei Typen. Der Konstruktor der Dienstklasse muss den Dienstanbieter festgelegt. In diesem Beispiel fügen wir einfach den Dienst für das Paket Code hinzu.  
  
6.  Fügen Sie die folgende using\-Anweisungen in der Paketdatei:  
  
    ```c#  
    using System.Threading;  
    using System.Threading.Tasks;  
    using System.Runtime.CompilerServices;  
    using System.IO;  
    ```  
  
7.  Hier ist die Dienst für die asynchrone Implementierung. Beachten Sie, dass der asynchronen Dienstanbieter anstelle der synchronen Dienstanbieter im Konstruktor festgelegt werden sollen:  
  
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
  
## Registrieren einen Dienst  
 Um einen Dienst zu registrieren, fügen die <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> auf das Paket, das den Dienst bereitstellt. Es gibt zwei Unterschiede aus der Registrierung eines synchronen:  
  
-   Wenn Sie es sind das Paket, die Sie hinzufügen müssen die <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> BackgroundLoad Wert für das Attribut. Weitere Informationen über das automatische Laden von VSPackages finden Sie unter [Laden von VSPackages](../extensibility/loading-vspackages.md).  
  
-   Sie müssen Hinzufügen der **AllowsBackgroundLoading \= True** Feld der <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>. Weitere Informationen zu den PackageRegistrationAttribute, finden Sie unter [Registrieren und Aufheben der Registrierung von VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Hier ist ein Beispiel für eine AsyncPackage mit einer asynchronen Service\-Registrierung:  
  
```c#  
[ProvideService((typeof(STextWriterService)), IsAsyncQueryable = true)]  
[ProvideAutoLoad(UIContextGuids80.SolutionExists, PackageAutoLoadFlags.BackgroundLoad)]  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]   
[Guid(TestAsyncPackage.PackageGuidString)]  
public sealed class TestAsyncPackage : AsyncPackage  
{. . . }  
```  
  
## Hinzufügen eines Diensts  
  
1.  In TestAsyncPackage.cs, entfernen Sie die `Initialize()` \-Methode und überschreiben die `InitializeAsync()` Methode. Fügen Sie den Dienst, und fügen Sie eine Rückrufmethode, um die Dienste zu erstellen. Hier ist ein Beispiel für die asynchrone Initialisierung Hinzufügen eines Diensts:  
  
    ```  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
2.  Fügen Sie einen Verweis auf Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll hinzu.  
  
3.  Implementieren Sie die Callback\-Methode als asynchrone Methode, die erstellt und den Dienst gibt.  
  
    ```c#  
    public async System.Threading.Tasks.Task<object> CreateService(IAsyncServiceContainer container, CancellationToken cancellationToken, Type serviceType)  
    {  
        STextWriterService service = null;  
        await System.Threading.Tasks.Task.Run(() => {  
                    service = new TextWriterService(this);  
             });  
  
        return service;  
    }  
  
    ```  
  
## Mithilfe eines Diensts  
 Nun können Sie den Dienst und seine Methoden verwenden.  
  
1.  Wir zeigen diese im Initialisierer allerdings erhalten Sie den Dienst an einer beliebigen Stelle des Diensts verwenden möchten.  
  
    ```c#  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await writer.WriteLineAsync(<userpath>), "this is a test");  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
     Vergessen Sie nicht, ändern Sie *\< Userpath \>* um einen Dateinamen und Pfad, die auf Ihrem Computer sinnvoll ist.  
  
2.  Erstellen Sie und führen Sie den Code. Wenn die experimentelle Instanz von Visual Studio angezeigt wird, öffnen Sie eine Projektmappe aus. Dies bewirkt, dass die AsyncPackage Automatisches Laden. Wenn die Initialisierung ausgeführt wurde, sollten Sie eine Datei am Speicherort finden, die Sie angegeben.  
  
## Verwenden einen Dienst für die asynchronen in einen Befehlshandler  
 Hier ist ein Beispiel zur Verwendung eines asynchronen Dienstes Menübefehl. Sie können den Dienst in anderen nicht asynchronen Methoden verwenden hier angezeigten Prozedur verwenden.  
  
1.  Fügen Sie einen Befehl zu Ihrem Projekt hinzu. \(In der **Projektmappen\-Explorer**, wählen Sie den Projektknoten, mit der rechten Maustaste und wählen Sie **Hinzufügen \/ neues Element \/ Erweiterbarkeit \/ Custom Command**.\) Benennen Sie die Datei **TestAsyncCommand.cs.**  
  
2.  Die benutzerdefinierten Vorlage erneut fügt die `Initialize()` Methode, um die Datei TestAsyncPackage.cs, um den Befehl zu initialisieren. Kopieren Sie die Zeile, die mit dem Befehl initialisiert, in der Initialize\(\)\-Methode. Es sollte wie folgt aussehen:  
  
    ```  
    TestAsyncCommand.Initialize(this);  
    ```  
  
     Verschieben dieser Zeile in der `InitializeAsync()` \-Methode in der Datei AsyncPackageForService.cs. Da dies eine asynchrone Initialisierung ist, müssen Sie in Wechseln der Haupt\-Thread vor dem Initialisieren Sie den Befehl mit <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Es sollte nun wie folgt aussehen:  
  
    ```c#  
  
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
  
3.  Löschen Sie die `Initialize()` Methode.  
  
4.  Suchen Sie in der Datei TestAsyncCommand.cs die `MenuItemCallback()` Methode. Löschen Sie den Text der Methode.  
  
5.  Fügen Sie eine using Anweisung:  
  
    ```  
    using System.IO;  
    ```  
  
6.  Fügen Sie eine asynchrone Methode mit dem Namen `GetAsyncService()`, die Ruft den Dienst und seine Methoden verwendet:  
  
    ```c#  
    private async System.Threading.Tasks.Task GetAsyncService()  
    {  
        ITextWriterService textService =   
           this.ServiceProvider.GetService(typeof(STextWriterService))  
              as ITextWriterService;  
        // don’t forget to change <userpath> to a local path  
        await writer.WriteLineAsync((<userpath>),"this is a test");  
       }  
  
    ```  
  
7.  Rufen Sie diese Methode aus der `MenuItemCallback()` Methode:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        GetAsyncService();  
    }  
  
    ```  
  
8.  Erstellen Sie die Projektmappe, und starten Sie das Debuggen. Wenn die experimentelle Instanz von Visual Studio angezeigt wird, wechseln Sie zu der **Tools** Menü und suchen Sie nach der **aufrufen TestAsyncCommand** Menüelement. Wenn Sie darauf klicken, schreibt der TextWriterService zu der Datei, die Sie angegeben haben. \(Sie müssen eine Projektmappe öffnen, da Aufrufen des Befehls das Paket wird geladen.\)  
  
## Siehe auch  
 [Verwendung und Bereitstellung von Diensten](../extensibility/using-and-providing-services.md)
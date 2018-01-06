---
title: 'Vorgehensweise: Bereitstellen einen asynchronen Visual Studio-Dienst | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0448274c-d3d2-4e12-9d11-8aca78a1f3f5
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c13a899e5c678040d6ffe5b1996fd3ee96e9cc09
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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
  
    -   Eine Schnittstelle, die den Dienst beschreibt. Viele dieser Schnittstellen sind leer, d. h., sie haben keine Methoden.  
  
    -   Eine Schnittstelle, die die Dienstschnittstelle beschreibt. Diese Schnittstelle enthält die Methoden implementiert werden.  
  
    -   Eine Klasse, die den Dienst und die Dienstschnittstelle implementiert.  
  
5.  Das folgende Beispiel zeigt eine sehr grundlegende Implementierung der drei Typen an. Der Konstruktor der Dienstklasse, muss den Dienstanbieter festgelegt. In diesem Beispiel fügen wir gerade den Dienst der Paket-Codedatei.  
  
6.  Fügen Sie die folgenden using-Anweisungen zur-Paketdatei:  
  
    ```csharp  
    using System.Threading;  
    using System.Threading.Tasks;  
    using System.Runtime.CompilerServices;  
    using System.IO;  
    ```  
  
7.  Hier ist die asynchrone-Implementierung. Beachten Sie, dass der asynchronen Dienstanbieter statt der synchronen Dienstanbieter im Konstruktor festgelegt werden sollen:  
  
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
  
## <a name="registering-a-service"></a>Registrieren eines Diensts  
 Um einen Dienst zu registrieren, fügen die <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> auf das Paket, das den Dienst bereitstellt. Es gibt zwei Unterschiede beim Registrieren eines synchronen Diensts:  
  
-   Wenn Sie Automatisches Laden sind das Paket, die Sie hinzufügen müssen die <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags> BackgroundLoad-Wert, der das Attribut. Weitere Informationen zu VSPackages Automatisches Laden, finden Sie unter [Laden von VSPackages](../extensibility/loading-vspackages.md).  
  
-   Müssen Sie hinzufügen, die **AllowsBackgroundLoading = "true"** Feld der <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>. Weitere Informationen zu den PackageRegistrationAttribute, finden Sie unter [registrieren und Aufheben der Registrierung von VSPackages](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Hier ist ein Beispiel für eine AsyncPackage mit einer asynchronen dienstregistrierung::  
  
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
  
    ```  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
2.  Fügen Sie einen Verweis auf Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll.  
  
3.  Implementieren Sie die Rückrufmethode als asynchrone Methode, die erstellt und den Dienst gibt.  
  
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
  
## <a name="using-a-service"></a>Mithilfe eines Diensts  
 Nun können Sie den Dienst und seine Methoden verwenden.  
  
1.  Wir zeigen dies im Initialisierer allerdings erhalten Sie den Dienst an einer beliebigen Stelle, den Sie den Dienst verwenden möchten.  
  
    ```csharp  
    protected override async System.Threading.Tasks.Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)  
    {  
        this.AddService(typeof(STextWriterService), CreateService);  
  
        ITextWriterService textService = await this.GetServiceAsync(typeof(STextWriterService)) as ITextWriterService;  
  
        await writer.WriteLineAsync(<userpath>), "this is a test");  
  
        await base.InitializeAsync(cancellationToken, progress);  
    }  
  
    ```  
  
     Vergessen Sie nicht so ändern Sie  *\<Userpath >* , einen Dateinamen und Pfad, der auf dem Computer sinnvoll.  
  
2.  Erstellen Sie und führen Sie den Code. Wenn die experimentelle Instanz von Visual Studio angezeigt wird, öffnen Sie eine Projektmappe aus. Dies bewirkt, dass die AsyncPackage auf Autoload. Wenn die Initialisierung ausgeführt wurde, sollten Sie eine Datei am Speicherort suchen, die Sie angegeben haben.  
  
## <a name="using-an-asynchronous-service-in-a-command-handler"></a>Verwenden einen Dienst für die asynchronen in Befehlshandler  
 Hier ist ein Beispiel zum Dienst für die asynchronen in einen Menübefehl zu verwenden. Sie können den Dienst in anderen nicht asynchronen Methoden verwenden hier angezeigten Prozedur verwenden.  
  
1.  Fügen Sie dem Projekt einen Menübefehl hinzu. (In der **Projektmappen-Explorer**, wählen Sie den Projektknoten aus, mit der rechten Maustaste und wählen Sie **hinzufügen / neues Element / Erweiterbarkeit / benutzerdefinierte Befehl**.) Benennen Sie die Befehlsdatei **TestAsyncCommand.cs.**  
  
2.  Die benutzerdefinierte Befehlsvorlage erneut fügt die `Initialize()` Methode, um die TestAsyncPackage.cs-Datei, um den Befehl zu initialisieren. Kopieren Sie die Zeile, die der Befehl initialisiert, in die Initialize()-Methode. Es sollte wie folgt aussehen:  
  
    ```  
    TestAsyncCommand.Initialize(this);  
    ```  
  
     Verschieben Sie diese Zeile, sodass die `InitializeAsync()` Methode in der Datei AsyncPackageForService.cs. Da dies in einer asynchronen Initialisierung ist, Sie müssen wechseln, auf den Hauptthread bevor Sie die Verwendung des Befehls initialisiert werden <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>. Es sollte jetzt wie folgt aussehen:  
  
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
  
3.  Löschen Sie die `Initialize()` Methode.  
  
4.  Suchen Sie in der Datei TestAsyncCommand.cs die `MenuItemCallback()` Methode. Löschen Sie den Text der Methode.  
  
5.  Fügen Sie eine using Anweisung:  
  
    ```  
    using System.IO;  
    ```  
  
6.  Fügen Sie eine asynchrone Methode mit dem Namen `GetAsyncService()`, dem ruft des Diensts und seine Methoden verwendet:  
  
    ```csharp  
    private async System.Threading.Tasks.Task GetAsyncService()  
    {  
        ITextWriterService textService =   
           this.ServiceProvider.GetService(typeof(STextWriterService))  
              as ITextWriterService;  
        // don't forget to change <userpath> to a local path  
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
  
8.  Erstellen Sie die Projektmappe, und beginnen Sie mit dem Debuggen. Wenn die experimentelle Instanz von Visual Studio angezeigt wird, wechseln Sie zu der **Tools** Menü- und suchen Sie nach der **TestAsyncCommand Aufrufen** Menüelement. Wenn Sie darauf klicken, schreibt der TextWriterService zu der Datei, die Sie angegeben haben. (Sie müssen eine Projektmappe öffnen zu ladenden Pakets Aufrufen des Befehls auch verursacht werden.)  
  
## <a name="see-also"></a>Siehe auch  
 [Verwenden und Bereitstellen von Diensten](../extensibility/using-and-providing-services.md)
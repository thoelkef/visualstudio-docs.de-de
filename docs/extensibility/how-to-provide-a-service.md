---
title: "Gewusst wie: Bereitstellen ein Diensts | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Bereitstellen von Diensten"
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# Gewusst wie: Bereitstellen ein Diensts
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ein VSPackage kann Dienste bereitstellen, die andere VSPackages verwenden können. Um einen Dienst bereitzustellen, muss ein VSPackage registrieren den Dienst mit Visual Studio und den Dienst hinzufügen.  
  
 Die <xref:Microsoft.VisualStudio.Shell.Package> \-Klasse implementiert sowohl <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> und <xref:System.ComponentModel.Design.IServiceContainer>.<xref:System.ComponentModel.Design.IServiceContainer> enthält die Rückrufmethoden bereit, die Dienste nach Bedarf bereitzustellen.  
  
 Weitere Informationen zu Diensten finden Sie unter [Service – Grundlagen](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
>  Wenn Sie ein VSPackage ist entladen wird, wartet auf Visual Studio alle Anfragen für Services, die ein VSPackage übermittelt wurden. Es lässt sich nicht auf neue Anforderungen für diese Dienste aus. Rufen Sie nicht explizit die <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> Methode, um einen Dienst zu widerrufen, beim Entladen.  
  
#### Implementieren eines Diensts  
  
1.  Erstellen Sie ein VSIX\-Projekt \(**Datei auf neu \/ Projekt \/ Visual C\#\-\/ Extensiblity \/ VSIX\-Projekt**\).  
  
2.  Fügen Sie ein VSPackage zum Projekt hinzu. Wählen Sie den Projektknoten in der **Projektmappen\-Explorer** und klicken Sie auf **Hinzufügen \/ neues Element \/ Visual C\#\-Elemente \/ Erweiterbarkeit \/ Visual Studio\-Paket**.  
  
3.  Um einen Dienst zu implementieren, müssen Sie drei Arten erstellen:  
  
    -   Eine Schnittstelle, die den Dienst beschreibt. Viele dieser Schnittstellen sind leer, d. h. sie haben keine Methoden.  
  
    -   Eine Schnittstelle, die die Dienstschnittstelle beschreibt. Diese Schnittstelle enthält die Methoden implementiert werden.  
  
    -   Eine Klasse, die den Dienst und die Dienstschnittstelle implementiert.  
  
     Das folgende Beispiel zeigt eine einfache Implementierung der drei Typen. Der Konstruktor der Dienstklasse muss den Dienstanbieter festgelegt.  
  
    ```c#  
    public class MyService : SMyService, IMyService  
    {  
        private Microsoft.VisualStudio.OLE.Interop.IServiceProvider serviceProvider;  
        private string myString;  
        public MyService(Microsoft.VisualStudio.OLE.Interop.IServiceProvider sp)  
        {  
            Trace.WriteLine(  
                   "Constructing a new instance of MyService");  
            serviceProvider = sp;  
        }  
        public void Hello()  
        {  
            myString = "hello";  
        }  
        public string Goodbye()  
        {  
           return "goodbye";  
        }  
    }  
    public interface SMyService  
    {  
    }  
    public interface IMyService  
    {  
        void Hello();  
        string Goodbye();  
    }  
  
    ```  
  
### Registrieren einen Dienst  
  
1.  Um einen Dienst zu registrieren, fügen die <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> die VSPackage, das den Dienst bereitstellt. Es folgt ein Beispiel:  
  
    ```c#  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     Dieses Attribut registriert `SMyService` mit Visual Studio.  
  
    > [!NOTE]
    >  Verwenden, um einen Dienst zu registrieren, die ein anderer Dienst mit dem gleichen Namen ersetzt die <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>. Beachten Sie die nur eine Überschreibung der Dienst ist zulässig.  
  
### Hinzufügen eines Diensts  
  
1.  1.	Klicken Sie in der Initialisierer VSPackage fügen Sie den Dienst hinzu, und fügen Sie eine Rückrufmethode, um die Dienste zu erstellen. Hier wird die Änderung an der <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode:  
  
    ```c#  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2.  Implementieren Sie die Rückrufmethode sollte erstellen und den Dienst, oder null, wenn sie erstellt werden kann.  
  
    ```  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Visual Studio kann eine Anforderung zur Bereitstellung eines Dienstes zurückgewiesen werden. Dies geschieht, wenn eine andere VSPackage bereits den Dienst bereitstellt.  
  
3.  Nun können Sie den Dienst und seine Methoden verwenden. Wir zeigen diese im Initialisierer allerdings erhalten Sie den Dienst an einer beliebigen Stelle des Diensts verwenden möchten.  
  
    ```c#  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
  
        MyService myService = (MyService) this.GetService(typeof(SMyService));  
        myService.Hello();  
        string helloString = myService.myString;  
  
        base.Initialize();  
    }  
    ```  
  
     Der Wert der `helloString` sollte "Hello".  
  
## Siehe auch  
 [Gewusst wie: Abrufen eines Diensts](../extensibility/how-to-get-a-service.md)   
 [Verwendung und Bereitstellung von Diensten](../extensibility/using-and-providing-services.md)   
 [Service – Grundlagen](../extensibility/internals/service-essentials.md)
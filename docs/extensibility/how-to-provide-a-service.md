---
title: 'Vorgehensweise: Bereitstellen ein Diensts | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 70d16085bc6cbc7f01a991a1eca731b8abed2b0f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-provide-a-service"></a>Vorgehensweise: Bereitstellen ein Diensts
Eine VSPackage kann Dienste bereitstellen, die anderen VSPackages verwenden können. Um einen Dienst zu gewährleisten, muss eine VSPackage registrieren den Dienst mit Visual Studio und fügen Sie den Dienst hinzu.  
  
 Die <xref:Microsoft.VisualStudio.Shell.Package> Klasse implementiert beide <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> und <xref:System.ComponentModel.Design.IServiceContainer>. <xref:System.ComponentModel.Design.IServiceContainer> enthält die Rückrufmethoden, die Dienste nach Bedarf bereitstellen.  
  
 Weitere Informationen zu Diensten finden Sie unter [Dienst Essentials](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
>  Wenn eine VSPackage ist, entladen werden soll, wartet auf Visual Studio alle Anforderungen für Dienste, die eine VSPackage übermittelt wurden. Sie können neue Anforderungen für diese Dienste lässt nicht zu. Rufen Sie nicht explizit die <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> Methode, um einen Dienst zu widerrufen, beim Entladen.  
  
#### <a name="implementing-a-service"></a>Implementieren eines Diensts  
  
1.  Erstellen Sie ein VSIX-Projekt (**Datei > Neu > Projekt > c# > Erweiterbarkeit > VSIX-Projekt**).  
  
2.  Fügen Sie dem Projekt ein VSPackage hinzu. Wählen Sie den Projektknoten in der **Projektmappen-Explorer** , und klicken Sie auf **hinzufügen > Neues Element > Visual C#-Elemente > Erweiterbarkeit > Visual Studio-Paket**.  
  
3.  Um einen Dienst zu implementieren, müssen Sie drei Arten erstellen:  
  
    -   Eine Schnittstelle, die den Dienst beschreibt. Viele dieser Schnittstellen sind leer, d. h., sie haben keine Methoden.  
  
    -   Eine Schnittstelle, die die Dienstschnittstelle beschreibt. Diese Schnittstelle enthält die Methoden implementiert werden.  
  
    -   Eine Klasse, die den Dienst und die Dienstschnittstelle implementiert.  
  
     Das folgende Beispiel zeigt eine grundlegende Implementierung der drei Typen an. Der Konstruktor der Dienstklasse, muss den Dienstanbieter festgelegt.  
  
    ```csharp  
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
  
### <a name="registering-a-service"></a>Registrieren eines Diensts  
  
1.  Um einen Dienst zu registrieren, fügen die <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> für das VSPackage, das den Dienst bereitstellt. Im Folgenden ein Beispiel:  
  
    ```csharp  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     Dieses Attribut registriert `SMyService` mit Visual Studio.  
  
    > [!NOTE]
    >  Um einen Dienst zu registrieren, die einen anderen Dienst mit dem gleichen Namen ersetzt, verwenden die <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>. Beachten Sie die nur eine Überschreibung der ein Dienst zulässig ist.  
  
### <a name="adding-a-service"></a>Hinzufügen eines Diensts  
  
1.  Klicken Sie im Initialisierer VSPackage fügen Sie den Dienst, und fügen Sie eine Rückrufmethode, um die Dienste zu erstellen. Hier wird die Änderung auf die <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2.  Implementieren Sie die Rückrufmethode, die sollten erstellen und Zurückgeben des Diensts oder null, wenn sie nicht erstellt werden kann.  
  
    ```csharp  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new MyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Visual Studio kann eine Anforderung zum Bereitstellen eines Diensts ablehnen. Dies geschieht, wenn einem anderen VSPackage bereits den Dienst bereitstellt.  
  
3.  Nun können Sie den Dienst und seine Methoden verwenden. Das folgende Beispiel zeigt die Verwendung des Diensts im Initialisierer, aber Sie erhalten den Dienst an einer beliebigen Stelle, den Sie den Dienst verwenden möchten.  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
  
        MyService myService = (MyService) this.GetService(typeof(SMyService));  
        myService.Hello();  
        string helloString = myService.Goodbye();  
  
        base.Initialize();  
    }  
    ```  
  
     Der Wert des `helloString` sollte "Hello" sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Abrufen eines Diensts](../extensibility/how-to-get-a-service.md)   
 [Verwenden und die Bereitstellung von Diensten](../extensibility/using-and-providing-services.md)   
 [Dienstgrundlagen](../extensibility/internals/service-essentials.md)

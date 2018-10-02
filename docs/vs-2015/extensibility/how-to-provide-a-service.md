---
title: 'Vorgehensweise: Bereitstellen ein Diensts | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 18cb5c28ab70b652b860d76fc6b7ad92e7262bf5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524641"
---
# <a name="how-to-provide-a-service"></a>Vorgehensweise: Bereitstellen ein Diensts
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Bereitstellen ein Diensts](https://docs.microsoft.com/visualstudio/extensibility/how-to-provide-a-service).  
  
Eine VSPackage kann Dienste bereitstellen, die anderen VSPackages verwenden können. Um einen Dienst bereitstellen zu können, muss eine VSPackage registrieren den Dienst mit Visual Studio, und fügen Sie den Dienst.  
  
 Die <xref:Microsoft.VisualStudio.Shell.Package> -Klasse implementiert beide <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> und <xref:System.ComponentModel.Design.IServiceContainer>. <xref:System.ComponentModel.Design.IServiceContainer> enthält die Rückrufmethoden, die Dienste nach Bedarf bereitstellen.  
  
 Weitere Informationen zu Diensten finden Sie unter [Dienstgrundlagen](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
>  Wenn eine VSPackage ist entladen wird, wartet Visual Studio, bis alle Anforderungen für Dienste, die ein VSPackage bereitstellt übermittelt wurden. Neue Anforderungen für diese Dienste ist nicht zulässig. Rufen Sie nicht explizit die <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> Methode, um einen Dienst zu widerrufen, beim Entladen.  
  
#### <a name="implementing-a-service"></a>Implementieren eines Diensts  
  
1.  Erstellen Sie ein VSIX-Projekt (**Datei / neu / Projekt / Visual c# / Erweiterbarkeit / VSIX-Projekt**).  
  
2.  Fügen Sie ein VSPackage zum Projekt hinzu. Wählen Sie den Projektknoten in der **Projektmappen-Explorer** , und klicken Sie auf **hinzufügen / neues Element / Visual c#-Elemente / Erweiterbarkeit / Visual Studio-Paket**.  
  
3.  Um einen Dienst zu implementieren, müssen Sie drei Arten erstellen:  
  
    -   Eine Schnittstelle, die den Dienst beschreibt. Viele dieser Schnittstellen sind leer, d. h., sie haben keine Methoden.  
  
    -   Eine Schnittstelle, die die Dienstschnittstelle beschreibt. Diese Schnittstelle enthält die Methoden implementiert werden.  
  
    -   Eine Klasse, die den Dienst und die Dienstschnittstelle implementiert.  
  
     Das folgende Beispiel zeigt eine sehr grundlegende Implementierung der drei Typen an. Der Konstruktor der Dienstklasse, muss den Dienstanbieter festgelegt.  
  
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
    >  Verwenden, um einen Dienst zu registrieren, die einen anderen Dienst mit dem gleichen Namen ersetzt, die <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>. Beachten Sie, nur eine außer Kraft setzen eines Diensts ist zulässig.  
  
### <a name="adding-a-service"></a>Hinzufügen eines Diensts  
  
1.  1.  Klicken Sie in der VSPackage-Initialisierer fügen Sie den Dienst, und fügen Sie eine Rückrufmethode, um die Dienste zu erstellen. Hier ist die Änderung an der <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2.  Implementieren Sie die Callback-Methode, die sollte erstellen und Zurückgeben des Diensts oder null, wenn sie nicht erstellt werden kann.  
  
    ```  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    >  Visual Studio kann eine Anforderung zur Bereitstellung eines Diensts ablehnen. Dies geschieht, wenn einem anderen VSPackage bereits den Dienst bereitstellt.  
  
3.  Jetzt können Sie den Dienst abrufen und seine Methoden verwenden. Wir zeigen dies im Initialisierer. allerdings erhalten Sie den Dienst an einer beliebigen Stelle, den Sie den Dienst verwenden möchten.  
  
    ```csharp  
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
  
     Der Wert des `helloString` sollte "Hello" sein.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Abrufen eines Diensts](../extensibility/how-to-get-a-service.md)   
 [Verwenden und Bereitstellen von Diensten](../extensibility/using-and-providing-services.md)   
 [Dienstgrundlagen](../extensibility/internals/service-essentials.md)


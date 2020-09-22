---
title: 'Vorgehensweise: Bereitstellen eines Dienstanbieter | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 565a8a91797c826b6419dc5a8488d7d3baf9cddc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841020"
---
# <a name="how-to-provide-a-service"></a>Gewusst wie: Bereitstellen eines Diensts
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein VSPackage kann Dienste bereitstellen, die andere VSPackages verwenden können. Um einen Dienst bereitzustellen, muss ein VSPackage den Dienst bei Visual Studio registrieren und den Dienst hinzufügen.  
  
 Die <xref:Microsoft.VisualStudio.Shell.Package> -Klasse implementiert sowohl <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> als auch <xref:System.ComponentModel.Design.IServiceContainer> . <xref:System.ComponentModel.Design.IServiceContainer> enthält Rückruf Methoden, die Dienste Bedarfs gesteuert bereitstellen.  
  
 Weitere Informationen zu Diensten finden Sie unter [Service Essentials](../extensibility/internals/service-essentials.md) .  
  
> [!NOTE]
> Wenn ein VSPackage entladen wird, wartet Visual Studio, bis alle Anforderungen von Diensten, die ein VSPackage bereitstellt, übermittelt wurden. Es sind keine neuen Anforderungen für diese Dienste zulässig. Die-Methode sollte nicht explizit aufgerufen werden <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> , um einen Dienst beim Entladen aufzuheben.  
  
#### <a name="implementing-a-service"></a>Implementieren eines Dienstanbieter  
  
1. Erstellen Sie ein VSIX-Projekt (**Datei/neu/Projekt/Visual c#/extensiblity/VSIX-Projekt**).  
  
2. Fügen Sie dem Projekt ein VSPackage hinzu. Wählen Sie den Projekt Knoten im **Projektmappen-Explorer** aus, und klicken Sie auf **Hinzufügen/Neues Element/Visual c# Elemente/Erweiterbarkeit/Visual Studio-Paket**.  
  
3. Um einen Dienst zu implementieren, müssen Sie drei Typen erstellen:  
  
   - Eine Schnittstelle, die den Dienst beschreibt. Viele dieser Schnittstellen sind leer, d. h., Sie haben keine Methoden.  
  
   - Eine Schnittstelle, die die Dienst Schnittstelle beschreibt. Diese Schnittstelle schließt die zu implementierenden Methoden ein.  
  
   - Eine Klasse, die sowohl den Dienst als auch die Dienst Schnittstelle implementiert.  
  
     Das folgende Beispiel zeigt eine grundlegende Implementierung der drei Typen. Der Konstruktor der Dienstklasse muss den Dienstanbieter festlegen.  
  
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
  
### <a name="registering-a-service"></a>Registrieren eines Dienstanbieter  
  
1. Um einen Dienst zu registrieren, fügen Sie dem <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> VSPackage hinzu, das den Dienst bereitstellt. Beispiel:  
  
    ```csharp  
    [ProvideService(typeof(SMyService))]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [Guid(VSPackage1.PackageGuidString)]  
    public sealed class VSPackage1 : Package  
    {. . . }  
    ```  
  
     Dieses Attribut wird `SMyService` bei Visual Studio registriert.  
  
    > [!NOTE]
    > Verwenden Sie zum Registrieren eines Dienstanbieter, der einen anderen Dienst mit demselben Namen ersetzt <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> . Beachten Sie, dass nur eine außer Kraft Setzung eines Dienes zulässig ist.  
  
### <a name="adding-a-service"></a>Hinzufügen eines Dienstes  
  
1. 1.  Fügen Sie im VSPackage-Initialisierer den Dienst hinzu, und fügen Sie eine Rückruf Methode hinzu, um die Dienste zu erstellen. Im folgenden finden Sie die Änderung an der- <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);  
  
        ((IServiceContainer)this).AddService(typeof(SMyService), callback);  
    . . .  
    }  
    ```  
  
2. Implementieren Sie die Rückruf Methode, die den Dienst erstellen und zurückgeben soll, oder NULL, wenn er nicht erstellt werden kann.  
  
    ```  
    private object CreateService(IServiceContainer container, Type serviceType)  
    {  
        if (typeof(SMyService) == serviceType)  
            return new SMyService(this);  
        return null;  
    }  
    ```  
  
    > [!NOTE]
    > Visual Studio kann eine Anforderung zur Bereitstellung eines dienstanzverweigerungs ablehnen. Dies geschieht, wenn der Dienst bereits von einem anderen VSPackage bereitstellt wird.  
  
3. Nun können Sie den Dienst erhalten und seine Methoden verwenden. Dies wird im Initialisierer gezeigt, aber Sie können den Dienst überall dort aufrufen, wo Sie den Dienst verwenden möchten.  
  
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
  
     Der Wert von `helloString` sollte "Hello" lauten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Vorgehensweise: erhalten eines Dienstanbieter](../extensibility/how-to-get-a-service.md)   
 [Verwenden von und Bereitstellen von Diensten](../extensibility/using-and-providing-services.md)   
 [Dienstgrundlagen](../extensibility/internals/service-essentials.md)

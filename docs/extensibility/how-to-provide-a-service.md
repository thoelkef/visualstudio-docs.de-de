---
title: 'Gewusst wie: Bereitstellen eines Dienstes | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, providing
ms.assetid: 12bc1f12-47b1-44f6-b8db-862aa88d50d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60cae5e8048a0234114e1f9e7d97728e26ee40f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710772"
---
# <a name="how-to-provide-a-service"></a>Gewusst wie: Bereitstellen eines Dienstes
Ein VSPackage kann Dienste bereitstellen, die andere VSPackages verwenden können. Um einen Dienst bereitzustellen, muss ein VSPackage den Dienst bei Visual Studio registrieren und den Dienst hinzufügen.

 Die <xref:Microsoft.VisualStudio.Shell.Package> Klasse implementiert <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> <xref:System.ComponentModel.Design.IServiceContainer>sowohl und . <xref:System.ComponentModel.Design.IServiceContainer>enthält Rückrufmethoden, die Dienste bei Bedarf bereitstellen.

 Weitere Informationen zu Diensten finden Sie unter [Service essentials](../extensibility/internals/service-essentials.md) .

> [!NOTE]
> Wenn ein VSPackage entladen werden soll, wartet Visual Studio, bis alle Anforderungen für Dienste, die ein VSPackage bereitstellt, übermittelt wurden. Neue Anforderungen für diese Dienste sind nicht zulässig. Sie sollten die <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService.RevokeService%2A> Methode zum Widerrufen eines Dienstes beim Entladen nicht explizit aufrufen.

## <a name="implement-a-service"></a>Implementieren eines Dienstes

1. Erstellen sie ein VSIX-Projekt (**Datei** > **Neues** > **Projekt** > Visual**C-Extensibility** > **Extensibility** > **VSIX Project**).

2. Fügen Sie dem Projekt ein VSPackage hinzu. Wählen Sie den Projektknoten im **Projektmappen-Explorer** aus, und klicken Sie auf**Neues Element** > **Visual C-Elements** > **Extensibility** > **Visual Studio-Paket** **hinzufügen** > .

3. Zum Implementieren eines Dienstes müssen Sie drei Typen erstellen:

   - Eine Schnittstelle, die den Dienst beschreibt. Viele dieser Schnittstellen sind leer, d. h. sie haben keine Methoden.

   - Eine Schnittstelle, die die Dienstschnittstelle beschreibt. Diese Schnittstelle enthält die zu implementierenden Methoden.

   - Eine Klasse, die sowohl den Dienst als auch die Dienstschnittstelle implementiert.

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

### <a name="register-a-service"></a>Registrieren eines Dienstes

1. Um einen Dienst zu <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> registrieren, fügen Sie die dem VSPackage hinzu, das den Dienst bereitstellt. Beispiel:

    ```csharp
    [ProvideService(typeof(SMyService))]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [Guid(VSPackage1.PackageGuidString)]
    public sealed class VSPackage1 : Package
    {. . . }
    ```

     Dieses Attribut `SMyService` wird bei Visual Studio registriert.

    > [!NOTE]
    > Um einen Dienst zu registrieren, der einen anderen <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute>Dienst mit demselben Namen ersetzt, verwenden Sie die . Beachten Sie, dass nur eine Außerkraftsetzung eines Dienstes zulässig ist.

### <a name="add-a-service"></a>Hinzufügen eines Diensts

1. Fügen Sie im VSPackage-Initialisierungsmodul den Dienst hinzu, und fügen Sie eine Rückrufmethode zum Erstellen der Dienste hinzu. Hier ist die Änderung <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> an der Methode zu machen:

    ```csharp
    protected override void Initialize()
    {
        ServiceCreatorCallback callback =new ServiceCreatorCallback(CreateService);

        ((IServiceContainer)this).AddService(typeof(SMyService), callback);
    . . .
    }
    ```

2. Implementieren Sie die Rückrufmethode, die den Dienst erstellen und zurückgeben soll, oder NULL, wenn er nicht erstellt werden kann.

    ```csharp
    private object CreateService(IServiceContainer container, Type serviceType)
    {
        if (typeof(SMyService) == serviceType)
            return new MyService(this);
        return null;
    }
    ```

    > [!NOTE]
    > Visual Studio kann eine Anforderung zum Bereitstellen eines Dienstes ablehnen. Dies geschieht, wenn ein anderes VSPackage den Dienst bereits bereitstellt.

3. Jetzt können Sie den Dienst abrufen und seine Methoden verwenden. Das folgende Beispiel zeigt die Verwendung des Dienstes im Initialisierer, aber Sie können den Dienst überall dort abrufen, wo Sie den Dienst verwenden möchten.

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

     Der Wert `helloString` von sollte "Hallo" sein.

## <a name="see-also"></a>Weitere Informationen
- [Gewusst wie: Holen Sie sich einen Service](../extensibility/how-to-get-a-service.md)
- [Nutzung und Bereitstellung von Dienstleistungen](../extensibility/using-and-providing-services.md)
- [Service-Essentials](../extensibility/internals/service-essentials.md)

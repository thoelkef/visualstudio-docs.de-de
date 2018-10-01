---
title: 'Vorgehensweise: Verwenden von AsyncPackage zum Laden von VSPackages im Hintergrund | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
caps.latest.revision: 9
ms.author: gregvanl
ms.openlocfilehash: 5c37ba734da58b1681f2eb70c106bd9cdac7c89b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516368"
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Vorgehensweise: Verwenden von AsyncPackage zum Laden von VSPackages im Hintergrund
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Verwenden von AsyncPackage zum Laden von VSPackages im Hintergrund](https://docs.microsoft.com/visualstudio/extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background).  
  
Laden und initialisieren ein Visual Studio-Paket können auf dem Datenträger-e/a führen. Wenn diese e/a im UI-Thread auftritt, kann es zu Probleme mit der Reaktionsfähigkeit führen. Um dieses Problem zu beheben, Visual Studio 2015 eingeführt, die <xref:Microsoft.VisualStudio.Shell.AsyncPackage> Klasse, die das Laden des Pakets in einem Hintergrundthread ermöglicht.  
  
## <a name="creating-an-asyncpackage"></a>Erstellen einer von AsyncPackage  
 Sie können zunächst erstellen ein VSIX-Projekt (**Datei / neu / Project / Visual C#-/ Erweiterbarkeit / VSIX-Projekt**) und dem Projekt eine VSPackage hinzugefügt (klicken Sie mit der rechten Maustaste auf das Projekt und **hinzufügen/neues Element / C#-Element/Erweiterungen/Visual Studio-Paket**). Sie können dann Ihre Dienste zu erstellen und diese Dienste zu Ihrem Paket hinzufügen.  
  
1.  Leiten Sie das Paket von <xref:Microsoft.VisualStudio.Shell.AsyncPackage>.  
  
2.  Wenn Sie Dienste bereitstellen, deren Abfragen zum Laden des Pakets verursachen:  
  
     Visual Studio an, dass Ihr Paket für das Laden im Hintergrund sicher ist und zum Aktivieren dieses Verhaltens, Ihre <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> sollte festgelegt **AllowsBackgroundLoading** Eigenschaft auf "true" in den Attributkonstruktor.  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
    ```  
  
     Um zu Visual Studio anzugeben, dass es sicher ist, Ihren Dienst in einem Hintergrundthread zu instanziieren, sollten Sie festlegen der <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> Eigenschaft auf "true", in der <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> Konstruktor.  
  
    ```csharp  
    [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
    ```  
  
3.  Wenn Sie über die Benutzeroberfläche-Kontexte geladen werden, geben Sie **PackageAutoLoadFlags.BackgroundLoad** für die <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> oder der Wert (0 x 2) in die Flags, die als den Wert des Eintrags für Ihres Pakets automatisch laden geschrieben.  
  
    ```csharp  
    [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
    ```  
  
4.  Wenn Sie asynchrone Initialisierung arbeiten durchführen müssen, sollten Sie überschreiben <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>. Entfernen Sie die **Initialize()** Methode, die durch die VSIX-Vorlage bereitgestellt. (Die **Initialize()** -Methode in der **von AsyncPackage** ist versiegelt). Können Sie eines der <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> Methoden, um asynchrone Dienste zu Ihrem Paket hinzuzufügen.  
  
     Hinweis: Zum Aufrufen **Basis. Initializeasync()"**, Sie können Ihren Quellcode zu ändern:  
  
    ```csharp  
    await base.InitializeAsync(cancellationToken, progress);  
    ```  
  
5.  Sie müssen peinlich RPCs (Entfernen von Procedure Call) nicht Stellen aus Ihrem Code für die asynchrone Initialisierung (in **"initializeasync"**). Dies können auftreten, wenn Sie aufrufen <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> direkt oder indirekt.  Bei der Synchronisierung lädt erforderlich sind, der UI-Thread blockiert mit <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>. Das Standardmodell für blockierende deaktiviert RPCs. Dies bedeutet, dass wenn Sie versuchen, einen RPC aus Ihrem asynchrone Aufgaben zu verwenden, Sie ein deadlock hervorruft, wenn der UI-Thread selbst die darauf warten, bis Ihr Paket geladen wird. Die allgemeine Alternative besteht darin, Code, um den UI-Thread zu marshallen, falls erforderlich, z. B. **beigetreten Aufgabenfactory**des <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> oder eines anderen Mechanismus, der keine RPC verwendet.  Verwenden Sie keine **ThreadHelper.Generic.Invoke** oder in der Regel blockiert den aufrufenden Thread, die darauf warten, um den UI-Thread zu erhalten.  
  
     Hinweis: Vermeiden Sie die Verwendung **"GetService"** oder **QueryService** in Ihre **"initializeasync"** Methode. Wenn Sie diese Komponenten verwenden müssen, müssen Sie zunächst zum UI-Thread zu wechseln. Die Alternative ist die Verwendung <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> aus Ihrem **von AsyncPackage** (durch umwandeln, damit <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>.)  
  
 C#: Erstellen einer von AsyncPackage:  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]       
[ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]   
public sealed class TestPackage : AsyncPackage   
{   
    protected override Task InitializeAsync(System.Threading.CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)   
    {               
        this.AddService(typeof(SMyTestService), CreateService, true);   
        return Task.FromResult<object>(null);   
    }   
}  
```  
  
## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Konvertieren Sie einen vorhandenen VSPackage in von AsyncPackage  
 Der Großteil der Arbeit entspricht dem Erstellen eines neuen **von AsyncPackage**. Sie müssen die Schritte 1 bis 5. Außerdem müssen Sie besondere Vorsicht für Folgendes ausführen:  
  
1.  Denken Sie daran, entfernen Sie die **initialisieren** außer Kraft setzen, die Sie in Ihrem Paket haben.  
  
2.  Vermeiden von Deadlocks: möglicherweise ausgeblendet RPCs in Ihrem Code die jetzt in einem Hintergrundthread ausgeführt. Sie müssen sicherstellen, dass wenn Sie RPC vornehmen (z. B. **"GetService"**), müssen Sie entweder (1) wechseln, an den primären Thread oder (2) verwenden die asynchrone Version der API eine vorhanden ist (z. B. **GetServiceAsync**).  
  
3.  Wechseln Sie nicht zwischen den Threads zu häufig. Versuchen Sie es, um die Arbeit zu lokalisieren, die in einem Hintergrundthread auftreten können. Dies reduziert die Ladezeit.  
  
## <a name="querying-services-from-asyncpackage"></a>Abfragen von Diensten von AsyncPackage  
 Ein **von AsyncPackage** kann oder möglicherweise je nach den Aufrufer nicht asynchron geladen. Zum Beispiel  
  
-   Wenn der Aufrufer aufgerufen **"GetService"** oder **QueryService** (sowohl synchrone APIs) oder  
  
-   Wenn der Aufrufer aufgerufen **IVsShell::LoadPackage** (oder **IVsShell5::LoadPackageWithContext**) oder  
  
-   Die Last durch einen UI-Kontext ausgelöst wird, aber Sie haben nicht angegeben, dass der UI-Kontext-Mechanismus Sie asynchron laden können  
  
 das Paket wird dann synchron geladen.  
  
 Beachten Sie, dass Ihr Paket noch Gelegenheit (in die asynchrone Initialisierung-Phase) Aufgaben des UI-Threads, obwohl für die Arbeit der Fertigstellung der UI-Thread blockiert wird. Wenn der Aufrufer verwendet **IAsyncServiceProvider** asynchron Abfrage für den Dienst klicken Sie dann die auslastungs- und die Initialisierung erfolgt asynchron vorausgesetzt, sie nicht sofort im resultierenden Aufgabenobjekt blockieren.  
  
 C#: Gewusst wie: Dienst asynchron abgefragt:  
  
```csharp  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await ayncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```


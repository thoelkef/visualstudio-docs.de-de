---
title: 'Vorgehensweise: Verwenden von AsyncPackage VSPackages im Hintergrund geladen | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.technology: vs-ide-sdk
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
ms.workload:
- vssdk
ms.openlocfilehash: 97f21f75020e77cf6780fa71c21eae827940d9ec
ms.sourcegitcommit: 342e5ec5cec4d07864d65379c2add5cec247f3d6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/27/2018
---
# <a name="how-to-use-asyncpackage-to-load-vspackages-in-the-background"></a>Vorgehensweise: Verwenden von AsyncPackage VSPackages im Hintergrund geladen
Laden und initialisieren ein Visual Studio-Paket können im Datenträger-e/a führen. Wenn solche e/a auf den UI-Thread auftritt, kann dies auf Probleme mit der Reaktionsfähigkeit führen. Um dieses Problem zu beheben, Visual Studio 2015 eingeführt der <xref:Microsoft.VisualStudio.Shell.AsyncPackage> Klasse, die das Laden des Pakets in einem Hintergrundthread ermöglicht.  
  
## <a name="creating-an-asyncpackage"></a>Erstellen eine AsyncPackage  
 Starten, erstellen ein VSIX-Projekt (**Datei > Neu > Projekt > Visual c# > Erweiterbarkeit > VSIX-Projekt**) und das Projekt eine VSPackage hinzufügen (klicken Sie mit der rechten Maustaste auf das Projekt und **hinzufügen/neues Element / C#-Element / Studio-Paket Extensibility/Visual**). Sie können dann Ihre Dienste erstellen und diese Dienste zu Ihrem Paket hinzufügen.  
  
1.  Leiten Sie das Paket von <xref:Microsoft.VisualStudio.Shell.AsyncPackage>.  
  
2.  Wenn Sie Dienste bereitstellen, deren Abfragen zum Laden des Pakets verursachen:  
  
     Visual Studio an, dass Ihr Paket für das Laden im Hintergrund sicher ist und zum Abonnieren dieses Verhalten Ihrer <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> sollte festgelegt **AllowsBackgroundLoading** Eigenschaft auf "true" in den Attributkonstruktor.  
  
    ```csharp  
    [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
    ```  
  
     Um zu Visual Studio anzugeben, dass es sich bei Ihrem Dienst in einem Hintergrundthread instanziiert werden kann, sollten Sie festlegen der <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> Eigenschaft auf "true" in der <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> Konstruktor.  
  
    ```csharp  
    [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
    ```  
  
3.  Wenn Sie über die Benutzeroberfläche Kontexte geladen werden, geben Sie **PackageAutoLoadFlags.BackgroundLoad** für die <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> oder der Wert (0 x 2) in die Flags geschrieben, als der Wert des Eintrags für Ihr Paket automatisch geladen.  
  
    ```csharp  
    [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
    ```  
  
4.  Wenn Sie die asynchrone Initialisierungsvorgänge ausführen müssen, sollten Sie überschreiben <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>. Entfernen Sie die **Initialize()** Methode, die durch die VSIX-Vorlage bereitgestellt. (Die **Initialize()** Methode im **AsyncPackage** ist versiegelt). Sie können keines der <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> Methoden zum Hinzufügen von asynchronen Dienste zu Ihrem Paket.  
  
     Hinweis: Zum Aufrufen **Basis. InitializeAsync()**, Sie können den Quellcode zu ändern:  
  
    ```csharp  
    await base.InitializeAsync(cancellationToken, progress);  
    ```  
  
5.  Sie müssen darauf achten RPCs (Remote Procedure Call) nicht zu Code asynchrone Initialisierung (in **InitializeAsync**). Dies können auftreten, wenn Sie aufrufen <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> direkt oder indirekt.  Bei der Synchronisierung lädt erforderlich sind, im UI-Thread blockiert mit <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>. Das Standardmodell blockierende deaktiviert RPCs. Dies bedeutet, dass wenn Sie versuchen, einen RPC über die asynchrone Aufgaben zu verwenden, Sie ein deadlock hervorruft, wenn im UI-Thread selbst zum Laden des Pakets gewartet wird. Die allgemeine Alternative besteht darin, den Code zum UI-Thread zu marshallen, etwa über bei Bedarf **beigetreten Aufgabenfactory**des <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> oder eines anderen Mechanismus, der keine RPC verwendet.  Verwenden Sie keine **ThreadHelper.Generic.Invoke** oder in der Regel blockiert den aufrufenden Thread darauf warten, um die UI-Thread zu erhalten.  
  
     Hinweis: Vermeiden Sie **GetService** oder **"QueryService"** in Ihrer **InitializeAsync** Methode. Wenn Sie diese verwenden, müssen Sie zuerst an den UI-Thread zu wechseln. Die Alternative ist die Verwendung <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> aus Ihrer **AsyncPackage** (durch Umwandlung es <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>.)  
  
 C#-: Erstellen einer AsyncPackage:  
  
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
  
## <a name="convert-an-existing-vspackage-to-asyncpackage"></a>Konvertieren eines vorhandenen VSPackages zu AsyncPackage  
 Der Großteil der Arbeit entspricht dem Erstellen eines neuen **AsyncPackage**. Sie müssen die Schritte 1 bis 5. Sie müssen auch die folgenden zusätzlichen Vorsicht schalten:  
  
1.  Denken Sie daran, entfernen Sie die **initialisieren** überschreiben Sie im Paket hatten.  
  
2.  Vermeiden von Deadlocks: Es ist möglicherweise ausgeblendet RPCs im Code die jetzt in einem Hintergrundthread eintreten. Sie müssen sicherstellen, dass wenn Sie RPC ausführen möchten (z. B. **GetService**), müssen Sie entweder (1) Switch auf den Hauptthread oder (2) verwenden Sie die asynchrone Version der API, sofern vorhanden ist (z. B. **GetServiceAsync**).  
  
3.  Nicht zwischen Threads zu häufig gewechselt. Versuchen Sie, die Arbeit zu lokalisieren, die in einem Hintergrundthread auftreten können. Dies reduziert die Ladezeit.  
  
## <a name="querying-services-from-asyncpackage"></a>Abfragen von Diensten aus AsyncPackage  
 Ein **AsyncPackage** kann oder möglicherweise je nach den Aufrufer nicht asynchron geladen. Zum Beispiel  
  
-   Wenn der Aufrufer aufgerufen **GetService** oder **"QueryService"** (beide synchrone APIs) oder  
  
-   Wenn der Aufrufer aufgerufen **IVsShell::LoadPackage** (oder **IVsShell5::LoadPackageWithContext**) oder  
  
-   Die Auslastung wird durch eine Benutzeroberflächenkontext ausgelöst, aber Sie haben nicht angegeben, dass der Kontext benutzeroberflächenmechanismus Sie asynchron geladen werden können  
  
 Ihr Paket lädt dann synchron.  
  
 Beachten Sie, dass Ihr Paket noch Gelegenheit besitzt (in seiner asynchrone Initialisierungsphase) zum Deaktivieren der UI-Thread, funktionieren jedoch auf den Abschluss dieser Arbeit im UI-Thread blockiert wird. Wenn der Aufrufer verwendet **IAsyncServiceProvider** abzufragende asynchron für den Dienst, klicken Sie dann die auslastungs- und die Initialisierung erfolgt asynchron vorausgesetzt, sie nicht sofort auf das resultierende Aufgabenobjekt blockieren.  
  
 C#-: Gewusst wie: Dienst asynchron abzufragen:  
  
```csharp  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await asyncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```
  

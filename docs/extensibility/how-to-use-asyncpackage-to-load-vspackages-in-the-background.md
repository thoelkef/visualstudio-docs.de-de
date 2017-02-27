---
title: "Gewusst wie: Verwenden von AsyncPackage VSPackages im Hintergrund geladen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dedf0173-197e-4258-ae5a-807eb3abc952
caps.latest.revision: 8
ms.author: "gregvanl"
caps.handback.revision: 8
---
# Gewusst wie: Verwenden von AsyncPackage VSPackages im Hintergrund geladen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Laden und initialisieren ein Visual Studio\-Paket können im Datenträger\-e\/a führen. Wenn diese e\/a auf den UI\-Thread auftritt, kann es zu Reaktionsfähigkeit Problemen führen. Um dieses Problem zu beheben, Visual Studio 2015 eingeführt, die <xref:Microsoft.VisualStudio.Shell.AsyncPackage> \-Klasse, die das Laden des Pakets in einem Hintergrundthread ermöglicht.  
  
## Erstellen einer AsyncPackage  
 Sie können zunächst erstellen ein VSIX\-Projekt \(**Datei \/ neuer \/ Project \/ Visual c\# \/ Erweiterbarkeit \/ VSIX\-Projekt**\) und dem Projekt ein VSPackage hinzugefügt \(klicken Sie mit der rechten Maustaste auf das Projekt und **Hinzufügen\/neues Element \/ C\#\-Element\/Erweiterbarkeit\/Visual Studio\-Paket**\). Sie können Ihre Dienste zu erstellen und diese Dienste dem Paket hinzufügen.  
  
1.  Leiten Sie das Paket von <xref:Microsoft.VisualStudio.Shell.AsyncPackage>.  
  
2.  Wenn Sie Dienste bereitstellen, deren Abfragen zum Laden des Pakets verursachen:  
  
     Visual Studio an, dass das Paket für das Laden im Hintergrund sicher ist und in dieses Verhalten deaktivieren Ihrer <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> fest **AllowsBackgroundLoading** Eigenschaft auf "true" in den Konstruktor des Attributs.  
  
    ```c#  
    [PackageRegistration(UseManagedResourcesOnly = true, AllowsBackgroundLoading = true)]  
  
    ```  
  
     Um Visual Studio zu verdeutlichen, dass es sicher ist, den Dienst auf einem Hintergrundthread zu instanziieren ist, sollten Sie festlegen der <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttributeBase.IsAsyncQueryable%2A> Eigenschaft auf "true" in der <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> Konstruktor.  
  
    ```c#  
    [ProvideService(typeof(SMyTestService), IsAsyncQueryable = true)]  
  
    ```  
  
3.  Wenn Sie über die Benutzeroberflächen\-Kontexte laden, geben Sie **PackageAutoLoadFlags.BackgroundLoad** für die <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> oder der Wert \(0 x 2\) in den Flags geschrieben, als der Wert des Eintrags für das Paket automatisch geladen.  
  
    ```c#  
    [ProvideAutoLoad(UIContextGuid, PackageAutoLoadFlags.BackgroundLoad)]  
  
    ```  
  
4.  Wenn Sie asynchrone Initialisierungsarbeit haben, sollten Sie überschreiben <xref:Microsoft.VisualStudio.Shell.AsyncPackage.InitializeAsync%2A>. Entfernen Sie die **Initialize\(\)** Methode, die durch die VSIX\-Vorlage bereitgestellt. \(Die **Initialize\(\)** \-Methode in **AsyncPackage** ist versiegelt\). Verwenden Sie eines der <xref:Microsoft.VisualStudio.Shell.AsyncPackage.AddService%2A> Methoden, um asynchrone Dienste zu Ihrem Paket hinzuzufügen.  
  
     Hinweis: Zum Aufrufen von **Basis. InitializeAsync\(\)**, Sie können den Quellcode zu ändern:  
  
    ```c#  
    await base.InitializeAsync(cancellationToken, progress);  
    ```  
  
5.  Achten Sie bei RPCs \(Entfernen Procedure Call\) nicht zu asynchrone Initialisierung Code \(in **InitializeAsync**\). Dies können auftreten, wenn Sie aufrufen <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> direkt oder indirekt.  Bei der Synchronisierung lädt erforderlich sind, der UI\-Thread blockiert mit <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>. Das Standardmodell blockierende deaktiviert RPCs. Dies bedeutet, dass wenn Sie versuchen, einen RPC aus der asynchronen Aufgaben verwenden, Sie deadlock, wenn im UI\-Thread selbst warten auf das Paket geladen wird. Die allgemeine Alternative besteht darin, Code zum UI\-Thread zu marshallen, bei Bedarf mit etwa **beigetreten Aufgabenfactory**des <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> oder einen anderen Mechanismus, der keine RPC verwendet.  Verwenden Sie keine **ThreadHelper.Generic.Invoke** oder in der Regel blockiert den aufrufenden Thread wartet auf den UI\-Thread.  
  
     Hinweis: Vermeiden Sie die Verwendung **GetService** oder **QueryService** in Ihrer **InitializeAsync** Methode. Wenn Sie diese verwenden, müssen Sie zuerst zum UI\-Thread zu wechseln. Die Alternative ist die Verwendung <xref:Microsoft.VisualStudio.Shell.AsyncServiceProvider.GetServiceAsync%2A> aus Ihrer **AsyncPackage** \(durch umwandeln, damit <xref:Microsoft.VisualStudio.Shell.Interop.IAsyncServiceProvider>.\)  
  
 C\#: Erstellen Sie eine AsyncPackage:  
  
```c#  
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
  
## Konvertieren Sie eine vorhandene VSPackage in AsyncPackage  
 Der Großteil der Arbeit entspricht dem Erstellen eines neuen **AsyncPackage**. Sie müssen Schritte 1 bis 5. Außerdem müssen Sie besonders vorsichtig auf den folgenden ausführen:  
  
1.  Denken Sie daran, entfernen Sie die **initialisieren** außer Kraft setzen, Sie im Paket hatten.  
  
2.  Vermeiden von Deadlocks: Es kann RPCs in Ihrem Code dies nun in einem Hintergrundthread ausgeblendet. Sie müssen sicherstellen, dass bei einem RPC \(z. B. **GetService**\), müssen Sie entweder \(1\) Umschalten auf den Hauptthread oder \(2\) verwenden die asynchrone Version der API, wenn eine vorhanden ist \(z. B. **GetServiceAsync**\).  
  
3.  Nicht zwischen Threads zu häufig wechseln. Versuchen Sie, die Arbeit zu lokalisieren, die in einem Hintergrundthread auftreten können. Dies reduziert die Ladezeit.  
  
## Abfragen von Diensten aus AsyncPackage  
 Ein **AsyncPackage** kann oder möglicherweise je nach den Aufrufer nicht asynchron geladen. Zum Beispiel  
  
-   Wenn der Aufrufer aufgerufen **GetService** oder **QueryService** \(sowohl synchrone APIs\) oder  
  
-   Wenn der Aufrufer aufgerufen **IVsShell::LoadPackage** \(oder **IVsShell5::LoadPackageWithContext**\) oder  
  
-   Die Auslastung wird durch eine Benutzeroberflächenkontext ausgelöst, aber nicht angegeben wurde, dass die UI\-Kontext\-Mechanismus Sie asynchron geladen werden kann  
  
 Anschließend wird das Paket synchron geladen.  
  
 Beachten Sie, dass das Paket noch Gelegenheit \(in der asynchronen Initialisierungsphase\) vom UI\-Thread, funktionieren jedoch für den Abschluss dieser Arbeit im UI\-Thread blockiert wird. Wenn der Aufrufer verwendet **IAsyncServiceProvider** asynchron Abfrage für den Dienst dann Ihrer Auslastung und die Initialisierung erfolgt asynchron vorausgesetzt sie nicht sofort auf das resultierende Aufgabenobjekt blockieren.  
  
 C\#: Gewusst wie: Dienst asynchron abzufragen:  
  
```c#  
using Microsoft.VisualStudio.Shell;   
using Microsoft.VisualStudio.Shell.Interop;   
  
IAsyncServiceProvider asyncServiceProvider = Package.GetService(typeof(SAsyncServiceProvider)) as IAsyncServiceProvider;   
IMyTestService testService = await ayncServiceProvider.GetServiceAsync(typeof(SMyTestService)) as IMyTestService;  
```
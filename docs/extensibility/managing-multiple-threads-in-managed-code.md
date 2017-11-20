---
title: 'Vorgehensweise: Verwalten von mehreren Threads in verwaltetem Code | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c246c8be1d10893b018d5d0c5727d4af42efdc6b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-managing-multiple-threads-in-managed-code"></a>Vorgehensweise: Verwalten von mehreren Threads in verwaltetem Code
Wenn Sie eine verwaltete VSPackage-Erweiterung, die asynchronen Methoden aufruft oder Vorgänge, die Threads als dem Visual Studio-UI-Thread ausgeführt hat haben, sollten Sie die unten angegebenen Richtlinien befolgen. Da nicht für die Arbeit in einem anderen Thread abgeschlossen warten muss, können Sie den UI-Thread reaktionsfähig bleibt. Sie können Lesbarkeit Ihres Codes erschweren effizienter, da Sie nicht über zusätzliche Threads verfügen, die Stapelspeicher einnehmen, und können zuverlässiger und einfacher zu debuggen, da Sie, Deadlocks und Blockaden vermeiden vornehmen.  
  
 Sie können im Allgemeinen vom UI-Thread wechseln Sie zu einem anderen Thread oder umgekehrt. Wenn der Rückgabewert dieser Methode ist der aktuelle Thread den Thread, von dem es ursprünglich aufgerufen wurde.  
  
> [!IMPORTANT]
>  Die folgenden Richtlinien verwenden Sie die APIs in der <xref:Microsoft.VisualStudio.Threading> Namespace, insbesondere die <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> Klasse. Die APIs in diesem Namespace sind neu in [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]. Erhalten Sie eine Instanz von einem <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> aus der <xref:Microsoft.VisualStudio.Shell.ThreadHelper> Eigenschaft `ThreadHelper.JoinableTaskFactory`.  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>Der Wechsel von UI-Thread zu einem Hintergrundthread  
  
1.  Wenn Sie die UI-Thread und asynchronen Arbeit in einem Hintergrundthread werden sollen, verwenden Sie Task.Run():  
  
    ```csharp  
    await Task.Run(async delegate{  
        // Now you're on a separate thread.  
    });  
    // Now you're back on the UI thread.  
  
    ```  
  
2.  Wenn Sie auf den UI-Thread und synchron zu blockieren, während der Durchführung von Arbeit in einem Hintergrundthread verwendet werden sollen die <xref:System.Threading.Tasks.TaskScheduler> Eigenschaft `TaskScheduler.Default` in <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:  
  
    ```csharp  
    // using Microsoft.VisualStudio.Threading;  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        await TaskScheduler.Default;  
        // You're now on a separate thread.  
        DoSomethingSynchronous();  
        await OrSomethingAsynchronous();  
    });  
    ```  
  
## <a name="switching-from-a-background-thread-to-the-ui-thread"></a>Der Wechsel von einem Hintergrundthread zum UI-Thread  
  
1.  Wenn Sie in einem Hintergrundthread eine Aktion an den UI-Thread verwendet werden sollen <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>:  
  
    ```csharp  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     Sie können die <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> Methode zum UI-Thread zu wechseln. Diese Methode sendet eine Meldung an den UI-Thread mit der Fortsetzung der aktuellen asynchronen Methode und kommuniziert auch mit dem Rest des threading Frameworks legen Sie die richtige Priorität und verhindern von Deadlocks.  
  
     Wenn die Hintergrund-Thread-Methode nicht asynchronen, und Sie nicht asynchrone unbedingt können, können Sie weiterhin mithilfe der `await` Syntax zum UI-Thread zu wechseln, indem Sie Ihre Arbeit mit wrapping <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>, wie in diesem Beispiel:  
  
    ```csharp  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```
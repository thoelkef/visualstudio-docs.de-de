---
title: 'Gewusst wie: Verwalten von mehreren Threads in verwaltetem Code | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 477f57bbca9c49e7d7d13155fc1f6e55ee4667a8
ms.openlocfilehash: 417dc6e5285859424dfa3b482a90f1a141cff163
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-managing-multiple-threads-in-managed-code"></a>Gewusst wie: Verwalten von mehreren Threads in verwaltetem Code
Wenn Sie eine verwaltete VSPackage-Erweiterung, die asynchrone Methoden aufruft, oder Vorgänge, die auf anderen Threads als dem Visual Studio-UI-Thread ausgeführt wurde verfügen, befolgen Sie die nachfolgenden Richtlinien. Sie können den UI-Thread reaktionsfähig bleiben, da sie nicht warten, für die Arbeit in einem anderen Thread abgeschlossen. Sie können den Code effizienter machen, da Sie nicht über zusätzliche Threads verfügen, die Stapelspeicher einnehmen, und haben, damit es zuverlässiger und einfacher zu debuggen, da Sie Deadlocks und Blockaden vermeiden.  
  
 Sie können im Allgemeinen vom UI-Thread wechseln Sie zu einem anderen Thread, und umgekehrt. Wenn die Methode zurückgibt, ist der aktuelle Thread der Thread, von dem es ursprünglich aufgerufen wurde.  
  
> [!IMPORTANT]
>  Die folgenden Richtlinien verwenden Sie die APIs im <xref:Microsoft.VisualStudio.Threading>Namespace, insbesondere die <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>Klasse.</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> </xref:Microsoft.VisualStudio.Threading> Die APIs in diesem Namespace sind neu in [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]. Erhalten Sie eine Instanz von einem <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>aus der <xref:Microsoft.VisualStudio.Shell.ThreadHelper>-Eigenschaft `ThreadHelper.JoinableTaskFactory`.</xref:Microsoft.VisualStudio.Shell.ThreadHelper> </xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory>  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>Wechsel vom UI-Thread zu einem Hintergrundthread  
  
1.  Wenn Sie auf dem UI-Thread und asynchronen Arbeit in einem Hintergrundthread geschehen soll, verwenden Sie Task.Run():  
  
    ```c#  
    await Task.Run(async delegate{  
        // Now you’re on a separate thread.  
    });  
    // Now you’re back on the UI thread.  
  
    ```  
  
2.  Wenn Sie auf den UI-Thread und synchron blockiert beim Durchführen von Aufgaben in einem Hintergrundthread verwendet werden soll die <xref:System.Threading.Tasks.TaskScheduler>Eigenschaft `TaskScheduler.Default` in <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> </xref:System.Threading.Tasks.TaskScheduler>  
  
    ```c#  
    // using Microsoft.VisualStudio.Threading;  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        await TaskScheduler.Default;  
        // You're now on a separate thread.  
        DoSomethingSynchronous();  
        await OrSomethingAsynchronous();  
    });  
    ```  
  
## <a name="switching-from-a-background-thread-to-the-ui-thread"></a>Der Wechsel von einem Hintergrundthread zum UI-Thread  
  
1.  Wenn Sie in einem Hintergrundthread und Sie etwas auf dem UI-Thread ausführen möchten, verwenden Sie <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>:</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>  
  
    ```c#  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     Sie können die <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>Methode, um zum Benutzeroberflächenthread wechseln.</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> Diese Methode sendet eine Meldung an den UI-Thread mit der Fortsetzung der aktuellen asynchronen Methode und auch kommuniziert mit dem Rest des threading-Frameworks legen Sie die richtige Priorität und Vermeiden von Deadlocks.  
  
     Wenn die Hintergrund-Thread-Methode nicht asynchron ist und Sie können es asynchrone, können Sie weiterhin mithilfe der `await` Syntax zum UI-Thread zu wechseln, indem die Arbeit mit wrapping <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>, wie in diesem Beispiel:</xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>  
  
    ```c#  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```

---
translation.priority.ht:
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
ms.openlocfilehash: 252c505260986bd08b5522ba79d1e00a82624241
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942958"
---
Sie benötigen Administratorberechtigungen auf dem Remotecomputer.  
  
1. Suchen Sie die Remotedebuggeranwendung. (Suchen Sie msvsmon.exe an dem Speicherort, in dem er installiert wurde, oder öffnen Sie das Menü "Start" und suchen Sie nach **Remotedebugger**.)
  
    Wenn Sie den Remotedebugger auf einem Remoteserver ausführen, können Sie mit der rechten Maustaste in der Remote Debugger-app und wählen Sie **als Administrator ausführen**. Wenn Sie Sie nicht auf einem Remoteserver ausgeführt werden, starten Sie es normalerweise.
  
2. Beim Starten von Remotetools zum ersten Mal (oder bevor Sie sie konfiguriert haben), wird die **Konfiguration für Remotedebugging** Dialogfeld wird angezeigt.  
  
    ![RemoteDebuggerConfWizardPage](../media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
3. Wenn die Windows-Dienst-API nicht installiert ist (Dies geschieht nur bei Windows Server 2008 R2), wählen Sie die **installieren** Schaltfläche.  
  
4. Wählen Sie die Netzwerktypen aus, in denen die Remotetools verwenden werden sollen. Es muss mindestens ein Netzwerktyp ausgewählt werden. Wenn die Computer über eine Domäne verbunden sind, müssen Sie das erste Element auswählen. Wenn die Computer über eine Arbeitsgruppe oder eine Heimnetzgruppe verbunden sind, müssen Sie das zweite bzw. dritte Element auswählen.  
  
5. Wählen Sie **Konfigurieren des Remotedebuggings** zum Konfigurieren der Firewall, und starten Sie das Tool.  
  
6. Wenn die Konfiguration abgeschlossen ist, wird das Remotedebugger-Fenster angezeigt.
  
    ![RemoteDebuggerWindow](../media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
    Der Remotedebugger wartet jetzt eine Verbindung. Notieren Sie sich den Namen des Servers und die Portnummer, die angezeigt wird, da dies mit der Konfiguration übereinstimmen muss, die Sie später in Visual Studio verwenden.  
  
   Wenn Sie das Debuggen und den Remotedebugger beendet werden muss abgeschlossen werden, klicken Sie auf **Datei > Beenden** im Fenster. Sie können es von den Neustart der **starten** Menü oder über die Befehlszeile:  
  
   **\<Remotedebugger-Installationsverzeichnis >\\< X86, X64, ARM, ARM64 oder Appx > \msvsmon.exe**.  

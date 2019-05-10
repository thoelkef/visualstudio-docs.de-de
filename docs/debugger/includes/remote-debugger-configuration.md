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
ms.openlocfilehash: d89dbc0b752c2b8c538ec53769c166b6edbd802f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62902869"
---
1. Suchen Sie auf dem Remotecomputer, und Starten der **Remote Debugger** aus der **starten** Menü. 
   
   Wenn Sie nicht über die Administratorberechtigungen auf dem Remotecomputer verfügen, mit der rechten Maustaste die **Remotedebugger** app, und wählen **als Administrator ausführen**. Andernfalls starten Sie es normalerweise.

   Möglicherweise gibt es unterschiedliche Versionen von *msvsmon.exe* in *X64*, *X32*, oder andere Ordner. Stellen Sie sicher, um die Version, die Sie benötigen zum Debuggen Ihrer app zu starten. 
   
1. Beim ersten Verwenden Sie den Remotedebugger zu starten (oder bevor Sie sie konfiguriert haben), die **Konfiguration für Remotedebugging** Dialogfeld wird angezeigt.  
  
    ![Konfiguration für Remotedebugging](../media/remotedebuggerconfwizardpage.png "Remote Debugger-Konfiguration.")  
  
1. Wenn die Windows-Webdienste-API nicht dies nur bei Windows Server 2008 R2 der Fall installiert ist, wählen Sie die **installieren** Schaltfläche.  
  
1. Wählen Sie mindestens ein Netzwerktyp, die Sie auf die Remotetools verwenden möchten. Wenn die Computer über eine Domäne verbunden sind, müssen Sie das erste Element auswählen. Wenn der Computer über eine Arbeitsgruppe oder eine Heimnetzgruppe verbunden sind, wählen Sie das zweite bzw. dritte Element nach Bedarf.  
  
1. Wählen Sie **Konfigurieren des Remotedebuggings** zum Konfigurieren der Firewall und den Remotedebugger zu starten.  
  
1. Wenn die Konfiguration abgeschlossen ist, wird die **Remotedebugger** Fenster wird angezeigt.
  
    ![Remote Debugger-Fenster](../media/remotedebuggerwindow.png "Remotedebugger-Fenster")
  
    Der Remotedebugger wartet jetzt eine Verbindung. Verwenden Sie den Namen des Servers und die Portnummer, die angezeigt wird, legen Sie die Konfiguration des remote-Verbindung in Visual Studio.  
  
Wählen Sie zum Beenden des Remotedebuggers **Datei** > **beenden**. Sie können es von den Neustart der **starten** Menü oder über die Befehlszeile:  
  
```cmd
<Remote debugger installation directory>\msvsmon.exe
```

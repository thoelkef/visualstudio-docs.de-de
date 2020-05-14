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
ms.openlocfilehash: 2e5782c49f26925d9eda81f04653b1a20666c6b1
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2019
ms.locfileid: "68149171"
---
1. Suchen und starten Sie auf dem Remotecomputer im Menü **Start** den **Remotedebugger**. 
   
   Wenn Sie auf dem Remotecomputer nicht über Administratorberechtigungen verfügen, klicken Sie mit der rechten Maustaste auf die App **Remotedebugger**, und wählen Sie **Als Administrator ausführen** aus. Starten Sie andernfalls die App auf normale Weise.

   Wenn Sie beabsichtigen, eine Verbindung mit einem Prozess herzustellen, der unter einem Administratorkonto oder einem anderen Benutzerkonto ausgeführt wird (z. B IIS), klicken Sie mit der rechten Maustaste auf die App **Remotedebugger**, und wählen Sie **Als Administrator ausführen** aus. Weitere Informationen finden Sie unter [Ausführen des Remotedebuggers als Administrator](../remote-debugging-errors-and-troubleshooting.md#run-the-remote-debugger-as-an-administrator).
   
1. Wenn Sie den Remotedebugger zum ersten Mal starten (oder bevor Sie ihn konfiguriert haben), wird das Dialogfeld **Konfiguration für Remotedebugging** angezeigt.  
  
    ![Konfiguration des Remotedebuggers](../media/remotedebuggerconfwizardpage.png "Konfiguration des Remotedebuggers")  
  
1. Wenn die Windows-Webdienste-API nicht installiert ist (geschieht nur unter Windows Server 2008 R2), klicken Sie auf die Schaltfläche **Installieren**.  
  
1. Wählen Sie mindestens einen Netzwerktyp aus, für den Sie die Remotetools verwenden möchten. Wenn die Computer über eine Domäne verbunden sind, müssen Sie das erste Element auswählen. Wenn die Computer über eine Arbeitsgruppe oder eine Heimnetzgruppe verbunden sind, wählen Sie das zweite bzw. dritte Element aus.  
  
1. Wählen Sie **Remotedebugging konfigurieren** aus, um die Firewall zu konfigurieren und den Remotedebugger zu starten.  
  
1. Wenn die Konfiguration abgeschlossen ist, wird das Fenster **Remotedebugger** angezeigt.
  
    ![Fenster „Remotedebugger“](../media/remotedebuggerwindow.png "Fenster „Remotedebugger“")
  
    Der Remotedebugger wartet nun auf eine Verbindung. Verwenden Sie den Servernamen und die Portnummer, die angezeigt werden, um die Remoteverbindungskonfiguration in Visual Studio festzulegen.  
  
Um den Remotedebugger zu beenden, wählen Sie **Datei** > **Beenden** aus. Sie können ihn über das Menü **Start** oder über die Befehlszeile neu starten:  
  
```cmd
<Remote debugger installation directory>\msvsmon.exe
```

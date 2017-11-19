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
ms.openlocfilehash: 05a288a2d8dff776d8a5d3faea47b06d101f2ea3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
Sie müssen über Administratorberechtigungen auf dem Remotecomputer verfügen.  
  
1.  Suchen Sie die Remotedebuggeranwendung. (Suchen Sie msvsmon.exe an dem Speicherort, in dem er installiert wurde, oder öffnen Sie das Menü "Start" und suchen Sie nach **Remotedebugger**.)
  
     Wenn Sie den Remotedebugger auf einem Remoteserver ausgeführt werden, können Sie mit der rechten Maustaste den Remotedebugger-app und wählen Sie **als Administrator ausführen**. Wenn Sie Sie nicht auf einem Remoteserver ausgeführt werden, starten Sie es normalerweise.
  
3.  Beim Starten von Remotetools zum ersten Mal (oder bevor Sie sie konfiguriert haben), wird die **Konfiguration für Remotedebugging** Dialogfeld wird angezeigt.  
  
     ![RemoteDebuggerConfWizardPage](../media/remotedebuggerconfwizardpage.png "RemoteDebuggerConfWizardPage")  
  
4.  Wenn der Windows-Dienst-API nicht installiert ist (Dies geschieht nur bei Windows Server 2008 R2), wählen Sie die **installieren** Schaltfläche.  
  
5.  Wählen Sie die Netzwerktypen aus, in denen die Remotetools verwenden werden sollen. Es muss mindestens ein Netzwerktyp ausgewählt werden. Wenn die Computer über eine Domäne verbunden sind, müssen Sie das erste Element auswählen. Wenn die Computer über eine Arbeitsgruppe oder eine Heimnetzgruppe verbunden sind, müssen Sie das zweite bzw. dritte Element auswählen.  
  
6.  Wählen Sie **Konfigurieren des Remotedebuggings** zum Konfigurieren der Firewall, und starten Sie das Tool.  
  
7.  Wenn die Konfiguration abgeschlossen ist, wird das Remotedebugger-Fenster angezeigt.
  
     ![RemoteDebuggerWindow](../media/remotedebuggerwindow.png "RemoteDebuggerWindow")
  
     Der Remotedebugger wartet jetzt eine Verbindung. Notieren Sie sich den Servernamen und port-Nummer, die angezeigt wird, da dies die Konfiguration übereinstimmen muss, die Sie später in Visual Studio verwenden.  
  
 Wenn Sie Debuggen und die Notwendigkeit, die den Remotedebugger beenden abgeschlossen sind, klicken Sie auf **Datei > Beenden** auf das Fenster. Sie können den Neustart aus der **starten** Menü oder über die Befehlszeile:  
  
 **\<Visual Studio-Installationsverzeichnis > \Common7\IDE\Remote Debugger\\< X86, X64 oder Appx\msvsmon.exe**.  
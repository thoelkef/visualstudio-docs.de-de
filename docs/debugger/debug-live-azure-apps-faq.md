---
title: Häufig gestellte Fragen zum Debuggen von Momentaufnahmen | Microsoft-Dokumentation
ms.date: 11/07/2017
ms.topic: reference
helpviewer_keywords:
- debugger
ms.assetid: 944f1eb0-a74b-4d28-ae2b-a370cd869add
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 315b24d384a1e3576af6590923c0e546785918ae
ms.sourcegitcommit: b468d71052a1b8a697f477ab23a3644de139f1e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/19/2019
ms.locfileid: "67255981"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Häufig gestellte Fragen zum Debuggen von Momentaufnahmen in Visual Studio

Hier ist eine Liste der Fragen, die beim Debuggen aktiver Azure-Anwendungen mit dem Momentaufnahmedebugger aufkommen könnten.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Wie hoch sind die Leistungseinbußen bei einer Momentaufnahme?

Wenn der Momentaufnahmedebugger eine Momentaufnahme Ihrer App erfasst, verzweigt er den Prozess der App und setzt die verzweigte Kopie aus. Wenn Sie eine Momentaufnahme debuggen, debuggen Sie die verzweigte Kopie des Prozesses. Dieser Vorgang dauert nur 10 bis 20 Millisekunden, kopiert aber nicht den vollständigen Heap der App. Stattdessen kopiert er nur die Seitentabelle und legt Seiten für das Kopieren beim Schreibvorgang fest. Wenn einige Ihrer App-Objekte auf dem Heap geändert werden, werden die entsprechenden Seiten kopiert. Darum beansprucht jede Momentaufnahme etwas Arbeitsspeicher (bei den meisten Apps in der Größenordnung von ein paar hundert Kilobytes).

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>Was geschieht, wenn ich einen horizontal hochskalierten Azure App Service habe (mehrere Instanzen meiner App)?

Wenn Sie mehrere Instanzen Ihrer App haben, werden die Andockpunkte auf jede einzelne Instanz angewendet. Nur der erste mit den angegebenen Bedingungen zu erreichende Andockpunkt erstellt eine Momentaufnahme. Wenn Sie mehrere Andockpunkte haben, stammen spätere Momentaufnahmen von der gleichen Instanz, die die erste Momentaufnahme erstellt hat. An das Ausgabefenster gesendete Protokollpunkte zeigen nur Meldungen von einer Instanz an, während an Anwendungsprotokolle gesendete Protokollpunkte Meldungen von jeder Instanz senden.

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>Wie lädt der Momentaufnahmedebugger Symbole?

Der Momentaufnahmedebugger erfordert, dass Sie die entsprechenden Symbole für Ihre Anwendung entweder lokal oder für Ihren Azure App Service bereitgestellt haben. (Eingebettete PDB-Dateien werden derzeit nicht unterstützt.) Der Momentaufnahmedebugger lädt automatisch Symbole von Ihrem Azure App Service. Ab Visual Studio 2017 Version 15.2 werden mit der Bereitstellung für Azure App Service auch die Symbole Ihrer App bereitgestellt.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>Arbeitet der Momentaufnahmedebugger mit Releasebuilds meiner Anwendung?

Ja, der Momentaufnahmedebugger soll mit Releasebuilds arbeiten. Wenn ein Andockpunkt in einer Funktion platziert wird, wird die Funktion zu einer Debugversion neu kompiliert und damit debugfähig. Beim Beenden des Momentaufnahmedebuggers werden die Funktionen auf die Version des Releasebuilds zurückgesetzt.

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Können Protokollpunkte in meiner Produktionsanwendung Nebeneffekte verursachen?

Nein – jegliche Meldungen, die Sie Ihrer App hinzufügen, werden virtuell ausgewertet. Sie können keine Nebeneffekte in Ihrer Anwendung auslösen. Allerdings ist der Zugriff auf einige native Eigenschaften mit Protokollpunkten vielleicht nicht möglich.

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>Funktioniert der Momentaufnahmedebugger, wenn mein Server unter Last steht?

Ja, das Momentaufnahmedebuggen kann bei Servern unter Last funktionieren. Wenn nur eine geringe Menge freien Arbeitsspeichers auf dem Server vorhanden ist, wird der Momentaufnahmedebugger gedrosselt und erfasst keine Momentaufnahmen.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Wie deinstalliere ich den Momentaufnahmedebugger?

Sie können die Momentaufnahmedebugger-Websiteerweiterung mit den folgenden Schritten in Ihrem App Service deinstallieren:

1. Deaktivieren Sie Ihren App Service über den Cloud-Explorer in Visual Studio oder im Azure-Portal aus.
1. Navigieren Sie zur Kudu-Website Ihres App Service (d.h. yourappservice.**scm**.azurewebsites.net), und navigieren Sie zu **Websiteerweiterungen**.
1. Klicken Sie auf das X der Momentaufnahmedebugger-Websiteerweiterung, um sie zu entfernen.

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>Warum werden während einer Momentaufnahmedebugger-Sitzung Ports geöffnet?

Der Momentaufnahmedebugger muss einen Satz von Ports öffnen, um die in Azure erstellten Momentaufnahmen zu debuggen. Hierbei handelt es sich um die gleichen Ports, die für das Remotedebuggen erforderlich sind. [Hier finden Sie die Liste der Ports](../debugger/remote-debugger-port-assignments.md).

#### <a name="how-do-i-disable-the-remote-debugger-extension"></a>Wie deaktiviere ich die Remote Debugger-Erweiterung?

App-Dienste:
1. Deaktivieren Sie Remote Debugger-Erweiterung über das Azure-Portal für Ihren App Service.
2. Azure-Portal > Ihr Anwendungsdienst-Ressourcenblatt > *Anwendungseinstellungen*
3. Navigieren Sie zu der *Debuggen* aus, und klicken Sie auf die *aus* Schaltfläche *Remotedebuggen*.

Für AKS:
1. Aktualisieren Sie die dockerfile-Datei zum Entfernen von der Abschnitten zu den [Visual Studio Snapshot Debugger auf Docker-Images](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Neu erstellen Sie, und stellen Sie das geänderte Docker-Image.

Gruppen entfernen die Remote Debugger-Erweiterung, Zertifikate, KeyVaults und eingehende NAT-Adresspools für VM/virtuellen VM-skalierungsgruppen wie folgt aus:

1. Entfernen Sie die Remote Debugger-Erweiterung  

   Es gibt mehrere Möglichkeiten, den Remotedebugger für virtuelle Computer und VM Scale Sets-Instanzen zu deaktivieren:  

      - Deaktivieren Sie den Remotedebugger über die Cloud-Explorer  

         - Cloud-Explorer > Ressource des virtuellen Computers > Debuggen deaktivieren (Debuggen deaktivieren ist nicht vorhanden für VM-Skalierungsgruppe auf Cloud-Explorer).  


      - Deaktivieren Sie den Remotedebugger mit PowerShell-Skripts/Cmdlets  

         Für den virtuellen Computer:  

         ```
         Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger  
         ```

         Für VM Scale Sets:  
         ```
         $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName  
         $extension = $vmss.VirtualMachineProfile.ExtensionProfile.Extensions | Where {$_.Name.StartsWith('VsDebuggerService')} | Select -ExpandProperty Name  
         Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name $extension  
         ```

      - Deaktivieren Sie den Remotedebugger über die Azure-portal
         - Azure-Portal > Ihr VM/virtual Machine Scale sets für Blatt "Ressourcen" > Extensions  
         - Deinstallieren Sie Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger-Erweiterung  


         > [!NOTE]
         > VM Scale Sets - Portal lässt keine DebuggerListener Ports entfernen. Sie müssen Azure PowerShell verwenden. Details finden Sie weiter unten.
  
2. Entfernen von Zertifikaten und Azure Key Vault

   Wenn Sie die Remote Debugger-Erweiterung für virtuellen Computer oder VM Scale Sets-Instanzen zu installieren, werden sowohl Client-als auch Zertifikate zur Authentifizierung des Visual Studio-Clients mit dem virtuellen Azure-Computer erstellt/Virtual Machine Scale sets für Ressourcen.  

   - Das Clientzertifikat  

      Dieses Zertifikat ist ein selbst signiertes Zertifikat im Zertifikatspeicher befinden: / CurrentUser/My /  

      ```
      Thumbprint                                Subject  
      ----------                                -------  

      1234123412341234123412341234123412341234  CN=ResourceName  
      ```

      Eine Möglichkeit, dieses Zertifikat von Ihrem Computer zu entfernen ist, über PowerShell

      ```
      $ResourceName = 'ResourceName' # from above  
      Get-ChildItem -Path Cert:\CurrentUser\My | Where-Object {$_.Subject -match $ResourceName} | Remove-Item  
      ```

   - Das Serverzertifikat
      - Der entsprechenden Serverzertifikat-Fingerabdruck, die als Geheimnis in Azure-Schlüsseltresor bereitgestellt wird. Visual Studio versucht, suchen oder erstellen einen Schlüsseltresor mit dem Präfix MSVSAZ * in der Region für den virtuellen Computer oder VM Scale sets-Ressource. Alle virtuellen Computer oder VM-skalierungsgruppen Ressourcen, die in dieser Region bereitgestellt werden daher den gleichen Schlüsseltresor gemeinsam.  
      - Um den Server-Zertifikat-Fingerabdruck geheimen Schlüssel zu löschen, wechseln Sie zum Azure-Portal, und finden Sie den Schlüsseltresor MSVSAZ * in der gleichen Region, die Ihre Ressource hostet. Löschen des geheimen Schlüssels mit der Bezeichnung werden sollte `remotedebugcert<<ResourceName>>`  
      - Sie müssen auch den Serverschlüssel aus Ihrer Ressource über PowerShell zu löschen.  

      Für virtuelle Computer:  

      ```
      $vm.OSProfile.Secrets[0].VaultCertificates.Clear()  
      Update-AzVM -ResourceGroupName $rgName -VM $vm  
      ```
                        
      Für VM Scale Sets:  

      ```
      $vmss.VirtualMachineProfile.OsProfile.Secrets[0].VaultCertificates.Clear()  
      Update-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName -VirtualMachineScaleSet $vmss  
      ```
                        
3. Entfernen Sie alle DebuggerListener eingehende NAT-Pools (VM-Skalierungsgruppe nur)  

   Der Remotedebugger führt DebuggerListener eingehende NAT-Pools, die für Ihre Skalierungsgruppe auf den Load Balancer angewendet werden.  

   ```
   $inboundNatPools = $vmss.VirtualMachineProfile.NetworkProfile.NetworkInterfaceConfigurations.IpConfigurations.LoadBalancerInboundNatPools  
   $inboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null  
                
   if ($LoadBalancerName)  
   {
      $lb = Get-AzLoadBalancer -ResourceGroupName $ResourceGroup -name $LoadBalancerName  
      $lb.FrontendIpConfigurations[0].InboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null  
      Set-AzLoadBalancer -LoadBalancer $lb  
   }
   ```

#### <a name="how-do-i-disable-snapshot-debugger"></a>Wie deaktiviere ich Momentaufnahmedebugger?

Für App Service:
1. Snapshot Debugger über das Azure-Portal für Ihren App Service zu deaktivieren.
2. Azure-Portal > Ihr Anwendungsdienst-Ressourcenblatt > *Anwendungseinstellungen*
3. Löschen Sie die folgenden App-Einstellungen im Azure-Portal, und speichern Sie die Änderungen zu. 
    - INSTRUMENTATIONENGINE_EXTENSION_VERSION
    - SNAPSHOTDEBUGGER_EXTENSION_VERSION

    > [!WARNING]
    > Alle Änderungen an Anwendungseinstellungen werden einen Neustart der app initiiert. Weitere Informationen zu Anwendungseinstellungen finden Sie unter [Konfigurieren einer App Service-app im Azure-Portal](/azure/app-service/web-sites-configure).

Für AKS:
1. Aktualisieren Sie die dockerfile-Datei zum Entfernen von der Abschnitten zu den [Visual Studio Snapshot Debugger auf Docker-Images](https://github.com/Microsoft/vssnapshotdebugger-docker).
2. Neu erstellen Sie, und stellen Sie das geänderte Docker-Image.

Für skalierungsgruppen für virtuelle Computer/virtuelle Computer:

Es gibt mehrere Möglichkeiten, den Momentaufnahmedebugger zu deaktivieren:
- Cloud-Explorer > Ihrer VM/virtuellen VM-Skalierungsgruppe Ressource > Diagnose deaktivieren

- Azure-Portal > Ihr VM/virtuellen VM-Skalierungsgruppe Blatt "Ressourcen" > Erweiterungen > deinstallieren Microsoft.Insights.VMDiagnosticsSettings-Erweiterung

- PowerShell-Cmdlets aus [Azure PowerShell](https://docs.microsoft.com/powershell/azure/overview)

    Virtueller Computer:
    ```
        Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.Insights.VMDiagnosticsSettings 
    ```
    
    VM-skalierungsgruppen:
    ```
        $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
        Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name Microsoft.Insights.VMDiagnosticsSettings
    ```

## <a name="see-also"></a>Siehe auch

- [Debuggen in Visual Studio](../debugger/index.md)
- [Debug live ASP.NET-Apps, die mit dem Momentaufnahmedebugger](../debugger/debug-live-azure-applications.md)
- [Debug live ASP.NET Azure Machines\Virtual VMs Scale Sets-Instanzen mit dem Momentaufnahmedebugger](../debugger/debug-live-azure-virtual-machines.md)
- [Debug live ASP.NET-Azure-Kubernetes, die mit dem Momentaufnahmedebugger](../debugger/debug-live-azure-kubernetes.md)
- [Problembehandlung und bekannte Probleme beim Debuggen von Momentaufnahmen](../debugger/debug-live-azure-apps-troubleshooting.md)
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
ms.openlocfilehash: 5e0d8839daac2d470f4275257bfcfbc83fc7a62f
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911405"
---
# <a name="frequently-asked-questions-for-snapshot-debugging-in-visual-studio"></a>Häufig gestellte Fragen zum Debuggen von Momentaufnahmen in Visual Studio

Hier ist eine Liste der Fragen, die beim Debuggen aktiver Azure-Anwendungen mit dem Momentaufnahmedebugger aufkommen könnten.

#### <a name="what-is-the-performance-cost-of-taking-a-snapshot"></a>Wie hoch sind die Leistungseinbußen bei einer Momentaufnahme?

Wenn der Momentaufnahmedebugger eine Momentaufnahme Ihrer App erfasst, verzweigt er den Prozess der App und setzt die verzweigte Kopie aus. Wenn Sie eine Momentaufnahme debuggen, debuggen Sie die verzweigte Kopie des Prozesses. Dieser Vorgang dauert nur 10 bis 20 Millisekunden, kopiert aber nicht den vollständigen Heap der App. Stattdessen kopiert er nur die Seitentabelle und legt Seiten für das Kopieren beim Schreibvorgang fest. Wenn einige Ihrer App-Objekte auf dem Heap geändert werden, werden die entsprechenden Seiten kopiert. Darum beansprucht jede Momentaufnahme etwas Arbeitsspeicher (bei den meisten Apps in der Größenordnung von ein paar hundert Kilobytes).

#### <a name="what-happens-if-i-have-a-scaled-out-azure-app-service-multiple-instances-of-my-app"></a>Was geschieht, wenn ich einen horizontal hochskalierten Azure App Service habe (mehrere Instanzen meiner App)?

Wenn Sie mehrere Instanzen Ihrer App haben, werden die Andockpunkte auf jede einzelne Instanz angewendet. Nur der erste mit den angegebenen Bedingungen zu erreichende Andockpunkt erstellt eine Momentaufnahme. Wenn Sie mehrere Andockpunkte haben, stammen spätere Momentaufnahmen von der gleichen Instanz, die die erste Momentaufnahme erstellt hat. An das Ausgabefenster gesendete Protokollpunkte zeigen nur Meldungen von einer Instanz an, während an Anwendungsprotokolle gesendete Protokollpunkte Meldungen von jeder Instanz senden.

#### <a name="how-does-the-snapshot-debugger-load-symbols"></a>Wie lädt der Momentaufnahmedebugger Symbole?

Der Momentaufnahmedebugger erfordert, dass Sie die entsprechenden Symbole für Ihre Anwendung entweder lokal oder für Ihren Azure App Service bereitgestellt haben. (Eingebettete pdsb werden zurzeit nicht unterstützt.) Der Momentaufnahmedebugger lädt automatisch Symbole aus Ihrem Azure App Service herunter. Ab Visual Studio 2017 Version 15.2 werden mit der Bereitstellung für Azure App Service auch die Symbole Ihrer App bereitgestellt.

#### <a name="does-the-snapshot-debugger-work-against-release-builds-of-my-application"></a>Arbeitet der Momentaufnahmedebugger mit Releasebuilds meiner Anwendung?

Ja, der Momentaufnahmedebugger soll mit Releasebuilds arbeiten. Wenn ein Andockpunkt in einer Funktion platziert wird, wird die Funktion zu einer Debugversion neu kompiliert und damit debugfähig. Beim Beenden des Momentaufnahmedebuggers werden die Funktionen auf die Version des Releasebuilds zurückgesetzt.

#### <a name="can-logpoints-cause-side-effects-in-my-production-application"></a>Können Protokollpunkte in meiner Produktionsanwendung Nebeneffekte verursachen?

Nein – jegliche Meldungen, die Sie Ihrer App hinzufügen, werden virtuell ausgewertet. Sie können keine Nebeneffekte in Ihrer Anwendung auslösen. Allerdings ist der Zugriff auf einige native Eigenschaften mit Protokollpunkten vielleicht nicht möglich.

#### <a name="does-the-snapshot-debugger-work-if-my-server-is-under-load"></a>Funktioniert der Momentaufnahmedebugger, wenn mein Server unter Last steht?

Ja, das Momentaufnahmedebuggen kann bei Servern unter Last funktionieren. Wenn nur eine geringe Menge freien Arbeitsspeichers auf dem Server vorhanden ist, wird der Momentaufnahmedebugger gedrosselt und erfasst keine Momentaufnahmen.

#### <a name="how-do-i-uninstall-the-snapshot-debugger"></a>Wie deinstalliere ich den Momentaufnahmedebugger?

Sie können die Momentaufnahmedebugger-Websiteerweiterung mit den folgenden Schritten in Ihrem App Service deinstallieren:

1. Deaktivieren Sie die APP Service entweder über die Cloud-Explorer in Visual Studio oder die Azure-Portal.
1. Navigieren Sie zur Kudu-Website Ihres App Service (d.h. yourappservice.**scm**.azurewebsites.net), und navigieren Sie zu **Websiteerweiterungen**.
1. Klicken Sie auf das X der Momentaufnahmedebugger-Websiteerweiterung, um sie zu entfernen.

#### <a name="why-are-ports-opened-during-a-snapshot-debugger-session"></a>Warum werden während einer Momentaufnahmedebugger-Sitzung Ports geöffnet?

Der Momentaufnahmedebugger muss einen Satz von Ports öffnen, um die in Azure erstellten Momentaufnahmen zu debuggen. Hierbei handelt es sich um die gleichen Ports, die für das Remotedebuggen erforderlich sind. [Hier finden Sie die Liste der Ports](../debugger/remote-debugger-port-assignments.md).

#### <a name="how-do-i-disable-the-remote-debugger-extension"></a>Gewusst wie die remotedebuggererweiterung deaktivieren?

App Services:
1. Deaktivieren Sie die remotedebuggererweiterung über die Azure-Portal für Ihre APP Service.
2. Azure-Portal > Sie das Anwendungs Dienst-Ressourcen Blatt > *Anwendungseinstellungen*
3. Navigieren Sie zum Abschnitt *Debuggen* , und klicken Sie auf die Schaltfläche *aus* für *Remote Debugging*.

Für AKS:
1. Aktualisieren Sie die dockerfile-Datei, um die Abschnitte zu entfernen, die dem [Visual Studio-Momentaufnahmedebugger auf docker-Images](https://github.com/Microsoft/vssnapshotdebugger-docker)entsprechen.
2. Erneutes Erstellen und erneutes Bereitstellen des geänderten docker-Images.

Entfernen Sie für virtuelle Computer/VM-Skalierungs Gruppen die remotedebuggererweiterung, Zertifikate, keyvault und eingehende NAT-Pools wie folgt:

1. Remotedebuggererweiterung entfernen

   Es gibt mehrere Möglichkeiten, den Remote Debugger für virtuelle Computer und VM-Skalierungs Gruppen zu deaktivieren:

      - Deaktivieren Sie den Remote Debugger durch Cloud-Explorer

         - Cloud-Explorer > der Ressource des virtuellen Computers > Debuggen deaktivieren (Debuggen ist für VM-Skalierungs Gruppe auf Cloud-Explorer nicht vorhanden).

      - Deaktivieren Sie den Remote Debugger mit PowerShell-Skripts/-Cmdlets.

         Für den virtuellen Computer:

         ```powershell
         Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.VisualStudio.Azure.RemoteDebug.VSRemoteDebugger
         ```

         Für VM-Skalierungs Gruppen:

         ```powershell
         $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
         $extension = $vmss.VirtualMachineProfile.ExtensionProfile.Extensions | Where {$_.Name.StartsWith('VsDebuggerService')} | Select -ExpandProperty Name
         Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name $extension
         ```

      - Deaktivieren Sie den Remote Debugger über die Azure-Portal
         - Azure-Portal > Ressourcen Blatt für virtuelle Computer/VM-Skalierungs Gruppen > Erweiterungen
         - Deinstallieren Sie die Erweiterung "Microsoft. VisualStudio. Azure. Remotedebug. vsremotedebugger".

         > [!NOTE]
         > VM-Skalierungs Gruppen: das Portal lässt das Entfernen der debuggerlistener-Ports nicht zu. Sie müssen Azure PowerShell verwenden. Details finden Sie weiter unten.

2. Entfernen von Zertifikaten und Azure Key Vault

   Beim Installieren der remotedebuggererweiterung für virtuelle Computer oder VM-Skalierungs Gruppen werden Client-und Server Zertifikate erstellt, um den vs-Client mit den Ressourcen virtueller Azure-Computer/VM-Skalierungs Gruppen zu authentifizieren.

   - Das Client Zertifikat

      Bei diesem Zertifikat handelt es sich um ein selbst signiertes Zertifikat im Zertifikat:/CurrentUser/My/

      ```
      Thumbprint                                Subject
      ----------                                -------

      1234123412341234123412341234123412341234  CN=ResourceName
      ```

      Eine Möglichkeit, dieses Zertifikat von Ihrem Computer zu entfernen, ist PowerShell.

      ```powershell
      $ResourceName = 'ResourceName' # from above
      Get-ChildItem -Path Cert:\CurrentUser\My | Where-Object {$_.Subject -match $ResourceName} | Remove-Item
      ```

   - Das Server Zertifikat
      - Der entsprechende Fingerabdruck des Serverzertifikats wird als geheimer Schlüssel in Azure Key Vault bereitgestellt. VS versucht, einen keyvault mit dem Präfix "msvsaz *" in der Region zu suchen oder zu erstellen, die der Ressource des virtuellen Computers oder der VM-Skalierungs Gruppen entspricht. Alle in dieser Region bereitgestellten Ressourcen für virtuelle Computer oder VM-Skalierungs Gruppen werden daher denselben Schlüssel Tresor verwenden.
      - Um den Schlüssel für den Fingerabdruck des Serverzertifikats zu löschen, wechseln Sie zum Azure-Portal, und suchen Sie in der gleichen Region, in der die Ressource gehostet wird, den Schlüssel Tresor msvsaz *. Löschen Sie den geheimen Schlüssel mit der Bezeichnung `remotedebugcert<<ResourceName>>`
      - Sie müssen auch den geheimen Server Schlüssel aus ihrer Ressource über PowerShell löschen.

      Für virtuelle Computer:

      ```powershell
      $vm.OSProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVM -ResourceGroupName $rgName -VM $vm
      ```

      Für VM-Skalierungs Gruppen:

      ```powershell
      $vmss.VirtualMachineProfile.OsProfile.Secrets[0].VaultCertificates.Clear()
      Update-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName -VirtualMachineScaleSet $vmss
      ```

3. Alle eingehenden NAT-Pools für debuggerlistener entfernen (nur VM-Skalierungs Gruppe)

   Der Remote Debugger führt debuggerlistener-gebundene NAT-Pools ein, die auf den Load Balancer Ihres scalesets angewendet werden.

   ```powershell
   $inboundNatPools = $vmss.VirtualMachineProfile.NetworkProfile.NetworkInterfaceConfigurations.IpConfigurations.LoadBalancerInboundNatPools
   $inboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null

   if ($LoadBalancerName)
   {
      $lb = Get-AzLoadBalancer -ResourceGroupName $ResourceGroup -name $LoadBalancerName
      $lb.FrontendIpConfigurations[0].InboundNatPools.RemoveAll({ param($pool) $pool.Id.Contains('inboundNatPools/DebuggerListenerNatPool-') }) | Out-Null
      Set-AzLoadBalancer -LoadBalancer $lb
   }
   ```

#### <a name="how-do-i-disable-snapshot-debugger"></a>Gewusst wie Momentaufnahmedebugger deaktivieren?

App Service:
1. Deaktivieren Sie Momentaufnahmedebugger über die Azure-Portal für Ihre APP Service.
2. Azure-Portal > Sie das Anwendungs Dienst-Ressourcen Blatt > *Anwendungseinstellungen*
3. Löschen Sie die folgenden App-Einstellungen im Azure-Portal, und speichern Sie die Änderungen.
   - INSTRUMENTATIONENGINE_EXTENSION_VERSION
   - SNAPSHOTDEBUGGER_EXTENSION_VERSION

   > [!WARNING]
   > Durch Änderungen an den Anwendungseinstellungen wird ein Neustart der APP initiiert. Weitere Informationen zu Anwendungseinstellungen finden Sie unter [Konfigurieren einer APP Service-APP in der Azure-Portal](/azure/app-service/web-sites-configure).

Für AKS:
1. Aktualisieren Sie die dockerfile-Datei, um die Abschnitte zu entfernen, die dem [Visual Studio-Momentaufnahmedebugger auf docker-Images](https://github.com/Microsoft/vssnapshotdebugger-docker)entsprechen.
2. Erneutes Erstellen und erneutes Bereitstellen des geänderten docker-Images.

Für virtuelle Computer/VM-Skalierungs Gruppen:

Es gibt mehrere Möglichkeiten, die Momentaufnahmedebugger zu deaktivieren:
- Cloud-Explorer > der Ressource des virtuellen Computers/der VM-Skalierungs Gruppe > die Diagnose deaktivieren

- Azure-Portal > Sie das Ressourcen Blatt des virtuellen Computers/der VM-Skalierungs Gruppe > Erweiterungen > Deinstallieren Sie die Erweiterung Microsoft. Insights. vmdiagnosticssettings.

- PowerShell-Cmdlets von [AZ PowerShell](/powershell/azure/overview)

   Virtueller Computer:

   ```powershell
      Remove-AzVMExtension -ResourceGroupName $rgName -VMName $vmName -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

   VM-Skalierungs Gruppen:

   ```powershell
      $vmss = Get-AzVmss -ResourceGroupName $rgName -VMScaleSetName $vmssName
      Remove-AzVmssExtension -VirtualMachineScaleSet $vmss -Name Microsoft.Insights.VMDiagnosticsSettings
   ```

## <a name="see-also"></a>Siehe auch

- [Debuggen in Visual Studio](../debugger/index.yml)
- [Debuggen von Live ASP.net-apps mithilfe der Momentaufnahmedebugger](../debugger/debug-live-azure-applications.md)
- [Live Debuggen ASP.net Azure Virtual machines\vm Scale Sets Using the Momentaufnahmedebugger](../debugger/debug-live-azure-virtual-machines.md)
- [Live Debuggen ASP.net Azure Kubernetes mithilfe der Momentaufnahmedebugger](../debugger/debug-live-azure-kubernetes.md)
- [Problembehandlung und bekannte Probleme beim Debuggen von Momentaufnahmen](../debugger/debug-live-azure-apps-troubleshooting.md)

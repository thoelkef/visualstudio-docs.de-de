---
title: Einrichten der Diagnose für Azure Cloud Services und Virtual Machines | Microsoft-Dokumentation
description: Informationen Sie zum Einrichten der Diagnose zum Debuggen von Azure-Clouddiensten und virtuellen Computern (VMs) in Visual Studio.
author: mikejo5000
manager: douge
ms.assetid: e70cd7b4-6298-43aa-adea-6fd618414c26
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 06/28/2018
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: 4448825c5d443887833a405aab14d2243a0e5216
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002086"
---
# <a name="set-up-diagnostics-for-azure-cloud-services-and-virtual-machines"></a>Einrichten der Diagnose für Azure-Clouddienste und virtuelle Azure-Computer
Wenn Sie ein Azure-Clouddienst oder virtuellen Computer beheben müssen, können Sie Visual Studio verwenden, um die Azure-Diagnose leichter einzurichten. Diagnose erfasst Systemdaten und Protokollierungsdaten auf den virtuellen Computern und VM-Instanzen, die Ihren Cloud-Dienst ausgeführt. Diagnose-Daten werden in einem Speicherkonto übertragen, die Sie auswählen. Weitere Informationen zur Diagnose diagnoseprotokollierung in Azure finden Sie unter [Aktivieren der diagnoseprotokollierung für Web-Apps in Azure App Service](/azure/app-service/web-sites-enable-diagnostic-log).

In diesem Artikel erfahren Sie, wie Sie mit Visual Studio zu aktivieren und Einrichten von Azure-Diagnose wird vor und nach der Bereitstellung. Erfahren Sie, Gewusst wie: Einrichten der Diagnose in Azure Virtual Machines, zum Auswählen der Arten von Diagnoseinformationen sammeln und Anzeigen der gesammelten Daten geschieht.

Sie können eine der folgenden Optionen zum Einrichten von Azure-Diagnose verwenden:

* Ändern der diagnoseeinstellungen in die **Diagnosekonfiguration** Dialogfeld in Visual Studio. Die Einstellungen werden in einer Datei namens "Diagnostics.wadcfgx" (in Azure SDK 2.4 und früher wird die Datei "Diagnostics.wadcfg" bezeichnet) gespeichert. Sie können auch die Konfigurationsdatei direkt ändern. Wenn Sie die Datei manuell aktualisieren, wirksam die Konfiguration der nächsten des Clouddiensts Bereitstellung in Azure oder den Dienst im Emulator ausführen.
* Verwenden Sie Cloud-Explorer oder Server-Explorer in Visual Studio so ändern Sie die diagnoseeinstellungen für einen Clouddienst oder virtuellen Computer, der ausgeführt wird.

## <a name="azure-sdk-26-diagnostics-changes"></a>Azure SDK 2.6-Diagnose-Änderungen
Die folgenden Änderungen gelten für Azure SDK 2.6 und später Projekte in Visual Studio:

* Der lokale Emulator unterstützt jetzt die Diagnose. Dies bedeutet, dass Sie Diagnosedaten erfassen können, und stellen Sie sicher, dass Ihre Anwendung die richtigen ablaufverfolgungen erstellt, beim Entwickeln und in Visual Studio testen. Die Verbindungszeichenfolge `UseDevelopmentStorage=true` aktiviert die Sammlung von Diagnosedaten während Sie Ihr clouddienstprojekt in Visual Studio ausgeführt werden, mithilfe des Azure-Speicheremulators. Alle Diagnosedaten werden im Entwicklungsspeicher Speicherkonto gesammelt.
* Die Verbindungszeichenfolge für Speicherkonto Diagnose `Microsoft.WindowsAzure.Plugins.Diagnostics.ConnectionString` befindet sich in der Dienstkonfigurationsdatei (.cscfg). In Azure SDK 2.5 wird das diagnosespeicherkonto in der Datei "Diagnostics.wadcfgx" angegeben.

Die Verbindungszeichenfolge funktioniert anders einige grundlegende Änderungen in Azure SDK 2.6 und später im Vergleich zu Azure SDK 2.4 und früher:

* In Azure SDK 2.4 und früher wird die Verbindungszeichenfolge als eine Laufzeit vom Diagnose-Plug-in verwendet, die Informationen zum Speicherkonto für die Übertragung der Diagnoseprotokolle abzurufen.
* In Azure SDK 2.6 und höher, verwendet Visual Studio die Diagnose-Verbindungszeichenfolge, um die Azure-Diagnose-Erweiterung mit den entsprechenden speicherkontoinformationen während der Veröffentlichung einzurichten. Sie können die Verbindungszeichenfolge verwenden, um verschiedene Speicherkonten für verschiedene Dienstkonfigurationen definieren, die Visual Studio während der Veröffentlichung verwendet. Jedoch, da die Diagnose-Plug-in nach Azure SDK 2.5 nicht verfügbar ist, kann nicht die cscfg-Datei allein die diagnoseerweiterung einrichten. Sie müssen die Erweiterung separat einrichten mithilfe von Tools wie Visual Studio oder PowerShell.
* Um den Prozess der Einrichtung der Diagnose-Erweiterungs mithilfe von PowerShell zu vereinfachen, enthält die paketausgabe von Visual Studio die öffentliche Konfigurations-XML für die diagnoseerweiterung für jede Rolle. Visual Studio verwendet die diagnoseverbindungszeichenfolge zum Ausfüllen der speicherkontoinformationen in der öffentlichen Konfiguration an. Die öffentlichen Konfigurationsdateien werden im Ordner "Extensions" erstellt. Die öffentlichen Konfigurationsdateien verwenden das Namensmuster PaaSDiagnostics. &lt;Rollenname\>. PubConfig.xml. Alle PowerShell-basierten Bereitstellungen können dieses Muster verwenden, um die einzelnen Konfigurationen einer Rolle zuzuordnen.
* Die [Azure-Portal](http://go.microsoft.com/fwlink/p/?LinkID=525040) verwendet die Verbindungszeichenfolge in der cscfg-Datei, um auf die Diagnosedaten zuzugreifen. Die Daten angezeigt, auf die **Überwachung** Registerkarte. Die Verbindungszeichenfolge muss der Dienst auf ausführliche Überwachungsdaten im Portal angezeigt.

## <a name="migrate-projects-to-azure-sdk-26-and-later"></a>Migrieren von Projekten zu Azure SDK 2.6 und höher
Wenn Sie von Azure SDK 2.5 zu Azure SDK 2.6 oder höher migrieren, wenn Sie ein diagnosespeicherkonto in der wadcfgx-Datei angegeben haben, verbleibt das Speicherkonto, in der Datei. Um die Flexibilität der Verwendung verschiedener Speicherkonten für unterschiedliche Speicherkonfigurationen nutzen zu können, müssen fügen Sie die Verbindungszeichenfolge manuell zu Ihrem Projekt hinzu. Wenn Sie ein Projekt aus Azure SDK 2.4 oder früher zu Azure SDK 2.6 migrieren, werden die diagnoseverbindungszeichenfolgen beibehalten. Beachten Sie jedoch die Änderungen im wie Verbindungszeichenfolgen in Azure SDK 2.6, die im vorherigen Abschnitt beschrieben werden.

### <a name="how-visual-studio-determines-the-diagnostics-storage-account"></a>Wie Visual Studio das diagnosespeicherkonto ermittelt
* Wenn eine diagnoseverbindungszeichenfolge in der cscfg-Datei angegeben ist, verwendet Visual Studio sie zum Einrichten der Diagnose-Erweiterungs, während der Veröffentlichung und beim Generieren der öffentlichen XML-Konfigurationsdateien beim Verpacken.
* Wenn eine diagnoseverbindungszeichenfolge in der cscfg-Datei nicht angegeben ist, fragt Visual Studio mit dem Speicherkonto, das in der wadcfgx-Datei zum Einrichten der Diagnose-Erweiterungs für die Veröffentlichung und zum Generieren der öffentlichen XML-Konfigurationsdatei angegeben ist die Dateien während des Verpackens.
* Die Diagnose-Verbindungszeichenfolge in der cscfg-Datei hat Vorrang vor den Storage-Konto in der wadcfgx-Datei. Wenn eine Diagnose-Verbindungszeichenfolge ist angegeben, in der cscfg-Datei, Visual Studio verwendet diese Verbindungszeichenfolge und ignoriert das Speicherkonto in der wadcfgx-Datei.

### <a name="what-does-the-update-development-storage-connection-strings-check-box-do"></a>Wozu dient das Kontrollkästchen "Update Development Storage Connection Strings"?
Die **Entwicklungsspeicher-Verbindungszeichenfolgen für Diagnose und zum Caching mit den Anmeldeinformationen des Microsoft Azure-Speicherkonto aktualisieren, beim Veröffentlichen in Microsoft Azure** Kontrollkästchen ist eine bequeme Möglichkeit, alle Entwicklungsspeicher aktualisieren Konto-Verbindungszeichenfolgen mit dem Azure Storage-Konto, mit dem Sie während der Veröffentlichung angegeben.

Gibt z. B. Wenn Sie dieses Kontrollkästchen, und die diagnoseverbindungszeichenfolge auswählen `UseDevelopmentStorage=true`, beim Veröffentlichen des Projekts in Azure, Visual Studio aktualisiert automatisch die diagnoseverbindungszeichenfolge mit dem Speicherkonto, die im angegeben Veröffentlichungs-Assistenten. Wenn ein echtes Speicherkonto als Diagnose-Verbindungszeichenfolge angegeben wurde, wird jedoch stattdessen dieses Konto verwendet.

## <a name="diagnostics-functionality-differences-in-azure-sdk-24-and-earlier-vs-azure-sdk-25-and-later"></a>Unterschiede zwischen Diagnosefunktionen in Azure SDK 2.4 und früher und. Azure SDK 2.5 und höher
Wenn Sie Ihr Projekt aus Azure SDK 2.4 und früher auf Azure SDK 2.5 oder höher aktualisieren, sollten beachten Sie die folgenden Unterschiede der Diagnosefunktionen:

* **Konfigurations-APIs sind veraltet**. Programmgesteuerte Konfiguration der Diagnose ist verfügbar, bis Azure SDK 2.4 und früher, jedoch in Azure SDK 2.5 und höher veraltet. Wenn die Diagnosekonfiguration derzeit im Code definiert ist, müssen Sie diese Einstellungen im migrierten Projekt für die Diagnose von Grund auf weiterhin neu konfigurieren. Die diagnosekonfigurationsdatei für Azure SDK 2.4 ist "Diagnostics.wadcfg". Die diagnosekonfigurationsdatei für Azure SDK 2.5 und höher ist "Diagnostics.wadcfgx".
* **Diagnose für clouddienstanwendungen kann konfiguriert werden, nur auf Rollenebene**. In Azure SDK 2.5 und höher können nicht Sie Diagnose für clouddienstanwendungen auf Instanzebene einrichten.
* **Jedes Mal, wenn Sie Ihre app bereitstellen, wird die Diagnosekonfiguration aktualisiert**. Dies kann paritätsprobleme verursachen, wenn Sie die Diagnosekonfiguration in Visual Studio Server Explorer ändern, und klicken Sie dann die app erneut bereitstellen.
* **In Azure SDK 2.5 und höher werden Absturzabbilder in der diagnosekonfigurationsdatei und nicht in Code konfiguriert**. Wenn Sie Absturzabbilder im Code konfiguriert haben, müssen Sie die Konfiguration manuell vom Code in die Konfigurationsdatei übertragen. Absturzabbilder werden nicht während der Migration zu Azure SDK 2.6 nicht übertragen.

## <a name="turn-on-diagnostics-in-cloud-service-projects-before-you-deploy-them"></a>Aktivieren der Diagnose in clouddienstprojekten vor der Bereitstellung
In Visual Studio können Sie Diagnosedaten für Rollen erfassen, die in Azure ausgeführt werden soll, wenn Sie den Dienst im Emulator vor der Bereitstellung ausführen. Alle Änderungen an den diagnoseeinstellungen in Visual Studio werden in der Konfigurationsdatei "Diagnostics.wadcfgx" gespeichert. Diese Einstellungen geben das Speicherkonto, in dem Diagnosedaten gespeichert werden, wenn Sie Ihren Clouddienst bereitstellen.

[!INCLUDE [cloud-services-wad-warning](./includes/cloud-services-wad-warning.md)]

### <a name="to-turn-on-diagnostics-in-visual-studio-before-deployment"></a>So schalten Sie die Diagnose in Visual Studio vor der Bereitstellung

1. Wählen Sie auf das Kontextmenü für die Rolle, **Eigenschaften**. In der Rolle **Eigenschaften** wählen Sie im Dialogfeld die **Konfiguration** Registerkarte.
2. In der **Diagnose** Abschnitt, stellen Sie sicher, dass die **Aktivieren der Diagnose** das Kontrollkästchen aktiviert ist.
   
    ![Zugriff auf die Option "Diagnose aktivieren"](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796660.png)
3. Wählen Sie die Schaltfläche mit den Auslassungspunkten (...), um das Speicherkonto für die Diagnose-Daten anzugeben.
   
    ![Geben Sie die zu verwendende Speicherkonto](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796661.png)
4. In der **Verbindungszeichenfolge für Speicherkonto** Dialogfeld geben, ob Sie manuell Anmeldeinformationen eingegebene oder mithilfe des Azure-Speicheremulators, ein Azure-Abonnement, eine Verbindung herstellen möchten.
   
    ![Dialogfeld "Speicherkonto"](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796662.png)
   
   * Bei Auswahl von **Microsoft Azure-Speicheremulator**, die Verbindungszeichenfolge nastaven NA hodnotu `UseDevelopmentStorage=true`.
   * Bei Auswahl von **Ihres Abonnements**, können Sie wählen die Azure-Abonnement, das Sie verwenden möchten und geben Sie einen Kontonamen ein. Wählen Sie zum Verwalten Ihrer Azure-Abonnements **Verwalten von Konten**.
   * Bei Auswahl von **manuell eingegebene Anmeldeinformationen**, geben Sie den Namen und Schlüssel des Azure-Kontos, das Sie verwenden möchten.
5. Anzeigen der **Diagnosekonfiguration** wählen Sie im Dialogfeld **konfigurieren**. Mit Ausnahme von **allgemeine** und **Protokollverzeichnisse**, jede Registerkarte stellt eine diagnosedatenquelle, die Sie erfassen können. Der Standardwert **allgemeine** Registerkarte enthält die Diagnose der folgenden Optionen: **nur Fehler**, **alle Informationen**, und **benutzerdefinierter Plan**. Der Standardwert **nur Fehler** Option verwendet den geringsten Speicherplatz, da es keine Warnungen oder Ablaufverfolgungsmeldungen übertragen. Die **alle Informationen** Option überträgt die meisten Informationen, verwendet den meisten Speicher und ist daher die teuerste Option.

   > [!NOTE]
   > Unterstützte Mindestgröße für "Datenträger Datenträgerkontingent in MB" beträgt 4GB. Wenn Sie Speicherabbilder erfasst werden, erhöhen Sie diese jedoch auf einen höheren Wert wie 10GB.
   >
  
    ![Aktivieren der Azure-Diagnose und Konfiguration](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)
6. Wählen Sie für dieses Beispiel die **benutzerdefinierter Plan** option, damit Sie die gesammelten Daten anpassen können.
7. In der **Datenträgerkontingent in MB** Feld, Sie können festlegen, wie viel Speicherplatz in Ihrem Speicherkonto für Diagnosedaten zuordnen. Sie können ändern, oder übernehmen Sie den Standardwert.
8. Wählen Sie auf jeder Registerkarte für Diagnosedaten, die Sie sammeln möchten, die **Übertragung Aktivieren von \<Protokolltyp\>**  Kontrollkästchen. Wenn auf Anwendungsprotokolle erfassen möchten z. B. die **Anwendungsprotokolle** Registerkarte die **Übertragung von Anwendungsprotokollen aktivieren** Kontrollkästchen. Geben Sie auch andere Informationen, die einzelnen diagnosedatentypen erforderlich ist. Informationen zu Konfigurationen für jede Registerkarte finden Sie im Abschnitt **Einrichten der diagnosedatenquellen** weiter unten in diesem Artikel. 
9. Nachdem Sie Sammlung aller gewünschten Diagnosedaten aktiviert haben, Sie möchten, wählen Sie **OK**.
10. Führen Sie das Azure-Cloud-Dienstprojekt in Visual Studio wie gewohnt. Wie Sie Ihre Anwendung verwenden, wird die Protokollinformationen, die Sie aktiviert zu Azure Storage-Konto gespeichert, die Sie angegeben haben.

## <a name="turn-on-diagnostics-on-azure-virtual-machines"></a>Aktivieren der Diagnose in Azure Virtual machines
In Visual Studio können Sie Diagnosedaten für virtuelle Azure-Computer sammeln.

### <a name="to-turn-on-diagnostics-on-azure-virtual-machines"></a>Zum Aktivieren der Diagnose in Azure Virtual machines

1. Klicken Sie im Server-Explorer wählen Sie den Azure-Knoten, und verbinden Sie dann mit Ihrem Azure-Abonnement, wenn Sie nicht bereits verbunden sind.
2. Erweitern Sie die **VMs** Knoten. Sie können einen neuen virtuellen Computer erstellen oder einen vorhandenen Knoten auswählen.
3. Wählen Sie auf das Kontextmenü für den virtuellen Computer werden sollen, **konfigurieren**. Im Dialogfeld für die Konfiguration der virtuellen Computer wird angezeigt.
   
    ![Konfigurieren von virtuellen Azure-Computer](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796663.png)
4. Wenn sie noch nicht installiert ist, fügen Sie der Microsoft Monitoring Agent-Diagnose-Erweiterung hinzu. Mit dieser Erweiterung können Sie Diagnosedaten für virtuelle Azure-Computer sammeln. Klicken Sie unter **installierte Erweiterungen**in die **verfügbare Erweiterung auswählen** wählen Sie im Dropdown-Listenfeld **Microsoft Monitoring Agent-Diagnose**.
   
    ![Installieren Sie eine Azure-VM-Erweiterung](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766024.png)
   
    > [!NOTE]
   > Andere diagnoseerweiterungen sind für Ihre virtuellen Computer verfügbar. Weitere Informationen finden Sie unter [VM-Erweiterungen und Features für Windows](https://docs.microsoft.com/azure/virtual-machines/windows/extensions-features).
   > 
   > 
5. Zum Hinzufügen der Erweiterung und die Ansicht der **Diagnosekonfiguration** wählen Sie im Dialogfeld **hinzufügen**.
6. Um ein Speicherkonto anzugeben, wählen **konfigurieren**, und wählen Sie dann **OK**.
   
    Jede Registerkarte (mit Ausnahme von **allgemeine** und **Protokollverzeichnisse**) stellt eine diagnosedatenquelle, die Sie erfassen können.
   
    ![Aktivieren der Azure-Diagnose und Konfiguration](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)
   
    Die Standardregisterkarte **allgemeine**, bietet Ihnen die folgenden Optionen für die diagnosedatensammlung: **nur Fehler**, **alle Informationen**, und **benutzerdefinierter Plan**. Die Standardoption, **nur Fehler**, dauert die geringste Menge an Speicher, da es keine Warnungen oder Ablaufverfolgungsmeldungen übertragen. Die **alle Informationen** Option überträgt die meisten Informationen und ist daher die teuerste Option in Bezug auf Speicher.
7. Wählen Sie für dieses Beispiel die **benutzerdefinierter Plan** erfasst Option, damit Sie die Daten anpassen können.
8. Die **Datenträgerkontingent in MB** Feld gibt an, wie viel Speicherplatz, die Sie zuweisen, in Ihrem Speicherkonto für Diagnosedaten möchten. Sie können den Standardwert ändern, wenn Sie möchten.
9. Wählen Sie auf jeder Registerkarte für Diagnosedaten, die Sie sammeln möchten, die **Übertragung Aktivieren von \<Protokolltyp\>**  Kontrollkästchen.
   
    Wählen Sie beispielsweise, wenn Sie Anwendungsprotokolle erfassen möchten, die **Übertragung von Anwendungsprotokollen aktivieren** auf das Kontrollkästchen der **Anwendungsprotokolle** Registerkarte. Geben Sie auch andere Informationen, die für die einzelnen diagnosedatentypen erforderlich sind. Informationen zu Konfigurationen für jede Registerkarte finden Sie im Abschnitt **Einrichten der diagnosedatenquellen** weiter unten in diesem Artikel.
10. Nachdem Sie die Sammlung aller gewünschten Diagnosedaten, die Sie möchten aktiviert haben, wählen Sie **OK**.
11. Das aktualisierte Projekt zu speichern.
    
    Eine Nachricht in die **Microsoft Azure-Aktivitätsprotokoll** Fenster gibt an, dass der virtuelle Computer aktualisiert wurde.

## <a name="set-up-diagnostics-data-sources"></a>Einrichten von diagnosedatenquellen
Nachdem Sie die Sammlung von Diagnosedaten aktivieren, können Sie genau, welche Datenquellen Sie sammeln möchten und welche Informationen gesammelt werden. Die nächsten Abschnitte beschreiben die Registerkarten in der **Diagnosekonfiguration** Dialogfeld und welche einzelnen Konfigurationsoptionen.

### <a name="application-logs"></a>Anwendungsprotokolle
Anwendungsprotokolle haben Diagnoseinformationen, die von einer Webanwendung erstellt wird. Wenn Sie Anwendungsprotokolle erfassen möchten, wählen Sie die **Übertragung von Anwendungsprotokollen aktivieren** Kontrollkästchen. Ändern Sie zum Erhöhen oder verringern das Intervall zwischen der Übertragung von Anwendungsprotokollen an Ihr Speicherkonto, das **Übertragungszeitraum (Min.)** Wert. Sie ändern auch die Menge an Informationen, die im Protokoll aufgezeichnet werden, durch Festlegen der **Protokollebene** Wert. Wählen Sie z. B. **ausführlich** um weitere Informationen zu erhalten, oder wählen **kritisch** nur kritische Fehler zu erfassen. Wenn Sie einen bestimmten Diagnoseanbieter, der Anwendungsprotokolle ausgibt haben, können Sie die Protokolle erfassen, indem Sie die GUID des Anbieters im Hinzufügen der **Anbieter-GUID** Feld.

  ![Anwendungsprotokolle](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758145.png)

Weitere Informationen zu Anwendungsprotokollen finden Sie unter [Aktivieren der diagnoseprotokollierung für Web-Apps in Azure App Service](/azure/app-service/web-sites-enable-diagnostic-log).

### <a name="windows-event-logs"></a>Windows-Ereignisprotokolle
Wenn Windows-Ereignisprotokolle erfassen möchten, wählen Sie die **Übertragung von Windows-Ereignisprotokollen aktivieren** Kontrollkästchen. Ändern Sie zum Erhöhen oder verringern das Intervall zwischen der Übertragung von Ereignisprotokollen an Ihr Speicherkonto, das **Übertragungszeitraum (Min.)** Wert. Wählen Sie die Kontrollkästchen für die Typen von Ereignissen, die Sie nachverfolgen möchten.

![Ereignisprotokolle](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796664.png)

Wenn Sie Azure SDK 2.6 oder höher verwenden, und Sie eine benutzerdefinierte Datenquelle angeben möchten, geben Sie ihn in das **\<Datenquellenname\>** Textfeld ein, und wählen Sie dann **hinzufügen**. Die Datenquelle wird die Datei "diagnostics.cfcfg" hinzugefügt.

Wenn Sie Azure SDK 2.5 verwenden und eine benutzerdefinierte Datenquelle angeben möchten, können Sie ihn zum Hinzufügen der `WindowsEventLog` im Abschnitt "Diagnostics.wadcfgx"-Datei wie im folgenden Beispiel:

```
<WindowsEventLog scheduledTransferPeriod="PT1M">
   <DataSource name="Application!*" />
   <DataSource name="CustomDataSource!*" />
</WindowsEventLog>
```
### <a name="performance-counters"></a>Leistungsindikatoren
Leistungsindikatorinformationen können Sie die Engpässe im System suchen und die System- und Anwendungsleistung zu optimieren. Weitere Informationen finden Sie unter [erstellen und Verwenden von Leistungsindikatoren in einer Azure-Anwendung](https://msdn.microsoft.com/library/azure/hh411542.aspx). Um Leistungsindikatoren zu erfassen, wählen Sie die **Übertragung der Leistungsindikatoren aktivieren** Kontrollkästchen. Ändern Sie zum Erhöhen oder verringern das Intervall zwischen der Übertragung von Ereignisprotokollen an Ihr Speicherkonto, das **Übertragungszeitraum (Min.)** Wert. Wählen Sie die Kontrollkästchen für die Leistungsindikatoren, die Sie nachverfolgen möchten.

![Leistungsindikatoren](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758147.png)

Um einen Leistungsindikator nachzuverfolgen, der nicht aufgeführt ist, geben Sie den Leistungsindikator mit der vorgeschlagenen Syntax ein. und wählen Sie dann **hinzufügen**. Das Betriebssystem auf dem virtuellen Computer bestimmt, welche Leistungsindikatoren Sie nachverfolgen können. Weitere Informationen zur Syntax finden Sie unter [angeben ein indikatorpfads](https://msdn.microsoft.com/library/windows/desktop/aa373193.aspx).

### <a name="infrastructure-logs"></a>Protokoly infrastruktury
Infrastrukturprotokolle enthalten Informationen zu Azure-Diagnoseinfrastruktur, das RemoteAccess-Modul und das RemoteForwarder-Modul. Um Informationen über Infrastrukturprotokolle zu sammeln, wählen Sie die **Übertragung von Infrastrukturprotokollen aktivieren** Kontrollkästchen. Ändern Sie zum Erhöhen oder verringern das Intervall zwischen der Übertragung von infrastrukturprotokollen an Ihr Speicherkonto, das **Übertragungszeitraum (Min.)** Wert.

![Diagnoseinfrastrukturprotokolle](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758148.png)

Weitere Informationen finden Sie unter [Sammeln von Protokollierungsdaten mit der Azure-Diagnose](https://msdn.microsoft.com/library/azure/gg433048.aspx).

### <a name="log-directories"></a>Protokollverzeichnisse
Protokollverzeichnisse enthalten Daten, die aus protokollverzeichnissen für Anforderungen (Internet Information Services, IIS), fehlerhaften Anforderungen oder, die von Ihnen ausgewählten Ordnern gesammelt. Wenn Sie Protokollverzeichnisse erfassen möchten, wählen Sie die **Übertragung von Protokollverzeichnissen aktivieren** Kontrollkästchen. Ändern Sie zum Erhöhen oder verringern das Intervall zwischen der Übertragung von Protokollen in Ihr Speicherkonto, das **Übertragungszeitraum (Min.)** Wert.

Wählen Sie die Kontrollkästchen der Protokolle, die Sie erfassen wie z. B., möchten **IIS-Protokolle** und **Anforderungsfehlern** Protokolle. Standardmäßige speichercontainernamen angegeben werden, aber Sie können die Namen ändern.

Sie können Protokolle aus einem beliebigen Ordner erfassen. Geben Sie den Pfad in der **Protokoll aus absolutem Verzeichnis** Abschnitt, und wählen Sie dann **Verzeichnis hinzufügen**. Die Protokolle werden in den angegebenen Containern erfasst.

![Protokollverzeichnisse](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796665.png)

### <a name="etw-logs"></a>ETW-Protokolle
Bei Verwendung von [Ereignisablaufverfolgung für Windows-Ereignis](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx) (ETW) und ETW-Protokolle erfassen, wählen Sie die **Übertragung von ETW-Protokollen aktivieren** Kontrollkästchen. Ändern Sie zum Erhöhen oder verringern das Intervall zwischen der Übertragung von Protokollen in Ihr Speicherkonto, das **Übertragungszeitraum (Min.)** Wert.

Von Ereignisquellen und ereignismanifesten, die Sie angeben, werden die Ereignisse erfasst. In einer Ereignisquelle, an die **Ereignisquellen** Abschnitt, geben Sie einen Namen, und wählen Sie dann **Ereignisquelle hinzufügen**. Auf ähnliche Weise können Sie ein ereignismanifest im Angeben der **Ereignismanifeste** Abschnitt, und wählen Sie dann **Ereignismanifest hinzufügen**.

![ETW-Protokolle](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766025.png)

Das ETW-Framework wird in ASP.NET durch Klassen im unterstützt die [System.Diagnostics.aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110)) Namespace. Der Microsoft.WindowsAzure.Diagnostics-Namespace, der erbt und diese erweitert [System.Diagnostics.aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110)) Klassen, ermöglicht die Verwendung von [System.Diagnostics.aspx](https://msdn.microsoft.com/library/system.diagnostics(v=vs.110)) als eine Protokollierung Framework in Azure-Umgebung. Weitere Informationen finden Sie unter [kontrollieren der Protokollierung und Ablaufverfolgung in Microsoft Azure](https://msdn.microsoft.com/magazine/ff714589.aspx) und [Aktivieren der Diagnose in Azure Cloud Services und Virtual Machines](/azure/cloud-services/cloud-services-dotnet-diagnostics).

### <a name="crash-dumps"></a>Absturzabbilder
Wählen Sie zum Erfassen von Informationen, wenn eine Rolleninstanz abstürzt, der **Übertragung von Absturzabbildern aktivieren** Kontrollkästchen. (Da ASP.NET die meisten Ausnahmen behandelt, ist dies in der Regel nur für Workerrollen nutzen.) Ändern Sie zum Erhöhen oder verringern den Prozentsatz des Speicherplatzes für die die Absturzabbilder, die **Verzeichniskontingent (%)** Wert. Sie können den Speichercontainer, in dem die Absturzabbilder gespeichert werden, und wählen Sie, ob Sie aufzeichnen möchten, Ändern einer **vollständige** oder **Mini** sichern.

Die derzeit nachverfolgten Prozesse werden im nächsten Screenshot aufgeführt. Wählen Sie die Kontrollkästchen für die Prozesse, die Sie erfassen möchten. Um einen anderen Prozess zur Liste hinzuzufügen, geben Sie den Namen des Prozesses, und wählen Sie dann **Prozess hinzufügen**.

![Absturzabbilder](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766026.png)

Weitere Informationen finden Sie unter [kontrollieren der Protokollierung und Ablaufverfolgung in Microsoft Azure](https://msdn.microsoft.com/magazine/ff714589.aspx) und [Microsoft Azure-Diagnose Teil 4: benutzerdefinierte Protokollierung-Komponenten und Azure Diagnostics 1.3 Changes](http://justazure.com/microsoft-azure-diagnostics-part-4-custom-logging-components-azure-diagnostics-1-3-changes/).

## <a name="view-the-diagnostics-data"></a>Anzeigen von Diagnosedaten
Nachdem Sie die Diagnosedaten für einen Clouddienst oder virtuellen Computer gesammelt haben, können Sie es anzeigen.

### <a name="to-view-cloud-service-diagnostics-data"></a>Zum Anzeigen von Diagnosedaten für Cloud-Dienst
1. Bereitstellen Sie des Clouddiensts wie gewohnt aus, und führen Sie sie.
2. Sie können die Diagnose-Daten in einem Bericht, den generiert Visual Studio, oder in Tabellen in Ihrem Speicherkonto anzeigen. Zum Anzeigen der Daten in einem Bericht, Öffnen von Cloud-Explorer oder Server-Explorer öffnen das Kontextmenü des Knotens für die Rolle, die Sie möchten, und wählen Sie dann **Anzeigen von Diagnosedaten**.
   
    ![Anzeigen von Diagnosedaten](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748912.png)
   
    Es wird ein Bericht, der den verfügbaren Daten angezeigt.
   
    ![Microsoft Azure-Diagnosebericht in Visual Studio](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796666.png)
   
    Wenn Sie die neuesten Daten nicht angezeigt werden, müssen Sie möglicherweise warten, bis der übertragungszeitraum leaseunterbrechungszeitraums abgewartet.
   
    Um die Daten sofort zu aktualisieren, wählen die **aktualisieren** Link. Um die Daten automatisch aktualisiert haben, wählen Sie ein Intervall in den **automatische Aktualisierung** im Dropdown Listenfeld. Wählen Sie zum Exportieren der Fehlerdaten die **exportieren nach CSV** klicken, um eine durch Trennzeichen getrennte Datei zu erstellen, die Sie in einem Excel-Arbeitsblatt öffnen können.
   
    Öffnen Sie im Cloud-Explorer oder Server-Explorer das Speicherkonto, das mit der Bereitstellung zugeordnet ist.
3. Öffnen Sie die Diagnosetabellen im tabellenviewer, und klicken Sie dann überprüfen Sie die Daten, die Sie erfasst. Für IIS-Protokolle und benutzerdefinierte Protokolle können Sie einen blobcontainer öffnen. Die folgende Tabelle enthält die Tabellen oder Blob-Container, die die Daten für die verschiedenen Protokolldateien enthalten. Zusätzlich zu den Daten für diese Protokolldatei enthalten die Tabelleneinträge **"eventtickcount"**, **DeploymentId**, **Rolle**, und **"roleinstance"** , können Sie ermitteln, welche virtuellen Computer und welche Rolle die Daten generiert hat und wann. 
   
   | Diagnosedaten | Beschreibung | Speicherort |
   | --- | --- | --- |
   | Anwendungsprotokolle |Protokolle, die der Code generiert, durch Aufrufen der Methoden, die von der **"System.Diagnostics.Trace"** Klasse. |WADLogsTable |
   | Ereignisprotokolle |Daten aus den Windows-Ereignisprotokollen auf den virtuellen Computern. Windows speichert Informationen in diesen Protokollen, aber Anwendungen und Dienste auch mithilfe der Protokolle, um Fehler zu melden oder Informationen zu protokollieren. |WADWindowsEventLogsTable |
   | Leistungsindikatoren |Sie können Daten zu jedem Leistungsindikator erfassen, die auf dem virtuellen Computer verfügbar ist. Das Betriebssystem bietet Leistungsindikatoren, darunter viele Statistiken, wie die Zeit für Arbeitsspeicher und Prozessorzeit. |WADPerformanceCountersTable |
   | Protokoly infrastruktury |Protokolle, die von der Diagnoseinfrastruktur selbst generiert werden. |WADDiagnosticInfrastructureLogsTable |
   | IIS-Protokolle |Protokolle, die webanforderungen aufzeichnen. Wenn Sie Ihren Clouddienst eine beträchtliche Menge an Datenverkehr abruft, können diese Protokolle sehr lang sein. Es ist eine gute Idee, sammeln und speichern Sie diese Daten nur bei Bedarf. |Sie finden Protokolle mit fehlgeschlagenen Anforderungen in den Blob-Container Wad-Iis-Failedreqlogs unter einem Pfad für diese Bereitstellung, Rolle und Instanz. Sie finden die vollständigen Protokolle unter "Wad-Iis-LogFiles". Einträge für jede Datei werden in der WADDirectories-Tabelle vorgenommen. |
   | Absturzabbilder |Stellt binäre Abbilder des Prozesses für den Cloud-Dienst (in der Regel eine workerrolle) bereit. |WAD-Crush-Dumps-blobcontainer |
   | Benutzerdefinierte Protokolldateien |Die Protokolle der Daten, die Sie vordefiniert. |Sie können im Code den Speicherort der benutzerdefinierten Protokolldateien in Ihrem Speicherkonto angeben. Beispielsweise können Sie einen benutzerdefinierten blobcontainer angeben. |
4. Wenn die Daten eines beliebigen Typs abgeschnitten ist, können Sie versuchen, erhöhen den Puffer für diesen Typ oder die Verkürzung des Intervalls zwischen Datenübertragungen vom virtuellen Computer in Ihrem Speicherkonto.
5. (Optional) Löschen von Daten aus dem Speicherkonto gelegentlich auf die Gesamtspeicherkosten zu verringern.
6. Wenn Sie eine vollständige Bereitstellung durchführen, die diagnostics.cscfg-Datei (bzw. für das Azure SDK 2.5) in Azure aktualisiert, und der Cloud-Dienst übernimmt alle Änderungen an Ihrer Diagnosekonfiguration. Wenn Sie stattdessen eine vorhandene Bereitstellung aktualisieren, ist nicht die cscfg-Datei in Azure nicht aktualisiert. Sie können diagnoseeinstellungen jedoch weiterhin ändern, anhand der Schritte im nächsten Abschnitt. Weitere Informationen zum Durchführen einer vollständigen Bereitstellung und Aktualisieren einer vorhandenen Bereitstellung finden Sie unter [Assistent zum Veröffentlichen eines Azure-Anwendungen](vs-azure-tools-publish-azure-application-wizard.md).

### <a name="to-view-virtual-machine-diagnostics-data"></a>VM-Diagnose-Daten anzeigen
1. Wählen Sie auf das Kontextmenü für den virtuellen Computer, **Anzeigen von Diagnosedaten**.
   
    ![Anzeigen von Diagnosedaten in einer Azure-VM](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766027.png)
   
    Die **diagnosezusammenfassung** Dialogfeld wird angezeigt.
   
    ![Souhrn diagnostiky auf dem virtuellen Azure-Computer](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796667.png)  
   
    Wenn Sie die neuesten Daten nicht angezeigt werden, müssen Sie möglicherweise warten, bis der übertragungszeitraum leaseunterbrechungszeitraums abgewartet.
   
    Um die Daten sofort zu aktualisieren, wählen die **aktualisieren** Link. Um die Daten automatisch aktualisiert haben, wählen Sie ein Intervall in den **automatische Aktualisierung** im Dropdown Listenfeld. Wählen Sie zum Exportieren der Fehlerdaten die **exportieren nach CSV** klicken, um eine durch Trennzeichen getrennte Datei zu erstellen, die Sie in einem Excel-Arbeitsblatt öffnen können.

## <a name="set-up-cloud-service-diagnostics-after-deployment"></a>Einrichten der clouddienstdiagnose nach der Bereitstellung
Wenn Sie ein Problem mit einem Clouddienst untersuchen, der bereits ausgeführt wird, sollten Sie zum Sammeln von Daten, die Sie angegeben haben, bevor Sie der Bereitstellung der Rolle. In diesem Fall können Sie das Sammeln von Daten durch Ändern der Einstellungen im Server-Explorer starten. Sie können festlegen, um die Diagnose für eine einzelne Instanz oder für alle Instanzen in einer Rolle sein, je nachdem, ob Sie öffnen die **Diagnosekonfiguration** Dialogfeld über das Kontextmenü für die Instanz oder für die Rolle. Wenn Sie den rollenknoten konfigurieren, gelten alle Änderungen, die Sie vornehmen, für alle Instanzen. Wenn Sie den Instanzknoten konfigurieren, gelten alle Änderungen, die Sie vornehmen, nur für diese Instanz.

### <a name="to-set-up-diagnostics-for-a-running-cloud-service"></a>Zum Einrichten der Diagnose für einen ausgeführten Clouddienst
1. Erweitern Sie im Server-Explorer die **Clouddienste** Knoten, und erweitern Sie dann die Liste der Knoten, um die Rolle oder Instanz (oder beides) zu suchen, die Sie untersuchen möchten.
   
    ![Konfigurieren der Diagnose](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748913.png)
2. Wählen Sie im Kontextmenü für einen Instanzknoten oder einen rollenknoten **Diagnoseeinstellungen aktualisieren**, und wählen Sie dann die diagnoseeinstellungen, die Sie sammeln möchten.
   
    Informationen zu den Konfigurationseinstellungen finden Sie im Abschnitt **Einrichten der diagnosedatenquellen** in diesem Artikel. Informationen über das Anzeigen von Diagnosedaten finden Sie im Abschnitt **Anzeigen von Diagnosedaten** in diesem Artikel.
   
    Wenn Sie die Datensammlung im Server-Explorer ändern, bleiben die Änderungen wirksam, bis Sie den Clouddienst vollständig erneut bereitstellen. Bei Verwendung der Standardeinstellungen veröffentlichungseinstellungen, die Änderungen nicht überschrieben. Die Standardeinstellung für die Veröffentlichung wird die vorhandene Bereitstellung aktualisieren, anstatt auf eine vollständige erneute Bereitstellung. Um sicherzustellen, dass die Einstellungen zum Zeitpunkt der Bereitstellung zu löschen, wechseln Sie zu der **Erweiterte Einstellungen** im Veröffentlichungs-Assistenten, und klicken Sie dann deaktivieren Sie die **bereitstellungsaktualisierung** Kontrollkästchen. Wenn Sie dieses Kontrollkästchen eine erneute Bereitstellung, die Einstellungen zurückgesetzt, die denen in der wadcfgx-Datei (oder wadcfg-Datei) festgelegt die **Eigenschaften** -Editor für die Rolle. Wenn Sie Ihre Bereitstellung aktualisieren, behält Azure die früheren Einstellungen an.

## <a name="troubleshoot-azure-cloud-service-issues"></a>Problembehandlung bei der Azure-Cloud-Dienst
Wenn Sie mit Ihren clouddienstprojekten, Probleme wie z. B. eine Rolle, die einen Status "beschäftigt" hat wiederholt wiederverwendet wird, oder Ausgabe eines internen Serverfehlers, stehen Tools und Techniken, mit denen Sie zum Diagnostizieren und beheben Sie das Problem. Spezifische Beispiele für allgemeine Probleme und Lösungen, und eine Übersicht über die Konzepte und Tools, die Sie zum Diagnostizieren und Beheben dieser Fehler verwenden können, finden Sie unter [Azure PaaS compute Diagnostics Data](http://blogs.msdn.com/b/kwill/archive/2013/08/09/windows-azure-paas-compute-diagnostics-data.aspx).

## <a name="q--a"></a>Fragen und Antworten
**Was ist die Größe des Puffers, und wie groß sollte er sein?**

Für jede virtuelle Computerinstanz gelten Kontingente an, wie viele Diagnosedaten auf dem lokalen Dateisystem gespeichert werden können. Darüber hinaus geben Sie eine Puffergröße für jeden Typ von Diagnosedaten, die verfügbar ist. Diese Puffergröße fungiert als individuelles Kontingent für diesen Datentyp ab. Um zu bestimmen, das Gesamtkontingent und der Menge an Arbeitsspeicher, finden Sie unten im Dialogfeld für den diagnosedatentyp aus. Wenn Sie größere Puffer oder mehr Datentypen angeben, müssen Sie dem Gesamtkontingent. Sie können das Gesamtkontingent ändern, indem Sie die Konfigurationsdatei "Diagnostics.wadcfg" bzw. "Diagnostics.wadcfgx" ändern. Die Diagnose-Daten ist auf das gleiche Dateisystem wie Ihre Anwendungsdaten gespeichert. Wenn Ihre Anwendung eine große Menge an Speicherplatz verwendet, darf nicht Sie das Gesamtkontingent für die Diagnose nicht erhöhen.

**Was ist das Übertragungsintervall, und wie lange sollte er sein?**

Der übertragungszeitraum ist die Zeitspanne, die abgelaufen ist, zwischen Daten erfasst. Nach jedem übertragungszeitraum werden Daten vom im lokalen Dateisystem auf einem virtuellen Computer auf Tabellen in Ihrem Speicherkonto verschoben. Wenn die Menge der Daten, die gesammelt wurden, werden das Kontingent vor dem Ende eines Übertragungszeitraums übersteigt, werden ältere Daten verworfen. Wenn Sie Daten verlieren, da Ihre Daten die Puffergröße oder das gesamte Kontingent überschreiten, empfiehlt es sich um den übertragungszeitraum verkürzen.

**Welcher Zeitzone sind die Zeitstempel?**

Zeitstempel werden in der lokalen Zeitzone des Rechenzentrums, die Ihren Cloud-Dienst hostet. Es werden die folgenden drei Zeitstempelspalten in den Protokolltabellen verwendet:

* **PreciseTimeStamp**: der ETW-Zeitstempel des Ereignisses. D. h. die Zeit, die das Ereignis wird vom Client protokolliert.
* **Zeitstempel**: der Wert für **PreciseTimeStamp** der precisetimestamp abgerundet. Z. B. wenn die uploadhäufigkeit 5 Minuten und das Ereignis Zeitpunkt 00:17:12 ist, ist die Zeitstempel, 00:15:00.
* **Zeitstempel**: der Zeitstempel, an dem die Entität in der Azure-Tabelle erstellt wurde.

**Wie verwalte ich Kosten beim Sammeln von Diagnoseinformationen?**

Die Standardeinstellungen (**Protokollebene** festgelegt **Fehler**, und **übertragungszeitraum** festgelegt **1 Minute**) dienen, um Kosten zu minimieren. Ihre Serverkosten steigen, wenn Sie weitere Diagnosedaten sammeln, oder wenn Sie den übertragungszeitraum verkürzen. Sammeln Sie nicht mehr Daten als benötigt werden, und vergessen Sie nicht die Datensammlung deaktivieren, wenn Sie nicht mehr benötigen. Sie können immer sie in diesem Fall auch zur Laufzeit aktivieren, wie weiter oben in diesem Artikel beschrieben.

**Wie erfasse ich Protokolle zu fehlgeschlagenen Anforderungen von IIS?**

Standardmäßig erfasst IIS keine Protokolle zu fehlgeschlagenen Anforderungen. Sie können IIS so einrichten, um Protokolle zu fehlgeschlagenen Anforderungen durch Bearbeiten der Datei "Web.config" für Ihre Webrolle zu sammeln.

**Ich erhalte keine Nachverfolgungsinformationen von RoleEntryPoint-Methoden wie OnStart. Wo liegt der Fehler?**

Die Methoden der **RoleEntryPoint** werden im Kontext von WAIISHost.exe und nicht von IIS aufgerufen. Die Konfigurationsinformationen in "Web.config", die normalerweise aktiviert die Ablaufverfolgung gelten nicht. Um dieses Problem zu beheben, Ihrem Webrollenprojekt eine config-Datei hinzugefügt, und nennen Sie die Datei mit der Ausgabeassembly übereinstimmt, die enthält die **RoleEntryPoint** Code. In der Standard-Webrollenprojekt sollte der Name der config-Datei "waiishost.exe.config" lauten. Fügen Sie dieser Datei die folgenden Zeilen hinzu:

```
<system.diagnostics>
  <trace>
      <listeners>
          <add name “AzureDiagnostics” type=”Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitorTraceListener”>
              <filter type=”” />
          </add>
      </listeners>
  </trace>
</system.diagnostics>
```

In der **Eigenschaften** legen die **in Ausgabeverzeichnis kopieren** Eigenschaft **immer kopieren**.

## <a name="next-steps"></a>Nächste Schritte
Weitere Informationen zur diagnoseprotokollierung in Azure finden Sie unter [Aktivieren der Diagnose in Azure Cloud Services und Virtual Machines](/azure/cloud-services/cloud-services-dotnet-diagnostics.md) und [Aktivieren der diagnoseprotokollierung für Web-Apps in Azure App Service](/azure/app-service/web-sites-enable-diagnostic-log).


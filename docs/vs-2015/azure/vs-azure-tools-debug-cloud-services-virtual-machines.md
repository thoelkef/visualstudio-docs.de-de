---
title: Debuggen eines Azure-Clouddienst oder virtuellen Computer in Visual Studio | Microsoft-Dokumentation
description: Debuggen eines Cloud-Diensts oder virtuellen Computers in Visual Studio
author: mikejo5000
manager: douge
ms.assetid: 945e06e0-2100-41af-b218-72347367ddab
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.openlocfilehash: b2c67ce81a42df4a17761fcee2dcd2f8a67c4941
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002008"
---
# <a name="debugging-an-azure-cloud-service-or-virtual-machine-in-visual-studio"></a>Debuggen eines Azure-Clouddienst oder virtuellen Computer in Visual Studio

Visual Studio bietet verschiedene Optionen für das Debuggen von Azure Cloud Services und Virtual Machines.

## <a name="debug-your-cloud-service-on-your-local-computer"></a>Debuggen des Clouddiensts auf dem lokalen computer

Sie können Zeit sparen und Geld sparen, mit dem Azure compute-Emulator zum Debuggen des Clouddiensts auf einem lokalen Computer. Durch lokales Debuggen eines Diensts, bevor Sie sie bereitstellen, können Sie die Zuverlässigkeit und Leistung verbessern, ohne dass Kosten für Compute-Zeit. Allerdings können einige Fehler nur wenn Sie einen Cloud-Dienst in Azure ausführen auftreten selbst. Sie können diese Fehler debuggen, wenn Sie Remotedebuggen beim Veröffentlichen des Diensts und dann den Debugger, zu einer Rolleninstanz Anfügen aktivieren.

Der Emulator simuliert den Azure Compute-Dienst und in Ihrer lokalen Umgebung ausgeführt werden, sodass Sie testen und des Clouddiensts, Debuggen bevor Sie sie bereitstellen können. Der Emulator behandelt den Lebenszyklus der Rolleninstanzen und bietet Zugriff auf simulierte Ressourcen wie lokalen Speicher. Beim Debuggen oder des Diensts in Visual Studio ausführen, der Emulator automatisch als hintergrundanwendung gestartet, und klicken Sie dann den Dienst im Emulator bereitgestellt. Sie können den Emulator verwenden, um Ihren Dienst anzeigen, wenn sie in der lokalen Umgebung ausgeführt wird. Sie können die vollständige Version oder die express-Version des Emulators ausführen. (Beginnend mit Azure 2.3, ist die express-Version des Emulators Standard.) Finden Sie unter [Verwenden von Emulator Express zum Ausführen und Debuggen einen Cloud-Dienst lokal](vs-azure-tools-emulator-express-debug-run.md).

### <a name="to-debug-your-cloud-service-on-your-local-computer"></a>Zum Debuggen des Clouddiensts auf dem lokalen computer

1. Wählen Sie auf der Menüleiste **Debuggen**, **Debuggen starten** um Ihrem Azure-Cloud-Dienstprojekt auszuführen. Als Alternative können Sie F5 drücken. Sie sehen eine Meldung, die der Serveremulator gestartet wird. Wenn der Emulator gestartet wird, wird Sie durch das Taskleistensymbol bestätigt.

    ![Azure-Emulator in der Taskleiste](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC783828.png)

2. Die Benutzeroberfläche des Serveremulators anzeigen, öffnen Sie das Kontextmenü für das Azure-Symbol im Infobereich der Taskleiste, und wählen Sie dann **Serveremulator-Benutzeroberfläche anzeigen**.

    Im linken Bereich der Benutzeroberfläche zeigt die Dienste, die derzeit bereitgestellt werden, um den Serveremulator sowie die Rolleninstanzen, die jedem Dienst ausgeführt werden. Sie können den Dienst oder die Rollen, um Lebenszyklus, Protokollierung und Diagnoseinformationen im rechten Bereich anzuzeigen. Wenn Sie den Fokus in den oberen Rand eines enthaltenen Fensters setzen, wird diese erweitert, um im rechten Bereich auszufüllen.

3. Durchlaufen Sie die Anwendung durch Auswählen von Befehlen auf die **Debuggen** Menü und Festlegen von Haltepunkten in Ihrem Code. Wie Sie die Anwendung im Debugger durchlaufen schrittweise, werden die Bereiche mit den aktuellen Status der Anwendung aktualisiert. Wenn Sie das Debuggen beenden, wird die anwendungsbereitstellung gelöscht. Wenn Ihre Anwendung eine Webrolle einschließt und Sie die Startaktion zum Starten des Webbrowsers festgelegt haben, startet Visual Studio Ihre Webanwendung im Browser. Wenn Sie die Anzahl der Instanzen einer Rolle in der Dienstkonfiguration ändern, müssen Sie den Clouddienst beenden, und klicken Sie dann den Debugvorgang neu starten, damit Sie diese neuen Instanzen der Rolle Debuggen können.

    **Hinweis:** beim Ausführen oder Debuggen des Diensts beenden, der lokale Serveremulator und -Speicheremulator nicht beendet. Sie müssen explizit über den Infobereich beendet werden.

## <a name="debug-a-cloud-service-in-azure"></a>Debuggen eines Clouddiensts in Azure

Um einen Cloud-Dienst von einem Remotecomputer zu debuggen, müssen Sie diese Funktion explizit aktivieren, wenn Sie Ihren Clouddienst bereitstellen, damit erforderliche Dienste (z. B. msvsmon.exe) auf den virtuellen Computern installiert sind, auf denen die Rolleninstanzen ausgeführt. Wenn Sie das Remotedebuggen, wenn der Dienst veröffentlicht aktiviert haben, müssen Sie den Dienst, die mit aktiviertem Remotedebuggen erneut veröffentlichen.

Wenn Sie das Remotedebuggen für einen Cloud-Dienst aktivieren, keine leistungsverschlechterung noch fallen zusätzliche Gebühren an. Verwenden Sie keine Remotedebuggen für einen Produktionsdienst, da sich negativ auf Clients Nutzer des Diensts auswirken können.

> [!NOTE]
> Wenn Sie einen Clouddienst über Visual Studio veröffentlichen, können Sie aktivieren **IntelliTrace** für alle Rollen in diesem Dienst, die auf .NET Framework 4 oder .NET Framework 4.5 ausgerichtet. Mithilfe von **IntelliTrace**, können Sie Ereignisse untersuchen, die in einer Rolleninstanz in der Vergangenheit aufgetreten sind und den Kontext zu diesem Zeitpunkt reproduzieren. Finden Sie unter [Debuggen eines veröffentlichten Clouddiensts mit IntelliTrace und Visual Studio](http://go.microsoft.com/fwlink/?LinkID=623016) und [mit IntelliTrace](https://msdn.microsoft.com/library/dd264915.aspx).

### <a name="to-enable-remote-debugging-for-a-cloud-service"></a>Aktivieren des Remotedebuggens für einen Cloud-Dienst

1. Öffnen Sie das Kontextmenü für das Azure-Projekt, und wählen Sie dann **veröffentlichen**.

2. Wählen Sie die **Staging** Umgebung und die **Debuggen** Konfiguration.

    Dies ist nur eine Empfehlung. Wahlweise können Sie Ihre Test-Umgebungen in einer produktionsumgebung ausführen. Allerdings können Sie Benutzer beeinträchtigen, wenn Sie das Remotedebuggen in der produktionsumgebung aktivieren. Sie können die Releasekonfiguration auswählen, aber die Debugkonfiguration vereinfacht das Debuggen.

    ![Wählen Sie die Debug-Konfiguration](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746717.gif)

3. Führen Sie die üblichen Schritte aus, aber wählen Sie die **Remotedebugger für alle Rollen aktivieren** auf das Kontrollkästchen der **Erweiterte Einstellungen** Registerkarte.

    ![Debug-Konfiguration](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746718.gif)

### <a name="to-attach-the-debugger-to-a-cloud-service-in-azure"></a>Um den Debugger anzufügen, um einen Clouddienst in Azure

1. Erweitern Sie im Server-Explorer den Knoten für Ihren Clouddienst aus.

2. Öffnen Sie das Kontextmenü für die Rolle oder Rolleninstanz, die Sie anfügen, und wählen Sie dann möchten **Debugger anfügen**.

    Wenn Sie eine Rolle Debuggen, fügt Visual Studio-Debugger für jede Instanz dieser Rolle an. Der Debugger wird an einem Haltepunkt für die erste Rolleninstanz unterbrochen, die diese Codezeile ausführt und alle Bedingungen dieses Haltepunkts erfüllt. Wenn Sie eine Instanz Debuggen, den Debugger angefügt nur dieser Instanz, und wird an einem Haltepunkt nur, wenn dieser bestimmten Instanz diese Codezeile ausführt und die Bedingungen des Haltepunkts erfüllt unterbrochen.

    ![Debugger anfügen](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746719.gif)

3. Nachdem der Debugger an eine Instanz angefügt wurde, werden wie gewohnt debuggen. Der Debugger wird automatisch an den entsprechenden Hostprozess für Ihre Rolle angefügt. Je nachdem, was die Rolle ist wird der Debugger w3wp.exe, WaWorkerHost.exe oder WaIISHost.exe angefügt. Erweitern Sie den Instanzknoten im Server-Explorer, um den Prozess zu überprüfen, zu dem der Debugger angefügt ist. Finden Sie unter [Azure-Rollenarchitektur](http://blogs.msdn.com/b/kwill/archive/2011/05/05/windows-azure-role-architecture.aspx) für Weitere Informationen zu Azure-Prozessen.

    ![Wählen Sie Code (Dialogfeld)](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

4. Um die Prozesse zu identifizieren, zu denen der Debugger angefügt ist, öffnen Sie das Dialogfeld "Prozesse", klicken Sie auf der Menüleiste die Optionen Debug "," Windows "," Prozesse. (Tastatur: Strg + Alt + Z) Um einen bestimmten Prozess zu trennen, öffnen Sie das Kontextmenü, und wählen Sie dann **Prozess abtrennen**. Oder suchen Sie den Instanzknoten in Server-Explorer, suchen Sie den Prozess, öffnen Sie das Kontextmenü und wählen Sie dann **Prozess abtrennen**.

    ![Debuggen von Prozessen](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC690787.gif)

> [!WARNING]
> Vermeiden Sie lange an Breakpoints beim Remotedebuggen anzuhalten Debuggen. Azure behandelt Prozesse, die angehalten wurden, mehr als ein paar Minuten lang als nicht reagierend und sendet keinen Datenverkehr an diese Instanz. Wenn Sie lange anhalten, wird msvsmon.exe vom Prozess getrennt.

Um den Debugger von allen Prozessen in Ihrer Instanz oder Rolle trennen möchten, öffnen Sie das Kontextmenü für die Rolle oder Instanz, die Sie debuggen möchten, und wählen Sie dann **Debugger abtrennen**.

## <a name="limitations-of-remote-debugging-in-azure"></a>Einschränkungen für das Remotedebuggen in Azure

Analog zu Azure SDK 2.3 gelten beim Remotedebuggen folgenden Einschränkungen:

* Remotedebuggen aktiviert, können nicht Sie einen Cloud-Dienst veröffentlichen, in dem eine Rolle mehr als 25 Instanzen aufweist.
* Der Debugger verwendet die Ports 30400 bis 30424, 31400 bis 31424 und 32400 bis 32424. Wenn Sie versuchen, diese Ports verwenden, nicht möglich, den Dienst veröffentlichen, und eine der folgenden Fehlermeldungen wird im Aktivitätsprotokoll für Azure angezeigt:

  * Fehler beim Überprüfen der cscfg-Datei anhand der csdef-Datei.
    Der reservierte Portbereich "Bereich" für Endpunkt überschneidet sich mit einem bereits definierten Port oder Bereich mit Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector der Rolle "Rolle" aus.
  * Fehler bei der Zuordnung. Bitte später erneut versuchen, versuchen Sie reduzieren Sie die VM-Größe oder Anzahl der Rolleninstanzen, oder in einer anderen Region bereitstellen.

## <a name="debugging-azure-virtual-machines"></a>Debuggen von virtuellen Azure-Computern

Sie können Programme debuggen, die auf virtuellen Azure-Computern ausgeführt werden soll, mithilfe von Server-Explorer in Visual Studio. Wenn Sie das Remotedebuggen auf virtuellen Azure-Computer aktivieren, installiert Azure Erweiterung für das Remotedebuggen auf dem virtuellen Computer an. Anschließend können Sie an Prozesse auf dem virtuellen Computer anzufügen und wie gewohnt debuggen.

> [!NOTE]
> Über das Azure-Ressourcen-Manager-Stapel erstellte virtuelle Computer können Remote mithilfe von Cloud-Explorer in Visual Studio 2015 gedebuggt werden. Weitere Informationen finden Sie unter [Verwalten von Azure-Ressourcen mit Cloud-Explorer](http://go.microsoft.com/fwlink/?LinkId=623031).

### <a name="to-debug-an-azure-virtual-machine"></a>Debuggen virtueller Azure-Computer

1. Im Server-Explorer erweitern Sie den VM-Knoten, und wählen Sie den Knoten des virtuellen Computers, die Sie debuggen möchten.

2. Öffnen Sie das Kontextmenü und wählen Sie **Debuggen aktivieren**. Wenn Sie gefragt, ob Sie zum Aktivieren des Debuggens auf dem virtuellen Computer, auf Wunsch sicher sind, **Ja**.

    Azure installiert die Erweiterung für das Remotedebuggen auf dem virtuellen Computer, um Debuggen zu aktivieren.

    ![Virtuellen Computer Debuggen-Befehl aktivieren](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Azure-Aktivitätsprotokoll](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

3. Nach der Erweiterung für das Remotedebuggen, die Installation abgeschlossen ist, öffnen Sie den VM Kontextmenü, und wählen **Debugger anfügen...**

    Azure Ruft eine Liste der Prozesse auf dem virtuellen Computer ab und zeigt diese an den verarbeiten (Dialogfeld) anhängen.

    ![Attach Debuggerbefehl](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

4. In der **an den Prozess anhängen** wählen Sie im Dialogfeld **wählen** beschränken die Ergebnisliste aus, um nur die Codetypen angezeigt werden, Sie debuggen möchten. Sie können verwalteten 32- oder 64-Bit-Code und/oder systemeigenen Code Debuggen.

    ![Wählen Sie Code (Dialogfeld)](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

5. Wählen Sie die Prozesse, die Sie verwenden möchten, auf dem virtuellen Computer zu debuggen, und wählen Sie dann **Anfügen**. Sie können z. B. den w3wp.exe-Prozess auswählen, wenn Sie eine Web-app auf dem virtuellen Computer debuggen möchten. Finden Sie unter [Debuggen mindestens eines Prozesses in Visual Studio](https://msdn.microsoft.com/library/jj919165.aspx) und [Azure-Rollenarchitektur](http://blogs.msdn.com/b/kwill/archive/2011/05/05/windows-azure-role-architecture.aspx) für Weitere Informationen.

## <a name="create-a-web-project-and-a-virtual-machine-for-debugging"></a>Erstellen Sie ein Webprojekt und einen virtuellen Computer für das Debuggen

Vor der Veröffentlichung Ihres Azure-Projekts an, Sie finden es möglicherweise sinnvoll, die in einer eigenständigen Umgebung testen, die Debug- und Testszenarien unterstützt und, in dem Sie Test- und Überwachungsprogramme installieren können. Eine Möglichkeit zum Ausführen solcher Tests ist das Remotedebuggen Ihrer app auf einem virtuellen Computer.

Visual Studio ASP.NET-Projekte bieten eine Option aus, um einen praktischen virtuellen Computer zu erstellen, den Sie für app-Tests verwenden können. Der virtuelle Computer umfasst häufig genutzte Endpunkte wie z.B. PowerShell, Remotedesktop und WebDeploy.

### <a name="to-create-a-web-project-and-a-virtual-machine-for-debugging"></a>Zum Erstellen eines Webprojekts und eines virtuellen Computers für das Debuggen

1. Erstellen Sie eine neue ASP.NET-Webanwendung in Visual Studio.

2. Wählen Sie im Abschnitt "Azure" im Dialogfeld Neues ASP.NET-Projekt **VM** im Dropdown-Listenfeld. Lassen Sie die **Remoteressourcen erstellen** Kontrollkästchen. Wählen Sie **OK** um den Vorgang fortzusetzen.

    Die **Erstellen des virtuellen Computers in Azure** Dialogfeld wird angezeigt.

    ![Dialogfeld für ASP.NET Web-Projekt erstellen](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746723.png)

    **Hinweis:** werden Sie aufgefordert, beim Azure-Konto anmelden, wenn Sie noch nicht angemeldet sind.

3. Wählen Sie die verschiedenen Einstellungen für den virtuellen Computer aus, und wählen Sie dann **OK**. Finden Sie unter [VMs](http://go.microsoft.com/fwlink/?LinkId=623033) für Weitere Informationen.

    Der Name, den Sie für DNS-Namen eingeben, werden der Name des virtuellen Computers.

    ![Erstellen des virtuellen Computers im Azure-Dialogfeld](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746724.png)

    Azure erstellt den virtuellen Computer und dann bereitgestellt und konfiguriert die Endpunkte wie Remotedesktop und Web Deploy

4. Nachdem der virtuelle Computer vollständig konfiguriert wurde, wählen Sie der VM Knoten im Server-Explorer.

5. Öffnen Sie das Kontextmenü und wählen Sie **Debuggen aktivieren**. Wenn Sie gefragt, ob Sie zum Aktivieren des Debuggens auf dem virtuellen Computer, auf Wunsch sicher sind, **Ja**.

    Azure installiert die Erweiterung für das Remotedebuggen mit dem virtuellen Computer, um Debuggen zu aktivieren.

    ![Virtuellen Computer Debuggen-Befehl aktivieren](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Azure-Aktivitätsprotokoll](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

6. Veröffentlichen Sie Ihr Projekt wie unter [Vorgehensweise: Bereitstellen einer Webanwendungsprojekts mit One-Click-Veröffentlichung in Visual Studio](https://msdn.microsoft.com/library/dd465337.aspx). Da Sie auf dem virtuellen Computer, auf debuggen möchten die **Einstellungen** auf der Seite der **Webveröffentlichung** Assistenten die Option **Debuggen** wie die Konfiguration. Dadurch wird sichergestellt, dass Codesymbole beim Debuggen verfügbar sind.

    ![Veröffentlichungseinstellungen](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718349.png)

7. In der **Dateiveröffentlichungsoptionen**Option **entfernen weiterer Dateien am Ziel** , wenn das Projekt zu einem früheren Zeitpunkt bereits bereitgestellt wurde.

8. Nachdem das Projekt veröffentlicht wird, auf der VM Kontextmenü im Server-Explorer wählen **Debugger anfügen...**

    Azure Ruft eine Liste der Prozesse auf dem virtuellen Computer ab und zeigt diese an den verarbeiten (Dialogfeld) anhängen.

    ![Attach Debuggerbefehl](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

9. In der **an den Prozess anhängen** wählen Sie im Dialogfeld **wählen** beschränken die Ergebnisliste aus, um nur die Codetypen angezeigt werden, Sie debuggen möchten. Sie können verwalteten 32- oder 64-Bit-Code und/oder systemeigenen Code Debuggen.

    ![Wählen Sie Code (Dialogfeld)](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

10. Wählen Sie die Prozesse, die Sie verwenden möchten, auf dem virtuellen Computer zu debuggen, und wählen Sie dann **Anfügen**. Sie können z. B. den w3wp.exe-Prozess auswählen, wenn Sie eine Web-app auf dem virtuellen Computer debuggen möchten. Finden Sie unter [Debuggen mindestens eines Prozesses in Visual Studio](https://msdn.microsoft.com/library/jj919165.aspx) für Weitere Informationen.

## <a name="next-steps"></a>Nächste Schritte

* Verwendung **Intellitrace** ein Protokoll der Aufrufe und Ereignisse von einem freigegebenen Server zu sammeln. Finden Sie unter [Debuggen eines veröffentlichten Clouddiensts mit IntelliTrace und Visual Studio](http://go.microsoft.com/fwlink/?LinkID=623016).

* Verwendung **Azure-Diagnose** um ausführliche Informationen über Code ausgeführt wird, in Rollen, zu protokollieren, ob die Rollen in der Entwicklungsumgebung oder in Azure ausgeführt werden. Finden Sie unter [Sammeln von Protokollierungsdaten mit Azure-Diagnose](http://go.microsoft.com/fwlink/p/?LinkId=400450).

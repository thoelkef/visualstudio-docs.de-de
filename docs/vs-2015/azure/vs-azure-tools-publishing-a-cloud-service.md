---
title: Veröffentlichen eines Clouddiensts mit den Azure Tools | Microsoft-Dokumentation
description: Erfahren Sie mehr über das Azure-clouddienstprojekten mit Visual Studio veröffentlichen.
author: ghogen
manager: douge
assetId: 1a07b6e4-3678-4cbf-b37e-4520b402a3d9
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: cf29e1cdde71d2e8ef7caa9bc91bc31c30c7bc41
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001957"
---
# <a name="publishing-a-cloud-service-using-visual-studio"></a>Veröffentlichen eines Clouddiensts unter Verwendung von Visual Studio

Visual Studio kann eine Anwendung direkt in Azure mit Unterstützung für Staging- und Produktionsumgebungen Umgebungen von einem Cloud-Dienst veröffentlichen. Beim Veröffentlichen wählen Sie die bereitstellungsumgebung und ein Speicherkonto, das vorübergehend für das Bereitstellungspaket verwendet wird.

Wenn Sie entwickeln und testen eine Azure-Anwendung, können Sie die Web Deploy verwenden, um Änderungen inkrementell für Ihre Webrollen zu veröffentlichen. Nachdem Sie Ihre Anwendung in einer bereitstellungsumgebung veröffentlicht haben, können Web Deploy Änderungen direkt an den virtuellen Computer bereitstellen, die die Web-Rolle ausgeführt wird. Sie müssen keinen zum Verpacken und veröffentlichen Ihre gesamte Azure-Anwendung jedes Mal, die Sie aktualisieren die Web-Rolle, die Änderungen zu testen möchten. Bei diesem Ansatz haben Sie Ihre webrollenänderungen in der Cloud zum Testen, ohne darauf warten, Ihre Anwendung in einer bereitstellungsumgebung veröffentlicht haben.

Verwenden Sie die folgenden Verfahren, die Azure-Anwendung zu veröffentlichen und aktualisieren Sie eine Webrolle mit Web Deploy:

- Veröffentlichen oder Verpacken einer Azure-Anwendung aus Visual Studio
- Aktualisieren einer Webrolle als Teil des Entwicklungs- und Testzyklus

## <a name="publish-or-package-an-azure-application-from-visual-studio"></a>Veröffentlichen oder Verpacken einer Azure-Anwendung aus Visual Studio

Wenn Sie Ihre Azure-Anwendung veröffentlichen, können Sie eine der folgenden Aufgaben ausführen:

- Erstellen eines Dienstpakets: Sie können dieses Paket und die Dienstkonfigurationsdatei verwenden, zum Veröffentlichen der Anwendung in einer bereitstellungsumgebung aus der [Azure-Portal](https://portal.azure.com).

- Veröffentlichen Sie Ihre Azure-Projekts in Visual Studio: um die Anwendung direkt in Azure zu veröffentlichen, die Sie verwenden den Veröffentlichungs-Assistenten. Weitere Informationen finden Sie unter [Assistent zum Veröffentlichen eines Azure-Anwendungen](vs-azure-tools-publish-azure-application-wizard.md).

### <a name="to-create-a-service-package-from-visual-studio"></a>Erstellen Sie ein Dienstpaket in Visual Studio

1. Wenn Sie zum Veröffentlichen der Anwendung bereit sind, öffnen Sie Projektmappen-Explorer zu, öffnen Sie das Kontextmenü für das Azure-Projekt mit den Rollen aus, und wählen Sie veröffentlichen.

1. Um nur ein Dienstpaket zu erstellen, gehen Sie folgendermaßen vor:

   a. Wählen Sie auf das Kontextmenü für das Azure-Projekt, **Paket**.

   b. In der **Azure-Anwendung Verpacken** Dialogfeld Wählen Sie die Dienstkonfiguration, die für die Sie ein Paket erstellen möchten, und wählen Sie dann die Buildkonfiguration.

   c. (Optional) Wählen Sie zum Aktivieren von Remotedesktop für den Clouddienst nach der Veröffentlichung **Remotedesktop für alle Rollen aktivieren**, und wählen Sie dann **Einstellungen** so konfigurieren Sie den Remotedesktop-Anmeldeinformationen. Weitere Informationen finden Sie unter [Aktivieren einer Remotedesktopverbindung für eine Rolle in Azure Cloud Services mithilfe von Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

      Sie können zum Debuggen des Clouddiensts, nach der Veröffentlichung zu aktivieren, Remotedebuggen, indem Sie auswählen **Remotedebugger für alle Rollen aktivieren**.

   d. Wählen Sie zum Erstellen des Pakets die **Paket** Link.

      Datei-Explorer zeigt den Speicherort der Datei des neu erstellten Pakets an. Sie können diesen Speicherort kopieren, sodass Sie sie aus dem Azure-Portal verwenden können.

   e. Um dieses Paket in einer bereitstellungsumgebung zu veröffentlichen, müssen Sie diesen Speicherort als Paketspeicherort verwenden, wenn Sie einen Clouddienst erstellen und dieses Paket in einer Umgebung mit dem Azure-Portal bereitstellen.

1. (Optional) Wählen Sie zum Abbrechen des Bereitstellungsprozesses auf das Kontextmenü für das Zeilenelement im Aktivitätsprotokoll, **Abbrechen und entfernen**. Mit diesem Befehl wird der Bereitstellungsprozess beendet und löscht die bereitstellungsumgebung aus Azure. Um die Umgebung nach der Bereitstellung zu entfernen, verwenden Sie das Azure-Portal.

1. (Optional) Nach dem Starten der Rolleninstanzen zeigt Visual Studio automatisch der bereitstellungsumgebung im der **Clouddienste** Knoten im Server-Explorer. Von hier aus können Sie den Status der einzelnen Rolleninstanzen finden Sie unter. Finden Sie unter [Verwalten von Azure-Ressourcen mit dem Cloud-Explorer](vs-azure-tools-resources-managing-with-cloud-explorer.md). Die folgende Abbildung zeigt die Rolleninstanzen, während Sie sich noch im Zustand "wird initialisiert" befinden:

    ![VST_DeployComputeNode](./media/vs-azure-tools-publishing-a-cloud-service/IC744134.png)

## <a name="update-a-web-role-as-part-of-the-development-and-testing-cycle"></a>Aktualisieren einer Webrolle als Teil des Entwicklungs- und Testzyklus

Wenn Back-End-Infrastruktur Ihrer app stabil ist, aber die Webrollen eine häufigere Aktualisierung, können Sie die Web Deploy verwenden, um nur eine Webrolle im Projekt zu aktualisieren. Web Deploy ist nützlich, wenn Sie nicht erneut erstellen und die Back-End-Workerrollen bereitstellen möchten, oder wenn Sie über mehrere Webrollen verfügen und Sie nur eine Webrolle aktualisieren möchten.

### <a name="requirements-for-using-web-deploy"></a>Anforderungen für die Verwendung von Web Deploy

- **Für Entwicklungs- und Testzwecke nur zu Testzwecken**: die Änderungen direkt an den virtuellen Computer vorgenommen werden, in dem die Webrolle ausgeführt wird. Wenn dieser virtuelle Computer neu gestartet werden muss, sind die Änderungen verloren, da des ursprünglichen Pakets, die Sie veröffentlicht verwendet wird, um den virtuellen Computer für die Rolle neu zu erstellen. Veröffentlichen Sie die Anwendung aus, um die aktuellen Änderungen für die Webrolle zu erhalten.

- **Nur Webrollen können aktualisiert werden**: Workerrollen können nicht aktualisiert werden. Darüber hinaus kann nicht aktualisiert die `RoleEntryPoint` in `web role.cs`.

- **Unterstützt nur eine einzelne Instanz einer Webrolle**: Sie können nicht mehrere Instanzen einer Webrolle in Ihrer bereitstellungsumgebung haben. Es werden jedoch mehrere Webrollen jeweils mit nur einer Instanz unterstützt.

- **Aktivieren von Remotedesktopverbindungen**: dieser Anforderung können für Web Deploy, mit dem Benutzernamen und Kennwort für die Verbindung mit dem virtuellen Computer, um die Änderungen an den Server bereitzustellen, die Internetinformationsdienste (Internet Information Services, IIS) ausgeführt wird. Darüber hinaus müssen Sie für die Verbindung mit dem virtuellen Computer ein vertrauenswürdiges Zertifikat in IIS auf diesem virtuellen Computer hinzufügen. (Dieses Zertifikat wird sichergestellt, dass die Remoteverbindung für IIS, mit dem Web Deploy sicher ist.)

Das folgende Verfahren wird davon ausgegangen, dass Sie verwenden die **Azure-Anwendung veröffentlichen** Assistenten.

### <a name="enable-web-deploy-when-you-publish-your-application"></a>Aktivieren Sie Web Deploy beim Veröffentlichen der Anwendung

1. So aktivieren Sie die **Web Deploy für alle Webrollen aktivieren** auswählen, müssen Sie zunächst Remotedesktopverbindungen konfigurieren. Wählen Sie **Remotedesktop aktivieren** für alle Rollen und geben Sie dann die Anmeldeinformationen, die zum Herstellen der Remoteverbindung im Verbindung die **Remotedesktopkonfiguration** Feld, das angezeigt wird. Finden Sie unter [Aktivieren einer Remotedesktopverbindung für eine Rolle in Azure Cloud Services mithilfe von Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

1. Um Web Deploy für alle Webrollen in Ihrer Anwendung zu aktivieren, wählen Sie **Web Deploy für alle Webrollen aktivieren**.

    Ein gelbes Warndreieck wird angezeigt. Web Deploy wird ein nicht vertrauenswürdiges, selbstsigniertes Zertifikat verwendet, wird standardmäßig nicht zum Hochladen von vertraulichen Daten empfohlen. Wenn Sie diesen Prozess für vertrauliche Daten schützen möchten, können Sie ein SSL-Zertifikat für Web Deploy-Verbindungen zu verwendende hinzufügen. Dieses Zertifikat muss ein vertrauenswürdiges Zertifikat sein. Weitere Informationen finden Sie unter [Web Bereitstellen sicherer machen](#make-web-deploy-secure).

1. Wählen Sie **Weiter** zum Anzeigen der **Zusammenfassung** Bildschirm, und wählen Sie dann **veröffentlichen** zum Bereitstellen von Cloud-Dienst.

    Der Clouddienst veröffentlicht wird. Die virtuelle Maschine, die erstellt wird hat es sich um Remoteverbindungen für IIS aktiviert, damit Web Deploy verwendet werden kann, Ihre Webrollen zu aktualisieren, ohne erneut veröffentlicht werden müssen.

   > [!NOTE]
   > Wenn Sie für eine Webrolle mehr als eine Instanz konfiguriert haben, wird eine Warnmeldung angezeigt, die besagt, dass jede Webrolle auf nur eine Instanz im Paket beschränkt ist, die zum Veröffentlichen der Anwendung erstellt wird. Wählen Sie **OK** um den Vorgang fortzusetzen. Wie im Abschnitt mit Anforderungen erwähnt, haben Sie mehr als eine Webrolle, aber nur eine Instanz jeder Rolle.

### <a name="update-your-web-role-by-using-web-deploy"></a>Aktualisieren Sie Ihrer Webrolle mit Web Deploy

1. Um Web Deploy verwenden, nehmen Sie codeänderungen vor, um das Projekt für alle Webrollen in Visual Studio, die Sie verwenden möchten, veröffentlichen, und klicken Sie dann mit der rechten Maustaste in diesen Projektknoten in der Projektmappe und zeigen Sie auf **veröffentlichen**. Die **Webveröffentlichung** Dialogfeld wird angezeigt.

1. (Optional) Wenn Sie ein vertrauenswürdiges SSL-Zertifikat für die Verwendung für Remoteverbindungen für IIS hinzugefügt haben, können Sie deaktivieren die **nicht vertrauenswürdiges Zertifikat zulassen** Kontrollkästchen. Informationen zum Hinzufügen eines Zertifikats aus, um Web Deploy sicher zu machen, finden Sie im Abschnitt **zum Schützen von Web Deploy** weiter unten in diesem Artikel.

1. Um Web Deploy verwenden, benötigt der Veröffentlichungsmethode, den Benutzernamen und Kennwort, das Sie für die Remotedesktopverbindung einrichten, wenn Sie das Paket zuerst veröffentlicht.

   a. In **Benutzernamen**, geben Sie den Benutzernamen ein.

   b. In **Kennwort**, geben Sie das Kennwort.

   c. (Optional) Wenn Sie dieses Kennwort in diesem Profil speichern möchten, wählen Sie **Kennwort speichern**.

1. Wählen Sie zum Veröffentlichen der Änderungen an der Webrolle **veröffentlichen**.

    Die Statuszeile zeigt **Veröffentlichungsvorgang wurde gestartet**. Wenn die Veröffentlichung abgeschlossen ist, **Veröffentlichen erfolgreich** angezeigt wird. Die Änderungen sind jetzt auf die Web-Rolle auf dem virtuellen Computer bereitgestellt. Nun können Sie Ihre Azure-Anwendung in Azure-Umgebung um Ihre Änderungen Testen beginnen.

### <a name="make-web-deploy-secure"></a>Achten Sie auf sichere Web bereitstellen

1. Web Deploy wird ein nicht vertrauenswürdiges, selbstsigniertes Zertifikat verwendet, wird standardmäßig nicht zum Hochladen von vertraulichen Daten empfohlen. Wenn Sie diesen Prozess für vertrauliche Daten schützen möchten, können Sie ein SSL-Zertifikat für Web Deploy-Verbindungen zu verwendende hinzufügen. Dieses Zertifikat muss ein vertrauenswürdiges Zertifikat sein, den Sie von einer Zertifizierungsstelle (CA) abrufen.

    Um Web Deploy für jeden virtuellen Computer für jede Webrolle sicher zu machen, müssen Sie das vertrauenswürdige Zertifikat, das Sie für das Web verwenden möchten Hochladen auf das Azure-Portal bereitstellen. Diesem Zertifikat wird sichergestellt, dass das Zertifikat mit dem virtuellen Computer hinzugefügt wird, die für die Webrolle erstellt wird, wenn Sie Ihre Anwendung veröffentlichen.

1. Um IIS zur Verwendung für Remoteverbindungen ein vertrauenswürdiges SSL-Zertifikat hinzuzufügen, gehen Sie folgendermaßen vor:

   a. Um eine Verbindung mit dem virtuellen Computer herzustellen, die die Web-Rolle ausgeführt wird, wählen Sie die Instanz der Webrolle in **Cloud-Explorer** oder **Server-Explorer**, und wählen Sie dann die **per Remotedesktop verbinden**  Befehl. Ausführliche Schritte zum Herstellen einer Verbindung mit dem virtuellen Computer finden Sie unter [Aktivieren einer Remotedesktopverbindung für eine Rolle in Azure Cloud Services mithilfe von Visual Studio](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio). Ihr Browser dazu aufgefordert, das Herunterladen einer `.rdp` Datei.

   b. Um ein SSL-Zertifikat hinzuzufügen, öffnen Sie den Verwaltungsdienst im IIS-Manager. Aktivieren von SSL in IIS-Manager durch Öffnen der **Bindungen** -link in der **Aktion** Bereich. Die **Sitebindung hinzufügen** Dialogfeld wird angezeigt. Wählen Sie **hinzufügen**, und wählen Sie dann HTTPS in der **Typ** Dropdown-Liste. In der **SSL-Zertifikat** Liste, wählen Sie das SSL-Zertifikat, dass von einer Zertifizierungsstelle signiert wurde und Sie in das Azure-Portal hochgeladen haben. Weitere Informationen finden Sie unter [Konfigurieren der Verbindungseinstellungen für den Verwaltungsdienst](http://go.microsoft.com/fwlink/?LinkId=215824).

      > [!NOTE]
      > Wenn Sie ein vertrauenswürdiges SSL-Zertifikat hinzufügen, wird das gelbe Warndreieck nicht mehr der **Veröffentlichungs-Assistenten**.

## <a name="include-files-in-the-service-package"></a>Einschließen von Dateien in das Dienstpaket

Sie müssen möglicherweise bestimmte Dateien in Ihr Dienstpaket einschließen, damit sie auf dem virtuellen Computer verfügbar sind, die für eine Rolle erstellt wird. Angenommen, Sie möchten Hinzufügen einer `.exe` oder `.msi` -Datei, die von einem Startskript des Dienstpakets verwendet wird. Oder Sie möchten eine Assembly hinzuzufügen, die eine Web- oder workerrolleninstanz erforderlich ist. Um Dateien einzuschließen, müssen sie der Projektmappe für Ihre Azure-Anwendung hinzugefügt werden.

1. Um einem Dienstpaket eine Assembly hinzuzufügen, verwenden Sie die folgenden Schritte aus:

   a. In **Projektmappen-Explorer**, öffnen Sie den Projektknoten für das Projekt, das die referenzierte Assembly fehlt.
   b. Um die Assembly zum Projekt hinzuzufügen, öffnen Sie das Kontextmenü für die **Verweise** Ordner und wählen Sie dann **Verweis hinzufügen**. Das Dialogfeld "Verweis hinzufügen" wird angezeigt.
   c. Wählen Sie den Verweis, den Sie hinzufügen möchten und wählen Sie dann **OK**. Der Verweis wird hinzugefügt, um der Liste unter der **Verweise** Ordner.
   d. Öffnen Sie das Kontextmenü für die Assembly, die Sie hinzugefügt haben, und wählen Sie **Eigenschaften**. Die **Eigenschaften** Fenster wird angezeigt.

      In dieser Assembly in das Dienstpaket einschließen der **Liste der lokalen Kopie** wählen **"true"**.
1. In **Projektmappen-Explorer** öffnen Sie den Projektknoten für das Projekt, das die referenzierte Assembly fehlt.

1. Um die Assembly zum Projekt hinzuzufügen, öffnen Sie das Kontextmenü für die **Verweise** Ordner und wählen Sie dann **Verweis hinzufügen**. Die **Verweis hinzufügen** Dialogfeld wird angezeigt.

1. Wählen Sie den Verweis, den Sie hinzufügen möchten und wählen Sie dann die **OK** Schaltfläche.

    Der Verweis wird hinzugefügt, um der Liste unter der **Verweise** Ordner.

1. Öffnen Sie das Kontextmenü für die Assembly, die Sie hinzugefügt haben, und wählen Sie **Eigenschaften**. Das Fenster "Eigenschaften" angezeigt wird.

1. In dieser Assembly in das Dienstpaket einschließen der **lokale Kopie** wählen **"true"**.

1. Zum Einschließen von Dateien in das Dienstpaket, die Ihrem Webrollenprojekt hinzugefügt wurden, öffnen Sie das Kontextmenü für die Datei, und wählen Sie dann **Eigenschaften**. Von der **Eigenschaften** Fenster wählen **Content** aus der **Buildvorgang** Listenfeld.

1. Zum Einschließen von Dateien in das Dienstpaket, die Ihrem workerrollenprojekt hinzugefügt wurden, öffnen Sie das Kontextmenü für die Datei, und wählen Sie dann **Eigenschaften**. Von der **Eigenschaften** Fenster wählen **kopieren, wenn neuer** aus der **in Ausgabeverzeichnis kopieren** Listenfeld.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zur Veröffentlichung in Azure aus Visual Studio finden Sie unter [Assistent zum Veröffentlichen eines Azure-Anwendungen](vs-azure-tools-publish-azure-application-wizard.md).

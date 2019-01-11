---
title: Debuggen von Erweiterungen für SharePoint-Tools in Visual Studio | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging extensions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8f838363b52a85faff022f49542fcc2fcc7e450d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950815"
---
# <a name="debug-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Debuggen von Erweiterungen für SharePoint-Tools in Visual Studio
  Sie können SharePoint-Tools-Erweiterungen in der experimentellen Instanz oder in der regulären Instanz von Visual Studio debuggen. Wenn Sie Fehler im Verhalten einer Erweiterung beheben müssen, können Sie auch Registrierungswerte ändern, um weitere Fehlerinformationen anzuzeigen und die Ausführung von SharePoint-Befehlen durch Visual Studio zu konfigurieren.

## <a name="debug-extensions-in-the-experimental-instance-of-visual-studio"></a>Debuggen der experimentellen Instanz von Visual Studio-Erweiterungen
 Um Visual Studio-Entwicklungsumgebung vor versehentlicher Beschädigung durch ungeprüfte Erweiterungen zu schützen, die Visual Studio-SDK enthält eine andere Visual Studio-Instanz, dem Namen der *experimentelle Instanz*, die Sie verwenden können zum Installieren und Testen von Erweiterungen. Die Entwicklung neuer Erweiterungen wird in der regulären Instanz von Visual Studio vorgenommen, das Debugging und die Ausführung erfolgen dagegen in der experimentellen Instanz. Weitere Informationen finden Sie unter [die experimentelle Instanz](../extensibility/the-experimental-instance.md).

 Wenn Sie die Erweiterung mithilfe eines VSIX-Projekts bereitstellen und es sich bei dem VSIX-Projekt um das Startprojekt in der Lösung handelt, wird die Erweiterung automatisch in der experimentellen Instanz installiert und ausgeführt, wenn Sie die Lösung debuggen. Das Startprojekt ist das Projekt, das beim Debuggen einer Lösung mit mehreren Projekten gestartet wird. Weitere Informationen zur Verwendung eines VSIX-Projekts zum Bereitstellen einer Erweiterung finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 In den folgenden exemplarischen Vorgehensweisen finden Sie Beispiele, die das Debuggen verschiedener Arten von Erweiterungen in der experimentellen Instanz von Visual Studio veranschaulichen:

-   [Exemplarische Vorgehensweise: Erweitern eines SharePoint-Projektelementtyps](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)

-   [Exemplarische Vorgehensweise: Erstellen Sie benutzerdefinierte Aktionsprojektelement, mit einer Elementvorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)

-   [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bereitstellungsschritts für SharePoint-Projekte](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)

-   [Exemplarische Vorgehensweise: Erweitern Sie Server-Explorer, um die Anzeige von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

-   [Exemplarische Vorgehensweise: Rufen Sie in der SharePoint-Clientobjektmodell innerhalb einer Server-explorererweiterung](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)

## <a name="debug-extensions-in-the-regular-instance-of-visual-studio"></a>Debuggen von Erweiterungen in der regulären Instanz von Visual Studio
 Installieren Sie zunächst die Erweiterung in der regulären Instanz, wenn Sie das Erweiterungsprojekt in der regulären Instanz von Visual Studio debuggen möchten. Fügen Sie dann den Debugger an einen zweiten Visual Studio-Prozess an. Anschließend können Sie die Erweiterung entfernen, damit sie auf dem Entwicklungscomputer nicht mehr geladen wird.

#### <a name="to-install-the-extension"></a>So installieren Sie die Erweiterung

1.  Schließen Sie alle Instanzen von Visual Studio.

2.  Öffnen Sie in den Buildausgabeordner für das Erweiterungsprojekt, das *VSIX* Datei, indem Sie darauf doppelklicken oder indem Sie das Kontextmenü öffnen und dann auf **öffnen**:

3.  In der **Installer für Visual Studio-Erweiterungen** Dialogfeld Wählen Sie die Edition von Visual Studio, die Sie möchten die Erweiterung installieren, und wählen Sie dann die **installieren** Schaltfläche.

     Visual Studio installiert die Erweiterungsdateien %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions\\*Autorenname*\\*Erweiterungsnamen* \\ *Version*. Die letzten drei Ordner in diesem Pfad bestehen aus den `Author`, `Name`, und `Version` Elemente in der *"Extension.vsixmanifest"* Datei für die Erweiterung.

4.  Nachdem die Erweiterung von Visual Studio installiert wird, wählen Sie die **schließen** Schaltfläche.

#### <a name="to-debug-the-extension"></a>So debuggen Sie die Erweiterung

1.  Starten Sie Visual Studio mit Administratorrechten, und öffnen Sie das Erweiterungsprojekt. Die folgenden Schritte aus, die mit dieser Instanz von Visual Studio als finden Sie die *zuerst Instanz*.

2.  Starten Sie eine weitere Instanz von Visual Studio mit Administratorrechten. Die folgenden Schritte aus, die mit dieser Instanz von Visual Studio als finden Sie die *zweite Instanz*.

3.  Wechseln Sie zur ersten Instanz von Visual Studio.

4.  Wählen Sie auf der Menüleiste **Debuggen**, **an den Prozess anhängen**.

5.  In der **verfügbare Prozesse** wählen *devenv.exe*. In diesem Eintrag wird auf die zweite Instanz von Visual Studio verwiesen. Dies ist die Instanz zum Debuggen der Projekterweiterung.

6.  Wählen Sie die **Anfügen** Schaltfläche.

     Das Erweiterungsprojekt wird im Debugmodus ausgeführt.

7.  Wechseln Sie zur zweiten Instanz von Visual Studio.

8.  Erstellen Sie ein neues SharePoint-Projekt, von dem die Erweiterung geladen wird. Wenn Sie eine Erweiterung für die Definition Projektelemente Debuggen, z. B. Erstellen einer **Listendefinition** Projekt.

9. Führen Sie die erforderlichen Schritte zum Testen des Erweiterungscodes aus.

10. Schließen Sie die zweite Instanz von Visual Studio, wenn das Debugging der Erweiterung abgeschlossen ist.

#### <a name="to-remove-the-extension"></a>So entfernen Sie die Erweiterung

1.  Wählen Sie in Visual Studio-Menüleiste den Menüpunkt **Tools**, **Erweiterungen und Updates**.

     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.

2.  Klicken Sie in der Liste der Erweiterungen, wählen Sie den Namen der Erweiterung, und wählen Sie dann die **Deinstallieren** Schaltfläche.

3.  Wählen Sie in das Dialogfeld, das angezeigt wird, die **Ja** , um zu bestätigen, dass Sie die Erweiterung deinstallieren möchten.

4.  Wählen Sie die **jetzt neu starten** Schaltfläche, um die Deinstallation abzuschließen.

## <a name="debug-sharepoint-commands"></a>Debuggen von SharePoint-Befehle
 Sollten Sie einen SharePoint-Befehl zu debuggen, die Teil einer SharePoint-Tools-Erweiterung ist, müssen Sie den Debugger Anfügen der *vssphost4.exe* Prozess. Hierbei handelt es sich um den 64-Bit-Hostprozess zum Ausführen von SharePoint-Befehlen. Weitere Informationen zu SharePoint-Befehle und *vssphost4.exe*, finden Sie unter [rufen Sie in der SharePoint-Objektmodelle](../sharepoint/calling-into-the-sharepoint-object-models.md).

#### <a name="to-attach-the-debugger-to-the-vssphost4exe-process"></a>So fügen Sie den Debugger an den Prozess vssphost4.exe an

1.  Debuggen Sie die Erweiterung in der experimentellen Instanz von Visual Studio oder in der regulären Instanz von Visual Studio, indem Sie die obigen Anweisungen befolgen.

2.  Wählen Sie in der Instanz von Visual Studio, in dem Sie den Debugger, in der Menüleiste ausführen, **Debuggen**, **an den Prozess anhängen**.

3.  In der **verfügbare Prozesse** wählen *vssphost.exe*.

    > [!NOTE]
    >  Wenn vssphost.exe nicht in der Liste angezeigt wird, müssen Sie starten die *vssphost4.exe* verarbeiten, in der Instanz von Visual Studio, die in der Sie die Erweiterung ausgeführt werden. In der Regel führen Sie dazu eine Aktion aus, durch die eine Verbindung von Visual Studio mit der SharePoint-Website auf dem Entwicklungscomputer hergestellt wird. Z. B. Visual Studio startet *vssphost4.exe* beim Erweitern eines Website-Verbindungsknoten (einen Knoten, eine Website-URL angezeigt, wird) unter den **SharePoint-Verbindungen** Knoten in der **Server-Explorer**  Fenster, oder wenn Sie bestimmte SharePoint-Projektelemente, z. B. hinzufügen **Listeninstanz** oder **Ereignisempfänger** Elemente zu einer SharePoint-Projekt.

4.  Wählen Sie die **Anfügen** Schaltfläche.

5.  Führen Sie in der Instanz von Visual Studio, für die das Debugging durchgeführt wird, die zum Ausführen des Befehls erforderlichen Schritte aus.

## <a name="modify-registry-values-to-help-debug-sharepoint-tools-extensions"></a>Ändern Sie die Registrierungswerte, um das Debuggen von SharePoint-Tools-Erweiterungen
 Wenn Sie eine Erweiterung der SharePoint-Tools in Visual Studio debuggen, können Sie Werte in der Registrierung ändern, um die Problembehandlung für die Erweiterung zu erleichtern. Die Werte sind unter der **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools** Schlüssel. Diese Werte sind standardmäßig nicht vorhanden.

 Um die Problembehandlung für Erweiterungen der SharePoint-Tools zu erleichtern, können Sie den Wert von EnableDiagnostics erstellen und festlegen. Dieser Wert wird der folgenden Tabelle beschrieben.

|Wert|Beschreibung|
|-----------|-----------------|
|EnableDiagnostics|REG_DWORD-Wert, der angibt, ob diagnosemeldungen, in angezeigt werden der **Ausgabe** Fenster.<br /><br /> Legen Sie diesen Wert auf "1" fest, wenn Diagnosemeldungen angezeigt werden sollen. Wenn keine Meldungen mehr angezeigt werden sollen, legen Sie diesen Wert auf 0 (null) fest, oder löschen Sie den Wert.<br /><br /> Zum Schreiben von Nachrichten an die **Ausgabe** Fenster aus einer SharePoint-tools Erweiterung, verwenden Sie die SharePoint-Projektdiensts. Weitere Informationen finden Sie unter [verwenden SharePoint-Projektdiensts](../sharepoint/using-the-sharepoint-project-service.md).|

 Wenn die Erweiterung einen SharePoint-Befehl einschließt, können Sie weitere Werte erstellen und festlegen, um die Problembehandlung des Befehls zu erleichtern. Diese Werte werden in der folgenden Tabelle beschrieben.

|Wert|Beschreibung|
|-----------|-----------------|
|AttachDebuggerToHostProcess|REG_DWORD-Wert, der angibt, ob ein Dialogfeld angezeigt, die Ihnen ermöglicht, den Debugger Anfügen *vssphost4.exe* sobald sie gestartet wird. Dies ist hilfreich, wenn der Befehl, für den das Debugging ausgeführt werden soll, direkt nach dem Start von vssphost.exe ausgeführt wird und die Zeit nicht ausreicht, um den Debugger vor dem Ausführen des Befehls manuell anzufügen. Um das Dialogfeld anzuzeigen *vssphost4.exe* Aufrufe der <xref:System.Diagnostics.Debugger.Break%2A> Methode, wenn er gestartet wird.<br /><br /> Legen Sie diesen Wert auf 1 fest, um dieses Verhalten zu aktivieren. Legen Sie diesen Wert auf 0 (null) fest, oder löschen Sie den Wert, um dieses Verhalten zu deaktivieren.<br /><br /> Wenn Sie diesen Wert auf 1 festlegen, sollten Sie auch erhöhen die HostProcessStartupTimeout-Wert, um ausreichend Zeit den Debugger anfügen, bevor Sie Visual Studio erwartet, dass *vssphost4.exe* zu signalisieren, dass sie erfolgreich gestartet.|
|ChannelOperationTimeout|REG_DWORD-Wert (in Sekunden), der angibt, wie lange von Visual Studio auf die Ausführung eines SharePoint-Befehls gewartet wird. Wird der Befehl nicht innerhalb des Zeitlimits ausgeführt, wird eine <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> ausgelöst.<br /><br /> Der Standardwert ist 120 Sekunden.|
|HostProcessStartupTimeout|REG_DWORD-Wert, der die Zeit in Sekunden angibt, dass Visual Studio wartet auf *vssphost4.exe* zu signalisieren, dass sie erfolgreich gestartet. Wenn *vssphost4.exe* erfolgreichen Starts ist nicht rechtzeitig, signalisieren eine <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> ausgelöst.<br /><br /> Der Standardwert ist 60 Sekunden.|
|MaxReceivedMessageSize|REG_DWORD-Wert, der angibt, die maximal zulässige Größe in Bytes, der WCF-Nachrichten, die zwischen Visual Studio übergeben werden und *vssphost4.exe*.<br /><br /> Der Standardwert ist 1.048.576 Bytes (1 MB).|
|MaxStringContentLength|REG_DWORD-Wert, der angibt, die maximal zulässige Größe in Byte von Zeichenfolgen, die zwischen Visual Studio übergeben werden und *vssphost4.exe*.<br /><br /> Der Standardwert ist 1.048.576 Bytes (1 MB).|

## <a name="see-also"></a>Siehe auch

- [Erweitern von SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)

---
title: "Debuggen von Erweiterungen für SharePoint-Tools in Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, debugging extensions
ms.assetid: 7cee8ce0-d07b-41f6-8ce1-b18e4be3b50c
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: cb6ddce35a45c71fb72a4e6d1f138e044afd50e7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Debuggen von Erweiterungen für die SharePoint-Tools in Visual Studio
  Sie können SharePoint-Tools-Erweiterungen in der experimentellen Instanz oder in der regulären Instanz von Visual Studio debuggen. Wenn Sie Fehler im Verhalten einer Erweiterung beheben müssen, können Sie auch Registrierungswerte ändern, um weitere Fehlerinformationen anzuzeigen und die Ausführung von SharePoint-Befehlen durch Visual Studio zu konfigurieren.  
  
## <a name="debugging-extensions-in-the-experimental-instance-of-visual-studio"></a>Debuggen von Erweiterungen in der experimentellen Instanz von Visual Studio  
 Um Ihr Visual Studio-Entwicklungsumgebung vor versehentlicher Beschädigung durch ungeprüfte Erweiterungen zu schützen, bietet Visual Studio SDK eine alternative Visual Studio-Instanz, die genannte der *experimentelle Instanz*, die Sie verwenden können zum Installieren und Testen von Erweiterungen. Die Entwicklung neuer Erweiterungen wird in der regulären Instanz von Visual Studio vorgenommen, das Debugging und die Ausführung erfolgen dagegen in der experimentellen Instanz. Weitere Informationen finden Sie unter [die experimentelle Instanz](/visualstudio/extensibility/the-experimental-instance).  
  
 Wenn Sie die Erweiterung mithilfe eines VSIX-Projekts bereitstellen und es sich bei dem VSIX-Projekt um das Startprojekt in der Lösung handelt, wird die Erweiterung automatisch in der experimentellen Instanz installiert und ausgeführt, wenn Sie die Lösung debuggen. Das Startprojekt ist das Projekt, das beim Debuggen einer Lösung mit mehreren Projekten gestartet wird. Weitere Informationen zur Verwendung eines VSIX-Projekts zum Bereitstellen einer Erweiterung finden Sie unter [Bereitstellen von Erweiterungen für SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  

 In den folgenden exemplarischen Vorgehensweisen finden Sie Beispiele, die das Debuggen verschiedener Arten von Erweiterungen in der experimentellen Instanz von Visual Studio veranschaulichen:  
  
-   [Exemplarische Vorgehensweise: Erweitern eines SharePoint-Projektelementtyps](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
-   [Exemplarische Vorgehensweise: Erstellen eines Projektelements „Benutzerdefinierte Aktion“ mit einer Elementvorlage, Teil 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)  
  
-   [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bereitstellungsschritts für SharePoint-Projekte](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)  
  
-   [Exemplarische Vorgehensweise: Erweitern des Server-Explorers für die Anzeige von Webparts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
-   [Exemplarische Vorgehensweise: Aufrufe in das SharePoint-Clientobjektmodell innerhalb einer Server-Explorererweiterung](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)  
  
## <a name="debugging-extensions-in-the-regular-instance-of-visual-studio"></a>Debuggen von Erweiterungen in der regulären Instanz von Visual Studio  
 Installieren Sie zunächst die Erweiterung in der regulären Instanz, wenn Sie das Erweiterungsprojekt in der regulären Instanz von Visual Studio debuggen möchten. Fügen Sie dann den Debugger an einen zweiten Visual Studio-Prozess an. Anschließend können Sie die Erweiterung entfernen, damit sie auf dem Entwicklungscomputer nicht mehr geladen wird.  
  
#### <a name="to-install-the-extension"></a>So installieren Sie die Erweiterung  
  
1.  Schließen Sie alle Instanzen von Visual Studio.  
  
2.  Öffnen Sie im Buildausgabeordner für das Erweiterungsprojekt die VSIX-Datei durch Doppelklicken oder indem Sie das Kontextmenü öffnen, und drücken Sie dann die **öffnen**:  
  
3.  In der **Installer für Visual Studio-Erweiterung** Dialogfeld Wählen Sie die Edition von Visual Studio, Sie möchten die Erweiterung zu installieren, und wählen Sie dann, die **installieren** Schaltfläche.  
  
     Visual Studio installiert die Erweiterungsdateien %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions\\*Name des Autors*\\*Erweiterungsnamen* \\ *Version*. Die letzten drei Ordner in diesem Pfad werden aus den Elementen `Author`, `Name` und `Version` der Datei "extension.vsixmanifest" für die Erweiterung erstellt.  
  
4.  Nachdem die Erweiterung von Visual Studio installiert wird, wählen Sie die **schließen** Schaltfläche.  
  
#### <a name="to-debug-the-extension"></a>So debuggen Sie die Erweiterung  
  
1.  Starten Sie Visual Studio mit Administratorrechten, und öffnen Sie das Erweiterungsprojekt. Die folgenden Schritte finden Sie in dieser Instanz von Visual Studio als die *zuerst Instanz*.  
  
2.  Starten Sie eine weitere Instanz von Visual Studio mit Administratorrechten. Die folgenden Schritte finden Sie in dieser Instanz von Visual Studio als die *zweite Instanz*.  
  
3.  Wechseln Sie zur ersten Instanz von Visual Studio.  
  
4.  Wählen Sie in der Menüleiste **Debuggen**, **an den Prozess anhängen**.  
  
5.  In der **verfügbare Prozesse** wählen devenv.exe. In diesem Eintrag wird auf die zweite Instanz von Visual Studio verwiesen. Dies ist die Instanz zum Debuggen der Projekterweiterung.  
  
6.  Wählen Sie die **Anfügen** Schaltfläche.  
  
     Das Erweiterungsprojekt wird im Debugmodus ausgeführt.  
  
7.  Wechseln Sie zur zweiten Instanz von Visual Studio.  
  
8.  Erstellen Sie ein neues SharePoint-Projekt, von dem die Erweiterung geladen wird. Wenn Sie eine Erweiterung für die Definition Projektelemente Debuggen, z. B. Erstellen einer **Listendefinition** Projekt.  
  
9. Führen Sie die erforderlichen Schritte zum Testen des Erweiterungscodes aus.  
  
10. Schließen Sie die zweite Instanz von Visual Studio, wenn das Debugging der Erweiterung abgeschlossen ist.  
  
#### <a name="to-remove-the-extension"></a>So entfernen Sie die Erweiterung  
  
1.  Wählen Sie in Visual Studio auf der Menüleiste **Tools**, **Erweiterungen und Updates**.  
  
     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.  
  
2.  Klicken Sie in der Liste der Erweiterungen, wählen Sie den Namen der Erweiterung, und wählen Sie dann die **Deinstallieren** Schaltfläche.  
  
3.  Wählen Sie im angezeigten Dialogfeld die **Ja** Schaltfläche, um sicherzustellen, dass Sie die Erweiterung deinstallieren möchten.  
  
4.  Wählen Sie die **jetzt neu starten** Schaltfläche, um die Deinstallation abzuschließen.  
  
## <a name="debugging-sharepoint-commands"></a>Debuggen von SharePoint-Befehlen  
 Wenn Sie einen SharePoint-Befehl debuggen möchten, der einen Teil einer SharePoint-Tools-Erweiterung darstellt, müssen Sie den Debugger an den Prozess vssphost4.exe anfügen. Hierbei handelt es sich um den 64-Bit-Hostprozess zum Ausführen von SharePoint-Befehlen. Weitere Informationen zu SharePoint-Befehle und vssphost4.exe, finden Sie unter [Aufrufe in die SharePoint-Objektmodelle](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
#### <a name="to-attach-the-debugger-to-the-vssphost4exe-process"></a>So fügen Sie den Debugger an den Prozess vssphost4.exe an  
  
1.  Debuggen Sie die Erweiterung in der experimentellen Instanz von Visual Studio oder in der regulären Instanz von Visual Studio, indem Sie die obigen Anweisungen befolgen.  
  
2.  Wählen Sie in der Instanz von Visual Studio, in dem Sie den Debugger in der Menüleiste ausführen, **Debuggen**, **an den Prozess anhängen**.  
  
3.  In der **verfügbare Prozesse** wählen vssphost.exe.  
  
    > [!NOTE]  
    >  Wenn vssphost.exe nicht in der Liste aufgeführt wird, müssen Sie den Prozess vssphost4.exe in der Instanz von Visual Studio starten, in der Sie die Erweiterung ausführen. In der Regel führen Sie dazu eine Aktion aus, durch die eine Verbindung von Visual Studio mit der SharePoint-Website auf dem Entwicklungscomputer hergestellt wird. Visual Studio startet z. B. vssphost4.exe, wenn Sie einen Website-Verbindungsknoten (einen Knoten, in dem eine Website-URL angezeigt wird) erweitern, unter dem **SharePoint-Verbindungen** Knoten in der **Server-Explorer** Fenster, oder wenn Sie Fügen Sie bestimmte SharePoint-Projektelemente, z. B. **Listeninstanz** oder **Ereignisempfänger** Elemente zu einer SharePoint-Projekt.  
  
4.  Wählen Sie die **Anfügen** Schaltfläche.  
  
5.  Führen Sie in der Instanz von Visual Studio, für die das Debugging durchgeführt wird, die zum Ausführen des Befehls erforderlichen Schritte aus.  
  
## <a name="modifying-registry-values-to-help-debug-sharepoint-tools-extensions"></a>Debuggen von SharePoint-Tools-Erweiterungen durch Ändern von Registrierungswerten  
 Wenn Sie eine Erweiterung der SharePoint-Tools in Visual Studio debuggen, können Sie Werte in der Registrierung ändern, um die Problembehandlung für die Erweiterung zu erleichtern. Die Werte sind unter dem Schlüssel HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools vorhanden. Diese Werte sind standardmäßig nicht vorhanden.  
  
 Um die Problembehandlung für Erweiterungen der SharePoint-Tools zu erleichtern, können Sie den Wert von EnableDiagnostics erstellen und festlegen. Dieser Wert wird der folgenden Tabelle beschrieben.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|EnableDiagnostics|REG_DWORD-Wert, der angibt, ob diagnosemeldungen, in angezeigt werden der **Ausgabe** Fenster.<br /><br /> Legen Sie diesen Wert auf "1" fest, wenn Diagnosemeldungen angezeigt werden sollen. Wenn keine Meldungen mehr angezeigt werden sollen, legen Sie diesen Wert auf 0 (null) fest, oder löschen Sie den Wert.<br /><br /> Zum Schreiben von Nachrichten an die **Ausgabe** Fenster von einer SharePoint-tools Erweiterung, verwenden Sie die SharePoint-Projektdienst. Weitere Informationen finden Sie unter [Verwenden des SharePoint-Projektdiensts](../sharepoint/using-the-sharepoint-project-service.md).|  
  
 Wenn die Erweiterung einen SharePoint-Befehl einschließt, können Sie weitere Werte erstellen und festlegen, um die Problembehandlung des Befehls zu erleichtern. Diese Werte werden in der folgenden Tabelle beschrieben.  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|AttachDebuggerToHostProcess|REG_DWORD. Hiermit wird angegeben, ob ein Dialogfeld angezeigt wird, in dem der Debugger sofort nach dem Start an vssphost4.exe angefügt werden kann. Dies ist hilfreich, wenn der Befehl, für den das Debugging ausgeführt werden soll, direkt nach dem Start von vssphost.exe ausgeführt wird und die Zeit nicht ausreicht, um den Debugger vor dem Ausführen des Befehls manuell anzufügen. Zum Anzeigen des Dialogfelds ruft vssphost4.exe beim Starten die <xref:System.Diagnostics.Debugger.Break%2A>-Methode auf.<br /><br /> Legen Sie diesen Wert auf 1 fest, um dieses Verhalten zu aktivieren. Legen Sie diesen Wert auf 0 (null) fest, oder löschen Sie den Wert, um dieses Verhalten zu deaktivieren.<br /><br /> Wenn Sie den Wert auf 1 festlegten, empfiehlt es sich, den Wert von HostProcessStartupTimeout zu vergrößern, sodass Sie über ausreichend Zeit zum Anfügen des Debuggers verfügen, bevor Visual Studio von vssphost4.exe der erfolgreiche Start mitgeteilt wird.|  
|ChannelOperationTimeout|REG_DWORD-Wert (in Sekunden), der angibt, wie lange von Visual Studio auf die Ausführung eines SharePoint-Befehls gewartet wird. Wird der Befehl nicht innerhalb des Zeitlimits ausgeführt, wird eine <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> ausgelöst.<br /><br /> Der Standardwert ist 120 Sekunden.|  
|HostProcessStartupTimeout|REG_DWORD-Wert (in Sekunden), der angibt, wie lange von Visual Studio darauf gewartet wird, dass der erfolgreiche Start von "vssphost4.exe" signalisiert wird. Erfolgt innerhalb des Zeitlimits keine Signalisierung des erfolgreichen Starts von "vssphost4.exe", wird eine <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> ausgelöst.<br /><br /> Der Standardwert ist 60 Sekunden.|  
|MaxReceivedMessageSize|REG_DWORD-Wert (in Bytes), der die maximal zulässige Größe für WCF-Meldungen angibt, die von Visual Studio an "vssphost4.exe" (und umgekehrt) übergeben werden.<br /><br /> Der Standardwert ist 1.048.576 Bytes (1 MB).|  
|MaxStringContentLength|REG_DWORD-Wert (in Bytes), der die maximal zulässige Größe für Zeichenfolgen angibt, die von Visual Studio an "vssphost4.exe" (und umgekehrt) übergeben werden.<br /><br /> Der Standardwert ist 1.048.576 Bytes (1 MB).|  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern der SharePoint-Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Bereitstellen von Erweiterungen für die SharePoint-Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  
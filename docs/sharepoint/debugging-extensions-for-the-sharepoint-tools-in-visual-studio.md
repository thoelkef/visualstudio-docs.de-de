---
title: "Debugging Extensions for the SharePoint Tools in Visual Studio"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, debugging extensions"
ms.assetid: 7cee8ce0-d07b-41f6-8ce1-b18e4be3b50c
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Debugging Extensions for the SharePoint Tools in Visual Studio
  Sie können SharePoint\-Tools\-Erweiterungen in der experimentellen Instanz oder in der regulären Instanz von Visual Studio debuggen.  Wenn Sie Fehler im Verhalten einer Erweiterung beheben müssen, können Sie auch Registrierungswerte ändern, um weitere Fehlerinformationen anzuzeigen und die Ausführung von SharePoint\-Befehlen durch Visual Studio zu konfigurieren.  
  
## Debuggen von Erweiterungen in der experimentellen Instanz von Visual Studio  
 Zum Schutz der Visual Studio\-Entwicklungsumgebung vor versehentlicher Beschädigung durch ungeprüfte Erweiterungen wird vom Visual Studio SDK eine alternative Visual Studio\-Instanz – die so genannte *experimentelle Instanz* – bereitgestellt, mit der Erweiterungen installiert und getestet werden können.  Die Entwicklung neuer Erweiterungen wird in der regulären Instanz von Visual Studio vorgenommen, das Debugging und die Ausführung erfolgen dagegen in der experimentellen Instanz.  Weitere Informationen finden Sie unter [Die experimentelle Instanz](../extensibility/the-experimental-instance.md).  
  
 Wenn Sie die Erweiterung mithilfe eines VSIX\-Projekts bereitstellen und es sich bei dem VSIX\-Projekt um das Startprojekt in der Lösung handelt, wird die Erweiterung automatisch in der experimentellen Instanz installiert und ausgeführt, wenn Sie die Lösung debuggen.  Das Startprojekt ist das Projekt, das beim Debuggen einer Lösung mit mehreren Projekten gestartet wird.  Weitere Informationen zum Bereitstellen einer Erweiterung mithilfe eines VSIX\-Projekts finden Sie unter [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  Weitere Informationen zu Startprojekten finden Sie unter [Gewusst wie: Festlegen von Startprojekten](http://msdn.microsoft.com/de-de/31465836-0911-48db-a5d9-e456b635e970).  
  
 In den folgenden exemplarischen Vorgehensweisen finden Sie Beispiele, die das Debuggen verschiedener Arten von Erweiterungen in der experimentellen Instanz von Visual Studio veranschaulichen:  
  
-   [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
-   [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)  
  
-   [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)  
  
-   [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
-   [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)  
  
## Debuggen von Erweiterungen in der regulären Instanz von Visual Studio  
 Installieren Sie zunächst die Erweiterung in der regulären Instanz, wenn Sie das Erweiterungsprojekt in der regulären Instanz von Visual Studio debuggen möchten.  Fügen Sie dann den Debugger an einen zweiten Visual Studio\-Prozess an.  Anschließend können Sie die Erweiterung entfernen, damit sie auf dem Entwicklungscomputer nicht mehr geladen wird.  
  
#### So installieren Sie die Erweiterung  
  
1.  Schließen Sie alle Instanzen von Visual Studio.  
  
2.  Öffnen Sie im Buildausgabeordner für das Erweiterungsprojekt die VSIX\-Datei, indem Sie auf diese doppelklicken oder indem Sie das Kontextmenü öffnen und dann **Öffnen** auswählen:  
  
3.  Wählen Sie im Dialogfeld **Installer für Visual Studio\-Erweiterungen** die Edition von Visual Studio aus, für die Sie die Erweiterung installieren möchten, und klicken Sie dann auf **Installieren**.  
  
     Die Erweiterungsdateien werden unter "%UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0\\Extensions\\*author name*\\*extension name*\\*version*" installiert.  Die letzten drei Ordner in diesem Pfad werden aus den Elementen `Author`, `Name` und `Version` der Datei "extension.vsixmanifest" für die Erweiterung erstellt.  
  
4.  Klicken Sie auf **Schließen**, nachdem die Erweiterung von Visual Studio installiert wurde.  
  
#### So debuggen Sie die Erweiterung  
  
1.  Starten Sie Visual Studio mit Administratorrechten, und öffnen Sie das Erweiterungsprojekt.  Diese Instanz von Visual Studio wird in den folgenden Schritten als *erste Instanz* bezeichnet.  
  
2.  Starten Sie eine weitere Instanz von Visual Studio mit Administratorrechten.  Diese Instanz von Visual Studio wird in den folgenden Schritten als *zweite Instanz* bezeichnet.  
  
3.  Wechseln Sie zur ersten Instanz von Visual Studio.  
  
4.  Wählen Sie auf der Menüleiste **Debuggen** aus und dann **An den Prozess anhängen**.  
  
5.  Wählen Sie in der Liste **Verfügbare Prozesse** "devenv.exe" aus.  In diesem Eintrag wird auf die zweite Instanz von Visual Studio verwiesen. Dies ist die Instanz zum Debuggen der Projekterweiterung.  
  
6.  Klicken Sie auf die Schaltfläche **Anhängen**.  
  
     Das Erweiterungsprojekt wird im Debugmodus ausgeführt.  
  
7.  Wechseln Sie zur zweiten Instanz von Visual Studio.  
  
8.  Erstellen Sie ein neues SharePoint\-Projekt, von dem die Erweiterung geladen wird.  Wenn Sie beispielsweise eine Erweiterung für die Projektelemente einer Listendefinition debuggen, erstellen Sie ein Projekt vom Typ **Listendefinition**.  
  
9. Führen Sie die erforderlichen Schritte zum Testen des Erweiterungscodes aus.  
  
10. Schließen Sie die zweite Instanz von Visual Studio, wenn das Debugging der Erweiterung abgeschlossen ist.  
  
#### So entfernen Sie die Erweiterung  
  
1.  Wählen Sie in Visual Studio auf der Menüleiste **Tools** und dann **Erweiterungen und Updates** aus.  
  
     Das Dialogfeld **Erweiterungen und Updates** wird geöffnet.  
  
2.  Klicken Sie in der Liste mit den Erweiterungen auf den Namen der Erweiterung und anschließend auf **Deinstallieren**.  
  
3.  Wählen Sie im angezeigten Dialogfeld die Schaltfläche **Ja** aus, um zu bestätigen, dass Sie die Erweiterung deinstallieren möchten.  
  
4.  Wählen Sie die Schaltfläche **Jetzt neu starten** aus, um die Deinstallation abzuschließen.  
  
## Debuggen von SharePoint\-Befehlen  
 Wenn Sie einen SharePoint\-Befehl debuggen möchten, der einen Teil einer SharePoint\-Tools\-Erweiterung darstellt, müssen Sie den Debugger an den Prozess vssphost4.exe anfügen.  Hierbei handelt es sich um den 64\-Bit\-Hostprozess zum Ausführen von SharePoint\-Befehlen.  Weitere Informationen zu SharePoint\-Befehlen und zu vssphost4.exe finden Sie unter [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
#### So fügen Sie den Debugger an den Prozess vssphost4.exe an  
  
1.  Debuggen Sie die Erweiterung in der experimentellen Instanz von Visual Studio oder in der regulären Instanz von Visual Studio, indem Sie die obigen Anweisungen befolgen.  
  
2.  Klicken Sie in der Instanz von Visual Studio, in der Sie den Debugger ausführen, auf der Menüleiste auf **Debuggen** und dann **An den Prozess anhängen**.  
  
3.  Wählen Sie in der Liste **Verfügbare Prozesse** "vssphost.exe" aus.  
  
    > [!NOTE]  
    >  Wenn vssphost.exe nicht in der Liste aufgeführt wird, müssen Sie den Prozess vssphost4.exe in der Instanz von Visual Studio starten, in der Sie die Erweiterung ausführen.  In der Regel führen Sie dazu eine Aktion aus, durch die eine Verbindung von Visual Studio mit der SharePoint\-Website auf dem Entwicklungscomputer hergestellt wird.  Visual Studio startet z. B. vssphost4.exe, wenn Sie einen Website\-Verbindungsknoten \(einen Knoten, von dem eine Website\-URL angezeigt wird\) unter dem Knoten **SharePoint\-Verbindungen** im Fenster **Server\-Explorer** erweitern oder wenn Sie einem SharePoint\-Projekt bestimmte SharePoint\-Projektelemente hinzufügen, beispielsweise die Elemente **Listeninstanz** oder **Ereignisempfänger**.  
  
4.  Klicken Sie auf die Schaltfläche **Anhängen**.  
  
5.  Führen Sie in der Instanz von Visual Studio, für die das Debugging durchgeführt wird, die zum Ausführen des Befehls erforderlichen Schritte aus.  
  
## Debuggen von SharePoint\-Tools\-Erweiterungen durch Ändern von Registrierungswerten  
 Wenn Sie eine Erweiterung der SharePoint\-Tools in Visual Studio debuggen, können Sie Werte in der Registrierung ändern, um die Problembehandlung für die Erweiterung zu erleichtern.  Die Werte sind unter dem Schlüssel HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\11.0\\SharePointTools vorhanden.  Diese Werte sind standardmäßig nicht vorhanden.  
  
 Um die Problembehandlung für Erweiterungen der SharePoint\-Tools zu erleichtern, können Sie den Wert von EnableDiagnostics erstellen und festlegen.  Dieser Wert wird der folgenden Tabelle beschrieben.  
  
|Wert|Beschreibung|  
|----------|------------------|  
|EnableDiagnostics|REG\_DWORD\-Wert, der angibt, ob Diagnosemeldungen im Ausgabefenster angezeigt werden.<br /><br /> Legen Sie diesen Wert auf "1" fest, wenn Diagnosemeldungen angezeigt werden sollen.  Wenn keine Meldungen mehr angezeigt werden sollen, legen Sie diesen Wert auf 0 \(null\) fest, oder löschen Sie den Wert.<br /><br /> Verwenden Sie den SharePoint\-Projektdienst, wenn Meldungen in das Ausgabefenster einer Erweiterung der SharePoint\-Tools geschrieben werden sollen.  Weitere Informationen finden Sie unter [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).|  
  
 Wenn die Erweiterung einen SharePoint\-Befehl einschließt, können Sie weitere Werte erstellen und festlegen, um die Problembehandlung des Befehls zu erleichtern.  Diese Werte werden in der folgenden Tabelle beschrieben.  
  
|Wert|Beschreibung|  
|----------|------------------|  
|AttachDebuggerToHostProcess|REG\_DWORD. Hiermit wird angegeben, ob ein Dialogfeld angezeigt wird, in dem der Debugger sofort nach dem Start an vssphost4.exe angefügt werden kann.  Dies ist hilfreich, wenn der Befehl, für den das Debugging ausgeführt werden soll, direkt nach dem Start von vssphost.exe ausgeführt wird und die Zeit nicht ausreicht, um den Debugger vor dem Ausführen des Befehls manuell anzufügen.  Zum Anzeigen des Dialogfelds ruft vssphost4.exe beim Starten die <xref:System.Diagnostics.Debugger.Break%2A>\-Methode auf.<br /><br /> Legen Sie diesen Wert auf 1 fest, um dieses Verhalten zu aktivieren.  Legen Sie diesen Wert auf 0 \(null\) fest, oder löschen Sie den Wert, um dieses Verhalten zu deaktivieren.<br /><br /> Wenn Sie den Wert auf 1 festlegten, empfiehlt es sich, den Wert von HostProcessStartupTimeout zu vergrößern, sodass Sie über ausreichend Zeit zum Anfügen des Debuggers verfügen, bevor Visual Studio von vssphost4.exe der erfolgreiche Start mitgeteilt wird.|  
|ChannelOperationTimeout|REG\_DWORD\-Wert \(in Sekunden\), der angibt, wie lange von Visual Studio auf die Ausführung eines SharePoint\-Befehls gewartet wird.  Wird der Befehl nicht innerhalb des Zeitlimits ausgeführt, wird eine <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> ausgelöst.<br /><br /> Der Standardwert ist 120 Sekunden.|  
|HostProcessStartupTimeout|REG\_DWORD\-Wert \(in Sekunden\), der angibt, wie lange von Visual Studio darauf gewartet wird, dass der erfolgreiche Start von "vssphost4.exe" signalisiert wird.  Erfolgt innerhalb des Zeitlimits keine Signalisierung des erfolgreichen Starts von "vssphost4.exe", wird eine <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> ausgelöst.<br /><br /> Der Standardwert ist 60 Sekunden.|  
|MaxReceivedMessageSize|REG\_DWORD\-Wert \(in Bytes\), der die maximal zulässige Größe für WCF\-Meldungen angibt, die von Visual Studio an "vssphost4.exe" \(und umgekehrt\) übergeben werden.<br /><br /> Der Standardwert ist 1.048.576 Bytes \(1 MB\).|  
|MaxStringContentLength|REG\_DWORD\-Wert \(in Bytes\), der die maximal zulässige Größe für Zeichenfolgen angibt, die von Visual Studio an "vssphost4.exe" \(und umgekehrt\) übergeben werden.<br /><br /> Der Standardwert ist 1.048.576 Bytes \(1 MB\).|  
  
## Siehe auch  
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  
---
title: "Das Debuggen für ASP.NET-Anwendungen aktivieren | Microsoft Docs"
ms.custom: H1HackMay2017
ms.date: 09/21/17
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
caps.latest.revision: "37"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9048f965ad2f04b4eed8fe3a753f6fddc280dbfa
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="debug-aspnet-applications-in-visual-studio"></a>Debuggen von ASP.NET-Anwendungen in Visual Studio

Sie können ASP.NET-Anwendungen aus Visual Studio debuggen.

## <a name="requirements"></a>Anforderungen

Um die Anweisungen in diesem Thema folgen zu können, müssen wie folgt vor:

- IIS Express, die standardmäßig in Visual Studio 2012 und höher enthalten ist

    - oder - 

- Eine lokale IIS web Server (Version 8.0 oder höher), richtig konfiguriert ist und die ASP.NET-Anwendung ohne Fehler ausführen kann.

Wenn Sie den Server remote verfügbar ist, muss der Remotedebugger auf dem Remotecomputer ausgeführt werden. Zum Debuggen auf einem IIS-Remoteserver finden Sie unter [Remote Debuggen von ASP.NET auf einem Computer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). 

## <a name="configure-debug-settings"></a>Debugeinstellungen konfigurieren

### <a name="enable-aspnet-debugging-in-the-project-properties"></a>Aktivieren Sie das ASP.NET-Debuggen in den Projekteigenschaften

1. Öffnen Sie das ASP.NET-Projekt in Visual Studio.

2. Mit der rechten Maustaste des Projekts im **Projektmappen-Explorer**, wählen Sie **Eigenschaften**, und klicken Sie dann auf die **Web** Registerkarte.

    Wählen Sie für einige Projekttypen **Eigenschaften > Debuggen** stattdessen. Klicken Sie für eine Web Forms-ASP.NET-Projekt mit der rechten Maustaste des Projekts, und wählen Sie **Eigenschaftenseiten > Startoptionen**.
  
3.  Aktivieren Sie unter **Debugger**das Kontrollkästchen **ASP.NET** .

    ![Debugger-Einstellungen](../debugger/media/dbg-aspnet-enable-debugging.png "Debugger-Einstellungen")

> [!NOTE]
> Bei der Erstellung eines neuen ASP.NET-Projekts (**Datei > Neues Projekt**), die Debugeinstellungen bereits ordnungsgemäß konfiguriert sind.

### <a name="enable-debugging-in-the-webconfig-file"></a>Aktivieren Sie das Debuggen in der Datei "Web.config"  

Um eine Web-app zu debuggen, muss die Datei web.config der Anwendung ordnungsgemäß konfiguriert sein. Eine Datei "Web.config" ist erforderlich, wenn Sie die Anwendung auf IIS oder IIS Express hosten.

Für ASP.NET Core aufweist wird die Datei "Web.config" automatisch erstellt, wenn die Anwendung bereitgestellt wird (wenn es nicht bereits vorhanden ist).

> [!TIP]
> Das Verfahren zum Bereitstellen, kann die Datei "Web.config"-Einstellungen aktualisieren. Überprüfen Sie bevor Sie versuchen zu debuggen deshalb die Einstellung "Web.config" auf dem Server.
  
1.  Öffnen Sie in Visual Studio die Datei web.config des Projekts.  
  
    > [!NOTE]  
    > Sie können nicht remote auf die Datei "Web.config" zuzugreifen, mithilfe eines Webbrowsers. Aus Sicherheitsgründen wird Microsoft IIS durch [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] so konfiguriert, dass ein direkter Browserzugriff auf die Web.config-Dateien nicht möglich ist. Wenn Sie versuchen, eine Konfigurationsdatei, die mithilfe eines Browsers zuzugreifen, erhalten Sie eine HTTP-Zugriffsfehler 403 (Verboten).  
  
2.  Suchen Sie das Element `configuration/system.web/compilation` . Wenn das compilation-Element nicht den vorhanden ist, erstellen Sie es.

    Web.config ist eine XML-Datei und enthält daher mit Tags markierte, geschachtelte Abschnitte.
  
3.  Wenn das `compilation` -Element kein `debug` -Attribut enthält, fügen Sie dem Element das Attribut hinzu.  
  
4.  Stellen Sie sicher, dass der `debug` -Attributwert auf `true`.  
  
Die Datei "Web.config" sollte wie im folgenden Beispiel aussehen:

> [!NOTE]
> In diesem Beispiel wird eine partielle web.config-Datei. Zusätzliche XML-Abschnitte sind in der Regel zwischen dem Konfigurations- und system.web-Elementen vorhanden. Das Compilation-Element möglicherweise auch andere Attribute und Elemente enthalten.
  
#### <a name="example"></a>Beispiel  
  
```  
<configuration>  
    ...  
    <system.web>  
        <compilation  
            debug="true"  
            ...  
        >  
        ...  
        </compilation>  
    </system.web>  
</configuration>  
```

Wenn Sie einen externen Server anstelle des Standardservers IIS Express verwenden, Sie müssen auch sicherstellen, dass die `targetFramework` Attributwert der Konfiguration auf dem Server entspricht.

> [!IMPORTANT]
> Legen Sie für optimale Leistung eine Produktions-app auf `debug=false` , und geben Sie einen Releasebuild, beim Erstellen und veröffentlichen Sie die app.

## <a name="configure-project-settings-for-the-server"></a>Projekteinstellungen für den Server konfigurieren

Festlegen von Projekteigenschaften für das Debuggen auf einem lokalen Webserver. Führen Sie für das Debuggen auf einem Remoteserver, die umfangreicheren Anleitungen, die in beschriebenen [Remote Debuggen von ASP.NET auf IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) stattdessen.

1. In der **Web** des Projekts auf der Registerkarte Eigenschaften, wählen Sie entweder **IIS Express** oder **externen Server** unter der **Server** Einstellungen. (Für einige Projekttypen, werden diese Einstellungen unter dem **Debuggen** stattdessen Registerkarte.)

    ![Servereinstellungen](../debugger/media/dbg-aspnet-server-settings.png "servereinstellungen")

    IIS Express ist Standardserver für ASP.NET und erfordert normalerweise keine besondere Konfiguration. Dies ist die einfachste Möglichkeit zum Debuggen einer ASP.NET-Anwendung.

    Eine Web Forms-ASP.NET-Projekt mit der rechten Maustaste des Projekts, wählen Sie **Eigenschaftenseiten > Startoptionen**, und wählen Sie entweder **Standardwebserver verwenden** oder **benutzerdefinierten Server verwenden** () anstelle von **externen Server**).

    ![Server-Einstellungen für Web Forms-Anwendung](../debugger/media/dbg-aspnet-server-settings-webforms.png "servereinstellungen für Web Forms-Anwendung")

2. Wenn Sie einen externen (benutzerdefinierten)-Server auswählen, geben Sie die richtige URL in die **Projekt-URL** (oder **Basis-URL**) Feld.

    Der externen Server lokale IIS ist, muss IIS installiert und ordnungsgemäß konfiguriert. Beispielsweise muss die richtige Version von ASP.NET in IIS konfiguriert werden. Weitere Informationen finden Sie unter [IIS 8.0 mithilfe von ASP.NET 3.5 und ASP.NET 4.5](https://docs.microsoft.com/en-us/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45). Wenn Sie die Bereitstellung sowie das Debuggen testen möchten, finden Sie unter [Bereitstellung zum Testen](https://docs.microsoft.com/en-us/aspnet/web-forms/overview/deployment/visual-studio-web-deployment/deploying-to-iis).

    Wenn der Quellserver ist [remote](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md), Sie an den Prozess anhängen stattdessen, und diese projekteinstellungen werden nicht zum Debuggen verwendet.

## <a name="local-iis-web-server-configure-iis"></a>(Lokale IIS-Webserver) Konfigurieren von IIS

Für IIS Express müssen Sie nicht den Webserver konfigurieren (überspringen Sie diesen Abschnitt). IIS Express wird für die ersten Tests empfohlen.

Wenn Sie lokale IIS-Webserver verwenden, gehen Sie folgendermaßen vor.

1. Stellen Sie sicher, dass IIS ordnungsgemäß installiert ist. Weitere Informationen finden Sie unter [IIS 8.0 mithilfe von ASP.NET 3.5 und ASP.NET 4.5](https://docs.microsoft.com/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    * Stellen Sie sicher, dass Sie die richtige Version von ASP.NET auf dem Server installieren. Verwenden Sie den Webplattform-Installer (WebPI), um ASP.NET 4.5 installieren (Wählen Sie den Serverknoten in Windows Server 2012 R2, **neue Webplattformkomponenten abrufen** und suchen Sie nach ASP.NET). Um ASP.NET Core installieren möchten, finden Sie unter [in IIS veröffentlichen](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration).

    > [!NOTE]
    > Wenn Sie Windows Server 2008 R2 verwenden, installieren Sie ASP.NET 4 stattdessen mit dem folgenden Befehl:

     **C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe - ir**

2. Öffnen der **Internetinformationsdienste (IIS) Manager**. (Wählen Sie im linken Bereich des Server-Managers **IIS**. Mit der rechten Maustaste in des Servers, und wählen Sie **(Internet Information Services, IIS) Manager**.)

3. Klicken Sie unter **Verbindungen** im linken Bereich, wechseln Sie zu **Sites**.

4. Klicken Sie mit der rechten Maustaste auf den Knoten **Standardwebsite** , und wählen Sie **Anwendung hinzufügen**aus.

5. Festlegen der **Alias** Feld **MyASPApp**, übernehmen Sie den Standardnamen Anwendungspool (**DefaultAppPool**), und legen Sie die **physischen Pfad** auf  **C:\inetpub\myNewFolder** (Erstellen eines neuen Ordners für die app).

6. Klicken Sie unter **Verbindungen**Option **Anwendungspools**. Open **DefaultAppPool** und legen Sie das Feld "Anwendungspool" auf den Wert, der richtige für Ihre Anwendung (verwenden Sie ASP.NET 4 für ASP.NET 4.5. Verwenden Sie **kein verwalteter Code** für ASP.NET Core).

## <a name="local-iis-web-server-deploy-the-app"></a>(Lokale IIS-Webserver) Bereitstellen der app

Für IIS Express, die Web-app wird automatisch bereitgestellt, wenn Sie das Debuggen starten (überspringen Sie diesen Abschnitt).

Wenn Sie lokale IIS-Webserver verwenden, gehen Sie folgendermaßen vor. Es gibt verschiedene Möglichkeiten zum Veröffentlichen der app in IIS. In den folgenden Schritten wird beschrieben, wie zum Erstellen und Verwenden eines Veröffentlichungsprofils, damit Sie mit dem Dateisystem bereitstellen können.

1. Starten Sie Visual Studio als Administrator an.

    Um mit dieser Methode bereitstellen, benötigen Sie Administratorrechte.

2. Klicken Sie in Visual Studio mit der rechten Maustaste des Projekts, und wählen Sie **veröffentlichen** (verwenden Sie für Web Forms, **Web-App veröffentlichen**).

3. Wählen Sie **IIS, FTP usw.** , und klicken Sie auf **veröffentlichen**.

    ![In IIS veröffentlichen](../debugger/media/dbg-aspnet-local-iis.png "in IIS veröffentlichen")

    Wählen Sie für eine Web Forms-app **benutzerdefinierte** Geben Sie im Dialogfeld "Veröffentlichen" einen Profilnamen ein, und wählen Sie **OK**.

4. In der **Veröffentlichungsmethode** Feld **Dateisystem**.

5. Für die **Zielpfade**, klicken Sie auf die **Durchsuchen** Schaltfläche.

6. (ASP.NET Core) Wählen Sie **Dateisystem** und wählen Sie den Ordner, in dem Sie zuvor erstellt für die app haben.

6. (ASP.NET) Wählen Sie **lokale IIS**, und wählen Sie die Website, die Sie zuvor erstellt haben, und klicken Sie dann auf **öffnen**.

    ![In IIS veröffentlichen](../debugger/media/dbg-aspnet-local-iis-select-site.png "in IIS veröffentlichen")

    > [!TIP]
    > Wenn Sie, dass eine Nachricht, die besagt, den Webserver dass nicht ordnungsgemäß konfiguriert ist sehen, stellen Sie sicher, dass die richtige Version von ASP.NET für IIS installiert ist.

7. Klicken Sie auf **Weiter** , und wählen Sie eine **Debuggen** Konfiguration.

    > [!NOTE]
    > Wenn Sie mit einer Release-Konfiguration bereitstellen, wird hiermit `debug=false` in der Datei "Web.config" der Serverdatei.

8. Klicken Sie auf **speichern** zum Speichern von Einstellungen für die Veröffentlichung, und klicken Sie dann auf **veröffentlichen**.

    > [!CAUTION]
    >  Wenn Sie den Code oder Rebuild ändern müssen, müssen Sie erneut veröffentlichen, und wiederholen Sie diesen Schritt. Die ausführbare Datei, die Sie auf den Remotecomputer kopiert haben, muss genau mit der lokalen Quelle und den lokalen Symbolen übereinstimmen.

## <a name="set-a-breakpoint-and-start-debugging"></a>Festlegen eines Haltepunkts und das Debuggen starten

1. In Ihr Projekt in Visual Studio Festlegen eines Haltepunkts auf Code, den Sie wissen, ausgeführt wird.

2. Drücken Sie zum Starten des Debugvorgangs **F5** (**Debuggen > Debuggen starten**).

3. Aktionen Sie zum Ausführen des Codes, die den Breakpoint enthält.

    Der Debugger hält, wo Sie den Haltepunkt festlegen.

### <a name="local-iis-troubleshooting-cannot-hit-the-breakpoint"></a>(Lokale IIS) Problembehandlung: Kann nicht der Haltepunkt erreicht.

1. Starten Sie die Web-app von IIS, und stellen Sie sicher, dass er ordnungsgemäß ausgeführt wird. Lassen Sie die Web-app ausgeführt wird.

2. Wählen Sie in Visual Studio **Debuggen > an den Prozess anhängen** und Herstellen einer Verbindung mit der ASP.NET-Prozess (i. d. r. **w3wp.exe** oder **dotnet.exe**). Weitere Informationen finden Sie unter [an den Prozess anhängen](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

    Wenn Sie über eine Verbindung herstellen können **an den Prozess anhängen** und können einen Haltepunkt erreicht, jedoch kann nicht gestartet werden Debuggen mit **F5**, ist es wahrscheinlich, dass eine Einstellung in den Projekteigenschaften falsch ist. Wenn Sie eine HOSTS-Datei verwenden, stellen Sie sicher, dass er ordnungsgemäß konfiguriert ist.

  
## <a name="robust-programming"></a>Stabile Programmierung  
An Web.config-Dateien vorgenommene Änderungen werden von [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] automatisch erkannt und die neuen Konfigurationseinstellungen angewendet. Sie müssen den Computer oder den IIS-Server nicht neu starten, damit die Änderungen wirksam werden.  
  
Eine Website kann mehrere virtuelle Verzeichnisse und Unterverzeichnisse enthalten, in denen möglicherweise Web.config-Dateien vorhanden sind. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Anwendungen erben Einstellungen von Web.config-Dateien auf höheren Ebenen im URL-Pfad. Mithilfe hierarchischer Konfigurationsdateien können Sie die Einstellungen für mehrere [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Anwendungen gleichzeitig ändern, z. B. für alle Anwendungen, die sich in der Hierarchie unterhalb der jeweiligen Konfigurationsdatei befinden. Jedoch wenn `debug` festgelegt ist in einer Datei, die sich in der Hierarchie, überschreibt er die höheren Wert.  
  
Sie können z. B. angeben `debug="true"` in www.microsoft.com/aaa/Web.config und alle Anwendungen im Ordner aaa und in jedem Unterordner von aaa Einstellung erbt. Wenn also Ihre [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] -Anwendung also unter www.microsoft.com/aaa/bbb, erbt diese Einstellung ebenso wie alle [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Anwendungen in www.microsoft.com/aaa/ccc, www.microsoft.com/aaa/ddd usw.. Die einzige Ausnahme stellen Anwendungen dar, die die Einstellungen mit einer eigenen Web.config-Datei auf einer niedrigeren Ebene überschreiben.  
  
> [!IMPORTANT]
> Erheblich Aktivieren des Debugmodus wirkt sich auf die Leistung Ihrer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Anwendung. Vergessen Sie nie, den Debugmodus zu deaktivieren, bevor Sie die Releaseversion einer Anwendung bereitstellen oder Leistungsmessungen durchführen.  
  
## <a name="see-also"></a>Siehe auch  
[ASP.NET-Debuggen: Systemanforderungen](aspnet-debugging-system-requirements.md)   
[Vorgehensweise: Ausführen des Workerprozesses unter einem Benutzerkonto](how-to-run-the-worker-process-under-a-user-account.md)   
[Vorgehensweise: herausfinden des ASP.NET-Prozessnamens](how-to-find-the-name-of-the-aspnet-process.md)   
[Debuggen bereitgestellte Webanwendungen](debugging-deployed-web-applications.md)   
[Exemplarische Vorgehensweise: Debuggen eines Web Forms](walkthrough-debugging-a-web-form.md)   
[Vorgehensweise: Debuggen von ASP.NET-Ausnahmen](how-to-debug-aspnet-exceptions.md)   
[Debuggen von Webanwendungen: Fehler und Problembehandlung](debugging-web-applications-errors-and-troubleshooting.md)
  
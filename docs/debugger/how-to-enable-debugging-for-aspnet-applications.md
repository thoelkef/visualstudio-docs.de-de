---
title: Aktivieren Sie das Debuggen für ASP.NET-Anwendungen | Microsoft-Dokumentation
ms.custom: H1HackMay2017
ms.date: 09/21/17
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 438e5a96ef07faf399d06ae517afe313a44673b4
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057849"
---
# <a name="debug-aspnet-applications-in-visual-studio"></a>Debuggen von ASP.NET-Anwendungen in Visual Studio

Sie können ASP.NET-Anwendungen in Visual Studio debuggen.

## <a name="requirements"></a>Anforderungen

Um die Anweisungen in diesem Thema folgen zu können, müssen wie folgt vor:

- IIS Express, die standardmäßig in Visual Studio 2012 und höher enthalten ist

    - oder - 

- Eine lokale IIS web-Server (Version 8.0 oder höher), richtig konfiguriert ist, und kann die ASP.NET-Anwendung ohne Fehler ausgeführt.

Wenn Sie den Server remote verfügbar ist, muss der Remotedebugger auf dem Remotecomputer ausgeführt werden. Zum Debuggen auf einem remote-IIS-Server finden Sie unter [Remotedebuggen von ASP.NET auf einem Computer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). 

## <a name="configure-debug-settings"></a>Konfigurieren von Einstellungen zum Debuggen

### <a name="enable-aspnet-debugging-in-the-project-properties"></a>Aktivieren Sie das ASP.NET-Debuggen in den Projekteigenschaften

1. Öffnen Sie Ihr ASP.NET-Projekt in Visual Studio.

2. Mit der rechten Maustaste in des Projekts im **Projektmappen-Explorer**, wählen Sie **Eigenschaften**, und klicken Sie dann auf die **Web** Registerkarte.

    Wählen Sie für einige Projekttypen **Eigenschaften > Debuggen** stattdessen. Für ein ASP.NET für Web Forms-Projekt mit der rechten Maustaste in des Projekts, und wählen Sie **Eigenschaftenseiten > Startoptionen**.
  
3.  Aktivieren Sie unter **Debugger**das Kontrollkästchen **ASP.NET** .

    ![Debuggereinstellungen](../debugger/media/dbg-aspnet-enable-debugging.png "Debuggereinstellungen")

> [!NOTE]
> Wenn Sie ein neues ASP.NET-Projekt erstellen (**Datei > Neues Projekt**), die Debugeinstellungen bereits ordnungsgemäß konfiguriert sind.

### <a name="enable-debugging-in-the-webconfig-file"></a>Aktivieren des Debuggens in der Datei "Web.config"  

Um eine Web-app zu debuggen, muss die Datei web.config der Anwendung ordnungsgemäß konfiguriert sein. Eine Datei "Web.config" ist erforderlich, wenn Sie die app auf IIS oder IIS Express hosten.

Für ASP.NET Core wird die Datei "Web.config" automatisch erstellt, wenn die app bereitgestellt wird (sofern es nicht bereits vorhanden ist).

> [!TIP]
> Ihr Bereitstellungsprozess kann es sich um die Einstellungen für die Datei "Web.config" aktualisieren. Überprüfen Sie vor dem Debuggen möchten, also der web.config-Einstellung auf dem Server.
  
1.  Öffnen Sie in Visual Studio die Projektdatei "Web.config" ein.  
  
    > [!NOTE]  
    > Sie können nicht die Datei "Web.config" Remotezugriff über einen Webbrowser. Aus Sicherheitsgründen wird Microsoft IIS durch [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] so konfiguriert, dass ein direkter Browserzugriff auf die Web.config-Dateien nicht möglich ist. Wenn Sie versuchen, eine Konfigurationsdatei, die mit einem Browser zuzugreifen, erhalten Sie eine HTTP-Zugriffsfehler 403 (Verboten).  
  
2.  Suchen Sie das Element `configuration/system.web/compilation` . Wenn das compilation-Element nicht den vorhanden ist, erstellen Sie es.

    Web.config ist eine XML-Datei und enthält daher mit Tags markierte, geschachtelte Abschnitte.
  
3.  Wenn das `compilation` -Element kein `debug` -Attribut enthält, fügen Sie dem Element das Attribut hinzu.  
  
4.  Stellen Sie sicher, dass der `debug` -Attributwert auf `true`.  
  
Die Datei "Web.config" sollte wie im folgenden Beispiel aussehen:

> [!NOTE]
> In diesem Beispiel ist eine partielle web.config-Datei. Zusätzliche XML-Abschnitte sind in der Regel vorhanden ist, zwischen den Konfigurations- und system.web-Elementen. Das Compilation-Element kann auch andere Attribute und Elemente enthalten.
  
#### <a name="example"></a>Beispiel  
  
```xml
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

Wenn Sie einen externen Server anstelle des Standardservers von IIS Express verwenden, Sie müssen auch sicherstellen, dass die `targetFramework` Attributwert der Konfiguration auf dem Server entspricht.

> [!IMPORTANT]
> Legen Sie für eine optimale Leistung eine Produktions-app auf `debug=false` , und geben Sie ein Releasebuild erstellt, wenn Sie beim Erstellen und veröffentlichen Sie die app.

## <a name="configure-project-settings-for-the-server"></a>Projekteinstellungen für den Server konfigurieren

Festlegen von Projekteigenschaften für das Debuggen auf einem lokalen Webserver. Für das Debuggen auf einem Remoteserver, führen Sie auf die ausführlichere Anweisungen, die in beschriebenen [Remote Debugging ASP.NET on IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) stattdessen.

1. In der **Web** des Projekts auf der Registerkarte Eigenschaften, wählen Sie entweder **IIS Express** oder **externen Server** unter der **Server** Einstellungen. (Bei einigen Projekttypen, diese Einstellungen werden angezeigt, unter dem **Debuggen** stattdessen die Registerkarte.)

    ![Servereinstellungen](../debugger/media/dbg-aspnet-server-settings.png "-servereinstellungen")

    IIS Express ist der Standardserver für ASP.NET und erfordert normalerweise keine spezielle Konfiguration. Dies ist die einfachste Möglichkeit zum Debuggen einer ASP.NET-Anwendung.

    Für ein ASP.NET für Web Forms-Projekt Maustaste auf das Projekt, wählen **Eigenschaftenseiten > Startoptionen**, und wählen Sie entweder **ndardwebserver verwenden** oder **benutzerdefinierten Server verwenden** () anstelle von **externen Server**).

    ![Server-Einstellungen für Web Forms-app](../debugger/media/dbg-aspnet-server-settings-webforms.png "-servereinstellungen für Web Forms-app")

2. Wenn Sie einen externen (benutzerdefinierten)-Server auswählen, geben Sie die richtige URL in die **Projekt-URL** (oder **Basis-URL**) Feld.

    Wenn der externe Server lokale IIS ist, muss IIS installiert und ordnungsgemäß konfiguriert. Beispielsweise muss die richtige Version von ASP.NET in IIS konfiguriert werden. Weitere Informationen finden Sie unter [IIS 8.0 mithilfe von ASP.NET 3.5 und ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45). Wenn Sie die Bereitstellung sowie das Debuggen von testen möchten, finden Sie unter [bereitstellen, um zu testen](/aspnet/web-forms/overview/deployment/visual-studio-web-deployment/deploying-to-iis).

    Wenn der externe Server [remote](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md), Sie an den Prozess anhängen stattdessen, und diese projekteinstellungen werden nicht für das Debuggen verwendet.

## <a name="local-iis-web-server-configure-iis"></a>(Lokale IIS-Webserver) Konfigurieren von IIS

Für IIS Express, müssen Sie nicht den Webserver konfigurieren (überspringen Sie diesen Abschnitt). IIS Express wird für die anfänglichen Tests empfohlen.

Wenn Sie lokale IIS-Webserver verwenden, gehen Sie wie folgt vor.

1. Stellen Sie sicher, dass IIS ordnungsgemäß installiert ist. Weitere Informationen finden Sie unter [IIS 8.0 mithilfe von ASP.NET 3.5 und ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    * Stellen Sie sicher, dass Sie die richtige Version von ASP.NET auf dem Server installieren. Verwenden Sie den Webplattform-Installer (WebPI) installieren Sie ASP.NET 4.5 (Wählen Sie den Serverknoten in Windows Server 2012 R2, **neue Webplattformkomponenten abrufen** und suchen Sie nach ASP.NET). So installieren ASP.NET Core, finden Sie unter [Publishing to IIS](https://docs.asp.net/en/latest/publishing/iis.html#iis-configuration).

    > [!NOTE]
    > Wenn Sie Windows Server 2008 R2 verwenden, installieren Sie ASP.NET 4 stattdessen mit dem folgenden Befehl aus:

     **C:\Windows\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -ir**

2. Öffnen der **Internetinformationsdienste (IIS) Manager**. (Wählen Sie im linken Bereich des Server-Managers **IIS**. Mit der rechten Maustaste in des Servers, und wählen Sie **(Internet Information Services, IIS) Manager**.)

3. Klicken Sie unter **Verbindungen** wechseln Sie im linken Bereich zu **Websites**.

4. Klicken Sie mit der rechten Maustaste auf den Knoten **Standardwebsite** , und wählen Sie **Anwendung hinzufügen**aus.

5. Festlegen der **Alias** Feld **MyASPApp**, übernehmen Sie den Standardwert-Anwendungspool (**DefaultAppPool**), und legen Sie die **physischer Pfad** zu  **C:\inetpub\myNewFolder** (erstellen Sie einen neuen Ordner für die app).

6. Klicken Sie unter **Verbindungen**Option **Anwendungspools**. Open **DefaultAppPool** und legen Sie das Feld "Anwendungspool" auf den Wert für Ihre Anwendung (verwenden Sie ASP.NET 4 für ASP.NET 4.5. Verwenden Sie **kein verwalteter Code** für ASP.NET Core).

## <a name="local-iis-web-server-deploy-the-app"></a>(Lokale IIS-Webserver) Bereitstellen der app

Für IIS Express, Web-app wird automatisch bereitgestellt, wenn Sie das Debuggen starten (überspringen Sie diesen Abschnitt).

Wenn Sie lokale IIS-Webserver verwenden, gehen Sie wie folgt vor. Es gibt verschiedene Möglichkeiten zum Veröffentlichen Ihrer app in IIS. In den folgenden Schritten wird beschrieben, wie zum Erstellen und verwenden ein Veröffentlichungsprofil aus, sodass Sie mit dem Dateisystem bereitstellen können.

1. Starten Sie Visual Studio als Administrator an.

    Um mit dieser Methode bereitstellen, benötigen Sie Administratorrechte.

2. Klicken Sie in Visual Studio mit der rechten Maustaste in des Projekts, und wählen Sie **veröffentlichen** (verwenden Sie für Web Forms, **Web-App veröffentlichen**).

3. Wählen Sie **IIS, FTP usw.** , und klicken Sie auf **veröffentlichen**.

    ![In IIS veröffentlichen](../debugger/media/dbg-aspnet-local-iis.png "in IIS veröffentlichen")

    Wählen Sie für eine Web Forms-app **benutzerdefinierte** veröffentlichungsdialogfeld, geben Sie einen Profilnamen ein, und wählen Sie **OK**.

4. In der **Veröffentlichungsmethode** Feld, und wählen Sie **Dateisystem**.

5. Für die **Zielspeicherort**, klicken Sie auf die **Durchsuchen** Schaltfläche.

6. (ASP.NET Core) Wählen Sie **Dateisystem** , und wählen Sie den Ordner, in dem Sie zuvor erstellt für die app haben.

6. (ASP.NET) Wählen Sie **lokale IIS**, und wählen Sie die Website, die Sie zuvor erstellt haben, und klicken Sie dann auf **öffnen**.

    ![In IIS veröffentlichen](../debugger/media/dbg-aspnet-local-iis-select-site.png "in IIS veröffentlichen")

    > [!TIP]
    > Wenn Sie, dass eine Nachricht den Webserver nicht ordnungsgemäß konfiguriert ist sehen, stellen Sie sicher, dass die richtige Version von ASP.NET für IIS installiert ist.

7. Klicken Sie auf **Weiter** , und wählen Sie eine **Debuggen** Konfiguration.

    > [!NOTE]
    > Wenn Sie mit einer Releasekonfiguration bereitstellen, wird hiermit `debug=false` in web.config-Datei des Servers.

8. Klicken Sie auf **speichern** zum Speichern von Einstellungen für die Veröffentlichung aus, und klicken Sie dann auf **veröffentlichen**.

    > [!CAUTION]
    >  Wenn Sie den Code oder die Neuerstellung ändern möchten, müssen Sie erneut veröffentlichen und wiederholen Sie diesen Schritt. Die ausführbare Datei, die Sie auf den Remotecomputer kopiert haben, muss genau mit der lokalen Quelle und den lokalen Symbolen übereinstimmen.

## <a name="set-a-breakpoint-and-start-debugging"></a>Festlegen eines Haltepunkts und das Debuggen starten

1. In Ihrem Projekt in Visual Studio wird für einen Code, den Sie wissen, einen Haltepunkt ausgeführt.

2. Drücken Sie zum Starten des Debuggens **F5** (**Debuggen > Debuggen starten**).

3. Führen Sie Aktionen, um den Code auszuführen, der den Haltepunkt enthält.

    Der Debugger hält, in dem Sie den Haltepunkt festgelegt, ist.

### <a name="local-iis-troubleshooting-cannot-hit-the-breakpoint"></a>(Lokale IIS) Problembehandlung: Kann nicht der Haltepunkt erreicht.

1. Starten Sie die Web-app von IIS aus, und stellen Sie sicher, dass er ordnungsgemäß ausgeführt wird. Lassen Sie die Web-app ausgeführt wird.

2. Wählen Sie in Visual Studio **Debuggen > an den Prozess anhängen** und eine Verbindung mit dem ASP.NET-Prozess (in der Regel **w3wp.exe** oder **dotnet.exe**). Weitere Informationen finden Sie unter [an den Prozess anhängen](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

    Wenn Sie über eine Verbindung herstellen können **an den Prozess anhängen** und können einen Haltepunkt, jedoch kann nicht gestartet werden Debuggen mit **F5**, ist es wahrscheinlich, dass eine Einstellung in den Projekteigenschaften falsch ist. Wenn Sie eine Datei "HOSTS" verwenden, stellen Sie sicher, dass er richtig konfiguriert ist.

  
## <a name="robust-programming"></a>Stabile Programmierung  
An Web.config-Dateien vorgenommene Änderungen werden von [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] automatisch erkannt und die neuen Konfigurationseinstellungen angewendet. Sie müssen den Computer oder den IIS-Server nicht neu starten, damit die Änderungen wirksam werden.  
  
Eine Website kann mehrere virtuelle Verzeichnisse und Unterverzeichnisse enthalten, in denen möglicherweise Web.config-Dateien vorhanden sind. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Anwendungen erben Einstellungen von Web.config-Dateien auf höheren Ebenen im URL-Pfad. Mithilfe hierarchischer Konfigurationsdateien können Sie die Einstellungen für mehrere [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Anwendungen gleichzeitig ändern, z. B. für alle Anwendungen, die sich in der Hierarchie unterhalb der jeweiligen Konfigurationsdatei befinden. Aber wenn `debug` festgelegt ist in einer Datei, die sich in der Hierarchie, überschreibt es den höheren Wert.  
  
Sie können z. B. angeben `debug="true"` in www.microsoft.com/aaa/Web.config, alle Anwendungen im Ordner aaa und in jedem Unterordner von aaa erbt und diese Einstellung. Wenn also Ihre [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] -Anwendung also unter www.microsoft.com/aaa/bbb ist, erbt er diese Einstellung ebenso wie alle [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Anwendungen in www.microsoft.com/aaa/ccc, www.microsoft.com/aaa/ddd und So weiter. Die einzige Ausnahme stellen Anwendungen dar, die die Einstellungen mit einer eigenen Web.config-Datei auf einer niedrigeren Ebene überschreiben.  
  
> [!IMPORTANT]
> Aktivieren des Debugmodus erheblich beeinträchtigt die Leistung der Ihre [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Anwendung. Vergessen Sie nie, den Debugmodus zu deaktivieren, bevor Sie die Releaseversion einer Anwendung bereitstellen oder Leistungsmessungen durchführen.  
  
## <a name="see-also"></a>Siehe auch  
[ASP.NET-Debugging: Systemanforderungen](aspnet-debugging-system-requirements.md)   
[Gewusst wie: Ausführen des Workerprozesses unter einem Benutzerkonto](how-to-run-the-worker-process-under-a-user-account.md)   
[Gewusst wie: herausfinden des ASP.NET-Prozessnamens](how-to-find-the-name-of-the-aspnet-process.md)   
[Debuggen bereitgestellter Webanwendungen](debugging-deployed-web-applications.md)   
[Exemplarische Vorgehensweise: Debuggen eines Web Forms](walkthrough-debugging-a-web-form.md)   
[Gewusst wie: Debuggen von ASP.NET-Ausnahmen](how-to-debug-aspnet-exceptions.md)   
[Debuggen von Webanwendungen: Fehler und Problembehandlung](debugging-web-applications-errors-and-troubleshooting.md)
  

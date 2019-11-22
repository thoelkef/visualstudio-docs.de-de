---
title: Aktivieren des Debuggens für ASP.net-apps | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/21/2018
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
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: a6f20a2272214a525b00ebf07ebc6e5e803b138c
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911356"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>ASP.net-oder ASP.net Core-apps in Visual Studio debuggen

Sie können ASP.net-und ASP.net Core-apps in Visual Studio debuggen. Der Prozess unterscheidet sich zwischen ASP.net und ASP.net Core sowie davon, ob Sie ihn auf IIS Express oder einem lokalen IIS-Server ausführen.

>[!NOTE]
>Die folgenden Schritte und Einstellungen gelten nur für das Debuggen von apps auf einem lokalen Server. Beim Debuggen von apps auf einem Remote-IIS-Server wird **Attach to Process**verwendet. diese Einstellungen werden ignoriert. Weitere Informationen und Anweisungen zum Remote Debuggen von ASP.net-apps auf IIS finden Sie unter [Remote Debuggen ASP.net auf einem IIS-Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) oder remotedebugASP.net Core [auf einem IIS-Remote Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

Der integrierte IIS Express Server ist in Visual Studio enthalten. IIS Express ist der standarddebugserver für ASP.net-und ASP.net Core-Projekte und ist vorkonfiguriert. Dies ist die einfachste Möglichkeit zum Debuggen und eignet sich ideal für das anfängliche Debuggen und testen.

Sie können auch eine ASP.net-oder ASP.net Core-App auf einem lokalen IIS-Server (Version 8,0 oder höher) Debuggen, der für die Ausführung der App konfiguriert ist. Zum Debuggen auf lokalen IIS müssen die folgenden Anforderungen erfüllt sein:

<a name="iis"></a>
- Wählen Sie **Entwicklungszeit-IIS-Unterstützung** bei der Installation von Visual Studio (Falls erforderlich, führen Sie die Visual Studio-Installer erneut aus, wählen Sie **ändern**aus, und fügen Sie diese Komponente hinzu.)
- Führen Sie Visual Studio als Administrator aus.
- Installieren und konfigurieren Sie IIS ordnungsgemäß mit den entsprechenden Versionen von ASP.net und/oder ASP.net Core. Weitere Informationen und Anweisungen finden Sie unter [IIS 8,0 Using ASP.NET 3,5 and ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) oder [Host ASP.net Core on Windows with IIS](/aspnet/core/host-and-deploy/iis/index).
- Stellen Sie sicher, dass die APP auf IIS ohne Fehler ausgeführt wird.

## <a name="debug-aspnet-apps"></a>Debuggen ASP.net apps

IIS Express ist die Standardeinstellung und ist vorkonfiguriert. Wenn Sie auf lokalen IIS Debuggen, stellen Sie sicher, [dass Sie die Anforderungen für das lokale IIS-Debugging](#iis)erfüllen.

1. Wählen Sie in Visual **Projektmappen-Explorer** Studio das Projekt ASP.net aus, und klicken Sie auf das Symbol " **Eigenschaften** ", drücken Sie die **alt** -Taste+**Eingabe**, **oder klicken Sie**mit der rechten Maustaste

1. Wählen Sie die Registerkarte **Web** aus.

1. Klicken Sie im Bereich **Eigenschaften** unter **Server**auf
   - Wählen Sie für IIS Express **IIS Express** aus der Dropdown Liste aus.
   - Für lokale IIS
     1. Wählen Sie in der Dropdown Liste **lokale IIS** aus.
     1. Wählen Sie neben dem Feld **Projekt-URL** die Option **virtuelles Verzeichnis erstellen**, wenn Sie die APP noch nicht in IIS eingerichtet haben.

1. Wählen **Sie unter "** Debug" die Option **ASP.net**aus.

   ![ASP.NET-Debugger-Einstellungen](media/dbg-aspnet-enable-debugging2.png "ASP.NET-Debugger-Einstellungen")

1. Verwenden Sie **File** > **ausgewählte Elemente speichern** oder **STRG**+**S** , um alle Änderungen zu speichern.

1. Wenn Sie die APP debuggen möchten, legen Sie in Ihrem Projekt Breakpoints für Code fest. Stellen Sie in der Visual Studio-Symbolleiste sicher, dass die Konfiguration auf **Debuggen**festgelegt ist, und der gewünschte Browser wird in **IIS Express (\<Browser Name >)** oder **lokale IIS (\<Browser Name >)** im Feld Emulator angezeigt.

1. Wählen Sie zum Starten des Debuggens **IIS Express (\<Browser Namen >)** oder **Lokales IIS (\<Browser Name >)** auf der Symbolleiste aus, wählen Sie im Menü **Debuggen** die Option **Debuggen starten** , oder drücken Sie **F5**. Der Debugger hält an den Breakpoints an. Wenn der Debugger die Breakpoints nicht erreichen kann, finden Sie weitere Informationen unter Problembehandlung beim [Debugging](#troubleshoot-debugging).

## <a name="debug-aspnet-core-apps"></a>Debuggen ASP.net Core apps

IIS Express ist die Standardeinstellung und ist vorkonfiguriert. Wenn Sie auf lokalen IIS Debuggen, stellen Sie sicher, [dass Sie die Anforderungen für das lokale IIS-Debugging](#iis)erfüllen.

1. Wählen Sie in Visual **Projektmappen-Explorer** Studio das Projekt ASP.net Core aus, und klicken Sie auf das Symbol " **Eigenschaften** ", drücken Sie **alt**+**Eingabe**, oder klicken Sie mit der rechten Maustaste auf **Eigenschaften**.

1. Klicken Sie auf die Registerkarte **Debuggen**.

1. Im Bereich **Eigenschaften** neben **Profil**,
   - Wählen Sie für IIS Express **IIS Express** aus der Dropdown Liste aus.
   - Wählen Sie für lokales IIS in der Dropdown Liste den Namen der APP aus, oder wählen Sie **neu**aus, erstellen Sie einen neuen Profilnamen, und wählen Sie **OK**aus.

1. Wählen Sie neben **Start**entweder **IIS Express** oder **IIS** aus der Dropdown Liste aus.

1. Stellen Sie sicher, dass **Start Browser** ausgewählt ist.

1. Stellen Sie unter **Umgebungsvariablen**sicher, dass **ASPNETCORE_ENVIRONMENT** mit einem Wert für **Entwicklung**vorhanden ist. Wenn nicht, wählen Sie **Hinzufügen** aus, und fügen Sie es hinzu

   ![Debugger-Einstellungen ASP.net Core](../debugger/media/dbg-aspnet-enable-debugging3.png "Debugger-Einstellungen ASP.net Core")

1. Verwenden Sie **File** > **ausgewählte Elemente speichern** oder **STRG**+**S** , um alle Änderungen zu speichern.

1. Wenn Sie die APP debuggen möchten, legen Sie in Ihrem Projekt Breakpoints für Code fest. Stellen Sie in der Visual Studio-Symbolleiste sicher, dass die Konfiguration auf **Debuggen**festgelegt ist und entweder **IIS Express**oder der neue Name des IIS-Profils im Feld Emulator angezeigt wird.

1. Wählen Sie zum Starten des Debuggens **IIS Express** oder **\<IIS-Profilnamen aus >** klicken Sie **auf der Symbol** Leiste auf **Debuggen starten** , oder drücken Sie **F5**. Der Debugger hält an den Breakpoints an. Wenn der Debugger die Breakpoints nicht erreichen kann, finden Sie weitere Informationen unter Problembehandlung beim [Debugging](#troubleshoot-debugging).

## <a name="troubleshoot-debugging"></a>Problembehandlung beim Debugging

Wenn das lokale IIS-Debugging nicht in den Breakpoint fortgesetzt werden kann, führen Sie die folgenden Schritte zur Problembehandlung aus

1. Starten Sie die Web-App über IIS, und stellen Sie sicher, dass Sie ordnungsgemäß ausgeführt wird Lassen Sie die Web-App ausgeführt.

2. Wählen Sie in Visual Studio **Debuggen > an den Prozess anhängen** , oder drücken Sie **STRG**+**alt**+**P**, und stellen Sie eine Verbindung mit dem ASP.net-oder ASP.net Core Prozess her (in der Regel **w3wp. exe** oder **dotnet. exe**). Weitere Informationen finden Sie unter [an den Prozess anhängen](attach-to-running-processes-with-the-visual-studio-debugger.md) und [Ermitteln des Namens des ASP.NET-Prozesses](how-to-find-the-name-of-the-aspnet-process.md).

Wenn Sie eine Verbindung herstellen und den Haltepunkt mithilfe von **an den Prozess anhängen**, aber nicht mithilfe von **Debug** > **Debuggen starten** oder **F5**erreichen können, ist eine Einstellung in den Projekteigenschaften wahrscheinlich falsch. Wenn Sie eine Hosts-Datei verwenden, stellen Sie sicher, dass Sie auch ordnungsgemäß konfiguriert ist.

## <a name="configure-debugging-in-the-webconfig-file"></a>Debuggen in der Datei "Web. config" Konfigurieren

ASP.net-Projekte verfügen standardmäßig über *Web. config* -Dateien, die sowohl App-Konfigurations-als auch Startinformationen enthalten, einschließlich Debugeinstellungen. Die *Web. config* -Dateien müssen ordnungsgemäß für das Debuggen konfiguriert werden. Die **Eigenschaften** Einstellungen in den vorherigen Abschnitten aktualisieren die *Web. config* -Dateien, Sie können Sie jedoch auch manuell konfigurieren.

> [!NOTE]
> ASP.net Core Projekte verfügen anfänglich nicht über *Web. config* -Dateien, verwenden jedoch die Dateien *appSettings. JSON* und *launchsettings. JSON* für die APP-Konfiguration und Startinformationen. Beim Bereitstellen der App werden eine *Web. config* -Datei oder Dateien im Projekt erstellt, aber Sie enthalten in der Regel keine Debuginformationen.

> [!TIP]
> Der Bereitstellungs Prozess kann die *Web. config* -Einstellungen aktualisieren. Stellen Sie daher vor dem Debuggen sicher, dass die Datei " *Web. config* " für das Debugging konfiguriert ist.

**So konfigurieren Sie eine *Web. config* -Datei manuell für das Debuggen:**

1. Öffnen Sie in Visual Studio die Datei *Web. config* des ASP.NET-Projekts.

2. *Web. config* ist eine XML-Datei, die die durch Tags markierten Abschnitte enthält. Machen Sie den Abschnitt `configuration/system.web/compilation` ausfindig. (Wenn das `compilation` Element nicht vorhanden ist, erstellen Sie es.)

3. Stellen Sie sicher, dass das `debug`-Attribut im `compilation`-Element auf `true`festgelegt ist. (Wenn das `compilation`-Element kein `debug`-Attribut enthält, fügen Sie es hinzu, und legen Sie es auf `true`fest.)

   Wenn Sie anstelle des Standard IIS Express Servers lokale IIS verwenden, stellen Sie sicher, dass der Wert des `targetFramework`-Attributs im `compilation`-Element mit dem Framework auf dem IIS-Server übereinstimmt.

   Das `compilation`-Element der Datei " *Web. config* " sollte wie im folgenden Beispiel aussehen:

   > [!NOTE]
   > Dieses Beispiel ist eine partielle *Web. config* -Datei. In den `configuration`-und `system.web` Elementen sind in der Regel weitere XML-Abschnitte enthalten, und das `compilation`-Element kann auch andere Attribute und Elemente enthalten.

   ```xml
   <configuration>
      ...
      <system.web>
          <compilation  debug="true"  targetFramework="4.6.1" ... >
             ...
          </compilation>
      </system.web>
   </configuration>
   ```

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] erkennt an *web.config*-Dateien vorgenommene Änderungen automatisch und wendet die neuen Konfigurationseinstellungen an. Sie müssen den Computer oder den IIS-Server nicht neu starten, damit die Änderungen wirksam werden.

Eine Website kann mehrere virtuelle Verzeichnisse und Unterverzeichnisse mit *Web. config* -Dateien enthalten. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-apps erben Konfigurationseinstellungen von *Web. config* -Dateien auf höheren Ebenen im URL-Pfad. Die hierarchischen Einstellungen der *Web. config* -Datei gelten für alle [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-apps, die sich in der Hierarchie befinden. Durch Festlegen einer anderen Konfiguration in einer *Web. config* -Datei, die sich weiter unten in der Hierarchie befand, werden die Einstellungen in der höheren Datei überschrieben

Wenn Sie z. b. `debug="true"` in <em>www.Microsoft.com/aaa/Web.config</em>angeben, erbt jede APP im *AAA* -Ordner oder in einem Unterordner von *AAA* diese Einstellung, es sei denn, eine dieser apps überschreibt die Einstellung mit ihrer eigenen *Web. config* -Datei. Datei.

## <a name="publish-in-debug-mode-using-the-file-system"></a>Veröffentlichen im Debugmodus mit dem Dateisystem

Es gibt verschiedene Möglichkeiten zum Veröffentlichen von apps in IIS. Diese Schritte zeigen, wie Sie ein debugveröffentlichungsprofil mithilfe des Dateisystems erstellen und bereitstellen. Zu diesem Zweck müssen Sie Visual Studio als Administrator ausführen.

> [!IMPORTANT]
> Wenn Sie Ihren Code ändern oder neu erstellen, müssen Sie diese Schritte wiederholen, um Sie erneut zu veröffentlichen.

1. Klicken Sie in Visual Studio mit der rechten Maustaste auf das Projekt, und wählen Sie **veröffentlichen**aus.

3. Wählen Sie **IIS, FTP usw. aus,** und klicken Sie auf **veröffentlichen**.

    ![Veröffentlichen in IIS](media/dbg-aspnet-local-iis.png "Veröffentlichen in IIS")

4. Wählen Sie im Dialogfeld **CustomProfile** für **Veröffentlichungs Methode**die Option **Dateisystem**aus.

5. Wählen Sie unter **Ziel Speicherort**die Option **Durchsuchen** ( **...** ) aus.

   - Wählen Sie für ASP.net die Option **Lokales IIS**aus, wählen Sie die Website aus, die Sie für die App erstellt haben, und wählen Sie dann **Öffnen**

     ![Veröffentlichen in ASP.net in IIS](media/dbg-aspnet-local-iis1.png "Veröffentlichen von ASP.net in IIS")

   - Wählen Sie für ASP.net Core **Datei System**aus, wählen Sie den Ordner aus, den Sie für die APP eingerichtet haben, und wählen Sie dann **Öffnen**aus.

1. Klicken Sie auf **Weiter**.

1. Wählen Sie unter **Konfiguration**in der Dropdown Liste **Debuggen** aus.

1. Klicken Sie auf **Speichern**.

1. Stellen Sie im Dialogfeld " **veröffentlichen** " sicher, dass **CustomProfile** (oder der Name des soeben erstellten Profils) angezeigt wird und dass **lastusedbuildconfiguration** auf **Debug**festgelegt ist.

1. Wählen Sie **Veröffentlichen**.

    ![Veröffentlichen in IIS](media/dbg-aspnet-local-iis-select-site.png "Veröffentlichen in IIS")

> [!IMPORTANT]
> Der Debugmodus verringert die Leistung Ihrer APP erheblich. Legen Sie `debug="false"` in der Datei " *Web. config* " fest, und geben Sie einen Releasebuild an, wenn Sie eine Produktions-App bereitstellen oder Leistungsmessungen durchführen.

## <a name="see-also"></a>Siehe auch
- [Debuggen von ASP.NET: Systemanforderungen](aspnet-debugging-system-requirements.md)
- [Gewusst wie: Ausführen des Workerprozesses unter einem Benutzerkonto](how-to-run-the-worker-process-under-a-user-account.md)
- [Gewusst wie: Herausfinden des ASP.NET-Prozessnamens](how-to-find-the-name-of-the-aspnet-process.md)
- [Debug deployed web applications (Debuggen bereitgestellter Webanwendungen)](debugging-deployed-web-applications.md)
- [Exemplarische Vorgehensweise: Debuggen eines Web Forms](walkthrough-debugging-a-web-form.md)
- [Gewusst wie: Debuggen von ASP.NET-Ausnahmen](how-to-debug-aspnet-exceptions.md)
- [Debug web applications: Errors and troubleshooting (Debuggen von Webanwendungen: Fehler und Problembehandlung)](debugging-web-applications-errors-and-troubleshooting.md)

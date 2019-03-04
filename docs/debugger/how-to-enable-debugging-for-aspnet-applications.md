---
title: Debuggen für ASP.NET-Anwendungen aktivieren | Microsoft-Dokumentation
ms.custom: H1HackMay2017
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
ms.openlocfilehash: d5fd04ffbe75aef544ded66546d15409bf3c0936
ms.sourcegitcommit: 1c8e07b98fc0a44b5ab90bcef77d9fac7b3eb452
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/25/2019
ms.locfileid: "56796906"
---
# <a name="debug-aspnet-or-aspnet-core-apps-in-visual-studio"></a>Debuggen von ASP.NET- oder ASP.NET Core-apps in Visual Studio

Sie können ASP.NET und ASP.NET Core-apps in Visual Studio debuggen. Der Vorgang unterscheidet sich zwischen ASP.NET und ASP.NET Core, und ob Sie sie in IIS Express oder einem lokalen IIS-Server ausgeführt werden.

>[!NOTE]
>Die folgenden Schritte und die Einstellungen gelten nur für das Debuggen von apps auf einem lokalen Server. Debuggen von apps auf einem Remotecomputer mit IIS-Server verwendet **an den Prozess anhängen**, und diese Einstellungen ignoriert. Weitere Informationen und Anweisungen für remote debugging ASP.NET-apps in IIS finden Sie unter [Remotedebuggen von ASP.NET auf einem Computer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) oder [Remote Debuggen von ASP.NET Core auf einem Remotecomputer mit IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md).

Der integrierten IIS Express-Server ist in Visual Studio enthalten. IIS Express ist der Standard-Debug-Server für ASP.NET- und ASP.NET Core-Projekte und vorkonfiguriert ist. Es ist die einfachste Möglichkeit zum Debuggen und Ideal für die anfängliche Debuggen und testen.

Sie können auch eine ASP.NET- oder ASP.NET Core-app auf einem lokalen IIS-Server (Version 8.0 oder höher) Debuggen, die zum Ausführen der app konfiguriert ist. Um auf lokale IIS zu debuggen, müssen Sie die folgenden Anforderungen erfüllen:

<a name="iis"></a>
- Wählen Sie **Entwicklungszeit-IIS-Unterstützung** bei der Installation von Visual Studio. (Falls erforderlich, führen Sie den Visual Studio-Installer erneut aus, wählen Sie **ändern**, und fügen Sie diese Komponente hinzu.)
- Werden die Visual Studio als Administrator ausführen.
- Installieren Sie und konfigurieren Sie IIS ordnungsgemäß mit den entsprechenden Versionen von ASP.NET bzw. ASP.NET Core. Weitere Informationen und Anweisungen hierzu finden Sie unter [IIS 8.0 mithilfe von ASP.NET 3.5 und ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) oder [Hosten von ASP.NET Core unter Windows mit IIS](https://docs.microsoft.com/aspnet/core/host-and-deploy/iis/index).
- Stellen Sie sicher, dass die Anwendung auf IIS ohne Fehler ausgeführt wird.

## <a name="debug-aspnet-apps"></a>Debuggen von ASP.NET-Anwendungen

IIS Express ist die Standardeinstellung und vorkonfiguriert ist. Wenn Sie auf lokale IIS Debuggen, stellen Sie sicher, dass Sie erfüllen die [Anforderungen für das lokale Debuggen von IIS](#iis).

1. Wählen Sie das ASP.NET-Projekt in Visual Studio **Projektmappen-Explorer** , und klicken Sie auf die **Eigenschaften** Symbol, drücken Sie **Alt**+**EINGABETASTE**, oder mit der rechten Maustaste, und wählen Sie **Eigenschaften**.

1. Wählen Sie die **Web** Registerkarte.

1. In der **Eigenschaften** Bereich unter **Server**,
   - Wählen Sie für IIS Express **IIS Express** aus der Dropdownliste aus.
   - Für die lokale IIS
     1. Wählen Sie **lokale IIS** aus der Dropdownliste aus.
     1. Neben der **Projekt-URL** die Option **virtuelles Verzeichnis erstellen**, wenn Sie noch kein Einrichtung der app in IIS festgelegt haben.

1. Klicken Sie unter **Debugger**Option **ASP.NET**.

   ![ASP.NET Debuggereinstellungen](media/dbg-aspnet-enable-debugging2.png "ASP.NET Debuggereinstellungen")

1. Verwendung **Datei** > **ausgewählte Elemente speichern** oder **STRG**+**S** , Änderungen zu speichern.

1. Legen Sie Haltepunkte zum Debuggen der app in Ihrem Projekt auf Code. In der Symbolleiste von Visual Studio sicher, dass die Konfiguration wird festgelegt, um **Debuggen**, und der gewünschten Browser angezeigt wird, im **IIS Express (\<Browsername >)** oder **lokale IIS (\< Browser-Name >)** in das Emulator-Feld.

1. Wählen Sie zum Starten des Debuggens **IIS Express (\<Browsername >)** oder **lokale IIS (\<Browsername >)** wählen Sie in der Symbolleiste **Debuggenstarten**aus der **Debuggen** Menü, oder drücken Sie **F5**. Der Debugger hält an den Haltepunkten. Wenn der Debugger Haltepunkte erreicht, kann nicht, finden Sie unter [Problembehandlung Debuggen](#troubleshoot-debugging).

## <a name="debug-aspnet-core-apps"></a>Debuggen von ASP.NET Core-apps

IIS Express ist die Standardeinstellung und vorkonfiguriert ist. Wenn Sie auf lokale IIS Debuggen, stellen Sie sicher, dass Sie erfüllen die [Anforderungen für das lokale Debuggen von IIS](#iis).

1. Wählen Sie das ASP.NET Core-Projekt in Visual Studio **Projektmappen-Explorer** , und klicken Sie auf die **Eigenschaften** Symbol, drücken Sie **Alt**+**EINGABETASTE**, oder mit der rechten Maustaste, und wählen Sie **Eigenschaften**.

1. Klicken Sie auf die Registerkarte **Debuggen**.

1. In der **Eigenschaften** Bereich, der neben **Profil**,
   - Wählen Sie für IIS Express **IIS Express** aus der Dropdownliste aus.
   - Für die lokalen IIS, wählen Sie den app-Namen aus der Dropdownliste aus, oder wählen Sie **neu**, erstellen Sie einen neuen Profilnamen, und wählen **OK**.

1. Neben **starten**, wählen Sie entweder **IIS Express** oder **IIS** aus der Dropdownliste aus.

1. Stellen Sie sicher, dass **Launch Browser** ausgewählt ist.

1. Klicken Sie unter **Umgebungsvariablen**, stellen Sie sicher, dass **"aspnetcore_environment"** ist vorhanden, mit dem Wert **Entwicklung**. Wählen Sie andernfalls **hinzufügen** und fügen Sie es hinzu.

   ![ASP.NET Core-Debuggereinstellungen](../debugger/media/dbg-aspnet-enable-debugging3.png "ASP.NET Core-Debugger-Einstellungen")

1. Verwendung **Datei** > **ausgewählte Elemente speichern** oder **STRG**+**S** , Änderungen zu speichern.

1. Legen Sie Haltepunkte zum Debuggen der app in Ihrem Projekt auf Code. In der Symbolleiste von Visual Studio sicher, dass die Konfiguration wird festgelegt, um **Debuggen**, und entweder **IIS Express**, oder der neue Namen der IIS-Profil, in der Emulator-Feld angezeigt wird.

1. Wählen Sie zum Starten des Debuggens **IIS Express** oder  **\<IIS Profilname >** wählen Sie in der Symbolleiste **Debuggen starten** aus der **Debuggen** Menü, oder drücken Sie **F5**. Der Debugger hält an den Haltepunkten. Wenn der Debugger Haltepunkte erreicht, kann nicht, finden Sie unter [Problembehandlung Debuggen](#troubleshoot-debugging).

## <a name="troubleshoot-debugging"></a>Problembehandlung beim Debuggen

Gehen folgendermaßen Sie vor, Problembehandlung, wenn die lokale IIS-Debuggen bis zum Haltepunkt gelangen kann, haben.

1. Starten Sie die Web-app von IIS aus, und stellen Sie sicher, dass er ordnungsgemäß ausgeführt wird. Lassen Sie die Web-app ausgeführt wird.

2. Wählen Sie in Visual Studio **Debuggen > an den Prozess anhängen** , oder drücken Sie **STRG**+**Alt**+**P**, und Verbinden mit der ASP.NET- oder ASP.NET Core-Prozess (normalerweise **w3wp.exe** oder **dotnet.exe**). Weitere Informationen finden Sie unter [an den Prozess anhängen](attach-to-running-processes-with-the-visual-studio-debugger.md) und [wie Sie den Namen des ASP.NET-Prozessnamens](how-to-find-the-name-of-the-aspnet-process.md).

Wenn Sie eine Verbindung herstellen und den Haltepunkt mit **an den Prozess anhängen**, aber nicht in **Debuggen** > **Debuggen starten** oder **F5**, eine Einstellung ist möglicherweise nicht in den Projekteigenschaften. Wenn Sie eine Datei "HOSTS" verwenden, stellen Sie sicher, dass er auch richtig konfiguriert ist.

## <a name="configure-debugging-in-the-webconfig-file"></a>Konfigurieren des Debuggens in der Datei "Web.config"

ASP.NET-Projekte verfügen über *"Web.config"* Dateien standardmäßig die beiden app-Konfiguration, und starten Sie Informationen, einschließlich der Einstellungen zum Debuggen von enthalten. Die *"Web.config"* Dateien müssen richtig konfiguriert sein, für das Debuggen. Die **Eigenschaften** Einstellungen in den vorherigen Abschnitten Update der *"Web.config"* Dateien, aber Sie können auch sie manuell konfigurieren.

> [!NOTE]
> ASP.NET Core-Projekte müssen zunächst keine *"Web.config"* -Dateien, aber verwenden *"appSettings.JSON"* und *"launchsettings.JSON"* -Dateien für app-Konfiguration, und starten Informationen. Bereitstellen der app erstellt ein *"Web.config"* Dateien im Projekt, aber sie Debuginformationen nicht in der Regel enthalten.

> [!TIP]
> Ihr Bereitstellungsprozess möglicherweise aktualisieren die *"Web.config"* Einstellungen, bevor Sie debuggen möchten, achten Sie also die *"Web.config"* für Debuggen konfiguriert ist.

**So konfigurieren Sie manuell eine *"Web.config"* -Datei zum Debuggen:**

1. Öffnen Sie in Visual Studio des ASP.NET-Projekts *"Web.config"* Datei.

2. *"Web.config"* eine XML-Datei, so enthält, die mithilfe von Tags markierte, geschachtelte Abschnitte. Machen Sie den Abschnitt `configuration/system.web/compilation` ausfindig. (Wenn die `compilation` Element nicht vorhanden ist, erstellen Sie ihn.)

3. Stellen Sie sicher, dass die `debug` -Attribut in der `compilation` Element nastaven NA hodnotu `true`. (Wenn die `compilation` Element nicht enthalten. ein `debug` Attribut, fügen Sie es hinzu, und legen Sie ihn auf `true`.)

   Wenn Sie lokale IIS anstelle des Standardservers von IIS Express verwenden, stellen sicher, dass die `targetFramework` -Attributwert in der `compilation` Element entspricht, das Framework auf dem IIS-Server.

   Die `compilation` Element der *"Web.config"* Datei sollte wie im folgenden Beispiel aussehen:

   > [!NOTE]
   > In diesem Beispiel wird eine partielle *"Web.config"* Datei. Befinden sich in der Regel zusätzliche XML-Abschnitte in der `configuration` und `system.web` Elemente, und die `compilation` Element enthalten möglicherweise auch, andere Attribute und Elemente.

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

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] erkennt an *web.config*-Dateien vorgenommene Änderungen automatisch und wendet die neuen Konfigurationseinstellungen an. Sie müssen den Computer oder den IIS-Server für die Änderungen wirksam werden neu zu starten.

Eine Website kann mehrere virtuelle Verzeichnisse und Unterverzeichnisse, mit enthalten *"Web.config"* Dateien in den einzelnen. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Apps erben Konfigurationseinstellungen zur von *"Web.config"* Dateien auf höheren Ebenen im URL-Pfad. Die hierarchische *"Web.config"* -dateieinstellungen gelten für alle [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] apps, darunter in der Hierarchie. Festlegen einer anderen Konfigurations in eine *"Web.config"* Datei, die sich in der Hierarchie überschreibt die Einstellungen in der Datei höher.

Wenn Sie angeben, z. B. `debug="true"` in <em>www.microsoft.com/aaa/web.config</em>, jede app in der *aaa* Ordner oder in jedem Unterordner von *aaa* erbt von dieser Einstellung werden außer wenn eine dieser Apps über die Einstellung mit eigenem überschreibt *"Web.config"* Datei.

## <a name="publish-in-debug-mode-using-the-file-system"></a>Veröffentlichen Sie im Debugmodus, die mit dem Dateisystem

Es gibt verschiedene Möglichkeiten zum Veröffentlichen von apps in IIS. Diese Schritte veranschaulichen das Erstellen und Bereitstellen einer Debugmodus-Veröffentlichungsprofil mit dem Dateisystem. Zu diesem Zweck müssen Sie Visual Studio als Administrator ausführen.

> [!IMPORTANT]
> Wenn Sie Codes oder der Neuerstellung ändern, müssen Sie die folgenden Schritte aus, um erneut zu veröffentlichen wiederholen.

1. Klicken Sie in Visual Studio mit der rechten Maustaste in des Projekts, und wählen Sie **veröffentlichen**.

3. Wählen Sie **IIS, FTP usw.** , und klicken Sie auf **veröffentlichen**.

    ![In IIS veröffentlichen](media/dbg-aspnet-local-iis.png "in IIS veröffentlichen")

4. In der **CustomProfile** im Dialogfeld für **Veröffentlichungsmethode**, wählen Sie **Dateisystem**.

5. Für **Zielspeicherort**Option **Durchsuchen** (**...** ).

   - Wählen Sie für ASP.NET, **lokale IIS**, wählen Sie die Website, die Sie für die app erstellt haben, und wählen Sie dann **öffnen**.

     ![In ASP.NET in IIS veröffentlichen](media/dbg-aspnet-local-iis1.png "ASP.NET in IIS veröffentlichen")

   - Wählen Sie für ASP.NET Core, **Dateisystem**, wählen Sie den Ordner, die Sie für die app einrichten, und wählen Sie dann **öffnen**.

1. Klicken Sie auf **Weiter**.

1. Klicken Sie unter **Konfiguration**Option **Debuggen** aus der Dropdownliste aus.

1. Klicken Sie auf **Speichern**.

1. In der **veröffentlichen** Dialogfeld stellen Sie sicher, dass **CustomProfile** (oder den Namen des Profils, das Sie gerade erstellt haben) angezeigt wird, und **LastUsedBuildConfiguration** nastaven NA hodnotu  **Debuggen von**.

1. Wählen Sie **Veröffentlichen**.

    ![In IIS veröffentlichen](media/dbg-aspnet-local-iis-select-site.png "in IIS veröffentlichen")

> [!IMPORTANT]
> Debugmodus sinkt die Leistung Ihrer App. Legen Sie für eine optimale Leistung `debug="false"` in die *"Web.config"* , und geben Sie einen Releasebuild aus, wenn Sie eine Produktions-app bereitstellen oder leistungsmessungen.

## <a name="see-also"></a>Siehe auch
- [Debuggen von ASP.NET: Systemanforderungen](aspnet-debugging-system-requirements.md)
- [Gewusst wie: Ausführen des Workerprozesses unter einem Benutzerkonto](how-to-run-the-worker-process-under-a-user-account.md)
- [Gewusst wie: Herausfinden des ASP.NET-Prozessnamens](how-to-find-the-name-of-the-aspnet-process.md)
- [Debug deployed web applications (Debuggen bereitgestellter Webanwendungen)](debugging-deployed-web-applications.md)
- [Exemplarische Vorgehensweise: Debuggen eines Web Forms](walkthrough-debugging-a-web-form.md)
- [Gewusst wie: Debuggen von ASP.NET-Ausnahmen](how-to-debug-aspnet-exceptions.md)
- [Debug web applications: Errors and troubleshooting (Debuggen von Webanwendungen: Fehler und Problembehandlung)](debugging-web-applications-errors-and-troubleshooting.md)

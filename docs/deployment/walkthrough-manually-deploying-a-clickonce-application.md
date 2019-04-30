---
title: 'Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Mage.exe, manual ClickOnce deployments
- MageUI.exe, manual ClickOnce deployments
- deploying applications [ClickOnce], manual ClickOnce deployments
- ClickOnce deployment, manually
- ClickOnce deployment, SDK tools
- manual ClickOnce deployments
- manifests [ClickOnce]
ms.assetid: ccee6551-a1b9-4ca2-8845-9c1cf4ac2560
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 60173bd8a48b067757bbccfad42a2feaf5633082
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63405798"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application"></a>Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung
Wenn Sie Visual Studio, zum Bereitstellen verwenden können Ihrer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , oder Sie müssen erweiterte Bereitstellungsfunktionen, wie z. B. die Bereitstellung einer vertrauenswürdigen Anwendung verwenden Sie die *Mage.exe* Befehlszeilentool, mit Ihrem Erstellen[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Manifeste. In dieser exemplarischen Vorgehensweise wird beschrieben, wie zum Erstellen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung mithilfe der Befehlszeilenversion (*Mage.exe*) oder die grafische Version (*MageUI.exe*) der dem Manifest Generation und Bearbeitungstool verwenden.

## <a name="prerequisites"></a>Vorraussetzungen
 In dieser exemplarischen Vorgehensweise hat einige Voraussetzungen und Optionen, die Sie vor dem Erstellen einer Bereitstellungstyps auswählen müssen.

- Installieren Sie *Mage.exe* und *MageUI.exe*.

   *Mage.exe* und *MageUI.exe* sind Teil der [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Sie müssen entweder die [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] installiert oder die Version des der [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] in Visual Studio enthalten. Weitere Informationen finden Sie unter [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=158044) auf MSDN.

- Geben Sie eine bereitzustellende Anwendung.

   In dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass Sie über eine Windows-Anwendung verfügen, die Sie bereitstellen möchten. Diese Anwendung wird als AppToDeploy bezeichnet werden.

- Bestimmen Sie, wie die Bereitstellung verteilt wird.

   Die Distribution-Optionen umfassen: Web-, Dateifreigabe oder CD. Weitere Informationen finden Sie unter [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md).

- Bestimmen Sie, ob die Anwendung mit erhöhten Rechten ein Maß an Vertrauenswürdigkeit erfordert.

   Wenn Ihre Anwendung volle Vertrauenswürdigkeit erfordert, z. B. Vollzugriff auf dem System des Benutzers – können Sie die `-TrustLevel` Option *Mage.exe* festlegen. Wenn Sie einen benutzerdefinierten Berechtigungssatz, der für Ihre Anwendung definieren möchten, können Sie im Internet oder Intranet Berechtigung Abschnitt aus einem anderen Manifest kopieren, ändern Sie sie entsprechend Ihren Anforderungen und fügen Sie es in das Anwendungsmanifest, die mit einen Text-Editor oder  *MageUI.exe*. Weitere Informationen finden Sie unter [Überblick über die Bereitstellung vertrauenswürdiger Anwendungen](../deployment/trusted-application-deployment-overview.md).

- Rufen Sie ein Authenticode-Zertifikat.

   Sie sollten Ihre Bereitstellung mit einem Authenticode-Zertifikat signieren. Sie können ein Testzertifikat generieren, indem Sie mithilfe von Visual Studio *MageUI.exe*, oder *MakeCert.exe* und *Pvk2Pfx.exe* Tools, oder Sie können ein Zertifikat aus einem Zertifikat abrufen Zertifizierungsstelle (CA). Wenn Sie die Bereitstellung vertrauenswürdiger Anwendungen verwenden möchten, müssen Sie auch eine einmalige Installation des Zertifikats auf allen Clientcomputern ausführen. Weitere Informationen finden Sie unter [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).

  > [!NOTE]
  > Sie können auch die Bereitstellung mit einem CNG-Zertifikat signieren, die Sie von einer Zertifizierungsstelle erhalten können.

- Stellen Sie sicher, dass die Anwendung nicht über ein Manifest mit UAC-Informationen verfügt.

   Sie müssen bestimmen, ob Ihre Anwendung ein Manifest mit der Benutzerkontensteuerung (UAC) Informationen, z. B. enthält eine `<dependentAssembly>` Element. Um ein Anwendungsmanifest zu untersuchen, können Sie die Windows Sysinternals [Sigcheck](http://go.microsoft.com/fwlink/?LinkId=158035) Hilfsprogramm.

   Wenn Ihre Anwendung ein Manifest mit UAC-Informationen enthält, müssen Sie es erneut ohne die UAC-Informationen erstellen. Öffnen Sie für ein C#-Projekt in Visual Studio die Projekteigenschaften, und wählen Sie die Registerkarte "Anwendung". In der **Manifest** Dropdown-Liste **Anwendung ohne Manifest erstellen**. Für eine Visual Basic-Projekt in Visual Studio, öffnen Sie die Projekteigenschaften, wählen Sie die Registerkarte "Anwendung", und klicken Sie auf **UAC-Anzeigeeinstellungen**. In der Manifestdatei geöffnet ist, entfernen Sie alle Elemente innerhalb der einzelnen `<asmv1:assembly>` Element.

- Bestimmen Sie, ob die Anwendung erforderlichen Komponenten auf dem Clientcomputer erforderlich ist.

   [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] in Visual Studio bereitgestellte Anwendungen können einen Bootstrapper für die Installation erforderlicher Komponenten einschließen (*setup.exe*) bei der Bereitstellung. In dieser exemplarischen Vorgehensweise erstellt, die zwei Manifeste erforderlich für eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung. Sie können einen erforderliche Bootstrapper erstellen, mit der [GenerateBootstrapper-Aufgabe](../msbuild/generatebootstrapper-task.md).

### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>Zum Bereitstellen einer Anwendung mit dem Befehlszeilentool Mage.exe

1. Erstellen Sie ein Verzeichnis, in dem Sie speichern, Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Dateien für die Bereitstellung.

2. Erstellen Sie in das Bereitstellungsverzeichnis, die, das Sie gerade erstellt haben, ein Versionsunterverzeichnis. Ist dies das erste Mal, dass Sie die Anwendung bereitstellen möchten, benennen Sie im Versionsunterverzeichnis **1.0.0.0**.

   > [!NOTE]
   > Die Version der Bereitstellung kann sich von der Version der Anwendung sein.

3. Kopieren Sie alle Ihre Anwendungsdateien im Versionsunterverzeichnis, einschließlich der ausführbaren Dateien, Assemblys, Ressourcen und -Datendateien. Bei Bedarf können Sie zusätzliche Unterverzeichnisse erstellen, die zusätzliche Dateien enthalten.

4. Öffnen der [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] oder die Eingabeaufforderung, und wechseln Sie zum Versionsunterverzeichnis Visual Studio-Befehl.

5. Erstellen Sie das Anwendungsmanifest mit einem Aufruf von *Mage.exe*. Die folgende Anweisung erstellt, einem Anwendungsmanifest für Code kompiliert, um auf dem Prozessor Intel X86 ausgeführt wird.

   ```cmd
   mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .
   ```

   > [!NOTE]
   > Achten Sie darauf, dass Sie nach dem den Punkt (.) enthalten die `-FromDirectory` auswählen, um das aktuelle Verzeichnis angibt. Wenn Sie nicht über den Punkt beinhalten, müssen Sie den Pfad an den Anwendungsdateien angeben.

6. Melden Sie das Anwendungsmanifest mit dem Authenticode-Zertifikat. Ersetzen Sie dies *mycert.pfx* durch den Pfad zu der Zertifikatsdatei. Ersetzen Sie dies *Passwd* durch das Kennwort für Ihre Zertifikatdatei.

   ```cmd
   mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd
   ```

   Ab .NET Framework 4.6.2 SDK, der mit Visual Studio und mit dem Windows SDK verteilt wird, *mage.exe* Manifeste mit CNG sowie mit Authenticode-Zertifikaten signiert. Verwenden Sie die gleichen Befehlszeilenparameter wie bei der Authenticode-Zertifikaten.

7. Ändern Sie in das Stammverzeichnis des das Bereitstellungsverzeichnis.

8. Generieren Sie das Bereitstellungsmanifest mit einem Aufruf von *Mage.exe*. In der Standardeinstellung *Mage.exe* kennzeichnen Ihrer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung als installierte Anwendung, damit die It-sowohl online ausgeführt werden kann und offline. Verwenden Sie die Anwendung zur Verfügung stellen möchten nur, wenn der Benutzer online ist, die `-Install` Option mit einem Wert von `false`. Wenn Sie die Standardeinstellung verwenden und Benutzer Ihre Anwendung von einer Website oder der Dateifreigabe installieren, stellen sicher, dass der Wert des der `-ProviderUrl` Option-verweist auf den Speicherort der Anwendung auf dem Webserver oder eine Freigabe manifest.

   ```cmd
   mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application
   ```

9. Melden Sie das Bereitstellungsmanifest mit dem Authenticode oder CNG-Zertifikat.

    ```cmd
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd
    ```

10. Kopieren Sie alle Dateien in das Bereitstellungsverzeichnis in das Bereitstellungsziel oder Medium. Dies kann entweder einen Ordner auf einer Website oder FTP-Site, eine Dateifreigabe oder eine CD-ROM sein.

11. Geben Sie Ihre Benutzer mit der URL, UNC oder physische Medien zur Installation Ihrer Anwendung erforderlich sind. Wenn Sie eine URL oder einen UNC-Pfad angeben, müssen Sie für Ihre Benutzer den vollständigen Pfad zum Bereitstellungsmanifest erteilen. Wenn AppToDeploy bereitgestellt wird, um z. B. http://webserver01/ im Verzeichnis AppToDeploy wäre die vollständige URL-Pfad http://webserver01/AppToDeploy/AppToDeploy.application.

### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>Zum Bereitstellen einer Anwendung mit dem grafischen Tool MageUI.exe

1. Erstellen Sie ein Verzeichnis, in dem Sie speichern, Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Dateien für die Bereitstellung.

2. Erstellen Sie in das Bereitstellungsverzeichnis, die, das Sie gerade erstellt haben, ein Versionsunterverzeichnis. Ist dies das erste Mal, dass Sie die Anwendung bereitstellen möchten, benennen Sie im Versionsunterverzeichnis **1.0.0.0**.

   > [!NOTE]
   > Die Version der Bereitstellung unterscheidet sich wahrscheinlich von der Version Ihrer Anwendung.

3. Kopieren Sie alle Ihre Anwendungsdateien im Versionsunterverzeichnis, einschließlich der ausführbaren Dateien, Assemblys, Ressourcen und -Datendateien. Bei Bedarf können Sie zusätzliche Unterverzeichnisse erstellen, die zusätzliche Dateien enthalten.

4. Starten Sie den *MageUI.exe* grafisches Tool.

   ```cmd
   MageUI.exe
   ```

5. Erstellen Sie ein neues Anwendungsmanifest dazu **Datei**, **neu**, **Anwendungsmanifest** aus dem Menü.

6. Auf der standardmäßigen **Namen** Registerkarte, geben Sie die Namen und die Versionsnummer die Anzahl dieser Bereitstellung. Geben Sie auch die **Prozessor** , die Ihre Anwendung, z. B. X86 erstellt wird.

7. Wählen Sie die **Dateien** Registerkarte, und klicken Sie auf die Auslassungspunkte (**...** ) neben dem **Anwendungsverzeichnis** Textfeld. Ein **Ordner** Dialogfeld wird angezeigt.

8. Wählen Sie das Versionsunterverzeichnis, das mit den Anwendungsdateien, und klicken Sie dann auf **OK**.

9. Wenn Sie von Internet Information Services (IIS) bereitstellen, wählen Sie die **Wenn Auffüllen Hinzufügen der Erweiterung ".deploy" alle Dateien, die es keinen** Kontrollkästchen.

10. Klicken Sie auf die **Auffüllen** , um alle Anwendungsdateien in die Liste der Dateien aufzunehmen. Wenn Ihre Anwendung mehr als eine ausführbare Datei enthält, markieren Sie die ausführbare Hauptdatei für diese Bereitstellung als startanwendung dazu **Einstiegspunkt** aus der **Dateityp** Dropdown-Liste. (Wenn Ihre Anwendung nur eine ausführbare Datei enthält *MageUI.exe* kennzeichnet diese für Sie.)

11. Wählen Sie die **erforderlichen Berechtigungen** Registerkarte, und wählen Sie die Ebene der Vertrauenswürdigkeit, die Sie benötigen, dass Ihre Anwendung aus, um zu bestätigen. Der Standardwert ist **FullTrust**, die für die meisten Anwendungen geeignet sein.

12. Wählen Sie **Datei**, **speichern** aus dem Menü. Ein Dialogfeld "Signaturoptionen" wird die Aufforderung zum Signieren des Anwendungsmanifests angezeigt.

13. Wenn Sie ein Zertifikat als Datei im Dateisystem gespeichert haben, verwenden Sie die **mit Zertifikatsdatei signieren** aus, und wählen Sie das Zertifikat aus dem Dateisystem mit den Auslassungspunkten (**...** ) Schaltfläche. Geben Sie dann das Zertifikatkennwort ein.

     - oder - 

     Wenn das Zertifikat im Zertifikatspeicher der von Ihrem Computer aus zugegriffen werden kann gehalten wird, wählen Sie die **mit gespeichertem Zertifikat signieren** aus, und wählen Sie das Zertifikat in der Liste.

14. Klicken Sie auf **OK** , melden Sie sich das Anwendungsmanifest. Die **speichern** Dialogfeld wird angezeigt.

15. In der **speichern** Dialogfeld Geben Sie das Versionsverzeichnis, und klicken Sie dann auf **speichern**.

16. Wählen Sie **Datei**, **neu**, **Bereitstellungsmanifest** aus, um das Bereitstellungsmanifest zu erstellen.

17. Auf der **Namen** Registerkarte, geben Sie einen Namen und Version für diese Bereitstellung (**1.0.0.0** in diesem Beispiel). Geben Sie auch die **Prozessor** , die Ihre Anwendung, z. B. X86 erstellt wird.

18. Wählen Sie die **Beschreibung** Registerkarte, und geben Sie Werte für **Verleger** und **Produkt**. (**Produkt** ist der Name für Ihre Anwendung über das Startmenü von Windows angegeben wird, wenn die Anwendung auf einem Clientcomputer für die Offlineverwendung installiert.)

19. Wählen Sie die **Bereitstellungsoptionen** Registerkarte, und klicken Sie in der **Startposition** Text geben den Speicherort des Anwendungsmanifests auf dem Webserver oder der Freigabe. Z. B.  *\\\myServer\myShare\AppToDeploy.application*.

20. Wenn Sie hinzugefügt haben die *".deploy"* wählen Sie die Erweiterung in einem vorherigen Schritt auch **verwenden Sie die Dateinamenerweiterung ".deploy"** hier.

21. Wählen Sie die **Clientupdateoptionen** Registerkarte, und geben Sie, wie oft Sie diese Anwendung aktualisiert werden soll. Wenn Ihre Anwendung verwendet <xref:System.Deployment.Application.UpdateCheckInfo> um selbst prüfen ob Updates, Deaktivieren der **diese Anwendung soll nach Updates suchen** Kontrollkästchen.

22. Wählen Sie die **Anwendungsverweis** Registerkarte, und klicken Sie dann auf die **Manifest auswählen** Schaltfläche. Ein geöffnetes Dialogfenster angezeigt wird.

23. Wählen Sie das Anwendungsmanifest, das Sie zuvor erstellt haben, und klicken Sie dann auf **öffnen**.

24. Wählen Sie **Datei**, **speichern** aus dem Menü. Ein **Signaturoptionen** im angezeigten Dialogfeld dazu aufgefordert, das Bereitstellungsmanifest zu signieren.

25. Wenn Sie ein Zertifikat als Datei im Dateisystem gespeichert haben, verwenden Sie die **mit Zertifikatsdatei signieren** aus, und wählen Sie das Zertifikat aus dem Dateisystem mit den Auslassungspunkten (**...** ) Schaltfläche. Geben Sie dann das Zertifikatkennwort ein.

     - oder - 

     Wenn das Zertifikat im Zertifikatspeicher der von Ihrem Computer aus zugegriffen werden kann gehalten wird, wählen Sie die **mit gespeichertem Zertifikat signieren** aus, und wählen Sie das Zertifikat in der Liste.

26. Klicken Sie auf **OK** das Bereitstellungsmanifest zu signieren. Die **speichern** Dialogfeld wird angezeigt.

27. In der **speichern** Dialogfeld verschieben Sie ein Verzeichnis in das Stammverzeichnis Ihrer Bereitstellung und klicken Sie dann auf **speichern**.

28. Kopieren Sie alle Dateien in das Bereitstellungsverzeichnis in das Bereitstellungsziel oder Medium. Dies kann entweder einen Ordner auf einer Website oder FTP-Site, eine Dateifreigabe oder eine CD-ROM sein.

29. Geben Sie Ihre Benutzer mit der URL, UNC oder physische Medien zur Installation Ihrer Anwendung erforderlich sind. Wenn Sie eine URL oder einen UNC-Pfad angeben, müssen Sie sich, Ihre Benutzer den vollständigen Pfad das Bereitstellungsmanifest erteilen. Wenn AppToDeploy bereitgestellt wird, um z. B. http://webserver01/ im Verzeichnis AppToDeploy wäre die vollständige URL-Pfad http://webserver01/AppToDeploy/AppToDeploy.application.

## <a name="next-steps"></a>Nächste Schritte
 Wenn Sie eine neue Version der Anwendung bereitstellen möchten, erstellen Sie ein neues Verzeichnis mit dem Namen der neuen Version – z. B. 1.0.0.1 kopieren Sie die neue Anwendungsdateien in das neue Verzeichnis. Als Nächstes müssen Sie die zuvor genannten Schritte zum Erstellen und Signieren ein neues Anwendungsmanifest, und aktualisieren und das Bereitstellungsmanifest zu signieren. Achten Sie darauf, dass Sie sowohl die gleiche höhere Version an die *Mage.exe* `-New` und `-Update` Aufrufe als [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aktualisiert nur neuere Versionen mit den wichtigsten am weitesten links ganzen Zahl. Wenn Sie verwendet *MageUI.exe*, Sie können das Bereitstellungsmanifest aktualisieren, indem Sie Sie öffnen, Auswählen der **Anwendungsverweis** klicken Sie auf die **Manifest auswählen** Schaltfläche, und Wählen Sie dann das aktualisierte Anwendungsmanifest.

## <a name="see-also"></a>Siehe auch
- [Mage.exe (Tool zum Generieren und Bearbeiten von Manifesten)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [MageUI.exe (Tool zum Generieren und Bearbeiten von Manifesten, grafischer Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
- [Publish ClickOnce applications (Veröffentlichen von ClickOnce-Anwendungen)](../deployment/publishing-clickonce-applications.md)
- [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md)
- [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md)
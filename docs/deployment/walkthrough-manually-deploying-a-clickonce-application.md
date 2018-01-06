---
title: 'Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "49"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload: multiple
ms.openlocfilehash: 2e0035641a8ed374892060dbaabe79d808150cc2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-manually-deploying-a-clickonce-application"></a>Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung
Wenn Sie Visual Studio, zum Bereitstellen verwenden können Ihrer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , oder Sie müssen erweiterte Funktionen verwenden, z. B. Bereitstellung vertrauenswürdiger Anwendungen, sollten Sie das Befehlszeilentool "Mage.exe" verwenden, um das Erstellen Ihrer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Manifeste. In dieser exemplarischen Vorgehensweise wird beschrieben, wie zum Erstellen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung mithilfe der Befehlszeilenversion (Mage.exe) oder die grafische Version (MageUI.exe), der das Manifest Tool zum Generieren und bearbeiten.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 In dieser exemplarischen Vorgehensweise verfügt über einige erforderliche Komponenten und Optionen, die Sie vor dem Erstellen einer Bereitstellung auswählen müssen.  
  
-   Installieren Sie Mage.exe und MageUI.exe.  
  
     Mage.exe und MageUI.exe sind Teil der [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Entweder muss Ihnen die [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] installiert oder die Version des der [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] in Visual Studio enthaltene. Weitere Informationen finden Sie unter [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=158044) auf MSDN.  
  
-   Geben Sie eine bereitzustellende Anwendung.  
  
     In dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass Sie eine Windows-Anwendung verfügen, die Sie bereitstellen möchten. Diese Anwendung wird als AppToDeploy bezeichnet werden.  
  
-   Bestimmen Sie, wie die Bereitstellung verteilt werden soll.  
  
     Die zu den Verteilungsoptionen gehören: Web, Dateifreigabe oder CD. Weitere Informationen finden Sie unter [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md).  
  
-   Bestimmen Sie, ob die Anwendung mit erhöhten Rechten ein Maß an Vertrauenswürdigkeit erforderlich ist.  
  
     Wenn Ihre Anwendung volle Vertrauenswürdigkeit erforderlich ist – z. B. vollen Zugriff auf das System des Benutzers – können Sie die `-TrustLevel` -Option von Mage.exe festlegen. Wenn Sie einen benutzerdefinierten Berechtigungssatz für die Anwendung definieren möchten, können Sie im Internet oder Intranet Berechtigung Abschnitt aus einem anderen Manifest kopieren, ändern Sie sie entsprechend Ihren Anforderungen und das Anwendungsmanifest mit einem Text-Editor oder MageUI.exe hinzugefügt. Weitere Informationen finden Sie unter [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
-   Rufen Sie ein Authenticode-Zertifikat.  
  
     Sie sollten Ihre Bereitstellung mit einem Authenticode-Zertifikat signieren. Generieren eines Testzertifikats können mithilfe von Tools für Visual Studio "," MageUI.exe "oder" MakeCert.exe "und" Pvk2Pfx.exe, oder Sie können ein Zertifikat von einer Zertifizierungsstelle (Certificate Authority, CA) abrufen. Falls gewünscht, um die Bereitstellung einer vertrauenswürdigen Anwendung verwenden, müssen Sie auch eine einmalige Installation des Zertifikats auf allen Clientcomputern ausführen. Weitere Informationen finden Sie unter [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
    > [!NOTE]
    >  Sie können auch die Bereitstellung mit einem CNG-Zertifikat signieren, die Sie von einer Zertifizierungsstelle erhalten können.  
  
-   Stellen Sie sicher, dass die Anwendung ein Manifest mit UAC-Informationen nicht verfügbar ist.  
  
     Sie müssen bestimmen, ob die Anwendung ein Manifest mit Informationen zur Benutzerkontensteuerung (UAC), z. B. enthält ein `<dependentAssembly>` Element. Um ein Anwendungsmanifest zu untersuchen, können Sie das Windows Sysinternals [Sigcheck](http://go.microsoft.com/fwlink/?LinkId=158035) Hilfsprogramm.  
  
     Wenn Ihre Anwendung ein Manifest mit UAC-Informationen enthält, müssen Sie es ohne die UAC-Informationen neu erstellt werden. Öffnen Sie für ein C#-Projekt in Visual Studio die Projekteigenschaften, und wählen Sie die Registerkarte "Anwendung". In der **Manifest** Dropdown-Liste **Anwendung ohne Manifest erstellen**. Für eine Visual Basic-Projekt in Visual Studio, öffnen Sie die Projekteigenschaften, wählen Sie die Registerkarte "Anwendung", und klicken Sie auf **UAC Ansichtseinstellungen**. In der Manifestdatei geöffnet ist, entfernen Sie alle Elemente innerhalb der einzelnen `<asmv1:assembly>` Element.  
  
-   Bestimmen Sie, ob die Anwendung erforderlichen Komponenten auf dem Clientcomputer erforderlich ist.  
  
     [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]in Visual Studio bereitgestellte Anwendungen können erforderlichen Installationskomponenten Bootstrapper (setup.exe) mit Ihrer Bereitstellung enthalten. In dieser exemplarischen Vorgehensweise erstellt, die zwei Manifeste erforderlich für eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung. Sie können einen erforderliche Bootstrapper erstellen, mit der [GenerateBootstrapper-Aufgabe](../msbuild/generatebootstrapper-task.md).  
  
### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>Zum Bereitstellen einer Anwendung mit dem Befehlszeilentool Mage.exe  
  
1.  Erstellen Sie ein Verzeichnis, in dem Sie speichern, Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellungsdateien.  
  
2.  Erstellen Sie in den Bereitstellungsordner, den Sie gerade erstellt haben eine Versionsunterverzeichnis. Ist dies das erste Mal, dass Sie die Anwendung bereitstellen möchten, benennen Sie die im Versionsunterverzeichnis **1.0.0.0**.  
  
    > [!NOTE]
    >  Die Version der Bereitstellung kann sich von der Version der Anwendung unterscheiden.  
  
3.  Kopieren Sie alle Ihre Anwendungsdateien zum Unterverzeichnis "Version", einschließlich der ausführbaren Dateien, Assemblys, Ressourcen und Datendateien. Bei Bedarf können Sie zusätzliche Unterverzeichnisse erstellen, die zusätzliche Dateien enthalten.  
  
4.  Öffnen der [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] oder der Eingabeaufforderung ein, und wechseln Sie zum Versionsunterverzeichnis des Visual Studio-Befehl.  
  
5.  Erstellen Sie das Anwendungsmanifest mit einem Aufruf von Mage.exe. Die folgende Anweisung erstellt ein Anwendungsmanifest für Code, der zum Ausführen der Intel X86-Prozessor kompiliert.  
  
    ```  
    mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
    ```  
  
    > [!NOTE]
    >  Achten Sie darauf, dass Sie nach dem Punkt (.) enthalten die `-FromDirectory` Option an, der das aktuelle Verzeichnis angegeben. Wenn Sie den Punkt nicht einschließen, müssen Sie den Pfad zu Anwendungsdateien angeben.  
  
6.  Melden Sie sich das Anwendungsmanifest mit Authenticode-Zertifikat. Ersetzen Sie *mycert.pfx* durch den Pfad zu der Zertifikatdatei. Ersetzen Sie *Folgendes* durch das Kennwort für die Zertifikatdatei.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
    ```  
  
     Verwenden Sie folgende Schritte aus, um das Anwendungsmanifest mit einem CNG-Zertifikat zu signieren. Ersetzen Sie *cngCert.pfx* durch den Pfad zu der Zertifikatdatei.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
7.  Ändern Sie in das Stammverzeichnis des Bereitstellungsverzeichnis.  
  
8.  Generieren Sie das Bereitstellungsmanifest mit einem Aufruf von Mage.exe. Standardmäßig Mage.exe markiert die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung als installierte Anwendung, damit die It sowohl online ausgeführt werden kann und offline. Um die Anwendung zur Verfügung stellen nur, wenn der Benutzer online ist, verwenden die `-Install` Option mit dem Wert `false`. Wenn Sie verwenden Sie den Standardnamen und Benutzer Ihre Anwendung von einer Website oder Dateifreigabe installieren, stellen sicher, dass der Wert des der `-ProviderUrl` Option verweist auf den Speicherort der Anwendung auf dem Webserver oder der Freigabe manifest.  
  
    ```  
    mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application  
    ```  
  
9. Melden Sie das Bereitstellungsmanifest mit Ihrem Authenticode oder CNG-Zertifikat.  
  
    ```  
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd  
    ```  
  
     oder  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
10. Kopieren Sie alle Dateien im Bereitstellungsverzeichnis in das Bereitstellungsziel oder ein Medium. Dies kann entweder einen Ordner auf einer Website oder FTP-Site, eine Dateifreigabe oder eine CD-ROM sein.  
  
11. Geben Sie Ihre Benutzer mit der URL, den UNC- oder die physische Medien, die zur Installation der Anwendungsstatus erforderlich sind. Wenn Sie eine URL oder eine UNC-angeben, müssen Sie Ihre Benutzer den vollständigen Pfad zum Bereitstellungsmanifest erteilen. Z. B. Wenn AppToDeploy für http://webserver01/ im Verzeichnis AppToDeploy bereitgestellt wird, wäre die vollständige URL-Pfad http://webserver01/AppToDeploy/AppToDeploy.application.  
  
### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>Zum Bereitstellen einer Anwendung mit dem grafischen Tool MageUI.exe  
  
1.  Erstellen Sie ein Verzeichnis, in dem Sie speichern, Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellungsdateien.  
  
2.  Erstellen Sie in den Bereitstellungsordner, den Sie gerade erstellt haben eine Versionsunterverzeichnis. Ist dies das erste Mal, dass Sie die Anwendung bereitstellen möchten, benennen Sie die im Versionsunterverzeichnis **1.0.0.0**.  
  
    > [!NOTE]
    >  Die Version der Bereitstellung unterscheidet sich wahrscheinlich von der Version der Anwendung.  
  
3.  Kopieren Sie alle Ihre Anwendungsdateien zum Unterverzeichnis "Version", einschließlich der ausführbaren Dateien, Assemblys, Ressourcen und Datendateien. Bei Bedarf können Sie zusätzliche Unterverzeichnisse erstellen, die zusätzliche Dateien enthalten.  
  
4.  Starten Sie das grafische Tool MageUI.exe.  
  
    ```  
    MageUI.exe  
    ```  
  
5.  Erstellen Sie ein neues Anwendungsmanifest dazu **Datei**, **neu**, **Anwendungsmanifest** aus dem Menü.  
  
6.  Auf dem standardmäßigen **Namen** Registerkarte, geben Sie die Anzahl der Name und Version dieser Bereitstellung. Geben Sie auch die **Prozessor** , die Ihre Anwendung, z. B. X86 erstellt wird.  
  
7.  Wählen Sie die **Dateien** Registerkarte, und klicken Sie auf die Auslassungspunkte (**...** ) neben dem **Anwendungsverzeichnis** Textfeld. Ein Dialogfeld Ordner suchen wird angezeigt.  
  
8.  Wählen Sie das Versionsunterverzeichnis, das Ihre Anwendungsdateien enthält, und klicken Sie dann auf **OK**.  
  
9. Wenn Sie von Internet Information Services (IIS) bereitstellen, wählen Sie die **Wenn Auffüllen Hinzufügen der Erweiterung ".deploy" eine Datei, die es keinen** Kontrollkästchen.  
  
10. Klicken Sie auf die **Auffüllen** , um Ihre Anwendungsdateien der Dateiliste hinzuzufügen. Wenn Ihre Anwendung mehr als eine ausführbare Datei enthält, markieren Sie die zentrale ausführbare Datei für diese Bereitstellung als startanwendung dazu **Einstiegspunkt** aus der **Dateityp** Dropdown-Liste. (Wenn die Anwendung nur eine ausführbare Datei enthält, wird diese MageUI.exe markiert.)  
  
11. Wählen Sie die **erforderlichen Berechtigungen** Registerkarte, und wählen Sie die Ebene der Vertrauenswürdigkeit, die Sie benötigen, Ihre Anwendung zu bestätigen. Die Standardeinstellung ist **FullTrust**, der für die meisten Anwendungen geeignet ist.  
  
12. Wählen Sie **Datei**, **speichern unter** aus dem Menü. Ein Dialogfeld "Signaturoptionen" wird die Aufforderung zum Signieren des Anwendungsmanifests angezeigt.  
  
13. Wenn Sie ein Zertifikat als Datei im Dateisystem gespeichert haben, verwenden Sie die **mit Zertifikatsdatei signieren** aus, und wählen Sie das Zertifikat aus dem Dateisystem mit den Auslassungspunkten (**...** ) Schaltfläche. Geben Sie dann das Kennwort für Ihr Zertifikat ein.  
  
     - oder -   
  
     Wenn das Zertifikat in keinem Zertifikatspeicher der von Ihrem Computer zugegriffen werden kann gehalten wird, wählen Sie die **mit gespeichertem Zertifikat signieren** aus, und wählen Sie das Zertifikat in der Liste.  
  
14. Klicken Sie auf **OK** das Anwendungsmanifest zu signieren. Das Dialogfeld Speichern unter wird angezeigt.  
  
15. Klicken Sie im Dialogfeld Speichern unter Geben Sie das Versionsverzeichnis, und klicken Sie dann auf **speichern**.  
  
16. Wählen Sie **Datei**, **neu**, **Bereitstellungsmanifest** aus, um das Bereitstellungsmanifest zu erstellen.  
  
17. Auf der **Namen** Registerkarte, geben einen Namen und Version für diese Bereitstellung (**1.0.0.0** in diesem Beispiel). Geben Sie auch die **Prozessor** , die Ihre Anwendung, z. B. X86 erstellt wird.  
  
18. Wählen Sie die **Beschreibung** Registerkarte, und geben Sie Werte für **Publisher** und **Produkt *** t**. (**Produkt** ist der Name für Ihre Anwendung auf Windows-Startmenü Wenn Ihre Anwendung auf einem Clientcomputer für die Offlineverwendung installiert wird.)  
  
19. Wählen Sie die **Bereitstellungsoptionen** Registerkarte, und klicken Sie in der **Startspeicherort** Text geben den Speicherort des Anwendungsmanifests auf dem Webserver oder der Freigabe. Beispielsweise \\\myServer\myShare\AppToDeploy.application.  
  
20. Wenn Sie die Erweiterung ".deploy" in einem vorherigen Schritt hinzugefügt haben, aktivieren Sie auch **verwenden Sie die Dateinamenerweiterung ".deploy"** hier.  
  
21. Wählen Sie die **Clientupdateoptionen** Registerkarte, und geben Sie, wie oft Sie diese Anwendung aktualisiert werden soll. Wenn Ihre Anwendung verwendet <xref:System.Deployment.Application.UpdateCheckInfo> um selbst Überprüfung auf Updates Deaktivieren der **diese Anwendung soll nach Updates suchen** Kontrollkästchen.  
  
22. Wählen Sie die **Anwendungsverweis** Registerkarte, und klicken Sie dann auf die **Manifest auswählen** Schaltfläche. Ein geöffnetes Dialogfenster wird angezeigt.  
  
23. Wählen Sie das Anwendungsmanifest, das Sie zuvor erstellt haben, und klicken Sie dann auf **öffnen**.  
  
24. Wählen Sie **Datei**, **speichern unter** aus dem Menü. Ein Dialogfeld "Signaturoptionen" angezeigt wird, dazu aufgefordert, dem das Bereitstellungsmanifest signiert.  
  
25. Wenn Sie ein Zertifikat als Datei im Dateisystem gespeichert haben, verwenden Sie die **mit Zertifikatsdatei signieren** aus, und wählen Sie das Zertifikat aus dem Dateisystem mit den Auslassungspunkten (**...** ) Schaltfläche. Geben Sie dann das Kennwort für Ihr Zertifikat ein.  
  
     - oder -   
  
     Wenn das Zertifikat in keinem Zertifikatspeicher der von Ihrem Computer zugegriffen werden kann gehalten wird, wählen Sie die **mit gespeichertem Zertifikat signieren** aus, und wählen Sie das Zertifikat in der Liste.  
  
26. Klicken Sie auf **OK** um das Bereitstellungsmanifest zu signieren. Das Dialogfeld Speichern unter wird angezeigt.  
  
27. In der **speichern unter** (Dialogfeld), verschieben Sie ein Verzeichnis in das Stammverzeichnis Ihrer Bereitstellung und klicken Sie dann auf **speichern**.  
  
28. Kopieren Sie alle Dateien im Bereitstellungsverzeichnis in das Bereitstellungsziel oder ein Medium. Dies kann entweder einen Ordner auf einer Website oder FTP-Site, eine Dateifreigabe oder eine CD-ROM sein.  
  
29. Geben Sie Ihre Benutzer mit der URL, den UNC- oder die physische Medien, die zur Installation der Anwendungsstatus erforderlich sind. Wenn Sie eine URL oder eine UNC-angeben, müssen Sie Ihre Benutzer den vollständigen Pfad des Bereitstellungsmanifests erteilen. Z. B. Wenn AppToDeploy für http://webserver01/ im Verzeichnis AppToDeploy bereitgestellt wird, wäre die vollständige URL-Pfad http://webserver01/AppToDeploy/AppToDeploy.application.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Wenn Sie eine neue Version der Anwendung bereitstellen, erstellen Sie ein neues Verzeichnis mit dem Namen der neuen Version – z. B. 1.0.0.1 kopieren Sie die neue Anwendungsdateien in das neue Verzeichnis. Als Nächstes müssen Sie die vorherigen Schritte zum Erstellen und Signieren ein neues Anwendungsmanifest und aktualisieren sowie das Bereitstellungsmanifest zu signieren. Achten Sie darauf, dass Sie an die gleiche höhere Version in beide Mage.exe `-New` und `-Update` Aufrufe als [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aktualisiert nur die am weitesten links Ganzzahl, die die wichtigsten höhere Versionen. Wenn Sie MageUI.exe verwenden, können Sie aktualisieren das Bereitstellungsmanifest öffnen, Auswahl der **Anwendungsverweis** Registerkarte, auf die **Manifest auswählen** Schaltfläche und wählen Sie dann die aktualisierte Anwendungsmanifest.  
  
## <a name="see-also"></a>Siehe auch  
 [„Mage.exe“ (Tool zum Generieren und Bearbeiten von Manifesten)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (Tool zum Generieren und Bearbeiten von Manifesten, grafischer Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)   
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [ClickOnce-Bereitstellungsmanifest](../deployment/clickonce-deployment-manifest.md)   
 [ClickOnce-Anwendungsmanifest](../deployment/clickonce-application-manifest.md)
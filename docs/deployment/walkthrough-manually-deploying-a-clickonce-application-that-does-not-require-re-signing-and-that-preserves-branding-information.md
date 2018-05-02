---
title: 'Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung, die keine erfordert Erneutes Signieren und Brandinginformationen beibehält | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- branding
- preserved branding information
- ClickOnce deployment, manually
- multiple ClickOnce deployment and branding
- ClickOnce deployment, SDK tools
- customer deployments
- manual ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, deployed by others
ms.assetid: c21822fb-d4ee-42e4-b72d-41ee9786efe5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cb4838e44549f762e609913c92d677832d897edb
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung, die kein erneutes Signieren erfordert und Brandinginformationen beibehält
Beim Erstellen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung und weisen Sie sie an einem Kunden zum Veröffentlichen und bereitstellen, wird der Kunde bisher musste das Bereitstellungsmanifest aktualisieren und signieren Sie es erneut. Zwar immer noch die bevorzugte Methode in den meisten Fällen ist .NET Framework 3.5 ermöglicht Ihnen die Erstellung [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellungen, die von Kunden bereitgestellt werden können, ohne ein neues Bereitstellungsmanifest erneut zu generieren. Weitere Informationen finden Sie unter [Bereitstellen von ClickOnce-Anwendungen für Tests und Produktionsserver ohne Resigning](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md).  
  
 Beim Erstellen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung und weisen Sie sie an einem Kunden zum Veröffentlichen und bereitstellen, wird die Anwendung kann die Brandinginformationen des Kunden oder Ihr branding beibehalten kann. Wenn die Anwendung eine einzelne proprietäre Anwendung ist, sollten Sie Ihr branding beibehalten. Wenn die Anwendung mit hoher für jeden Kunden angepasst wird, empfiehlt es sich um branding des Kunden verwenden. .NET Framework 3.5 können Sie Ihr branding beibehalten, zum Verleger und Sicherheitssignatur, wenn Sie eine bereitzustellende Anwendung für eine Organisation gewähren. Weitere Informationen finden Sie unter [Erstellen von ClickOnce-Anwendungen für andere bereitstellen](../deployment/creating-clickonce-applications-for-others-to-deploy.md).  
  
> [!NOTE]
>  In dieser exemplarischen Vorgehensweise erstellen Sie Bereitstellungen manuell über das Befehlszeilentool Mage.exe oder das grafische Tool MageUI.exe. Weitere Informationen zur manuellen Bereitstellung, finden Sie unter [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Um die Schritte in dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Eine Windows Forms-Anwendung, die Sie bereitstellen möchten. Diese Anwendung wird als WindowsFormsApp1 bezeichnet werden.  
  
-   Visual Studio oder das Windows SDK.  
  
### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>Zum Bereitstellen einer ClickOnce-Anwendung mit mehreren Bereitstellung und verwenden Mage.exe branding-Unterstützung  
  
1.  Öffnen Sie Visual Studio-Eingabeaufforderung oder einer [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] -Eingabeaufforderung, und wechseln Sie zum Verzeichnis, in dem Sie speichern, Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Dateien.  
  
2.  Erstellen Sie ein Verzeichnis namens nach der aktuellen Version von Ihrer Bereitstellung. Ist dies das erste Mal, dass Sie die Anwendung bereitstellen möchten, wählen Sie wahrscheinlich **1.0.0.0**.  
  
    > [!NOTE]
    >  Die Version der Bereitstellung möglicherweise nicht die Version der Anwendungsdateien identisch sein.  
  
3.  Erstellen Sie ein Unterverzeichnis mit dem Namen **"bin"** und kopieren Sie alle Anwendungsdateien, einschließlich der ausführbaren Dateien, Assemblys, Ressourcen und Datendateien.  
  
4.  Das Anwendungsmanifest mit einem Aufruf von Mage.exe zu generieren.  
  
    ```  
    mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"  
    ```  
  
5.  Melden Sie sich das Anwendungsmanifest mit digitalen Zertifikats.  
  
    ```  
    mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx  
    ```  
  
6.  Generieren Sie das Bereitstellungsmanifest mit einem Aufruf von Mage.exe. Standardmäßig Mage.exe markiert die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Bereitstellung als installierte Anwendung, damit die It sowohl online ausgeführt werden kann und offline. Um die Anwendung zur Verfügung stellen nur, wenn der Benutzer online ist, verwenden die `-i` Argument mit einem Wert von `f`. Da diese Anwendung mehrere Bereitstellungsfunktion nutzen werden, schließen die `-providerUrl` Argument Mage.exe. (In Versionen von .NET Framework vor Version 3.5, ausgenommen `-providerUrl` für eine offline-Anwendung zu einem Fehler führen wird.)  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest   
    ```  
  
7.  Melden Sie das Bereitstellungsmanifest nicht.  
  
8.  Geben Sie alle Dateien an dem Kunden, der die Anwendung auf seinem Netzwerk bereitgestellt wird.  
  
9. An diesem Punkt muss der Kunde das Bereitstellungsmanifest mit seinem eigenen selbst generiertes Zertifikat signieren. Wenn der Kunde für ein Unternehmen namens Adventure Works funktioniert, kann er beispielsweise ein selbstsigniertes Zertifikat mithilfe des Tools MakeCert.exe generieren. Als Nächstes verwenden Sie das Tool Pvk2pfx.exe, kombinieren Sie die Dateien mit MakeCert.exe erstellt in eine PFX-Datei, die an Mage.exe übergeben werden kann.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
10. Anschließend verwendet der Kunde dieses Zertifikat zum Signieren des Bereitstellungsmanifests.  
  
    ```  
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx  
    ```  
  
11. Der Kunde stellt die Anwendung an ihre Benutzer bereit.  
  
### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>Zum Bereitstellen einer ClickOnce-Anwendung mit mehreren Bereitstellung und mit MageUI.exe branding-Unterstützung  
  
1.  Öffnen Sie Visual Studio-Eingabeaufforderung oder einer [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] -Eingabeaufforderung, und navigieren Sie zu dem Verzeichnis, in dem Sie speichern, Ihre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Dateien.  
  
2.  Erstellen Sie ein Unterverzeichnis mit dem Namen **"bin"** und kopieren Sie alle Anwendungsdateien, einschließlich der ausführbaren Dateien, Assemblys, Ressourcen und Datendateien.  
  
3.  Erstellen Sie ein Unterverzeichnis, das nach der aktuellen Version von Ihrer Bereitstellung. Ist dies das erste Mal, dass Sie die Anwendung bereitstellen möchten, wählen Sie wahrscheinlich **1.0.0.0**.  
  
    > [!NOTE]
    >  Die Version der Bereitstellung möglicherweise nicht die Version der Anwendungsdateien identisch sein.  
  
4.  Verschieben der \\ **"bin"** Verzeichnis in das Verzeichnis, das Sie in Schritt 2 erstellt haben.  
  
5.  Starten Sie das grafische Tool MageUI.exe.  
  
    ```  
    MageUI.exe  
    ```  
  
6.  Erstellen Sie ein neues Anwendungsmanifest dazu **Datei**, **neu**, **Anwendungsmanifest** aus dem Menü.  
  
7.  Auf dem standardmäßigen **Namen** Registerkarte, geben Sie den Namen und Version dieser Bereitstellung. Geben Sie auch einen Wert für **Verleger**, bei der Bereitstellung wird als Ordnername für die Anwendung Verknüpfung im Startmenü verwendet werden wird.  
  
8.  Wählen Sie die **Anwendungsoptionen** Registerkarte, und klicken Sie auf **Anwendungsmanifest für Vertrauensinformationen verwenden**. Dadurch können Drittanbieter-branding für diesen [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Anwendung.  
  
9. Wählen Sie die **Dateien** Registerkarte, und klicken Sie auf die **Durchsuchen** Schaltfläche neben dem Textfeld Anwendungsverzeichnis.  
  
10. Wählen Sie das Verzeichnis, das Ihre Anwendungsdateien enthält, die Sie in Schritt 2 erstellt haben, und klicken Sie auf **OK** auf im Dialogfeld für die Auswahl des Ordners.  
  
11. Klicken Sie auf die **Auffüllen** , um Ihre Anwendungsdateien der Dateiliste hinzuzufügen. Wenn Ihre Anwendung mehr als eine ausführbare Datei enthält, markieren Sie die zentrale ausführbare Datei für diese Bereitstellung als startanwendung dazu **Einstiegspunkt** aus der **Dateityp** Dropdown-Liste. (Wenn die Anwendung nur eine ausführbare Datei enthält, wird diese MageUI.exe markiert.)  
  
12. Wählen Sie die **erforderlichen Berechtigungen** Registerkarte, und wählen Sie die Ebene der Vertrauenswürdigkeit, die Sie benötigen Ihre Anwendung zu bestätigen. Die Standardeinstellung ist **volle Vertrauenswürdigkeit**, der für die meisten Anwendungen geeignet ist.  
  
13. Wählen Sie **Datei**, **speichern** aus dem Menü, und speichern Sie das Anwendungsmanifest. Sie werden aufgefordert, das Anwendungsmanifest zu signieren, wenn Sie es speichern.  
  
14. Wenn Sie ein Zertifikat als Datei im Dateisystem gespeichert haben, verwenden Sie die **als Zertifikatsdatei signieren** aus, und wählen Sie das Zertifikat aus dem Dateisystem, die mit den Auslassungspunkten (**...** ) Schaltfläche.  
  
     - oder -   
  
     Wenn das Zertifikat im Zertifikatspeicher gehalten wird, die von Ihrem Computer zugegriffen werden kann, wählen Sie die **Option mit gespeichertem Zertifikat signieren**, und wählen Sie das Zertifikat aus der Liste aus.  
  
15. Wählen Sie **Datei**, **neu**, **Bereitstellungsmanifest** aus, um das Bereitstellungsmanifest zu erstellen, und klicken Sie dann auf die **Namen** Registerkarte, geben Sie einen Name und die Versionsnummer (**1.0.0.0** in diesem Beispiel).  
  
16. Wechseln Sie zu der **aktualisieren** Registerkarte, und geben an, wie oft diese Anwendung aktualisiert werden soll. Wenn Ihre Anwendung verwendet die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Deployment API nach Updates suchen, deaktivieren Sie das Kontrollkästchen mit der Bezeichnung **diese Anwendung soll nach Updates suchen**.  
  
17. Wechseln Sie zu der **Anwendungsverweis** Registerkarte. Sie können alle Werte auf dieser Registerkarte vorab auffüllen, indem Sie auf die **Manifest auswählen** Schaltfläche und wählen das Anwendungsmanifest ist Sie in den vorherigen Schritten erstellt.  
  
18. Wählen Sie **speichern** und speichern Sie das Bereitstellungsmanifest auf dem Datenträger. Sie werden aufgefordert, das Anwendungsmanifest zu signieren, wenn Sie es speichern. Klicken Sie auf **"Abbrechen"** Speichern des Manifests, ohne es zu signieren.  
  
19. Geben Sie alle Dateien der Anwendung an dem Kunden.  
  
20. An diesem Punkt muss der Kunde das Bereitstellungsmanifest mit seinem eigenen selbst generiertes Zertifikat signieren. Wenn der Kunde für ein Unternehmen namens Adventure Works funktioniert, kann er beispielsweise ein selbstsigniertes Zertifikat mithilfe des Tools MakeCert.exe generieren. Als Nächstes verwenden Sie das Tool Pvk2pfx.exe, kombinieren Sie die Dateien mit MakeCert.exe erstellt in eine PFX-Datei, die an MageUI.exe übergeben werden kann.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
21. Mit dem Zertifikat generiert signiert der Kunde das Bereitstellungsmanifest durch Öffnen des Bereitstellungsmanifests in MageUI.exe und anschließend zu speichern. Wenn die Signatur im Dialogfeld angezeigt wird, wählt der Kunde **als Zertifikatsdatei signieren** aus, und wählt die PFX-Datei, die er auf der Festplatte gespeichert wurde.  
  
22. Der Kunde stellt die Anwendung an ihre Benutzer bereit.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
## <a name="see-also"></a>Siehe auch  
 [„Mage.exe“ (Tool zum Generieren und Bearbeiten von Manifesten)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [MageUI.exe (Tool zum Generieren und Bearbeiten von Manifesten, grafischer Client)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)   
 [MakeCert](https://msdn.microsoft.com/library/windows/desktop/aa386968.aspx)
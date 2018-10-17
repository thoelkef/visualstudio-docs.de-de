---
title: 'Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung, die kein erneutes Signieren erfordert und Brandinginformationen beibehält | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 2d6531a94a99e2a1c24d80e9f326d23fcc6c4ec3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49252992"
---
# <a name="walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung, die kein erneutes Signieren erfordert und Brandinginformationen beibehält
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bei der Erstellung einer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung und geben Sie ihm für einem Kunden zum Veröffentlichen und bereitstellen, wird der Kunde musste früher das Bereitstellungsmanifest aktualisieren und erneut signieren. Weiterhin ist die bevorzugte Methode in den meisten Fällen .NET Framework 3.5 ermöglicht Ihnen die Erstellung [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellungen, die von Kunden bereitgestellt werden können, ohne dass ein neues Bereitstellungsmanifest erneut zu generieren. Weitere Informationen finden Sie unter [Bereitstellen von ClickOnce-Anwendungen für Tests und Produktionsserver ohne Resigning](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md).  
  
 Bei der Erstellung einer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung und geben Sie ihm für einem Kunden zum Veröffentlichen und bereitstellen, wird die Anwendung des Kunden Brandinginformationen verwenden oder Ihr branding beibehalten kann. Z. B., wenn die Anwendung eine einzelne geschützte Anwendung ist, möchten Sie Ihr branding beibehalten. Wenn die Anwendung hoch für jeden Kunden angepasst wird, empfiehlt es sich mit branding des Kunden. .NET Framework 3.5 können Sie Ihr branding beibehalten, Herausgeberinformationen und Security-Signatur, wenn Sie eine bereitzustellende Anwendung für eine Organisation geben. Weitere Informationen finden Sie unter [Erstellen von ClickOnce-Anwendungen für andere bereitstellen](../deployment/creating-clickonce-applications-for-others-to-deploy.md).  
  
> [!NOTE]
>  In dieser exemplarischen Vorgehensweise erstellen Sie Bereitstellungen manuell mithilfe der entweder das Befehlszeilentool Mage.exe oder MageUI.exe über das grafische Tool. Weitere Informationen zur manuellen Bereitstellung finden Sie unter [Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Zum Ausführen der Schritte in dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Eine Windows Forms-Anwendung, die Sie bereitstellen möchten. Diese Anwendung wird als WindowsFormsApp1 bezeichnet werden.  
  
-   Visual Studio oder das Windows SDK.  
  
### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>Bereitstellen eine ClickOnce-Anwendung mit mehreren Bereitstellung und mit "Mage.exe" branding-Unterstützung  
  
1.  Öffnen Sie Visual Studio-Eingabeaufforderung oder ein [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] -Eingabeaufforderung, und ändern Sie in das Verzeichnis, in dem Sie speichern, Ihre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Dateien.  
  
2.  Erstellen Sie ein Verzeichnis namens nach der aktuellen Version der Bereitstellung. Ist dies das erste Mal, dass Sie die Anwendung bereitstellen möchten, wählen Sie wahrscheinlich **1.0.0.0**.  
  
    > [!NOTE]
    >  Die Version der Bereitstellung kann sich von der Version der Anwendungsdateien unterscheiden.  
  
3.  Erstellen Sie ein Unterverzeichnis mit dem Namen **Bin** und kopieren Sie alle Ihre Anwendungsdateien, einschließlich der ausführbaren Dateien, Assemblys, Ressourcen und -Datendateien.  
  
4.  Das Anwendungsmanifest mit einem Aufruf von Mage.exe zu generieren.  
  
    ```  
    mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"  
    ```  
  
5.  Melden Sie das Anwendungsmanifest mit das digitale Zertifikat.  
  
    ```  
    mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx  
    ```  
  
6.  Das Bereitstellungsmanifest mit einem Aufruf von Mage.exe zu generieren. In der Standardeinstellung Mage.exe kennzeichnen Ihrer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellung als installierte Anwendung, damit die It-sowohl online ausgeführt werden kann und offline. Verwenden Sie die Anwendung zur Verfügung stellen möchten nur, wenn der Benutzer online ist, die `-i` Argument mit einem Wert von `f`. Da diese Anwendung mehrere-Bereitstellungsfeature des nutzen wird, schließen Sie die `-providerUrl` Mage.exe Argument. (In Versionen von .NET Framework vor Version 3.5, ausgenommen `-providerUrl` für eine offline-Anwendung zu einem Fehler führt.)  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest   
    ```  
  
7.  Melden Sie sich das Bereitstellungsmanifest nicht.  
  
8.  Geben Sie alle Dateien an dem Kunden, der die Anwendung auf seinem Netzwerk bereitgestellt wird.  
  
9. An diesem Punkt muss der Kunde das Bereitstellungsmanifest mit seinen eigenen selbst generiertes Zertifikat signieren. Wenn der Kunde für ein Unternehmen namens Adventure Works geeignet ist, kann er z. B. ein selbstsigniertes Zertifikat mithilfe des Tools MakeCert.exe generieren. Als Nächstes verwenden Sie das Tool Pvk2pfx.exe, kombinieren Sie die erstellten Dateien von MakeCert.exe in einer PFX-Datei, die an Mage.exe übergeben werden kann.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
10. Der Kunde verwendet anschließend dieses Zertifikat zum Signieren des Bereitstellungsmanifests.  
  
    ```  
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx  
    ```  
  
11. Der Kunde stellt die Anwendung für ihre Benutzer bereit.  
  
### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>Bereitstellen eine ClickOnce-Anwendung mit mehreren Bereitstellung und branding-Unterstützung mit MageUI.exe  
  
1.  Öffnen Sie Visual Studio-Eingabeaufforderung oder ein [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] -Eingabeaufforderung, und navigieren Sie zu dem Verzeichnis, in dem Sie speichern, Ihre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Dateien.  
  
2.  Erstellen Sie ein Unterverzeichnis mit dem Namen **Bin** und kopieren Sie alle Ihre Anwendungsdateien, einschließlich der ausführbaren Dateien, Assemblys, Ressourcen und -Datendateien.  
  
3.  Erstellen Sie ein Unterverzeichnis für die aktuelle Version der Bereitstellung. Ist dies das erste Mal, dass Sie die Anwendung bereitstellen möchten, wählen Sie wahrscheinlich **1.0.0.0**.  
  
    > [!NOTE]
    >  Die Version der Bereitstellung kann sich von der Version der Anwendungsdateien unterscheiden.  
  
4.  Verschieben der \\ **Bin** Verzeichnis in das Verzeichnis, das Sie in Schritt 2 erstellt haben.  
  
5.  Starten Sie das grafische Tool MageUI.exe.  
  
    ```  
    MageUI.exe  
    ```  
  
6.  Erstellen Sie ein neues Anwendungsmanifest dazu **Datei**, **neu**, **Anwendungsmanifest** aus dem Menü.  
  
7.  Auf der standardmäßigen **Namen** Registerkarte, geben Sie Name und Version dieser Bereitstellung. Geben Sie auch einen Wert für **Verleger**, bei der Bereitstellung als Ordnername für verknüpfungs-Link mit der Anwendung im Startmenü verwendet werden wird.  
  
8.  Wählen Sie die **Anwendungsoptionen** Registerkarte, und klicken Sie auf **Anwendungsmanifest für Vertrauensinformationen verwenden**. Dadurch werden von Drittanbietern für dieses branding [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung.  
  
9. Wählen Sie die **Dateien** Registerkarte, und klicken Sie auf die **Durchsuchen** Schaltfläche neben dem Textfeld Anwendungsverzeichnis.  
  
10. Wählen Sie das Verzeichnis, das Ihre Anwendungsdateien enthält, die Sie in Schritt 2 erstellt haben, und klicken Sie auf **OK** auf im Dialogfeld für die Auswahl des Ordners.  
  
11. Klicken Sie auf die **Auffüllen** , um alle Anwendungsdateien in die Liste der Dateien aufzunehmen. Wenn Ihre Anwendung mehr als eine ausführbare Datei enthält, markieren Sie die ausführbare Hauptdatei für diese Bereitstellung als startanwendung dazu **Einstiegspunkt** aus der **Dateityp** Dropdown-Liste. (Wenn Ihre Anwendung nur eine ausführbare Datei enthält, wird diese MageUI.exe markiert.)  
  
12. Wählen Sie die **erforderlichen Berechtigungen** Registerkarte, und wählen Sie die Ebene der Vertrauenswürdigkeit, die Sie benötigen Ihre Anwendung aus, um zu bestätigen. Der Standardwert ist **volle Vertrauenswürdigkeit**, die für die meisten Anwendungen geeignet sein.  
  
13. Wählen Sie **Datei**, **speichern** aus dem Menü, und speichern Sie das Anwendungsmanifest. Sie werden aufgefordert, das Anwendungsmanifest zu signieren, wenn Sie sie speichern.  
  
14. Wenn Sie ein Zertifikat als Datei im Dateisystem gespeichert haben, verwenden Sie die **als Zertifikatsdatei signieren** aus, und wählen Sie das Zertifikat aus dem Dateisystem mit den Auslassungspunkten (**...** ) Schaltfläche.  
  
     - oder -   
  
     Wenn das Zertifikat im Zertifikatspeicher gespeichert wird, der von Ihrem Computer aus zugegriffen werden kann, wählen Sie die **Option mit gespeicherten Zertifikat signieren**, und wählen Sie das Zertifikat aus der Liste aus.  
  
15. Wählen Sie **Datei**, **neu**, **Bereitstellungsmanifest** aus, um das Bereitstellungsmanifest zu erstellen, und klicken Sie dann auf die **Namen** Registerkarte, geben Sie einen Name und Versionsnummer (**1.0.0.0** in diesem Beispiel).  
  
16. Wechseln Sie zu der **aktualisieren** Registerkarte, und geben Sie, wie oft die Anwendung aktualisiert werden sollen. Wenn Ihre Anwendung verwendet die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Deployment API nach Updates suchen, deaktivieren Sie das Kontrollkästchen **diese Anwendung soll nach Updates suchen**.  
  
17. Wechseln Sie zu der **Anwendungsverweis** Registerkarte. Sie können alle Werte auf dieser Registerkarte vorab auffüllen, indem Sie auf die **Manifest auswählen** Schaltfläche, und wählen das Anwendungsmanifest ist Sie in den vorherigen Schritten erstellt.  
  
18. Wählen Sie **speichern** und das Bereitstellungsmanifest auf Datenträger speichern. Sie werden aufgefordert, das Anwendungsmanifest zu signieren, wenn Sie sie speichern. Klicken Sie auf **Abbrechen** Speichern des Manifests, ohne es zu signieren.  
  
19. Geben Sie alle Dateien der Anwendung können Sie an, an dem Kunden.  
  
20. An diesem Punkt muss der Kunde das Bereitstellungsmanifest mit seinen eigenen selbst generiertes Zertifikat signieren. Wenn der Kunde für ein Unternehmen namens Adventure Works geeignet ist, kann er z. B. ein selbstsigniertes Zertifikat mithilfe des Tools MakeCert.exe generieren. Als Nächstes verwenden Sie das Tool Pvk2pfx.exe, kombinieren Sie die erstellten Dateien von MakeCert.exe in einer PFX-Datei, die an MageUI.exe übergeben werden kann.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
21. Mit dem Zertifikat generiert wird meldet sich an der Kunden jetzt das Bereitstellungsmanifest durch Öffnen des Bereitstellungsmanifests in MageUI.exe, und klicken Sie dann speichern. Wenn das Dialogfeld "Signatur" angezeigt wird, wählt der Kunde **als Zertifikatsdatei signieren** aus, und wählt die PFX-Datei, die er auf dem Datenträger gespeichert wurde.  
  
22. Der Kunde stellt die Anwendung für ihre Benutzer bereit.  
  
## <a name="next-steps"></a>Nächste Schritte  
  
## <a name="see-also"></a>Siehe auch  
 [„Mage.exe“ (Tool zum Generieren und Bearbeiten von Manifesten)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (Tool zum Generieren und Bearbeiten von Manifesten, grafischer Client)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)   
 [Makecert.exe (Tool für die Zertifikaterstellung)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)




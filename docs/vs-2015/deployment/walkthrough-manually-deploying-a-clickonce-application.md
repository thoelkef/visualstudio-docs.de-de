---
title: 'Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 51
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e1099eaf8d766088612abbb399bdf004e6378e4
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74294685"
---
# <a name="walkthrough-manually-deploying-a-clickonce-application"></a>Exemplarische Vorgehensweise: Manuelles Bereitstellen einer ClickOnce-Anwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie Visual Studio nicht verwenden können, um Ihre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendung bereitzustellen, oder Sie erweiterte Bereitstellungs Funktionen wie die Bereitstellung einer vertrauenswürdigen Anwendung verwenden müssen, sollten Sie das Befehlszeilen Tool "Mage. exe" verwenden, um Ihre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Manifeste zu erstellen. In dieser exemplarischen Vorgehensweise wird beschrieben, wie Sie eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellung entweder mithilfe der Befehlszeilenversion (Mage. exe) oder der grafischen Version (MageUI. exe) des Manifest Generation and Editing Tool erstellen.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Diese exemplarische Vorgehensweise enthält einige Voraussetzungen und Optionen, die Sie vor dem Aufbau einer Bereitstellung auswählen müssen.  
  
- Installieren Sie "Mage. exe" und "MageUI. exe".  
  
     "Mage. exe" und "MageUI. exe" sind Teil der [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]. Sie müssen entweder die [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] installiert haben, oder die Version des [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)], die in Visual Studio enthalten ist. Weitere Informationen finden Sie unter [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=158044) auf MSDN.  
  
- Stellen Sie eine bereit zustellende Anwendung bereit.  
  
     In dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass Sie eine Windows-Anwendung haben, die Sie bereitstellen können. Diese Anwendung wird als apptobereitstellung bezeichnet.  
  
- Bestimmen Sie, wie die Bereitstellung verteilt wird.  
  
     Die Verteilungs Optionen umfassen: Web, Dateifreigabe oder CD. Weitere Informationen finden Sie unter [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md).  
  
- Stellen Sie fest, ob die Anwendung eine höhere Vertrauens Ebene erfordert.  
  
     Wenn für Ihre Anwendung volle Vertrauenswürdigkeit erforderlich ist – z. b. Vollzugriff auf das System des Benutzers – können Sie die Option `-TrustLevel` von "Mage. exe" verwenden, um dies festzulegen. Wenn Sie einen benutzerdefinierten Berechtigungs Satz für Ihre Anwendung definieren möchten, können Sie den Abschnitt Internet-oder Intranet-Berechtigung aus einem anderen Manifest kopieren, an Ihre Anforderungen anpassen und ihn mit einem Text-Editor oder mit "MageUI. exe" dem Anwendungs Manifest hinzufügen. Weitere Informationen finden Sie unter [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
- Rufen Sie ein Authenticode-Zertifikat ab.  
  
     Sie sollten Ihre Bereitstellung mit einem Authenticode-Zertifikat signieren. Sie können ein Test Zertifikat mithilfe von Visual Studio, MageUI. exe oder Makecert. exe-und Pvk2pfx. exe-Tools generieren, oder Sie können ein Zertifikat von einer Zertifizierungsstelle (ca) abrufen. Wenn Sie die Bereitstellung einer vertrauenswürdigen Anwendung verwenden, müssen Sie auch eine einmalige Installation des Zertifikats auf allen Client Computern durchführen. Weitere Informationen finden Sie unter [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
    > [!NOTE]
    > Sie können die Bereitstellung auch mit einem CNG-Zertifikat signieren, das Sie von einer Zertifizierungsstelle erhalten können.  
  
- Stellen Sie sicher, dass die Anwendung nicht über ein Manifest mit UAC-Informationen verfügt.  
  
     Sie müssen bestimmen, ob Ihre Anwendung ein Manifest mit Informationen zur Benutzerkontensteuerung (User Account Control, UAC) enthält, z. b. ein `<dependentAssembly>` Element. Wenn Sie ein Anwendungs Manifest untersuchen möchten, können Sie das Hilfsprogramm Windows Sysinternals [Sigcheck](https://go.microsoft.com/fwlink/?LinkId=158035) verwenden.  
  
     Wenn Ihre Anwendung ein Manifest mit UAC-Details enthält, müssen Sie Sie ohne die UAC-Informationen neu erstellen. Öffnen Sie C# für ein Projekt in Visual Studio die Projekteigenschaften, und wählen Sie die Registerkarte Anwendung aus. Wählen Sie in der Dropdown Liste **Manifest** die Option **Anwendung ohne Manifest erstellen**aus. Öffnen Sie für ein Visual Basic Projekt in Visual Studio die Projekteigenschaften, wählen Sie die Registerkarte Anwendung aus, und klicken Sie auf **UAC-Einstellungen anzeigen**. Entfernen Sie in der geöffneten Manifest-Datei alle-Elemente innerhalb des einzelnen `<asmv1:assembly>`-Elements.  
  
- Bestimmen Sie, ob für die Anwendung erforderliche Komponenten auf dem Client Computer erforderlich sind.  
  
     [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Anwendungen, die von Visual Studio bereitgestellt werden, können einen erforderlichen Installations-Boots Trapper (Setup. exe) mit Ihrer Bereitstellung enthalten. In dieser exemplarischen Vorgehensweise werden die beiden Manifeste für eine [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellung erstellt. Sie können einen erforderlichen Boots Trapper mithilfe der [GenerateBootstrapper-Aufgabe](../msbuild/generatebootstrapper-task.md)erstellen.  
  
### <a name="to-deploy-an-application-with-the-mageexe-command-line-tool"></a>So stellen Sie eine Anwendung mit dem Befehlszeilen Tool "Mage. exe" bereit  
  
1. Erstellen Sie ein Verzeichnis, in dem Sie Ihre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellungs Dateien speichern.  
  
2. Erstellen Sie im soeben erstellten Bereitstellungs Verzeichnis ein Versions Unterverzeichnis. Wenn Sie die Anwendung zum ersten Mal bereitstellen, benennen Sie die Version Unterverzeichnis **1.0.0.0**.  
  
    > [!NOTE]
    > Die Version der Bereitstellung kann sich von der Version der Anwendung unterscheiden.  
  
3. Kopieren Sie alle Anwendungs Dateien in das Versions Unterverzeichnis, einschließlich ausführbarer Dateien, Assemblys, Ressourcen und Datendateien. Bei Bedarf können Sie zusätzliche Unterverzeichnisse erstellen, die zusätzliche Dateien enthalten.  
  
4. Öffnen Sie die [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)]-oder Visual Studio-Eingabeaufforderung, und wechseln Sie zum Unterverzeichnis Version.  
  
5. Erstellen Sie das Anwendungs Manifest mit einem aufzurufenden Befehl "Mage. exe". Mit der folgenden Anweisung wird ein Anwendungs Manifest für den Code erstellt, der auf dem Intel x86-Prozessor ausgeführt werden soll.  
  
    ```  
    mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
    ```  
  
    > [!NOTE]
    > Stellen Sie sicher, dass Sie den Punkt (.) nach der `-FromDirectory`-Option einschließen, die das aktuelle Verzeichnis angibt. Wenn Sie den Punkt nicht einschließen, müssen Sie den Pfad zu den Anwendungs Dateien angeben.  
  
6. Signieren Sie das Anwendungs Manifest mit Ihrem Authenticode-Zertifikat. Ersetzen Sie *mycert. pfx* durch den Pfad zu Ihrer Zertifikatsdatei. Ersetzen Sie *Kennwort* durch das Kennwort für die Zertifikat Datei.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
    ```  
  
     Verwenden Sie Folgendes, um das Anwendungs Manifest mit einem CNG-Zertifikat zu signieren. Ersetzen Sie *cngcert. pfx* durch den Pfad zu Ihrer Zertifikatsdatei.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
7. Wechseln Sie zum Stammverzeichnis des Bereitstellungs Verzeichnisses.  
  
8. Generieren Sie das Bereitstellungs Manifest mit einem-Befehl von "Mage. exe". Standardmäßig wird die [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellung von "Mage. exe" als installierte Anwendung gekennzeichnet, sodass Sie sowohl online als auch offline ausgeführt werden kann. Um die Anwendung nur verfügbar zu machen, wenn der Benutzer online ist, verwenden Sie die `-Install`-Option mit dem Wert `false`. Wenn Sie die Standardeinstellung verwenden und Benutzer die Anwendung von einer Website oder Dateifreigabe installieren, müssen Sie sicherstellen, dass der Wert der `-ProviderUrl`-Option auf den Speicherort des Anwendungs Manifests auf dem Webserver oder der Freigabe verweist.  
  
    ```  
    mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application  
    ```  
  
9. Signieren Sie das Bereitstellungs Manifest mit Ihrem Authenticode-oder CNG-Zertifikat.  
  
    ```  
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd  
    ```  
  
     oder  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile cngCert.pfx  
    ```  
  
10. Kopieren Sie alle Dateien im Bereitstellungs Verzeichnis auf das Bereitstellungs Ziel oder auf das Zielmedium. Hierbei kann es sich entweder um einen Ordner auf einer Website oder einer FTP-Website, eine Dateifreigabe oder eine CD-ROM handeln.  
  
11. Stellen Sie Ihren Benutzern die URL, das UNC-oder das physische Medium zur Verfügung, die für die Installation der Anwendung erforderlich sind. Wenn Sie eine URL oder einen UNC-Namen angeben, müssen Sie Ihren Benutzern den vollständigen Pfad zum Bereitstellungs Manifest erteilen. Wenn beispielsweise apptbereitstellung auf http://webserver01/ im Verzeichnis appto-Bereitstellung bereitgestellt wird, wird der vollständige URL-Pfad http://webserver01/AppToDeploy/AppToDeploy.application.  
  
### <a name="to-deploy-an-application-with-the-mageuiexe-graphical-tool"></a>So stellen Sie eine Anwendung mit dem grafischen Tool "MageUI. exe" bereit  
  
1. Erstellen Sie ein Verzeichnis, in dem Sie Ihre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Bereitstellungs Dateien speichern.  
  
2. Erstellen Sie im soeben erstellten Bereitstellungs Verzeichnis ein Versions Unterverzeichnis. Wenn Sie die Anwendung zum ersten Mal bereitstellen, benennen Sie die Version Unterverzeichnis **1.0.0.0**.  
  
    > [!NOTE]
    > Die Version Ihrer-Bereitstellung unterscheidet sich wahrscheinlich von der Version Ihrer Anwendung.  
  
3. Kopieren Sie alle Anwendungs Dateien in das Versions Unterverzeichnis, einschließlich ausführbarer Dateien, Assemblys, Ressourcen und Datendateien. Bei Bedarf können Sie zusätzliche Unterverzeichnisse erstellen, die zusätzliche Dateien enthalten.  
  
4. Starten Sie das grafische Tool "MageUI. exe".  
  
    ```  
    MageUI.exe  
    ```  
  
5. Erstellen Sie ein neues Anwendungs Manifest, indem Sie im Menü **Datei**, **neu**und **Anwendungs Manifest** auswählen.  
  
6. Geben Sie auf der Registerkarte Standard **Name** den Namen und die Versionsnummer dieser Bereitstellung ein. Geben Sie außerdem den **Prozessor** an, für den Ihre Anwendung erstellt wurde, z. b. x86.  
  
7. Wählen Sie die Registerkarte **Dateien** aus, und klicken Sie auf die Schaltfläche mit den Auslassungs Punkten ( **...** ) neben dem Textfeld **Anwendungsverzeichnis** . Das Dialogfeld Ordner suchen wird angezeigt.  
  
8. Wählen Sie das Unterverzeichnis Version aus, das Ihre Anwendungs Dateien enthält, und klicken Sie dann auf **OK**.  
  
9. Wenn Sie die Bereitstellung über Internetinformationsdienste (IIS) durchführt, aktivieren Sie das Kontrollkästchen **Hinzufügen der Erweiterung zu einer beliebigen Datei, für die es nicht vorhanden** ist.  
  
10. Klicken Sie **auf die Schalt** Fläche auffüllen, um alle Anwendungs Dateien der Datei Liste hinzuzufügen. Wenn die Anwendung mehr als eine ausführbare Datei enthält, markieren Sie die ausführbare Hauptdatei für diese Bereitstellung als Start Anwendung, indem Sie in der Dropdown Liste **Dateityp** den **Eintrag Einstiegspunkt** auswählen. (Wenn Ihre Anwendung nur eine ausführbare Datei enthält, wird Sie von "MageUI. exe" für Sie markiert.)  
  
11. Wählen Sie die Registerkarte **erforderliche Berechtigungen** aus, und wählen Sie die Vertrauens Ebene aus, die von der Anwendung bestätigt werden muss. Der Standardwert ist " **FullTrust**", der für die meisten Anwendungen geeignet ist.  
  
12. Wählen Sie im Menü **Datei**, **Speichern** unter aus. Im Dialogfeld Signierungs Optionen werden Sie aufgefordert, das Anwendungs Manifest zu signieren.  
  
13. Wenn Sie ein Zertifikat haben, das als Datei auf Ihrem Dateisystem gespeichert ist, verwenden Sie die Option **Zertifikat Datei signieren** , und wählen Sie das Zertifikat aus dem Dateisystem aus, indem Sie die Schaltfläche mit den Auslassungs Punkten ( **...** ) verwenden. Geben Sie dann Ihr Zertifikat Kennwort ein.  
  
     \- oder -  
  
     Wenn Ihr Zertifikat in einem Zertifikat Speicher gespeichert ist, der von Ihrem Computer aus zugänglich ist, aktivieren Sie die Option **gespeichertes Zertifikat signieren** , und wählen Sie das Zertifikat aus der Liste bereitgestellt aus.  
  
14. Klicken Sie zum Signieren des Anwendungs Manifests auf **OK** . Das Dialogfeld Speichern unter wird angezeigt.  
  
15. Geben Sie im Dialogfeld Speichern unter das Versions Verzeichnis an, und klicken Sie dann auf **Speichern**.  
  
16. Wählen Sie im Menü **Datei**, **neu**und **Bereitstellungs Manifest** aus, um das Bereitstellungs Manifest zu erstellen.  
  
17. Geben Sie auf der Registerkarte **Name** einen Namen und eine Versionsnummer für diese Bereitstellung an (in diesem Beispiel**1.0.0.0** ). Geben Sie außerdem den **Prozessor** an, für den Ihre Anwendung erstellt wurde, z. b. x86.  
  
18. Wählen Sie die Registerkarte **Beschreibung** aus, und geben Sie Werte für **Publisher** und **Product**an. (**Product** ist der Name, der der Anwendung im Windows-Startmenü zur Verfügung gestellt wird, wenn die Anwendung auf einem Client Computer für die Offline Verwendung installiert wird.)  
  
19. Wählen Sie die Registerkarte **Bereitstellungs Optionen** aus, und geben Sie im Textfeld **Start Speicherort** den Speicherort des Anwendungs Manifests auf dem Webserver oder der Freigabe an. Beispielsweise \\\myserver\myshare\appdedeploy.Application.  
  
20. Wenn Sie in einem vorherigen Schritt die Erweiterung. Bereitstellung hinzugefügt haben, wählen Sie hier verwenden aus. Stellen Sie hier die **Dateinamenerweiterung** bereit.  
  
21. Wählen Sie die Registerkarte **Update Optionen** aus, und geben Sie an, wie oft diese Anwendung aktualisiert werden soll. Wenn Ihre Anwendung <xref:System.Deployment.Application.UpdateCheckInfo> verwendet, um nach Updates zu suchen, deaktivieren Sie das Kontrollkästchen **diese Anwendung sollte auf Updates überprüfen** .  
  
22. Wählen Sie die Registerkarte **Anwendungs Verweis** aus, und klicken Sie auf die Schaltfläche **Manifest auswählen** . Ein Dialogfeld öffnen wird angezeigt.  
  
23. Wählen Sie das Anwendungs Manifest aus, das Sie zuvor erstellt haben, und klicken Sie auf **Öffnen**.  
  
24. Wählen Sie im Menü **Datei**, **Speichern** unter aus. Im Dialogfeld Signierungs Optionen werden Sie aufgefordert, das Bereitstellungs Manifest zu signieren.  
  
25. Wenn Sie ein Zertifikat haben, das als Datei auf Ihrem Dateisystem gespeichert ist, verwenden Sie die Option **Zertifikat Datei signieren** , und wählen Sie das Zertifikat aus dem Dateisystem aus, indem Sie die Schaltfläche mit den Auslassungs Punkten ( **...** ) verwenden. Geben Sie dann Ihr Zertifikat Kennwort ein.  
  
     \- oder -  
  
     Wenn Ihr Zertifikat in einem Zertifikat Speicher gespeichert ist, der von Ihrem Computer aus zugänglich ist, aktivieren Sie die Option **gespeichertes Zertifikat signieren** , und wählen Sie das Zertifikat aus der Liste bereitgestellt aus.  
  
26. Klicken Sie zum Signieren des Bereitstellungs Manifests auf **OK** . Das Dialogfeld Speichern unter wird angezeigt.  
  
27. Wechseln Sie im Dialogfeld **Speichern** unter in das Stammverzeichnis der Bereitstellung, und klicken Sie dann auf **Speichern**.  
  
28. Kopieren Sie alle Dateien im Bereitstellungs Verzeichnis auf das Bereitstellungs Ziel oder auf das Zielmedium. Hierbei kann es sich entweder um einen Ordner auf einer Website oder einer FTP-Website, eine Dateifreigabe oder eine CD-ROM handeln.  
  
29. Stellen Sie Ihren Benutzern die URL, das UNC-oder das physische Medium zur Verfügung, die für die Installation der Anwendung erforderlich sind. Wenn Sie eine URL oder einen UNC-Namen angeben, müssen Sie Ihren Benutzern den vollständigen Pfad zum Bereitstellungs Manifest erteilen. Wenn beispielsweise apptbereitstellung auf http://webserver01/ im Verzeichnis appto-Bereitstellung bereitgestellt wird, wird der vollständige URL-Pfad http://webserver01/AppToDeploy/AppToDeploy.application.  
  
## <a name="next-steps"></a>Nächste Schritte  
 Wenn Sie eine neue Version der Anwendung bereitstellen müssen, erstellen Sie ein neues Verzeichnis, das nach der neuen Version benannt ist – z. b. 1.0.0.1 –, und kopieren Sie die neuen Anwendungs Dateien in das neue Verzeichnis. Als nächstes müssen Sie die vorherigen Schritte ausführen, um ein neues Anwendungs Manifest zu erstellen und zu signieren und das Bereitstellungs Manifest zu aktualisieren und zu signieren. Achten Sie darauf, die gleiche höhere Version sowohl in der "Mage. exe"-`-New` als auch in `–Update` aufrufen anzugeben, da [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] nur höhere Versionen aktualisiert, wobei die ganz links größte Ganzzahl am signifikantesten ist. Wenn Sie "MageUI. exe" verwendet haben, können Sie das Bereitstellungs Manifest aktualisieren, indem Sie es öffnen, die Registerkarte " **Anwendungs Verweis** " auswählen, auf die Schaltfläche " **Manifest auswählen** " klicken und dann das aktualisierte Anwendungs Manifest auswählen.  
  
## <a name="see-also"></a>Siehe auch  
 [„Mage.exe“ (Tool zum Generieren und Bearbeiten von Manifesten)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (Tool zum Generieren und Bearbeiten von Manifesten, grafischer Client)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)   
 [Veröffentlichen von ClickOnce-Anwendungen](../deployment/publishing-clickonce-applications.md)   
 [ClickOnce-Bereitstellungs Manifest](../deployment/clickonce-deployment-manifest.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)

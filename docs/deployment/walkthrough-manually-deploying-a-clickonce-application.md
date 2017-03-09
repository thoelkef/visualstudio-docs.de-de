---
title: "Walkthrough: Manually Deploying a ClickOnce Application | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Mage.exe, manual ClickOnce deployments"
  - "MageUI.exe, manual ClickOnce deployments"
  - "deploying applications [ClickOnce], manual ClickOnce deployments"
  - "ClickOnce deployment, manually"
  - "ClickOnce deployment, SDK tools"
  - "manual ClickOnce deployments"
  - "manifests [ClickOnce]"
ms.assetid: ccee6551-a1b9-4ca2-8845-9c1cf4ac2560
caps.latest.revision: 49
caps.handback.revision: 47
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Walkthrough: Manually Deploying a ClickOnce Application
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung nicht mit Visual Studio bereitstellen können oder wenn Sie erweiterte Bereitstellungsfunktionen, z. B. die Bereitstellung vertrauenswürdiger Anwendungen, benötigen, sollten Sie zum Erstellen der [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Manifeste das Befehlszeilentool Mage.exe verwenden.  In dieser exemplarischen Vorgehensweise wird beschrieben, wie Sie eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellung mithilfe der Befehlszeilenversion \(Mage.exe\) oder der grafischen Version \(MageUI.exe\) des Tools zum Generieren und Bearbeiten von Manifesten erstellen.  
  
## Vorbereitungsmaßnahmen  
 In dieser exemplarischen Vorgehensweise müssen Sie erforderliche Komponenten und Optionen auswählen, bevor Sie eine Bereitstellung erstellen.  
  
-   Installieren Sie Mage.exe und MageUI.exe.  
  
     Mage.exe und MageUI.exe sind Teil des [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  Das [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] oder die Version des in Visual Studio enthaltenen [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] muss installiert sein.  Weitere Informationen finden Sie auf MSDN unter [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=158044).  
  
-   Geben Sie eine Anwendung an, die bereitgestellt werden soll.  
  
     In dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass Sie über eine Windows\-Anwendung verfügen, die bereitgestellt werden kann.  Diese Anwendung wird als AppToDeploy bezeichnet.  
  
-   Bestimmen Sie, wie die Bereitstellung verteilt wird.  
  
     Verteilungsoptionen sind Web, Dateifreigabe oder CD.  Weitere Informationen finden Sie unter [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md).  
  
-   Bestimmen Sie, ob die Anwendung eine höhere Vertrauensebene erfordert.  
  
     Wenn die Anwendung volle Vertrauenswürdigkeit, z. B. vollständigen Zugriff auf das System des Benutzers, erfordert, können Sie dies mit der `-TrustLevel`\-Option von Mage.exe festlegen.  Wenn Sie einen benutzerdefinierten Berechtigungssatz für die Anwendung definieren möchten, können Sie den Abschnitt mit der Internet\- oder Intranetberechtigung aus einem anderen Manifest kopieren, mit einem Text\-Editor oder MageUI.exe nach Bedarf bearbeiten und dem Anwendungsmanifest hinzufügen.   Weitere Informationen finden Sie unter [Überblick über die Bereitstellung vertrauenswürdiger Anwendungen](../deployment/trusted-application-deployment-overview.md).  
  
-   Rufen Sie ein Authenticode\-Zertifikat ab.  
  
     Signieren Sie die Bereitstellung mit einem Authenticode\-Zertifikat.  Sie können mit Visual Studio, MageUI.exe oder den Tools MakeCert.exe und Pvk2Pfx.exe ein Testzertifikat generieren oder ein Zertifikat von einer Zertifizierungsstelle abrufen.  Wenn Sie sich für die Bereitstellung vertrauenswürdiger Anwendungen entscheiden, müssen Sie das Zertifikat einmal auf allen Clientcomputern installieren.  Weitere Informationen finden Sie unter [Überblick über die Bereitstellung vertrauenswürdiger Anwendungen](../deployment/trusted-application-deployment-overview.md).  
  
-   Stellen Sie sicher, dass die Anwendung kein Manifest mit UAC\-Informationen aufweist.  
  
     Sie müssen bestimmen, ob die Anwendung ein Manifest mit UAC \(User Account Control\)\-Informationen, z. B. ein `<dependentAssembly>`\-Element, enthält.  Um ein Anwendungsmanifest zu untersuchen, können Sie das Windows Sysinternals\-Hilfsprogramm [Sigcheck](http://go.microsoft.com/fwlink/?LinkId=158035) verwenden.  
  
     Wenn die Anwendung ein Manifest mit UAC\-Informationen enthält, müssen Sie es ohne die UAC\-Informationen neu erstellen.  Öffnen Sie für ein C\#\-Projekt in Visual Studio die Projekteigenschaften, und wählen Sie die Registerkarte Anwendung aus.  Wählen Sie in der Dropdownliste **Manifest** die Option **Anwendung ohne Manifest erstellen** aus.  Öffnen Sie für ein Visual Basic\-Projekt in Visual Studio die Projekteigenschaften, wählen Sie die Registerkarte Anwendung aus, und klicken Sie auf **Einstellungen für die Benutzerkontensteuerung anzeigen**.  Entfernen Sie in der geöffneten Manifestdatei alle Elemente innerhalb des einzelnen `<asmv1:assembly>`\-Elements.  
  
-   Bestimmen Sie, ob für die Anwendung erforderliche Komponenten auf dem Clientcomputer vorhanden sein müssen.  
  
     Von Visual Studio bereitgestellte [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendungen können einen Bootstrapper für die Installation erforderlicher Komponenten \(setup.exe\) enthalten.  In dieser exemplarischen Vorgehensweise werden die beiden für eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellung erforderlichen Manifeste erstellt.  Sie können mit der [GenerateBootstrapper Task](../msbuild/generatebootstrapper-task.md) einen Bootstrapper für erforderliche Komponenten erstellen.  
  
### So stellen Sie eine Anwendung mit dem Befehlszeilentool Mage.exe bereit  
  
1.  Erstellen Sie ein Verzeichnis, in dem Sie die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellungsdateien speichern.  
  
2.  Erstellen Sie in dem Bereitstellungsverzeichnis, das Sie gerade erstellt haben, ein Versionsunterverzeichnis.  Wenn Sie die Anwendung zum ersten Mal bereitstellen, legen Sie für das Versionsunterverzeichnis den Namen 1.0.0.0 fest.  
  
    > [!NOTE]
    >  Die Version der Bereitstellung muss nicht unbedingt mit der Version der Anwendung identisch sein.  
  
3.  Kopieren Sie alle Anwendungsdateien, d. h. ausführbare Dateien, Assemblys, Ressourcen und Datendateien, in das Versionsunterverzeichnis.  Sie können ggf. zusätzliche Unterverzeichnisse erstellen, die weitere Dateien enthalten.  
  
4.  Öffnen Sie die [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)]\- oder Visual Studio\-Eingabeaufforderung, und wechseln Sie zum Versionsunterverzeichnis.  
  
5.  Erstellen Sie mit einem Aufruf von Mage.exe das Anwendungsmanifest.  Mit der folgenden Anweisung wird ein Anwendungsmanifest für Code erstellt, der für die Ausführung mit dem Intel\-x86\-Prozessor kompiliert wurde.  
  
    ```  
    mage -New Application -Processor x86 -ToFile AppToDeploy.exe.manifest -name "My App" -Version 1.0.0.0 -FromDirectory .   
    ```  
  
    > [!NOTE]
    >  Fügen Sie nach der `-FromDirectory`\-Option, die das aktuelle Verzeichnis angibt, unbedingt den Punkt \(.\) ein.  Wenn Sie den Punkt nicht einfügen, müssen Sie den Pfad der Anwendungsdateien angeben.  
  
6.  Signieren Sie das Anwendungsmanifest mit dem Authenticode\-Zertifikat.  Ersetzen Sie *mycert.pfx* durch den Pfad der Zertifikatdatei.  Ersetzen Sie *passwd* durch das Kennwort für die Zertifikatdatei.  
  
    ```  
    mage -Sign AppToDeploy.exe.manifest -CertFile mycert.pfx -Password passwd  
    ```  
  
7.  Wechseln Sie zum Stamm des Bereitstellungsverzeichnisses.  
  
8.  Generieren Sie das Bereitstellungsmanifest mit einem Aufruf von Mage.exe.  Mage.exe markiert die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellung standardmäßig als installierte Anwendung, sodass sie sowohl online als auch offline ausgeführt werden kann.  Wenn die Anwendung nur verfügbar sein soll, während der Benutzer online ist, verwenden Sie die `-Install`\-Option mit dem Wert `false`.  Bei Verwendung der Standardeinstellung, bei der Benutzer die Anwendung von einer Website oder Dateifreigabe installieren, muss der Wert der `-ProviderUrl`\-Option auf den Speicherort des Anwendungsmanifests auf dem Webserver bzw. der Freigabe verweisen.  
  
    ```  
    mage -New Deployment -Processor x86 -Install true -Publisher "My Co." -ProviderUrl "\\myServer\myShare\AppToDeploy.application" -AppManifest 1.0.0.0\AppToDeploy.exe.manifest -ToFile AppToDeploy.application  
    ```  
  
9. Signieren Sie das Bereitstellungsmanifest mit dem Authenticode\-Zertifikat.  
  
    ```  
    mage -Sign AppToDeploy.application -CertFile mycert.pfx -Password passwd  
    ```  
  
10. Kopieren Sie alle Dateien im Bereitstellungsverzeichnis in das Bereitstellungsziel oder auf das Bereitstellungsmedium.  Dabei kann es sich um einen Ordner auf einer Website oder FTP\-Site, eine Dateifreigabe oder eine CD\-ROM handeln.  
  
11. Geben Sie den Benutzern die URL oder einen UNC\-Pfad für die Anwendungsinstallation an, oder stellen Sie das physische Medium bereit.  Wenn Sie eine URL oder einen UNC\-Pfad angeben, müssen Sie den Benutzern den vollständigen Pfad zum Bereitstellungsmanifest mitteilen.  Wenn AppToDeploy z. B. unter http:\/\/webserver01\/ im Verzeichnis AppToDeploy bereitgestellt wird, lautet der vollständige URL\-Pfad http:\/\/webserver01\/AppToDeploy\/AppToDeploy.application.  
  
### So stellen Sie eine Anwendung mit dem grafischen Tool MageUI.exe bereit  
  
1.  Erstellen Sie ein Verzeichnis, in dem Sie die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellungsdateien speichern.  
  
2.  Erstellen Sie in dem Bereitstellungsverzeichnis, das Sie gerade erstellt haben, ein Versionsunterverzeichnis.  Wenn Sie die Anwendung zum ersten Mal bereitstellen, legen Sie für das Versionsunterverzeichnis den Namen 1.0.0.0 fest.  
  
    > [!NOTE]
    >  Die Version der Bereitstellung ist wahrscheinlich nicht mit der Version der Anwendung identisch.  
  
3.  Kopieren Sie alle Anwendungsdateien, d. h. ausführbare Dateien, Assemblys, Ressourcen und Datendateien, in das Versionsunterverzeichnis.  Sie können ggf. zusätzliche Unterverzeichnisse erstellen, die weitere Dateien enthalten.  
  
4.  Starten Sie das grafische Tool MageUI.exe.  
  
    ```  
    MageUI.exe  
    ```  
  
5.  Erstellen Sie ein neues Anwendungsmanifest, indem Sie im Menü **Datei** die Optionen **Neu** und **Anwendungsmanifest** auswählen.  
  
6.  Geben Sie auf der standardmäßig angezeigten Registerkarte **Name** den Namen und die Versionsnummer dieser Bereitstellung ein.  Geben Sie außerdem den **Prozessor** an, für den die Anwendung erstellt wurde, z. B. x86.  
  
7.  Wählen Sie die Registerkarte **Dateien** aus, und klicken Sie neben dem Textfeld **Anwendungsverzeichnis** auf die Schaltfläche mit den Auslassungszeichen \(**...**\).  Das Dialogfeld Ordner suchen wird angezeigt.  
  
8.  Wählen Sie das Versionsunterverzeichnis aus, das die Anwendungsdateien enthält, und klicken Sie dann auf **OK**.  
  
9. Wenn die Bereitstellung über Internetinformationsdienste \(IIS\) erfolgt, aktivieren Sie das Kontrollkästchen **Beim Füllen die Erweiterung ".deploy" zu allen Dateien ohne diese Erweiterung hinzufügen**.  
  
10. Klicken Sie auf die Schaltfläche **Auffüllen**, um alle Anwendungsdateien zur Dateiliste hinzuzufügen.  Wenn die Anwendung mehrere ausführbare Dateien enthält, markieren Sie die zentrale ausführbare Datei für diese Bereitstellung als Startanwendung. Wählen Sie dazu in der Dropdownliste **Dateityp** die Option **Einstiegspunkt** aus.  \(Wenn die Anwendung nur eine ausführbare Datei enthält, wird diese automatisch markiert.\)  
  
11. Wählen Sie die Registerkarte **Erforderliche Berechtigungen** aus, und wählen Sie dann die Vertrauensebene aus, die die Anwendung anfordern muss.  Die Standardeinstellung lautet **FullTrust**. Diese ist für die meisten Anwendungen geeignet.  
  
12. Wählen Sie im Menü **Datei** die Option **Speichern unter** aus.  Das Dialogfeld Signaturoptionen wird mit der Aufforderung angezeigt, das Anwendungsmanifest zu signieren.  
  
13. Wenn ein Zertifikat als Datei im Dateisystem gespeichert ist, verwenden Sie die Option **Mit Zertifikatsdatei signieren**, und wählen Sie mit der Schaltfläche mit den Auslassungszeichen \(**...**\) das Zertifikat im Dateisystem aus.  Geben Sie dann das Zertifikatkennwort ein.  
  
     \- oder \-  
  
     Wenn das Zertifikat in einem Zertifikatspeicher vorhanden ist, auf den Sie von Ihrem Computer aus zugreifen können, wählen Sie die Option **Mit gespeichertem Zertifikat signieren** aus, und wählen Sie dann das Zertifikat aus der Liste aus.  
  
14. Klicken Sie auf **OK**, um das Anwendungsmanifest zu signieren.  Das Dialogfeld Speichern unter wird angezeigt.  
  
15. Geben Sie im Dialogfeld Speichern unter das Versionsverzeichnis an, und klicken Sie dann auf **Speichern**.  
  
16. Wählen Sie im Menü **Datei**, **Neu**, **Bereitstellungsmanifest** aus, um das Bereitstellungsmanifest zu erstellen.  
  
17. Geben Sie auf der Registerkarte **Name** einen Namen und eine Versionsnummer für die Bereitstellung \(in diesem Beispiel 1.0.0.0\) an.  Geben Sie außerdem den **Prozessor** an, für den die Anwendung erstellt wurde, z. B. x86.  
  
18. Wählen Sie die Registerkarte **Beschreibung** aus, und geben Sie Werte für **Herausgeber** und **Produkt** an.  \(**Produkt** ist der im Windows\-Startmenü für die Anwendung angegebene Name, wenn die Anwendung auf einem Clientcomputer für die Offlineverwendung installiert wird.\)  
  
19. Wählen Sie die Registerkarte **Bereitstellungsoptionen** aus, und geben Sie im Textfeld **Startposition** den Speicherort des Anwendungsmanifests auf dem Webserver oder der Freigabe an.  Beispiel: \\\\myServer\\myShare\\AppToDeploy.application.  
  
20. Wenn Sie in einem vorherigen Schritt die Erweiterung .deploy hinzugefügt haben, wählen Sie jetzt außerdem **Dateinamenerweiterung ".deploy" verwenden** aus.  
  
21. Wählen Sie die Registerkarte **Aktualisierungsoptionen** aus, und geben Sie an, wie oft die Anwendung aktualisiert werden soll.  Wenn die Anwendung <xref:System.Deployment.Application.UpdateCheckInfo> verwendet, um selbst nach Updates zu suchen, deaktivieren Sie das Kontrollkästchen **Diese Anwendung soll nach Updates suchen**.  
  
22. Wählen Sie die Registerkarte **Anwendungsverweis** aus, und klicken Sie dann auf die Schaltfläche **Manifest auswählen**.  Das Dialogfeld Öffnen wird angezeigt.  
  
23. Wählen Sie das Anwendungsmanifest aus, das Sie zuvor erstellt haben, und klicken Sie dann auf **Öffnen**.  
  
24. Wählen Sie im Menü **Datei** die Option **Speichern unter** aus.  Das Dialogfeld Signaturoptionen wird mit der Aufforderung angezeigt, das Bereitstellungsmanifest zu signieren.  
  
25. Wenn ein Zertifikat als Datei im Dateisystem gespeichert ist, verwenden Sie die Option **Mit Zertifikatsdatei signieren**, und wählen Sie mit der Schaltfläche mit den Auslassungszeichen \(**...**\) das Zertifikat im Dateisystem aus.  Geben Sie dann das Zertifikatkennwort ein.  
  
     \- oder \-  
  
     Wenn das Zertifikat in einem Zertifikatspeicher vorhanden ist, auf den Sie von Ihrem Computer aus zugreifen können, wählen Sie die Option **Mit gespeichertem Zertifikat signieren** aus, und wählen Sie dann das Zertifikat aus der Liste aus.  
  
26. Klicken Sie auf **OK**, um das Bereitstellungsmanifest zu signieren.  Das Dialogfeld Speichern unter wird angezeigt.  
  
27. Wechseln Sie im Dialogfeld **Speichern unter** zum Stammverzeichnis der Bereitstellung, und klicken Sie auf **Speichern**.  
  
28. Kopieren Sie alle Dateien im Bereitstellungsverzeichnis in das Bereitstellungsziel oder auf das Bereitstellungsmedium.  Dabei kann es sich um einen Ordner auf einer Website oder FTP\-Site, eine Dateifreigabe oder eine CD\-ROM handeln.  
  
29. Geben Sie den Benutzern die URL oder einen UNC\-Pfad für die Anwendungsinstallation an, oder stellen Sie das physische Medium bereit.  Wenn Sie eine URL oder einen UNC\-Pfad angeben, müssen Sie den Benutzern den vollständigen Pfad zum Bereitstellungsmanifest mitteilen.  Wenn AppToDeploy z. B. unter http:\/\/webserver01\/ im Verzeichnis AppToDeploy bereitgestellt wird, lautet der vollständige URL\-Pfad http:\/\/webserver01\/AppToDeploy\/AppToDeploy.application.  
  
## Nächste Schritte  
 Um eine neue Version der Anwendung bereitzustellen, erstellen Sie ein neues Verzeichnis, dessen Name der neuen Version entspricht, z. B. 1.0.0.1, und kopieren Sie die neuen Anwendungsdateien in das neue Verzeichnis.  Danach müssen Sie die vorherigen Schritte ausführen, um ein neues Anwendungsmanifest zu erstellen und zu signieren, und das Bereitstellungsmanifest aktualisieren und signieren.  Sie müssen im `-New`\-Aufruf und im `–Update`\-Aufruf von Mage.exe die gleiche höhere Version angeben, da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nur höhere Versionen aktualisiert, wobei die äußerste linke ganze Zahl die höchste Signifikanz aufweist.  Wenn Sie MageUI.exe verwenden, können Sie das Bereitstellungsmanifest aktualisieren, indem Sie es öffnen, die Registerkarte **Anwendungsverweis** auswählen, auf die Schaltfläche **Manifest auswählen** klicken und dann das aktualisierte Anwendungsmanifest auswählen.  
  
## Siehe auch  
 [Mage.exe \(Tool zum Generieren und Bearbeiten von Manifesten\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)   
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [ClickOnce Deployment Manifest](../deployment/clickonce-deployment-manifest.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)
---
title: "Walkthrough: Manually Deploying a ClickOnce Application that Does Not Require Re-Signing and that Preserves Branding Information | Microsoft Docs"
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
  - "branding"
  - "preserved branding information"
  - "ClickOnce deployment, manually"
  - "multiple ClickOnce deployment and branding"
  - "ClickOnce deployment, SDK tools"
  - "customer deployments"
  - "manual ClickOnce deployments"
  - "manifests [ClickOnce]"
  - "ClickOnce applications, deployed by others"
ms.assetid: c21822fb-d4ee-42e4-b72d-41ee9786efe5
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Walkthrough: Manually Deploying a ClickOnce Application that Does Not Require Re-Signing and that Preserves Branding Information
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung erstellen und sie zur Veröffentlichung und Bereitstellung an einen Kunden weitergeben, musste der Kunde früher das Bereitstellungsmanifest aktualisieren und neu signieren. Auch wenn dies meistens noch die bevorzugte Vorgehensweise ist, können Sie mit .NET Framework 3.5 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellungen erstellen, die von Kunden eingesetzt werden können, ohne dass ein neues Bereitstellungsmanifest generiert werden muss.  Weitere Informationen finden Sie unter [Deploying ClickOnce Applications For Testing and Production Servers without Resigning](../deployment/deploying-clickonce-applications-for-testing-and-production-servers-without-resigning.md).  
  
 Wenn Sie eine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung erstellen und sie zur Veröffentlichung und Bereitstellung an einen Kunden weitergeben, kann die Anwendung die Brandinginformationen des Kunden verwenden oder Ihr Branding beibehalten.  Wenn die Anwendung z. B. eine einzelne proprietäre Anwendung ist, möchten Sie vielleicht Ihr Branding beibehalten.  Wenn die Anwendung für jeden Kunden speziell angepasst wird, können Sie das Branding des Kunden verwenden.  Mit .NET Framework 3.5 können Sie Ihr Branding sowie Ihre Herausgeberinformationen und Sicherheitssignatur beibehalten, wenn Sie eine Anwendung zur Bereitstellung an ein Unternehmen weitergeben.  Weitere Informationen finden Sie unter [Creating ClickOnce Applications for Others to Deploy](../deployment/creating-clickonce-applications-for-others-to-deploy.md).  
  
> [!NOTE]
>  In dieser exemplarischen Vorgehensweise erstellen Sie manuell Bereitstellungen, indem Sie das Befehlszeilentool Mage.exe oder das grafische Tool MageUI.exe verwenden.  Weitere Informationen zu manuellen Bereitstellungen finden Sie unter [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
## Vorbereitungsmaßnahmen  
 Zum Ausführen der Schritte in dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:  
  
-   Eine Windows Forms\-Anwendung, die bereitgestellt werden soll.  Diese Anwendung wird als WindowsFormsApp1 bezeichnet.  
  
-   Visual Studio oder das Windows SDK.  
  
### So stellen Sie eine ClickOnce\-Anwendung mit Unterstützung mehrerer Bereitstellungen und Brandings mithilfe von Mage.exe bereit  
  
1.  Öffnen Sie eine Visual Studio\-Eingabeaufforderung oder eine [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)]\-Eingabeaufforderung, und wechseln Sie in das Verzeichnis, in dem Sie die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Dateien speichern möchten.  
  
2.  Erstellen Sie ein Verzeichnis, das Sie nach der aktuellen Version der Bereitstellung benennen.  Wenn Sie die Anwendung zum ersten Mal bereitstellen, wählen Sie wahrscheinlich den Namen 1.0.0.0.  
  
    > [!NOTE]
    >  Die Version der Bereitstellung muss nicht unbedingt mit der Version der Anwendungsdateien identisch sein.  
  
3.  Erstellen Sie ein Unterverzeichnis mit dem Namen bin, und kopieren Sie alle Anwendungsdateien, d. h. ausführbare Dateien, Assemblys, Ressourcen und Datendateien, in dieses Verzeichnis.  
  
4.  Generieren Sie das Anwendungsmanifest mit einem Aufruf von Mage.exe.  
  
    ```  
    mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"  
    ```  
  
5.  Signieren Sie das Anwendungsmanifest mit dem digitalen Zertifikat.  
  
    ```  
    mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx  
    ```  
  
6.  Generieren Sie das Bereitstellungsmanifest mit einem Aufruf von Mage.exe.  Mage.exe markiert die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellung standardmäßig als installierte Anwendung, sodass sie sowohl online als auch offline ausgeführt werden kann.  Wenn die Anwendung nur verfügbar sein soll, während der Benutzer online ist, verwenden Sie das `-i`\-Argument mit dem Wert `f`.  Da diese Anwendung den Vorteil mehrerer Bereitstellungen nutzt, schließen Sie das `-providerUrl`\-Argument für Mage.exe aus.  \(Wenn Sie in .NET Framework\-Versionen vor 3.5 `-providerUrl` für eine Offlineanwendung ausschließen, tritt ein Fehler auf.\)  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest   
    ```  
  
7.  Signieren Sie das Bereitstellungsmanifest nicht.  
  
8.  Übergeben Sie alle Dateien an den Kunden, der die Anwendung in seinem Netzwerk bereitstellt.  
  
9. An diesem Punkt muss der Kunde das Bereitstellungsmanifest mit seinem eigenen selbst generierten Zertifikat signieren.  Wenn der Kunde beispielsweise für ein Unternehmen mit dem Namen Adventure Works arbeitet, kann er mithilfe des Tools MakeCert.exe ein selbst signiertes Zertifikat generieren.  Als Nächstes verwenden Sie das Tool Pvk2pfx.exe, um die mit MakeCert.exe erstellten Dateien in einer PFX\-Datei zu kombinieren, die an Mage.exe übergeben werden kann.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
10. Anschließend verwendet der Kunde dieses Zertifikat zum Signieren des Bereitstellungsmanifests.  
  
    ```  
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx  
    ```  
  
11. Der Kunde stellt die Anwendung für die jeweiligen Benutzer bereit.  
  
### So stellen Sie eine ClickOnce\-Anwendung mit Unterstützung mehrerer Bereitstellungen und Brandings mithilfe von MageUI.exe bereit  
  
1.  Öffnen Sie eine Visual Studio\-Eingabeaufforderung oder eine [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)]\-Eingabeaufforderung, und greifen Sie auf das Verzeichnis zu, in dem Sie die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Dateien speichern möchten.  
  
2.  Erstellen Sie ein Unterverzeichnis mit dem Namen bin, und kopieren Sie alle Anwendungsdateien, d. h. ausführbare Dateien, Assemblys, Ressourcen und Datendateien, in dieses Verzeichnis.  
  
3.  Erstellen Sie ein Unterverzeichnis, das Sie entsprechend der aktuellen Version der Bereitstellung benennen.  Wenn Sie die Anwendung zum ersten Mal bereitstellen, wählen Sie wahrscheinlich den Namen 1.0.0.0.  
  
    > [!NOTE]
    >  Die Version der Bereitstellung muss nicht unbedingt mit der Version der Anwendungsdateien identisch sein.  
  
4.  Verschieben Sie das Verzeichnis \\bin in das Verzeichnis, das Sie in Schritt 2 erstellt haben.  
  
5.  Starten Sie das grafische Tool MageUI.exe.  
  
    ```  
    MageUI.exe  
    ```  
  
6.  Erstellen Sie ein neues Anwendungsmanifest, indem Sie im Menü **Datei** die Optionen **Neu** und **Anwendungsmanifest** auswählen.  
  
7.  Geben Sie auf der standardmäßig angezeigten Registerkarte **Name** den Namen und die Versionsnummer dieser Bereitstellung ein.  Geben Sie außerdem einen Wert für **Herausgeber** an, der bei der Bereitstellung als Ordnername für die Anwendungsverknüpfung im Startmenü angezeigt wird.  
  
8.  Wählen Sie die Registerkarte **Anwendungsoptionen** aus, und klicken Sie auf **Anwendungsmanifest für Vertrauensstellungsinformationen verwenden**.  Dadurch wird die Verwendung des Brandings eines Drittanbieters für diese [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung ermöglicht.  
  
9. Wählen Sie die Registerkarte **Dateien** aus, und klicken Sie auf die Schaltfläche **Durchsuchen** neben dem Textfeld Anwendungsverzeichnis.  
  
10. Wählen Sie im Dialogfeld für die Ordnerauswahl das in Schritt 2 erstellte Verzeichnis mit den Anwendungsdateien aus, und klicken Sie auf **OK**.  
  
11. Klicken Sie auf die Schaltfläche **Auffüllen**, um alle Anwendungsdateien zur Dateiliste hinzuzufügen.  Wenn die Anwendung mehrere ausführbare Dateien enthält, markieren Sie die zentrale ausführbare Datei für diese Bereitstellung als Startanwendung. Wählen Sie dazu in der Dropdownliste **Dateityp** die Option **Einstiegspunkt** aus.  \(Wenn die Anwendung nur eine ausführbare Datei enthält, wird diese automatisch markiert.\)  
  
12. Wählen Sie die Registerkarte **Erforderliche Berechtigungen** aus, und wählen Sie dann die Vertrauensebene aus, die die Anwendung anfordern muss.  Die Standardeinstellung lautet **FullTrust**. Diese ist für die meisten Anwendungen geeignet.  
  
13. Wählen Sie im Menü **Datei** die Option **Speichern** aus, und speichern Sie das Anwendungsmanifest.  Beim Speichern werden Sie aufgefordert, das Anwendungsmanifest zu signieren.  
  
14. Wenn ein Zertifikat als Datei im Dateisystem gespeichert ist, verwenden Sie die Option **Als Zertifikatsdatei signieren**, und wählen Sie das Zertifikat über die Schaltfläche mit den drei Punkten \(**...**\) aus dem Dateisystem aus.  
  
     \- oder \-  
  
     Befindet sich das Zertifikat in einem Zertifikatsspeicher, auf den Sie von Ihrem Computer aus zugreifen können, wählen Sie die Option **Mit gespeichertem Zertifikat signieren** und dann das Zertifikat aus der Liste aus.  
  
15. Wählen Sie im Menü **Datei** nacheinander die Optionen **Neu** und **Bereitstellungsmanifest** aus, um das Bereitstellungsmanifest zu erstellen. Geben Sie dann auf der Registerkarte **Name** einen Namen und eine Versionsnummer an \(in diesem Beispiel 1.0.0.0\).  
  
16. Wechseln Sie zur Registerkarte **Aktualisieren**, und geben Sie an, wie oft diese Anwendung aktualisiert werden soll.  Wenn die Anwendung die API für die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellung verwendet, um selbst nach Updates zu suchen, deaktivieren Sie das Kontrollkästchen **Die Anwendung soll nach Updates suchen**.  
  
17. Wechseln Sie zur Registerkarte **Anwendungsverweis**.  Sie können alle Werte auf dieser Registerkarte automatisch einfügen, indem Sie auf die Schaltfläche **Manifest auswählen** klicken und das zuvor erstellte Anwendungsmanifest auswählen.  
  
18. Wählen Sie **Speichern** aus, und speichern Sie das Bereitstellungsmanifest auf dem Datenträger.  Beim Speichern werden Sie aufgefordert, das Anwendungsmanifest zu signieren.  Klicken Sie auf **Abbrechen**, um das Manifest zu speichern, ohne es zu signieren.  
  
19. Stellen Sie alle Anwendungsdateien für den Kunden bereit.  
  
20. An diesem Punkt muss der Kunde das Bereitstellungsmanifest mit seinem eigenen selbst generierten Zertifikat signieren.  Wenn der Kunde beispielsweise für ein Unternehmen mit dem Namen Adventure Works arbeitet, kann er mithilfe des Tools MakeCert.exe ein selbst signiertes Zertifikat generieren.  Als Nächstes verwenden Sie das Tool Pvk2pfx.exe, um die mit MakeCert.exe erstellten Dateien in einer PFX\-Datei zu kombinieren, die an MageUI.exe übergeben werden kann.  
  
    ```  
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer  
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx  
    ```  
  
21. Nachdem das Zertifikat generiert wurde, signiert der Kunde das Bereitstellungsmanifest, indem er es in MageUI.exe öffnet und dann speichert.  Wenn das Dialogfeld zur Signierung angezeigt wird, aktiviert der Kunde die Option **Als Zertifikatsdatei signieren** und wählt die auf dem Datenträger gespeicherte PFX\-Datei aus.  
  
22. Der Kunde stellt die Anwendung für die jeweiligen Benutzer bereit.  
  
## Nächste Schritte  
  
## Siehe auch  
 [Mage.exe \(Tool zum Generieren und Bearbeiten von Manifesten\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md)   
 [Makecert.exe \(Certificate Creation Tool\)](../Topic/Makecert.exe%20\(Certificate%20Creation%20Tool\).md)
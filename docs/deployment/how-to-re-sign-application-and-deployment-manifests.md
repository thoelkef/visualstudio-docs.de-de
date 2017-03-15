---
title: "How to: Re-sign Application and Deployment Manifests | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "Office applications, signing manifests"
  - "deploying applications [ClickOnce], signing manifests"
  - "deploying applications, signing manifests"
  - "ClickOnce deployment, signing manifests"
  - "Office development in Visual Studio, signing manifests"
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# How to: Re-sign Application and Deployment Manifests
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nachdem Sie im Anwendungsmanifest für Windows Forms\-Anwendungen, Windows Presentation Foundation\-Anwendungen \(.xbap\) oder Office\-Projektmappen Bereitstellungseigenschaften geändert haben, müssen Sie das Anwendungsmanifest und das Bereitstellungsmanifest erneut mit einem Zertifikat signieren.  So können Sie sicherstellen, dass auf Endbenutzercomputern keine manipulierten Dateien installiert werden.  
  
 Manifeste müssen möglicherweise auch erneut signiert werden, wenn die Kunden das Anwendungs\- und Bereitstellungsmanifest mit einem eigenen Zertifikat signieren möchten.  
  
## Erneute Signierung von Anwendungs\- und Bereitstellungsmanifesten  
 In diesem Verfahren wird angenommen, dass Sie bereits Änderungen an der Anwendungsmanifestdatei \(.manifest\) vorgenommen haben.  Weitere Informationen finden Sie unter [Gewusst wie: Ändern von Bereitstellungseigenschaften](http://msdn.microsoft.com/de-de/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### So signieren Sie die Anwendungs\- und Bereitstellungsmanifeste mit Mage.exe erneut  
  
1.  Öffnen Sie das Fenster **Visual Studio\-Eingabeaufforderung \(2010\)**.  
  
2.  Wechseln Sie in den Ordner, der die zu signierenden Manifestdateien enthält.  
  
3.  Geben Sie den folgenden Befehl ein, um die Anwendungsmanifestdatei zu signieren.  Ersetzen Sie ManifestFileName durch den Namen Ihrer Manifestdatei und die Erweiterung.  Ersetzen Sie Certificate durch den relativen oder vollqualifizierten Pfad der Zertifikatsdatei, und ersetzen Sie Password durch das Kennwort für das Zertifikat.  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Sie können z. B. den folgenden Befehl ausführen, um ein Anwendungsmanifest für ein Add\-In, eine Windows Forms\-Anwendung oder eine Windows Presentation Foundation\-Browseranwendung zu signieren.  Von Visual Studio erstellte temporäre Zertifikate werden nicht für die Bereitstellung in Produktionsumgebungen empfohlen.  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4.  Geben Sie den folgenden Befehl ein, um eine Bereitstellungsmanifestdatei zu aktualisieren und zu signieren. Ersetzen Sie dabei die Platzhalternamen wie im vorigen Schritt.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Sie können z. B. den folgenden Befehl ausführen, um ein Bereitstellungsmanifest für ein Excel\-Add\-In, eine Windows Forms\-Anwendung oder eine Windows Presentation Foundation\-Browseranwendung zu aktualisieren und zu signieren.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Optional können Sie das Masterbereitstellungsmanifest \(publish\\*Anwendungsname*.application\) in das Bereitstellungsverzeichnis für Ihre Version \(publish\\Application Files\\*Anwendungsname*\_*Version*\) kopieren.  
  
## Aktualisieren und erneutes Signieren von Anwendungs\- und Bereitstellungsmanifesten  
 Bei dieser Prozedur wird davon ausgegangen, dass Sie bereits Änderungen an der Anwendungsmanifestdatei \(MANIFEST\-Format\) vorgenommen haben, aber andere Dateien aktualisiert wurden.  Wenn Dateien aktualisiert werden, muss der die Datei darstellende Hash ebenfalls aktualisiert werden.  
  
#### So aktualisieren und signieren Sie die Anwendungs\- und Bereitstellungsmanifeste mit "Mage.exe" erneut  
  
1.  Öffnen Sie das Fenster **Visual Studio\-Eingabeaufforderung \(2010\)**.  
  
2.  Wechseln Sie in den Ordner, der die zu signierenden Manifestdateien enthält.  
  
3.  Entfernen Sie die DEPLOY\-Dateierweiterung aus den Dateien im Ausgabeordner für die Veröffentlichung.  
  
4.  Geben Sie den folgenden Befehl ein, um das Anwendungsmanifest mit den neuen Hashs für die aktualisierten Dateien zu aktualisieren und die Anwendungsmanifestdatei zu signieren.  Ersetzen Sie ManifestFileName durch den Namen Ihrer Manifestdatei und die Erweiterung.  Ersetzen Sie Certificate durch den relativen oder vollqualifizierten Pfad der Zertifikatsdatei, und ersetzen Sie Password durch das Kennwort für das Zertifikat.  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Sie können z. B. den folgenden Befehl ausführen, um ein Anwendungsmanifest für ein Add\-In, eine Windows Forms\-Anwendung oder eine Windows Presentation Foundation\-Browseranwendung zu signieren.  Von Visual Studio erstellte temporäre Zertifikate werden nicht für die Bereitstellung in Produktionsumgebungen empfohlen.  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Geben Sie den folgenden Befehl ein, um eine Bereitstellungsmanifestdatei zu aktualisieren und zu signieren. Ersetzen Sie dabei die Platzhalternamen wie im vorigen Schritt.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Sie können z. B. den folgenden Befehl ausführen, um ein Bereitstellungsmanifest für ein Excel\-Add\-In, eine Windows Forms\-Anwendung oder eine Windows Presentation Foundation\-Browseranwendung zu aktualisieren und zu signieren.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6.  Fügen Sie den Dateien, außer den Anwendungs\- und Bereitstellungsmanifestdateien, die DEPLOY\-Dateierweiterung wieder hinzu.  
  
7.  Optional können Sie das Masterbereitstellungsmanifest \(publish\\*Anwendungsname*.application\) in das Bereitstellungsverzeichnis für Ihre Version \(publish\\Application Files\\*Anwendungsname*\_*Version*\) kopieren.  
  
## Siehe auch  
 [Sichern von ClickOnce\-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Codezugriffssicherheit für ClickOnce\-Anwendungen](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce und Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Überblick über die Bereitstellung vertrauenswürdiger Anwendungen](../deployment/trusted-application-deployment-overview.md)   
 [How to: Enable ClickOnce Security Settings](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Gewusst wie: Festlegen einer Sicherheitszone für eine ClickOnce\-Anwendung](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Gewusst wie: Festlegen benutzerdefinierter Berechtigungen für eine ClickOnce\-Anwendung](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Gewusst wie: Debuggen einer ClickOnce\-Anwendung mit eingeschränkten Berechtigungen](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Gewusst wie: Hinzufügen eines vertrauenswürdigen Herausgebers zu einem Clientcomputer für ClickOnce\-Anwendungen](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [How to: Configure the ClickOnce Trust Prompt Behavior](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)
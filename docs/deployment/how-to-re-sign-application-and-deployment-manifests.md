---
title: 'Vorgehensweise: Erneutes Signieren von Anwendungs- und Bereitstellungsmanifeste | Microsoft Docs'
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
- Office applications, signing manifests
- deploying applications [ClickOnce], signing manifests
- deploying applications, signing manifests
- ClickOnce deployment, signing manifests
- Office development in Visual Studio, signing manifests
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
caps.latest.revision: "17"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: baa3e9310946482a4c7c64fdb619ce612a21dbda
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Gewusst wie: Erneutes Signieren von Anwendungs- und Bereitstellungsmanifesten
Nachdem Sie die Bereitstellungseigenschaften in das Anwendungsmanifest für Windows Forms-Anwendungen, Windows Presentation Foundation-Anwendungen (Xbap) und Office-Projektmappen ändern, müssen Sie sowohl die Anwendung erneut anmelden und die Bereitstellungsmanifeste mit einem Zertifikat. Dieser Prozess trägt dazu bei, dass manipulierte Dateien nicht auf Endbenutzercomputern installiert sind.  
  
 Ein weiteres Szenario, in dem Sie das Manifest neu signieren können, ist, wenn Ihre Kunden zum Signieren der Anwendung und die Bereitstellungsmanifeste mit einem eigenen Zertifikat.  
  
## <a name="re-signing-the-application-and-deployment-manifests"></a>Erneut signieren der Anwendung und die Bereitstellung von Manifesten  
 Dieses Verfahren setzt voraus, dass Sie bereits in die Anwendungsmanifestdatei (Manifest) geändert haben. Weitere Informationen finden Sie unter [Vorgehensweise: Ändern von Bereitstellungseigenschaften](http://msdn.microsoft.com/en-us/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Um erneut signieren Sie die Anwendungs- und Bereitstellungsmanifeste mit Mage.exe  
  
1.  Öffnen einer **Visual Studio-Eingabeaufforderung** Fenster.  
  
2.  Wechseln Sie zu dem Ordner, der die Manifestdateien jedoch enthält, die sich anmelden möchten.  
  
3.  Geben Sie den folgenden Befehl aus, um die Anwendungsmanifestdatei zu signieren. Ersetzen Sie ManifestFileName durch den Namen der Manifestdatei sowie die Erweiterung. Ersetzen des Zertifikats mit dem relativen oder einen vollqualifizierten Pfad der Zertifikatsdatei, und Ersetzen von Kennwort mit dem Kennwort für das Zertifikat.  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Beispielsweise können Sie den folgenden Befehl zum Signieren von einem Anwendungsmanifest für ein Add-in, eine Windows Forms-Anwendung oder eine Windows Presentation Foundation-Browseranwendung ausführen. Temporäre Zertifikate, die von Visual Studio erstellt werden für die Bereitstellung in produktionsumgebungen nicht empfohlen.  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4.  Geben Sie den folgenden Befehl zum Aktualisieren und Signieren die Bereitstellungsmanifestdatei, ersetzen die Platzhalternamen wie im vorherigen Schritt.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Beispielsweise können Sie den folgenden Befehl zum Aktualisieren und Signieren ein Bereitstellungsmanifest für eine Excel-add-in, Windows Forms-Anwendung oder eine Windows Presentation Foundation-Browseranwendung ausführen.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Optional, kopieren Sie die master Bereitstellungsmanifest (Veröffentlichen\\*Appname*.application) in Ihre Version Bereitstellungsverzeichnis (Publish\Application Dateien\\*Appname*_ *Version*).  
  
## <a name="updating-and-re-signing-the-application-and-deployment-manifests"></a>Aktualisieren und erneutes Signieren von Anwendungs- und Bereitstellungsmanifeste  
 Dieses Verfahren setzt voraus, dass Sie Änderungen an Ihrer Anwendung, die Manifestdatei (Manifest) bereits vorgenommen haben, aber es gibt noch andere Dateien, die aktualisiert wurden. Wenn Dateien aktualisiert werden, muss auch der Hash, der die Datei darstellt, die aktualisiert werden.  
  
#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Signieren Sie die Anwendung und die Bereitstellung erneut und aktualisieren Sie Manifeste mit Mage.exe  
  
1.  Öffnen einer **Visual Studio-Eingabeaufforderung** Fenster.  
  
2.  Wechseln Sie zu dem Ordner, der die Manifestdateien jedoch enthält, die sich anmelden möchten.  
  
3.  Entfernen Sie die Erweiterung ".deploy" aus den Dateien im Ausgabeordner veröffentlichen.  
  
4.  Geben Sie den folgenden Befehl zum Aktualisieren des Anwendungsmanifests mit den neuen Hashs für die aktualisierten Dateien und Signieren die Manifestdatei der Anwendung. Ersetzen Sie ManifestFileName durch den Namen der Manifestdatei sowie die Erweiterung. Ersetzen des Zertifikats mit dem relativen oder einen vollqualifizierten Pfad der Zertifikatsdatei, und Ersetzen von Kennwort mit dem Kennwort für das Zertifikat.  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Beispielsweise können Sie den folgenden Befehl zum Signieren von einem Anwendungsmanifest für ein Add-in, eine Windows Forms-Anwendung oder eine Windows Presentation Foundation-Browseranwendung ausführen. Temporäre Zertifikate, die von Visual Studio erstellt werden für die Bereitstellung in produktionsumgebungen nicht empfohlen.  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Geben Sie den folgenden Befehl zum Aktualisieren und Signieren die Bereitstellungsmanifestdatei, ersetzen die Platzhalternamen wie im vorherigen Schritt.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Beispielsweise können Sie den folgenden Befehl zum Aktualisieren und Signieren ein Bereitstellungsmanifest für eine Excel-add-in, Windows Forms-Anwendung oder eine Windows Presentation Foundation-Browseranwendung ausführen.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6.  Fügen Sie die Erweiterung ".deploy" wieder auf die Dateien, außer die Anwendung und die Bereitstellung laufwerkmanifestdateien.  
  
7.  Optional, kopieren Sie die master Bereitstellungsmanifest (Veröffentlichen\\*Appname*.application) in Ihre Version Bereitstellungsverzeichnis (Publish\Application Dateien\\*Appname*_ *Version*).  
  
## <a name="see-also"></a>Siehe auch  
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Codezugriffssicherheit für ClickOnce-Anwendungen](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce und Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Überblick über die Bereitstellung vertrauenswürdiger Anwendungen](../deployment/trusted-application-deployment-overview.md)   
 [Vorgehensweise: Aktivieren von ClickOnce-Sicherheitseinstellungen](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Vorgehensweise: Festlegen einer Sicherheitszone für eine ClickOnce-Anwendung](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [How to: Set Custom Permissions for a ClickOnce Application](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Vorgehensweise: Debuggen eine ClickOnce-Anwendung mit eingeschränkten Berechtigungen](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Vorgehensweise: Hinzufügen eines vertrauenswürdigen Herausgebers auf einen Clientcomputer für ClickOnce-Anwendungen](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Gewusst wie: Konfigurieren des Verhaltens der ClickOnce-Eingabeaufforderung zur Vertrauenswürdigkeit](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)
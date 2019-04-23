---
title: 'Vorgehensweise: Erneutes Signieren von Anwendungs- und Bereitstellungsmanifesten | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e934832f20ea7ab11484cdeb345f989aa842e06d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60097016"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Vorgehensweise: Erneutes Signieren von Anwendungs- und Bereitstellungsmanifesten
Nachdem Sie Änderungen an Eigenschaften in das Anwendungsmanifest für Windows Forms-Anwendungen, Windows Presentation Foundation-Anwendungen (Xbap) und Office-Projektmappen vornehmen, müssen Sie die Anwendung neu signieren und die Bereitstellungsmanifeste mit einem das Zertifikat. Durch diesen Prozess können Sie sicherstellen, dass manipulierte Dateien nicht auf den Computern von Endbenutzern installiert werden.

 Ein weiteres Szenario, in dem Sie das Manifest neu signieren können, ist, wenn Ihre Kunden, zum Signieren der Anwendung wünschen und die Bereitstellungsmanifeste mit einem eigenen Zertifikat.

## <a name="re-sign-the-application-and-deployment-manifests"></a>Erneutes Signieren der Anwendungs- und Bereitstellungsmanifeste
 Dieses Verfahren setzt voraus, dass Sie bereits Ihre Datei für das Anwendungsmanifest geändert haben (*". manifest"*). Weitere Informationen finden Sie unter [Vorgehensweise: Ändern Sie Bereitstellungseigenschaften](https://msdn.microsoft.com/library/66052a3a-8127-4964-8147-2477ef5d1472).

#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Um erneut signieren Sie die Anwendungs- und Bereitstellungsmanifeste mit Mage.exe

1. Öffnen einer **Visual Studio-Eingabeaufforderung** Fenster.

2. Wechseln Sie zu dem Ordner, der die Manifesten-Dateien enthält, die Sie signieren möchten.

3. Geben Sie den folgenden Befehl aus, um die Manifestdatei der Anwendung anmelden. Ersetzen Sie dies *ManifestFileName* durch den Namen der Manifestdatei mit der Erweiterung. Ersetzen Sie dies *Zertifikat* durch den relativen oder vollqualifizierten Pfad der Zertifikatdatei und Ersetzen *Kennwort* durch das Kennwort für das Zertifikat.

    ```cmd
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     Beispielsweise können Sie den folgenden Befehl zum Signieren von einem Anwendungsmanifest für ein Add-in, eine Windows Forms-Anwendung oder einer Windows Presentation Foundation-Browseranwendung ausführen. Temporäre Zertifikate, die von Visual Studio erstellt werden für die Bereitstellung in produktionsumgebungen nicht empfohlen.

    ```cmd
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

4. Geben Sie den folgenden Befehl zum Aktualisieren und Signieren die Datei mit dem Bereitstellungsmanifest, und Ersetzen Sie dabei die Platzhalternamen wie im vorherigen Schritt.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     Beispielsweise können Sie den folgenden Befehl zum Aktualisieren, und melden Sie ein Bereitstellungsmanifest für ein Excel-add-in, einer Windows Forms-Anwendung oder einer Windows Presentation Foundation-Browseranwendung ausführen.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. Optional, kopieren Sie das Bereitstellungsmanifest für die master (*veröffentlichen\\\<Appname > .application*) in Ihrer Version Bereitstellungsverzeichnis (*Publish\Application Dateien\\ \<Appname > _\<Version >*).

## <a name="update-and-re-sign-the-application-and-deployment-manifests"></a>Aktualisieren und erneut signieren der Anwendungs- und Bereitstellungsmanifesten
 Dieses Verfahren setzt voraus, dass Sie bereits Ihre Datei für das Anwendungsmanifest geändert haben (*". manifest"*), aber es gibt noch andere Dateien, die aktualisiert wurden. Bei der Dateien aktualisiert werden, muss auch der Hash, der die Datei repräsentiert aktualisiert werden.

#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Zum Aktualisieren und erneut signieren, die Anwendungs- und Bereitstellungsmanifeste mit Mage.exe

1. Öffnen einer **Visual Studio-Eingabeaufforderung** Fenster.

2. Wechseln Sie zu dem Ordner, der die Manifesten-Dateien enthält, die Sie signieren möchten.

3. Entfernen Sie die *".deploy"* Dateierweiterung aus den Dateien bei der Veröffentlichung Ausgabeordner.

4. Geben Sie den folgenden Befehl zum Aktualisieren das Anwendungsmanifest mit den neuen Hashes für die aktualisierten Dateien und die Manifestdatei der Anwendung anmelden. Ersetzen Sie dies *ManifestFileName* durch den Namen der Manifestdatei mit der Erweiterung. Ersetzen Sie dies *Zertifikat* durch den relativen oder vollqualifizierten Pfad der Zertifikatdatei und Ersetzen *Kennwort* durch das Kennwort für das Zertifikat.

    ```cmd
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     Beispielsweise können Sie den folgenden Befehl zum Signieren von einem Anwendungsmanifest für ein Add-in, eine Windows Forms-Anwendung oder einer Windows Presentation Foundation-Browseranwendung ausführen. Temporäre Zertifikate, die von Visual Studio erstellt werden für die Bereitstellung in produktionsumgebungen nicht empfohlen.

    ```cmd
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. Geben Sie den folgenden Befehl zum Aktualisieren und Signieren die Datei mit dem Bereitstellungsmanifest, und Ersetzen Sie dabei die Platzhalternamen wie im vorherigen Schritt.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     Beispielsweise können Sie den folgenden Befehl zum Aktualisieren, und melden Sie ein Bereitstellungsmanifest für ein Excel-add-in, einer Windows Forms-Anwendung oder einer Windows Presentation Foundation-Browseranwendung ausführen.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

6. Hinzufügen der *".deploy"* Dateierweiterung an den Dateien, mit der Ausnahme von Dateien die Anwendungs- und Bereitstellungsmanifesten.

7. Optional, kopieren Sie das Bereitstellungsmanifest für die master (*veröffentlichen\\\<Appname > .application*) in Ihrer Version Bereitstellungsverzeichnis (*Publish\Application Dateien\\ \<Appname > _\<Version >*).

## <a name="see-also"></a>Siehe auch
- [Secure ClickOnce applications (Sichern von ClickOnce-Anwendungen)](../deployment/securing-clickonce-applications.md)
- [Codezugriffssicherheit für ClickOnce-Anwendungen](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce und Authenticode](../deployment/clickonce-and-authenticode.md)
- [Trusted application deployment overview (Überblick: Bereitstellen vertrauenswürdiger Anwendungen)](../deployment/trusted-application-deployment-overview.md)
- [Vorgehensweise: ClickOnce-Sicherheitseinstellungen aktivieren](../deployment/how-to-enable-clickonce-security-settings.md)
- [Vorgehensweise: Festlegen einer Sicherheitszone für eine ClickOnce-Anwendung](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Vorgehensweise: Festlegen Sie benutzerdefinierter Berechtigungen für eine ClickOnce-Anwendung](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Vorgehensweise: Debuggen einer ClickOnce-Anwendung mit eingeschränkten Berechtigungen](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)
- [Vorgehensweise: Hinzufügen eines vertrauenswürdigen Herausgebers auf einen Clientcomputer für ClickOnce-Anwendungen](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Vorgehensweise: Konfigurieren des Verhaltens der ClickOnce-Eingabeaufforderung zur Vertrauenswürdigkeit](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)
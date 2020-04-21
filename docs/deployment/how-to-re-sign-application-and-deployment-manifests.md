---
title: 'Gewusst wie: Erneutes Signieren von Anwendungs- und Bereitstellungsmanifesten | Microsoft Docs'
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
ms.openlocfilehash: fc69ce1f79644d7f4b35fbb1c1e3a41691761390
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649187"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Vorgehensweise: Erneutes Signieren von Anwendungs- und Bereitstellungsmanifesten
Nachdem Sie Änderungen an Bereitstellungseigenschaften im Anwendungsmanifest für Windows Forms-Anwendungen, Windows Presentation Foundation-Anwendungen (xbap) oder Office-Lösungen vorgenommen haben, müssen Sie sowohl das Anwendungs- als auch das Bereitstellungsmanifest mit einem Zertifikat neu signieren. Durch diesen Prozess können Sie sicherstellen, dass manipulierte Dateien nicht auf den Computern von Endbenutzern installiert werden.

 Ein weiteres Szenario, in dem Sie die Manifeste erneut signieren können, ist, wenn Ihre Kunden die Anwendung und Bereitstellungsmanifeste mit ihrem eigenen Zertifikat signieren möchten.

## <a name="re-sign-the-application-and-deployment-manifests"></a>Erneutes Signieren der Anwendungs- und Bereitstellungsmanifeste
 Bei diesem Verfahren wird davon ausgegangen, dass Sie bereits Änderungen an der Anwendungsmanifestdatei (*.manifest*) vorgenommen haben. Weitere Informationen finden Sie unter [Gewusst wie: Ändern von Bereitstellungseigenschaften](https://msdn.microsoft.com/library/66052a3a-8127-4964-8147-2477ef5d1472).

#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>So signieren Sie die Anwendungs- und Bereitstellungsmanifeste erneut mit Mage.exe

1. Öffnen Sie ein **Visual Studio-Eingabeaufforderungsfenster.**

2. Ändern Sie Verzeichnisse in den Ordner, der die Manifestdateien enthält, die Sie signieren möchten.

3. Geben Sie den folgenden Befehl ein, um die Anwendungsmanifestdatei zu signieren. Ersetzen Sie *ManifestFileName* durch den Namen Der Manifestdatei plus die Erweiterung. Ersetzen Sie *Zertifikat* durch den relativen oder vollqualifizierten Pfad der Zertifikatdatei, und ersetzen Sie *Kennwort* durch das Kennwort für das Zertifikat.

    ```cmd
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     Sie können z. B. den folgenden Befehl ausführen, um ein Anwendungsmanifest für ein Add-In, eine Windows Form-Anwendung oder eine Windows Presentation Foundation-Browseranwendung zu signieren. Von Visual Studio erstellte temporäre Zertifikate werden für die Bereitstellung in Produktionsumgebungen nicht empfohlen.

    ```cmd
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

4. Geben Sie den folgenden Befehl ein, um die Bereitstellungsmanifestdatei zu aktualisieren und zu signieren, und ersetzen Sie die Platzhalternamen wie im vorherigen Schritt.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     Sie können z. B. den folgenden Befehl ausführen, um ein Bereitstellungsmanifest für ein Excel-Add-In, eine Windows Forms-Anwendung oder eine Windows Presentation Foundation-Browseranwendung zu aktualisieren und zu signieren.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. Kopieren Sie optional das Masterbereitstellungsmanifest (*Appname\\\<>.application veröffentlichen*) in Ihr Versionsbereitstellungsverzeichnis (*Appname\\\<\<>_ Version>veröffentlichen. *

## <a name="update-and-re-sign-the-application-and-deployment-manifests"></a>Aktualisieren und erneutes Signieren der Anwendungs- und Bereitstellungsmanifeste
 Bei diesem Verfahren wird davon ausgegangen, dass Sie bereits Änderungen an der Anwendungsmanifestdatei (*.manifest*) vorgenommen haben, dass jedoch andere Dateien aktualisiert wurden. Wenn Dateien aktualisiert werden, muss auch der Hash, der die Datei darstellt, aktualisiert werden.

#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>So aktualisieren und signieren Sie die Anwendungs- und Bereitstellungsmanifeste mit Mage.exe

1. Öffnen Sie ein **Visual Studio-Eingabeaufforderungsfenster.**

2. Ändern Sie Verzeichnisse in den Ordner, der die Manifestdateien enthält, die Sie signieren möchten.

3. Entfernen Sie die *Dateierweiterung .deploy* aus den Dateien im Veröffentlichungsausgabeordner.

4. Geben Sie den folgenden Befehl ein, um das Anwendungsmanifest mit den neuen Hashes für die aktualisierten Dateien zu aktualisieren und die Anwendungsmanifestdatei zu signieren. Ersetzen Sie *ManifestFileName* durch den Namen Der Manifestdatei plus die Erweiterung. Ersetzen Sie *Zertifikat* durch den relativen oder vollqualifizierten Pfad der Zertifikatdatei, und ersetzen Sie *Kennwort* durch das Kennwort für das Zertifikat.

    ```cmd
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     Sie können z. B. den folgenden Befehl ausführen, um ein Anwendungsmanifest für ein Add-In, eine Windows Form-Anwendung oder eine Windows Presentation Foundation-Browseranwendung zu signieren. Von Visual Studio erstellte temporäre Zertifikate werden für die Bereitstellung in Produktionsumgebungen nicht empfohlen.

    ```cmd
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. Geben Sie den folgenden Befehl ein, um die Bereitstellungsmanifestdatei zu aktualisieren und zu signieren, und ersetzen Sie die Platzhalternamen wie im vorherigen Schritt.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     Sie können z. B. den folgenden Befehl ausführen, um ein Bereitstellungsmanifest für ein Excel-Add-In, eine Windows Forms-Anwendung oder eine Windows Presentation Foundation-Browseranwendung zu aktualisieren und zu signieren.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

6. Fügen Sie die *Dateierweiterung .deploy* wieder zu den Dateien hinzu, mit Ausnahme der Anwendungs- und Bereitstellungsmanifestdateien.

7. Kopieren Sie optional das Masterbereitstellungsmanifest (*Appname\\\<>.application veröffentlichen*) in Ihr Versionsbereitstellungsverzeichnis (*Appname\\\<\<>_ Version>veröffentlichen. *

## <a name="see-also"></a>Siehe auch
- [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)
- [Codezugriffssicherheit für ClickOnce-Anwendungen](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce und Authenticode](../deployment/clickonce-and-authenticode.md)
- [Übersicht über das Bereitstellen vertrauenswürdiger Anwendungen](../deployment/trusted-application-deployment-overview.md)
- [Vorgehensweise: Aktivieren von ClickOnce-Sicherheitseinstellungen](../deployment/how-to-enable-clickonce-security-settings.md)
- [Gewusst wie: Festlegen einer Sicherheitszone für eine ClickOnce-Anwendung](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Vorgehensweise: Festlegen von benutzerdefinierten Berechtigungen für eine ClickOnce-Anwendung](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Gewusst wie: Debuggen einer ClickOnce-Anwendung mit eingeschränkten Berechtigungen](securing-clickonce-applications.md)
- [Vorgehensweise: Hinzufügen eines vertrauenswürdigen Herausgebers zu einem Clientcomputer für ClickOnce-Anwendungen](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Gewusst wie: Konfigurieren des ClickOnce-Vertrauensaufforderungsverhaltens](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)
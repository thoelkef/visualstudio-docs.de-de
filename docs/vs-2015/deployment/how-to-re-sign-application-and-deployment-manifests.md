---
title: 'Vorgehensweise: Erneutes Signieren von Anwendungs-und Bereitstellungs Manifesten | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d5956ad23fe22c7c36b712fac61df268586142df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697559"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Gewusst wie: Erneutes Signieren von Anwendungs- und Bereitstellungsmanifesten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nachdem Sie im Anwendungs Manifest Änderungen an den Bereitstellungs Eigenschaften für Windows Forms Anwendungen, Windows Presentation Foundation Anwendungen (XBAP) oder Office-Projektmappen vorgenommen haben, müssen Sie sowohl die Anwendungs-als auch die Bereitstellungs Manifeste mit einem Zertifikat signieren. Durch diesen Prozess können Sie sicherstellen, dass manipulierte Dateien nicht auf den Computern von Endbenutzern installiert werden.  
  
 Ein weiteres Szenario, in dem Sie die Manifeste neu signieren können, ist, wenn Ihre Kunden die Anwendungs-und Bereitstellungs Manifeste mit Ihrem eigenen Zertifikat signieren möchten.  
  
## <a name="re-signing-the-application-and-deployment-manifests"></a>Erneutes Signieren der Anwendungs-und Bereitstellungs Manifeste  
 Bei diesem Verfahren wird davon ausgegangen, dass Sie bereits Änderungen an der Anwendungs Manifest-Datei (. manifest) vorgenommen haben. Weitere Informationen finden Sie unter Vorgehens [Weise: Ändern von Bereitstellungs Eigenschaften](https://msdn.microsoft.com/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Zum erneuten Signieren der Anwendung und der Bereitstellungs Manifeste mit Mage.exe  
  
1. Öffnen Sie ein **Visual Studio-Eingabe** Aufforderungs Fenster.  
  
2. Wechseln Sie in den Ordner, der die Manifest-Dateien enthält, die Sie signieren möchten.  
  
3. Geben Sie den folgenden Befehl ein, um die Anwendungs Manifest-Datei zu signieren Ersetzen Sie ManifestFileName durch den Namen der Manifestressource zuzüglich der Erweiterung. Ersetzen Sie Certificate durch den relativen oder voll qualifizierten Pfad der Zertifikatsdatei, und ersetzen Sie Password durch das Kennwort für das Zertifikat.  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Beispielsweise können Sie den folgenden Befehl ausführen, um ein Anwendungs Manifest für ein Add-in, eine Windows Form-Anwendung oder eine Windows Presentation Foundation Browser-Anwendung zu signieren. Temporäre Zertifikate, die von Visual Studio erstellt werden, werden nicht für die Bereitstellung in Produktionsumgebungen empfohlen.  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4. Geben Sie den folgenden Befehl ein, um die Bereitstellungs Manifest-Datei zu aktualisieren und zu signieren. ersetzen Sie dabei die Platzhalter Namen wie im vorherigen Schritt.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Beispielsweise können Sie den folgenden Befehl ausführen, um ein Bereitstellungs Manifest für ein Excel-Add-in, eine Windows Forms-Anwendung oder eine Windows Presentation Foundation Browser-Anwendung zu aktualisieren und zu signieren.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5. Kopieren Sie optional das Master Bereitstellungs Manifest (Publish \\ *appname*. Application) in Ihr Versions Bereitstellungs Verzeichnis (publish\anwendungsdateien \\ *appname*_*Version*).  
  
## <a name="updating-and-re-signing-the-application-and-deployment-manifests"></a>Aktualisieren und erneutes Signieren der Anwendungs-und Bereitstellungs Manifeste  
 Bei diesem Verfahren wird davon ausgegangen, dass Sie bereits Änderungen an ihrer Anwendungs Manifest-Datei (. manifest) vorgenommen haben, aber dass andere Dateien aktualisiert wurden. Wenn Dateien aktualisiert werden, muss der Hash, der die Datei darstellt, ebenfalls aktualisiert werden.  
  
#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>So können Sie die Anwendungs-und Bereitstellungs Manifeste mit Mage.exe aktualisieren und erneut signieren  
  
1. Öffnen Sie ein **Visual Studio-Eingabe** Aufforderungs Fenster.  
  
2. Wechseln Sie in den Ordner, der die Manifest-Dateien enthält, die Sie signieren möchten.  
  
3. Entfernen Sie die Dateierweiterung ". bereitstellen" aus den Dateien im Veröffentlichungs Ausgabeordner.  
  
4. Geben Sie den folgenden Befehl ein, um das Anwendungs Manifest mit den neuen Hashes für die aktualisierten Dateien zu aktualisieren und die Anwendungs Manifest-Datei zu signieren. Ersetzen Sie ManifestFileName durch den Namen der Manifestressource zuzüglich der Erweiterung. Ersetzen Sie Certificate durch den relativen oder voll qualifizierten Pfad der Zertifikatsdatei, und ersetzen Sie Password durch das Kennwort für das Zertifikat.  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Beispielsweise können Sie den folgenden Befehl ausführen, um ein Anwendungs Manifest für ein Add-in, eine Windows Form-Anwendung oder eine Windows Presentation Foundation Browser-Anwendung zu signieren. Temporäre Zertifikate, die von Visual Studio erstellt werden, werden nicht für die Bereitstellung in Produktionsumgebungen empfohlen.  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5. Geben Sie den folgenden Befehl ein, um die Bereitstellungs Manifest-Datei zu aktualisieren und zu signieren. ersetzen Sie dabei die Platzhalter Namen wie im vorherigen Schritt.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Beispielsweise können Sie den folgenden Befehl ausführen, um ein Bereitstellungs Manifest für ein Excel-Add-in, eine Windows Forms-Anwendung oder eine Windows Presentation Foundation Browser-Anwendung zu aktualisieren und zu signieren.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6. Fügen Sie die Dateierweiterung. Bereitstellen der Dateien mit Ausnahme der Dateien für die Anwendung und das Bereitstellungs Manifest wieder hinzu.  
  
7. Kopieren Sie optional das Master Bereitstellungs Manifest (Publish \\ *appname*. Application) in Ihr Versions Bereitstellungs Verzeichnis (publish\anwendungsdateien \\ *appname*_*Version*).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Sichern von ClickOnce-Anwendungen](../deployment/securing-clickonce-applications.md)   
 [Code Zugriffssicherheit für ClickOnce-Anwendungen](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce und Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Übersicht über bereit Stellungen vertrauenswürdiger Anwendungen](../deployment/trusted-application-deployment-overview.md)   
 [Gewusst wie: Aktivieren von ClickOnce-Sicherheitseinstellungen](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Vorgehensweise: Festlegen einer Sicherheits Zone für eine ClickOnce-Anwendung](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Gewusst wie: Festlegen benutzerdefinierter Berechtigungen für eine ClickOnce-Anwendung](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Gewusst wie: Debuggen einer ClickOnce-Anwendung mit eingeschränkten Berechtigungen](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Vorgehensweise: Hinzufügen eines vertrauenswürdigen Herausgebers zu einem Client Computer für ClickOnce-Anwendungen](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Gewusst wie: Konfigurieren des Verhaltens der ClickOnce-Eingabeaufforderung zur Vertrauenswürdigkeit](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)

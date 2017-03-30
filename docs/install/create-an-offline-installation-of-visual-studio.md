---
title: "Erstellen eines Offlineinstallationsprogramms für Visual Studio 2017 | Microsoft-Dokumentation"
description: Hier erfahren Sie, wie Sie ein Offlineinstallationsprogramm von Visual Studio erstellen.
ms.custom: 
ms.date: 03/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- offline installer [Visual Studio]
- ISO [Visual Studio]
ms.assetid: 7bd7e724-7bfd-43f1-9935-981919be5a00
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5b6334c38a6c058f274498c06f8e07c934931910
ms.openlocfilehash: 563c78a49eb55886b1ddbd4f437951c99c6568e5
ms.lasthandoff: 03/22/2017

---
# <a name="create-an-offline-installer-for-visual-studio-2017"></a>Erstellen eines Offlineinstallationsprogramms für Visual Studio 2017
Wir wissen, dass viele Kunden ein Offlineinstallationsprogramm für [Visual Studio 2017](https://go.microsoft.com/fwlink/?linkid=844067) wünschen. Obwohl wir kein ISO-Image anbieten, ist es einfach, einen Ordner zu erstellen, den Sie verwenden können, um offline zu installieren.

Gehen Sie folgendermaßen vor:

## <a name="download-the-setup-file-you-want"></a>Laden Sie die Setupdatei herunter, die Sie wünschen.
**[Laden](https://www.visualstudio.com/downloads?utm_source=mscom&utm_campaign=msdocs)** Sie die Edition von Visual Studio herunter, die Sie wünschen. Achten Sie darauf, auf **Speichern** zu klicken, und dann auf **Ordner öffnen**.

Ihre Setupdatei &mdash; oder genauer gesagt, eine Bootstrapperdatei &mdash; entspricht einer der folgenden.

|Edition | Datei|  
|-------------|-----------------------|  
|Visual Studio Enterprise |**vs_enterprise.exe**|  
|Visual Studio Professional |**vs_professional.exe**|  
|Visual Studio-Community |**vs_community.exe**|

Andere unterstützte Bootstrapper sind u.a. „vs_buildtools.exe“, „vs_feedbackclient.exe“, „vs_teamexplorer.exe“, „vs_testagent.exe“, „vs_testcontroller.exe“ und „vs_testprofessional.exe“.

## <a name="create-an-offline-installation-folder"></a>Erstellen eines Offlineinstallationsordners
Um eine Offlineinstallation mit allen Sprachen und allen Funktionen zu erstellen, verwenden Sie einen der Befehle in den folgenden Beispielen.

(Stellen Sie sicher, dass Sie den Befehl im Download-Verzeichnis ausführen. Dies ist in der Regel `C:\Users\<username>\Downloads` auf einem Computer mit Windows 10).

- Führen Sie für Visual Studio Enterprise aus: <br>  ```vs_enterprise.exe --layout c:\vs2017offline```
- Führen Sie für Visual Studio Professional aus: <br> ```vs_professional.exe --layout c:\vs2017offline```
- Führen Sie für Visual Studio-Community aus: <br> ```vs_community.exe --layout c:\vs2017offline```

Weitere Beispiele finden Sie auf dieser Seite im Abschnitt [Gewusst wie: Anpassen Ihres Offlineinstallationsprogramms](#how-to-customize-your-offline- installer).

## <a name="install-from-the-offline-installation-folder"></a>Installieren aus dem Offlineinstallationsordner
Führen Sie die Offlineinstallation jetzt oder später durch; die Entscheidung liegt bei Ihnen. Aber gehen Sie dabei folgendermaßen vor.

  1. Installieren Sie die Zertifikate (Sie befinden sich im Ordner für Zertifikate, der sich in Ihrem Layout-Ordner befindet. Einfach jeweils mit der rechten Maustaste darauf klicken, um es zu installieren.).

  2. Führen Sie die Installationsdatei aus. Führen Sie zum Beispiel aus: <br> ```c:\vs2017offline\vs_enterprise.exe```

## <a name="additional-tips-for-offline-installers"></a>Zusätzliche Tipps zu Offlineinstallationsprogrammen
Sie können Ihr Offlineinstallationsprogramm mühelos anpassen oder aktualisieren – wir zeigen es Ihnen. Und wenn ein Fehler bei Ihrem Offlineinstallationsprogramm auftritt, bieten wir Ihnen auch Problembehandlung und Supportinformationen.

### <a name="how-to-customize-your-offline-installer"></a>Gewusst wie: Anpassen Ihres Offlineinstallationsprogramms
Es gibt viele Optionen, die Sie zum Anpassen des Offlineinstallationsprogramms verwenden können. Hier sind einige Beispiele zum Anpassen des [Gebietsschemas](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales).

 - Führen Sie zum Herunterladen aller Arbeitsauslastungen und Komponenten für nur eine Sprache Folgendes aus: <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US```
 - Führen Sie zum Herunterladen aller Arbeitsauslastungen und Komponenten für mehrere Sprachen Folgendes aus: <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US de-DE ja-JP```
 - Führen Sie zum Herunterladen einer Arbeitsauslastung für alle Sprachen Folgendes aus: <br> ```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure ```
 - Führen Sie zum Herunterladen von zwei Arbeitsauslastungen und einer optionalen Komponenten für drei Sprachen Folgendes aus: <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure Microsoft.VisualStudio.Workload.ManagedDesktop Component.GitHub.VisualStudio --lang en-US de-DE ja-JP ``` Weitere Informationen zu den Optionen, mit denen Sie Ihre Installation anpassen können, finden Sie auf unserer Seite [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio 2017 RC](use-command-line-parameters-to-install-visual-studio.md).


### <a name="how-to-update-an-offline-installer"></a>Gewusst wie: Aktualisieren eines Offlineinstallationsprogramms
Möglicherweise möchten Sie Ihr Offlineinstallationsprogramm zu einem späteren Zeitpunkt aktualisieren. Gehen Sie folgendermaßen vor:
* Um eine Visual Studio-Instanz zu aktualisieren, die Sie aus einem Offlineinstallationsordner installiert haben, führen Sie das Installationsprogramm für Visual Studio aus, und klicken Sie dann auf **Aktualisieren**.
* Um Ihren Offlineinstallationsordner zu aktualisieren, damit er die neuesten Updates enthält, führen Sie den ```--layout```-Befehl erneut aus. Vergewissern Sie sich, dass Sie auf den gleichen Ordner verweisen, den Sie bisher verwendet haben; auf diese Weise werden nur die Komponenten heruntergeladen, die seit der letzten Ausführung von ```--layout``` aktualisiert wurden.


### <a name="how-to-troubleshoot-an-offline-installer"></a>Gewusst wie: Problembehandlung bei einem Offlineinstallationsprogramm
Manchmal geht etwas schief. Hier ist eine Tabelle mit bekannten Problemen und einigen Problemumgehungen, die helfen könnten.

| Problem       | Element                   | Lösung |
| ----------- | ---------------------- | -------- |
| Sie erhalten die Warnmeldung, dass Sie nicht in der Lage seien, einige Komponenten und Pakete zu installieren.  | Android SDK-Installation (API-Ebene) | Wenn Sie Android SDK-Pakete (API-Ebene) einschließen möchten, benötigen Sie eine Internetverbindung bei der Erstellung des Offlineinstallationsprogramms. In einem eingeschränkten Netzwerk müssen Sie den Zugriff auf die folgenden URLs zulassen: <br><br> - http://dl.google.com:443 <br> - http://dl-ssl.google.com:443 <br>  - https://dl-ssl.google.com/android/repository/*<br><br>Weitere Informationen zur Behebung möglicher Probleme mit Proxyeinstellungen finden Sie im Blogbeitrag [Visual Studio 2015 install failures (Android SDK Setup) behind a Proxy](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) (Fehler bei der Installation von Visual Studio 2015 – Android SDK-Installation – hinter einem Proxy).  |  
| Benutzer haben keinen Zugriff auf Dateien. | Berechtigungen (ACLs) | Stellen Sie sicher, dass Sie die Berechtigungen (ACLs) so anpassen, dass anderen Benutzern Lesezugriff erteilt wird, *bevor* Sie die Offlineinstallation freigeben. |
| Neue Arbeitslasten, Komponenten oder Sprachen werden nicht installiert.  | `--layout`  | Stellen Sie sicher, dass Sie über Internetzugriff verfügen, wenn Sie eine Installation aus einem partiellen Layout heraus ausführen und Arbeitsauslastungen, Komponenten oder Sprachen auswählen, die im früheren Layout nicht verfügbar sind. |

### <a name="how-to-get-support-for-your-offline-installer"></a>Gewusst wie: Anfordern von Support für Ihr Offlineinstallationsprogramm
Wenn ein Problem mit der Offlineinstallation auftritt, möchten wir dies erfahren. Die beste Möglichkeit, uns zu informieren, ist die Verwendung des [Problem melden](../ide/how-to-report-a-problem-with-visual-studio-2017.md)-Tools. Wenn Sie dieses Tool verwenden, können Sie uns die Telemetriedaten und Protokolle senden, die wir benötigen, um uns Diagnose und Behebung des Problems zu erleichtern.

Wir bieten auch noch weitere Supportoptionen. Eine entsprechende Liste finden Sie auf unserer Seite [Melden eines Problems mit Visual Studio 2017 RC](../ide/how-to-report-a-problem-with-visual-studio-2017.md).


## <a name="see-also"></a>Siehe auch
* [Installieren von Visual Studio](install-visual-studio.md)
* [Administratorhandbuch für Visual Studio 2017 RC](visual-studio-administrator-guide.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Arbeitsauslastung und Komponenten-IDs von Visual Studio](workload-and-component-ids.md)


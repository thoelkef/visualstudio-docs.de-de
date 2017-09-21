---
title: Erstellen einer Offlineinstallation von Visual Studio 2017 RC | Microsoft-Dokumentation
description: Hier erfahren Sie, wie Sie eine Offlineinstallation von Visual Studio erstellen.
ms.custom: 
ms.date: 02/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
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
ms.sourcegitcommit: d4d1bd45ce697017480b3f63d0c7feb5ab20d2d6
ms.openlocfilehash: 33e765d205aa7ad8a3d8c5b871863ab659092a77
ms.lasthandoff: 02/22/2017

---
# <a name="create-an-offline-installation-of-visual-studio-2017-rc"></a>Erstellen einer Offlineinstallation von Visual Studio 2017 RC

## <a name="create-a-layout"></a>Erstellen eines Layouts
Wenn Sie [Visual Studio 2017 RC](https://www.visualstudio.com/vs/visual-studio-2017-rc/) auf einem anderen Computer installieren möchten, der über keinen Internetzugriff verfügt, erstellen Sie hierfür zuerst ein Layout für die Offlineinstallation, das alle Visual Studio-Dateien und -Komponenten enthält, die Sie benötigen.

Anschließend installieren Sie Visual Studio mithilfe des von Ihnen erstellten Layouts für die Offlineinstallation auf dem Zielcomputer.     

> [!WARNING]
> Aktuell unterstützt das Android SDK keine Oberfläche zur Offlineinstallation. Wenn Sie die Setupelemente des Android SDKs auf einem Computer installieren, der keine Internetverbindung aufweist, tritt bei der Installation möglicherweise ein Fehler auf. Weitere Informationen hierzu finden Sie im Abschnitt [Problembehandlung bei einer Offlineinstallation](#tshootofflineinstall) in diesem Thema.


#### <a name="to-create-an-offline-installation-layout-of-visual-studio"></a>So erstellen Sie ein Layout für die Offlineinstallation von Visual Studio
1. Laden Sie die ausführbare Setupdatei für Visual Studio auf ein Laufwerk des lokalen Computers herunter.
  [Laden Sie z.B. die Datei „vs_enterprise.exe“ herunter](https://www.visualstudio.com/vs/visual-studio-2017-rc/).
2. Führen Sie `vs_enterprise.exe` mit den folgenden Argumenten (Schaltern) an einer Eingabeaufforderung aus:

   a. Fügen Sie `--layout <path>` hinzu, wobei `<path>` der Speicherort ist, auf den Sie das Layout herunterladen möchten. Beachten Sie, das relative Pfade (z.B. `..\vs2017`) derzeit nicht unterstützt werden. Standardmäßig werden alle Sprachen heruntergeladen. (Siehe Beispiel A.)

   b. Beschränken Sie den Download durch Angabe des Arguments `--lang <language>` auf eine Teilmenge der verfügbaren Sprachen, wobei `<language>` mindestens ein Sprachgebietsschema ist.  (Siehe Beispiel B und Beispiel C)

   c. Schränken Sie den Download durch Angabe des Arguments `--add <package ID>` auf eine Teilmenge von Arbeitsauslastungen und Komponenten ein. Dadurch werden nur die Arbeitsauslastungen und Komponenten (und deren Abhängigkeiten) heruntergeladen, die Sie angeben. (Siehe Beispiel D und Beispiel E)

   Eine vollständige Liste der Arbeitsauslastungs- und Komponenten-IDs, sortiert nach Visual Studio-Produkt, finden Sie auf unserer Seite [Arbeitsauslastungs- und Komponenten-IDs in Visual Studio 2017](https://aka.ms/vs2017componentids).

### <a name="examples"></a>Beispiele
**Beispiel A**: Herunterladen aller Arbeitsauslastungen und Komponenten für alle Sprachen
  > ```vs_enterprise.exe --layout C:\vs2017```

**Beispiel B**: Herunterladen aller Arbeitsauslastungen und Komponenten für eine Sprache  
  > ```vs_enterprise.exe --layout C:\vs2017 --lang en-US```

**Beispiel C**: Herunterladen aller Arbeitsauslastungen und Komponenten für mehrere Sprachen
  > ```vs_enterprise.exe --layout C:\vs2017 --lang en-US de-DE ja-JP```

**Beispiel D**: Herunterladen einer Arbeitsauslastung für alle Sprachen
  > ```vs_enterprise.exe --layout C:\vs2017 --add Microsoft.VisualStudio.Workload.Azure ```

**Beispiel E**: Herunterladen von zwei Arbeitsauslastungen und einer optionalen Komponenten für drei Sprachen
  > ```vs_enterprise.exe --layout C:\vs2017 --add Microsoft.VisualStudio.Workload.Azure Microsoft.VisualStudio.Workload.ManagedDesktop Component.GitHub.VisualStudio --lang en-US de-DE ja-JP ```

  > [!WARNING]
  > Der Parameter „--layout“ schlägt fehl, wenn der Setup-.exe-Dateiname Ziffern enthält. Um dieses Problem zu umgehen, müssen Sie die Ziffern aus dem Dateinamen entfernen &mdash; z.B. *vs_community__198521760.1486960229.exe* in ***vs_community.exe*** umbenennen.

### <a name="language-locales"></a>Gebietsschemas

| Gebietsschema | Sprache |
| -----   | ----- |
| cs-CZ    | Tschechisch |
| de-DE    | Deutsch |
| en-US    | Englisch |
| es-ES    | Spanisch |
| fr-FR    | Französisch |
| it-IT    | Italienisch |
| ja-JP    | Japanisch |
| ko-KR    | Koreanisch |
| pl-PL    | Polnisch |
| pt-BR    | Portugiesisch (Brasilien) |
| ru-RU    | Russisch |
| tr-TR    | Türkisch |
| zh-CN    | Chinesisch (vereinfacht) |
| zh-TW    | Chinesisch (traditionell) |


## <a name="install-from-a-layout"></a>Installation über ein Layout
#### <a name="to-install-visual-studio-from-an-offline-installation-layout"></a>So installieren Sie Visual Studio über ein Layout für die Offlineinstallation
1. Navigieren Sie auf dem Zielcomputer zum Ordner **Zertifikate** im Ordner „Layout“.
2. Mit der rechten Maustaste klicken Sie auf und installieren alle Zertifikate im Ordner **Zertifikate**.

  (Wenn Sie nach der Installation eines Zertifikats zur Eingabe eines Kennworts aufgefordert werden, klicken Sie auf **Weiter**.)  
3. Führen Sie `vs_enterprise.exe` aus dem Ordner **Layout** heraus aus.

Hinweis: Wenn Sie eine Installation aus einem partiellen Layout heraus ausführen und Arbeitsauslastungen, Komponenten oder Sprachen auswählen, die im Layout nicht verfügbar sind, wird versucht, diese herunterzuladen.  Wenn Sie über keinen Internetzugriff verfügen, können diese Elemente nicht installiert werden.

> [!CAUTION]
> Das Layout für die Offlineinstallation erstellt derzeit einige Dateien mit eingeschränkten Berechtigungen (ACLs), auf die nicht alle Benutzer zugreifen können.  Stellen Sie sicher, dass Sie die Berechtigungen (ACLs) so anpassen, dass anderen Benutzern Lesezugriff erteilt wird, *bevor* Sie die Offlineinstallation freigeben.

## <a name="update-an-installation-layout"></a>Aktualisieren eines Installationslayouts
Wenn Updates für Visual Studio 2017 RC verfügbar sind, führen Sie den Befehl `--layout` unter Verweis auf denselben Layoutordner erneut aus, um sicherzustellen, dass der Ordner die neuesten Komponenten enthält. Es werden nur die Komponenten heruntergeladen, die seit der letzten Ausführung von `--layout` aktualisiert wurden.

## <a id="tshootofflineinstall"> </a>Beheben von Problemen mit einem Installationslayout
Wenn Sie eine Offlineinstallation aus dem Offlineinstallationscache ausführen, werden möglicherweise Fehlermeldungen angezeigt, die darauf hinweisen, dass einige Komponenten und Pakete nicht installiert werden können. Die folgende Tabelle enthält mögliche Lösungen für diese Szenarien.

| Komponente oder Paket | Lösung |
| -------------------- | -------- |
|Android SDK-Installation (API-Ebene)| Für die Installation von Android SDK-Paketen (API-Ebene) benötigen Sie einen Internetzugang. In einem eingeschränkten Netzwerk müssen Sie zur Installation von Visual Studio den Zugriff auf die folgenden URLs zulassen: <br><br> - http://dl.google.com:443 <br>- http://dl-ssl.google.com:443 <br>  - https://dl-ssl.google.com/android/repository/*<br><br>Weitere Informationen zur Behebung möglicher Probleme mit Proxyeinstellungen finden Sie im Blogbeitrag [Visual Studio&2015; install failures (Android SDK Setup) behind a Proxy](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) (Fehler bei der Installation von Visual Studio&2015; – Android SDK-Installation – hinter einem Proxy).  |  

 > [!IMPORTANT]
 > Während Visual Studio 2017 RC im Allgemeinen für die Verwendung in einer Produktionsumgebung unterstützt wird, werden die Arbeitsauslastungen und Komponenten, die in der Benutzeroberfläche der Installation als „Vorschau“ gekennzeichnet sind, nicht für die Verwendung in einer Produktionsumgebung unterstützt.

 ## <a name="see-also"></a>Siehe auch
 * [Installieren von Visual Studio](install-visual-studio.md)
 * [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [Melden eines Problems mit Visual Studio](../ide/how-to-report-a-problem-with-visual-studio-2017.md)


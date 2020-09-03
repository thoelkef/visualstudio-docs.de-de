---
title: Erstellen einer Offlineinstallation | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- offline installation
- offline install
- ISO
ms.assetid: 85d65709-42be-449f-9663-914bf1045089
caps.latest.revision: 22
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a6a9707d517a8a43d9a9ca156a5f7291ecee9bee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "81445063"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Erstellen einer Offlineinstallation von Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation zu Visual Studio finden Sie unter [Erstellen einer Offlineinstallation von Visual Studio](/visualstudio/install/create-an-offline-installation-of-visual-studio) oder [Erstellen einer Netzwerkinstallation von Visual Studio](/visualstudio/install/create-a-network-installation-of-visual-studio).

Diese Seite beschreibt, wie Sie Visual Studio 2015 installieren, wenn Sie nicht mit dem Internet verbunden sind. Zum Durchführen einer „getrennten“ Installation müssen Sie aber zuerst ein Layout für die Offlineinstallation mithilfe eines Computers erstellen, der mit dem Internet verbunden ist. Und so gehen Sie dabei vor.

> [!IMPORTANT]
> Wenn auf Ihrem Offlinecomputer Windows 7 SP1 oder Windows Server 2008 R2 ausgeführt wird, finden Sie spezielle Anweisungen dazu im Abschnitt [Problembehandlung bei einer Offlineinstallation](#BKMK_tshoot) in diesem Thema.  Sie müssen diesen Anweisungen folgen, *bevor* Sie Visual Studio 2015 installieren.

## <a name="installing-by-creating-an-offline-installation"></a><a name="BKMK_Offline"></a> Installieren durch Erstellen einer Offlineinstallation

#### <a name="to-create-an-offline-installation-layout"></a>So erstellen Sie ein Layout für die Offlineinstallation

1. Wählen Sie die Edition von Visual Studio aus, die Sie von der Downloadseite [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) installieren möchten.

2. Nachdem Sie das Installationsprogramm an einen Speicherort im Dateisystem heruntergeladen haben, führen Sie " \<executable name> /Layout" aus.

     Führen Sie zum Beispiel `vs_enterprise.exe /layout D:\VisualStudio2015` aus.

     Mit dem `/layout`-Switch können Sie fast alle Installationspakete herunterladen und nicht nur diejenigen, die für den Downloadcomputer vorgesehen sind. Mit diesem Ansatz erhalten Sie die Dateien, die Sie benötigen, um dieses Installationsprogramm überall ausführen. Darüber hinaus sind sie möglicherweise hilfreich, wenn Sie Komponenten installieren möchten, die ursprünglich nicht installiert wurden.

3. Nachdem Sie diesen Befehl ausgeführt haben, wird ein Dialogfeld angezeigt, in dem Sie den Ordner ändern können, in dem das Layout für die Offlineinstallation gespeichert werden soll.   Klicken Sie anschließend auf die Schaltfläche **herunterladen** .

     Wenn der Paket Download erfolgreich ist, wird eine Meldung mit dem Hinweis angezeigt, dass **Setup erfolgreich abgeschlossen wurde. Alle angegebenen Komponenten wurden erfolgreich abgerufen.**

4. Suchen Sie den Ordner, den Sie zuvor angegeben haben (Suchen Sie z. b. nach d:\visualstudio2015.). Dieser Ordner enthält alles, was Sie zum Kopieren an einen freigegebenen Speicherort oder zum Installieren von Medien benötigen.

    > [!CAUTION]
    > Aktuell unterstützt das Android SDK keine Oberfläche zur Offlineinstallation. Wenn Sie die Setupelemente des Android SDKs auf einem Computer installieren, der keine Internetverbindung aufweist, tritt bei der Installation möglicherweise ein Fehler auf. Weitere Informationen finden Sie im Abschnitt „Problembehandlung bei einer Offlineinstallation“ in diesem Thema.

5. Führen Sie die Installation vom Dateispeicherort oder von den Installationsmedien aus.

## <a name="updating-an-offline-installation"></a>Aktualisieren einer Offlineinstallation
 Microsoft hat mehrere Updates für Visual Studio 2015 veröffentlicht. Zum Aktualisieren Ihrer Visual Studio-Installation laden Sie einfach die gewünschte Edition von der Downloadseite [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) herunter. Führen Sie anschließend die Schritte in diesem Thema zum Erstellen eines neuen Layouts für die Offlineinstallation aus, und verwenden Sie dann dieses Layout, um Ihre Kopie von Visual Studio 2015 zu aktualisieren.

## <a name="troubleshooting-an-offline-installation"></a><a name="BKMK_tshoot"></a> Problembehandlung bei einer Offlineinstallation
 Wenn Sie eine Offlineinstallation aus dem Offlineinstallationscache ausführen, werden möglicherweise Fehlermeldungen angezeigt, die darauf hinweisen, dass einige Komponenten und Pakete nicht installiert werden können. Die folgende Tabelle enthält mögliche Lösungen für diese Szenarien.

| Komponente oder Paket | Lösung |
|-|-|
| Dotfuscator und Analytics Community Edition 5.19.1 (für die Community-, Professional- und Enterprise-Editionen von Visual Studio wie unter **Windows 7 SP1** und **Windows Server 2008 R2** installiert) | Wenn auf Ihrem Offlinecomputer **Windows 7 SP1** oder **Windows Server 2008 R2** ausgeführt wird, müssen Sie vor der Installation von Visual Studio 2015 die folgenden Schritte ausführen:<br /><br /> 1. Konfigurieren Sie eine Datei oder einen Webserver, um die CTL-Dateien herunterzuladen.<br /><br /> 2. Umleiten der Microsoft-URL für automatische Updates für eine nicht verbundene Umgebung.<br /><br /> Weitere Informationen finden Sie auf der Seite [Konfigurieren vertrauenswürdiger Stämme und unzulässiger Zertifikate](https://technet.microsoft.com/library/dn265983.aspx) auf der Microsoft TechNet-Website. |
| Android SDK-Installation (API-Ebene) | Für die Installation von Android SDK-Paketen (API-Ebene) benötigen Sie einen Internetzugang. In einem eingeschränkten Netzwerk müssen Sie zur Installation von Visual Studio den Zugriff auf die folgenden URLs zulassen:<br /><br /> -   `https://dl.google.com:443`<br />-   `https://dl-ssl.google.com:443`<br />-   `https://dl-ssl.google.com/android/repository/*`<br /> <br />Weitere Informationen zur Behebung möglicher Probleme mit Proxyeinstellungen finden Sie im Blogbeitrag [Visual Studio 2015 install failures (Android SDK Setup) behind a Proxy (Fehler bei der Installation von Visual Studio 2015 – Android SDK-Setup – hinter einem Proxy)](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/). |
| Vorlagen für Visual Studio-Erweiterbarkeit<br /><br /> GitHub-Erweiterung für Visual Studio<br /><br /> PowerShell Tools for Visual Studio | Wenn Sie bei der Installation von Visual Studio 2015 über keine Internetverbindung verfügen, können Sie einen speziellen Offlinefeed verwenden, um das Layout für die Offlineinstallation zu generieren. **Hinweis:** Dieser spezielle Feed enthält die neuesten Updates für Visual Studio 2015. <br /><br /> Zum Erstellen des speziellen Offlinefeeds führen Sie den folgenden Befehl aus: /layout *Laufwerk:* \VisualStudio2015 /overridefeeduri *URL_zur_Feed-XML*<br /><br /> Führen Sie z.B. für einen speziellen Offlinefeed von Visual Studio 2015 Enterprise in englischer Sprache den folgenden Befehl aus:<br /><br /> `vs_enterprise_ENU.exe /layout D:\VisualStudio2015 /overridefeeduri "https://go.microsoft.com/fwlink/?LinkID=785882&clcid0x409"`<br /><br /> Eine vollständige Liste von URLs, die Sie zum Erstellen eines speziellen Offlinefeeds in der gewünschten Sprache verwenden können, finden Sie in der folgenden Tabelle. |

 Verwenden Sie die folgenden URLs, um einen speziellen Offlinefeed in einer bestimmten Sprache zu erstellen, wie in der Tabelle oben beschrieben.

|       Sprache        |                            URL                            |
|-----------------------|-----------------------------------------------------------|
| Chinesisch (vereinfacht)  | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x804 |
| Chinesisch (traditionell) | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x404 |
|         Tschechisch         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x405 |
|        Deutsch         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x407 |
|        Englisch        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x409 |
|        Spanisch        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0xC0A |
|        Französisch         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x40C |
|        Italienisch        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x410 |
|       Japanisch        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x411 |
|        Koreanisch         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x412 |
|        Polnisch         | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x415 |
|      Portugiesisch       | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x416 |
|        Russisch        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x419 |
|        Türkisch        | https://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x41F |

## <a name="see-also"></a>Weitere Informationen

- [Installieren von Visual Studio](install-visual-studio-2015.md)
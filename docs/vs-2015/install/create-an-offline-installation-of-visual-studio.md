---
title: Erstellen einer Offlineinstallation von Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- offline installation
- offline install
- ISO
ms.assetid: 85d65709-42be-449f-9663-914bf1045089
caps.latest.revision: 22
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 6d17d8e7e5edcff6913e0046f0b580362cbc4950
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755666"
---
# <a name="create-an-offline-installation-of-visual-studio"></a>Erstellen einer Offlineinstallation von Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation für Visual Studio 2017 finden Sie unter [installieren Sie Visual Studio 2017 mit niedriger Bandbreite oder-unzuverlässigen netzwerkumgebungen](https://docs.microsoft.com/visualstudio/install/install-vs-inconsistent-quality-network), oder [Erstellen einer Netzwerkinstallation von Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/create-a-network-installation-of-visual-studio) und [Besondere Überlegungen für die Installation von Visual Studio 2017 in einer offlineumgebung](https://docs.microsoft.com/visualstudio/install/install-visual-studio-in-offline-environment).

Diese Seite beschreibt, wie Sie Visual Studio 2015 installieren, wenn Sie nicht mit dem Internet verbunden sind. Allerdings müssen zur Durchführung einer "getrennten" Installations können Sie zuerst erstellen ein Layout für die offline-Installation mithilfe eines virtuellen Computers, das mit dem Internet verbunden ist. Und so gehen Sie dabei vor.  

> [!IMPORTANT]
>  Wenn Ihr Computer im Offlinemodus Windows 7 SP1 oder Windows Server 2008 R2 ausgeführt wird, finden Sie unter den speziellen Anweisungen in der [Problembehandlung bei einer offline-Installation](#BKMK_tshoot) Abschnitt dieses Themas.  Sie müssen diese Anweisungen befolgen *vor* Sie Visual Studio 2015 installieren.  

##  <a name="BKMK_Offline"></a> Durch das Erstellen einer offline-Installations installieren  

#### <a name="to-create-an-offline-installation-layout"></a>Erstellen Sie ein Layout für die offline-installation  

1.  Wählen Sie die Edition von Visual Studio, die Sie installieren möchten an der [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) Downloadseite.  

2.  Nachdem Sie das Installationsprogramm an einem Speicherort im Dateisystem heruntergeladen haben, führen Sie "\<Name der ausführbaren Datei >/Layout".  

     Führen Sie zum Beispiel aus: `vs_enterprise.exe /layout D:\VisualStudio2015`  

     Mithilfe der `/layout` wechseln, Sie können fast aller Installationspakete, nicht nur diejenigen, die für den Download-Computer gelten. Dieser Ansatz bietet Ihnen die Dateien, die dieses Installationsprogramm überall ausgeführt werden sollen, und es kann hilfreich sein, wenn Sie möchten, um Komponenten zu installieren, die ursprünglich nicht installiert wurden.  

3.  Nach dem Ausführen dieses Befehls wird ein Dialogfeld angezeigt, mit dem Sie zum Ändern des Ordners, in denen das Layout der offline-Installation gespeichert werden sollen.   Klicken Sie anschließend die **herunterladen** Schaltfläche.  

     Wenn der Paketdownload erfolgreich durchgeführt wurde, sollte eine Nachricht angezeigt **Setup wurde erfolgreich abgeschlossen! Alle angegebenen Komponenten wurden erfolgreich abgerufen.**  

4.  Suchen Sie den Ordner, den Sie zuvor angegeben haben. (Suchen Sie z. B. D:\VisualStudio2015.) Dieser Ordner enthält alles, was Sie an einem freigegebenen Speicherort kopieren oder Installieren von Medien benötigen.  

    > [!CAUTION]
    >  Aktuell unterstützt das Android SDK keine Oberfläche zur Offlineinstallation. Wenn Sie die Setupelemente des Android SDKs auf einem Computer installieren, der keine Internetverbindung aufweist, tritt bei der Installation möglicherweise ein Fehler auf. Weitere Informationen finden Sie im Abschnitt "Problembehandlung bei einer offline-Installation" in diesem Thema.  

5.  Führen Sie die Installation von Speicherort der Datei oder von den installierten Medien.  

## <a name="updating-an-offline-installation"></a>Aktualisieren von einer offline-Installations  
 Microsoft hat mehrere Updates für Visual Studio 2015 veröffentlicht. Um Visual Studio-Installation zu aktualisieren, laden Sie einfach die Edition, die aus der von der [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20Enterprise%202015) Downloadseite. Führen Sie anschließend die Schritte in diesem Thema erstellen Sie ein neues Layout für die offline-Installation, und dann verwenden Sie, um Ihre Kopie von Visual Studio 2015 aktualisiert.  

##  <a name="BKMK_tshoot"></a> Problembehandlung bei einer offline-installation  
 Wenn Sie eine Offlineinstallation aus dem Offlineinstallationscache ausführen, werden möglicherweise Fehlermeldungen angezeigt, die darauf hinweisen, dass einige Komponenten und Pakete nicht installiert werden können. Die folgende Tabelle enthält mögliche Lösungen für diese Szenarien.  


|                                                                                       Komponente oder Paket                                                                                       |                                                                                                                                                                                                                                                                                                                                                                                                   Lösung                                                                                                                                                                                                                                                                                                                                                                                                   |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Dotfuscator und Analytics Community Edition 5.19.1 (für die Community, Professional und Enterprise-Editionen von Visual Studio als installiert **Windows 7 SP1** und **Windows Server 2008 R2**) |                                                                                                                                       Wenn Ihr Computer im Offlinemodus ausgeführt wird **Windows 7 SP1** oder **Windows Server 2008 R2**, Sie müssen die folgenden Schritte ausführen, vor der Installation von Visual Studio 2015:<br /><br /> 1.  Konfigurieren eines Servers Datei- oder Webservers zum Herunterladen der CTL-Dateien.<br /><br /> 2.    Umleiten der Microsoft Automatic Update URL für eine nicht verbundene Umgebung.<br /><br /> Weitere Informationen finden Sie unter den [konfigurieren vertrauenswürdiger Stämme und Unzulässiger Zertifikate](https://technet.microsoft.com/library/dn265983.aspx) Seite auf der Microsoft TechNet-Website.                                                                                                                                       |
|                                                                                  Android SDK-Installation (API-Ebene)                                                                                   |                                                                        Für die Installation von Android SDK-Paketen (API-Ebene) benötigen Sie einen Internetzugang. In einem eingeschränkten Netzwerk müssen Sie zur Installation von Visual Studio den Zugriff auf die folgenden URLs zulassen:<br /><br /> -   http://dl.google.com:443<br />-   http://dl-ssl.google.com:443<br />-   https://dl-ssl.google.com/android/repository/*<br /> <br />Weitere Informationen dazu, wie Sie mögliche Probleme mit Proxyeinstellungen finden Sie unter den [Fehler (Android SDK-Setup) hinter einem Proxy installieren Sie Visual Studio 2015](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) Blogbeitrag.                                                                         |
|                             Elementvorlagen für Visual Studio-Erweiterbarkeit<br /><br /> GitHub-Erweiterung für Visual Studio<br /><br /> PowerShell-Tools für Visual Studio                             | Wenn Sie nicht über eine Internetverbindung verfügen, wenn Sie Visual Studio 2015 installieren, können Sie eine spezielle offlinefeed, um das Layout der offline-Installation zu generieren. **Hinweis:** dieses spezielle Datenfeed enthält die neuesten Updates für Visual Studio 2015. <br /><br /> Um die spezielle offlinefeed erstellen möchten, führen Sie den folgenden Befehl aus: / Layout *Laufwerk:* \VisualStudio2015 /overridefeeduri *URL Feed-Xml*<br /><br /> Beispielsweise für eine englischsprachige spezielle offlinefeed von Visual Studio 2015 Enterprise ausführen:<br /><br /> `vs_enterprise_ENU.exe /layout D:\VisualStudio2015 /overridefeeduri "http://go.microsoft.com/fwlink/?LinkID=785882&clcid0x409"`<br /><br /> Eine vollständige Liste von URLs, die Sie verwenden können, um eine spezielle offlinefeed in der Sprache Ihrer Wahl zu erstellen, finden Sie in der folgenden Tabelle. |

 Verwenden Sie die folgenden URLs um einen speziellen offline sprachspezifische-Feed zu erstellen, wie in der obigen Tabelle beschrieben.  


|       Sprache        |                            URL                            |
|-----------------------|-----------------------------------------------------------|
| Chinesisch (vereinfacht)  | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x804 |
| Chinesisch (traditionell) | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x404 |
|         Tschechisch         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x405 |
|        Deutsch         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x407 |
|        Englisch        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x409 |
|        Spanisch        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0xC0A |
|        Französisch         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x40C |
|        Italienisch        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x410 |
|       Japanisch        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x411 |
|        Koreanisch         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x412 |
|        Polnisch         | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x415 |
|      Portugiesisch       | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x416 |
|        Russisch        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x419 |
|        Türkisch        | http://go.microsoft.com/fwlink/?LinkID=785882&clcid=0x41F |

## <a name="see-also"></a>Siehe auch  
 [Installieren von Visual Studio]()
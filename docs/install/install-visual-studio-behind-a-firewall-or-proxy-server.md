---
title: Installieren von Visual Studio hinter einer Firewall oder einem Proxyserver | Microsoft-Dokumentation
description: 
ms.custom: 
ms.date: 08/01/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
- list of domains, locations, URLs
ms.assetid: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3862c6ed49e00ffa3800cccbedb2b846823418ed
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="install-visual-studio-behind-a-firewall-or-proxy-server"></a>Installieren von Visual Studio hinter einer Firewall oder einem Proxyserver

Der Installer für Visual Studio lädt Dateien aus verschiedenen Domänen und deren Downloadserver herunter. Diese Seite listet die Domänen-URLs auf, die Sie möglicherweise der Whitelist als vertrauenswürdig in Ihren Entwicklungsskripts hinzufügen möchten.

Wenn es für Ihre Umgebung möglich ist, fügen Sie eventuell die folgenden Domänen mit jeweils HTTP- und HTTPS-Protokollen hinzu.

## <a name="microsoft-domains"></a>Microsoft-Domänen
| Domäne | Zweck |
| ------ | ------- |
| go.microsoft.com | Einrichten der URL-Lösung |
| aka.ms | Einrichten der URL-Lösung |
| download.visualstudio.microsoft.com | Einrichten des Speicherorts für den Paketdownload |
| 0download.microsoft.com | Einrichten des Speicherorts für den Paketdownload |
| download.visualstudio.com | Einrichten des Speicherorts für den Paketdownload |
| dl.xamarin.com | Einrichten des Speicherorts für den Paketdownload |
| visualstudiogallery.msdn.microsoft.com | Speicherort des Downloads der Visual Studio-Erweiterungen |
| www.visualstudio.com | Speicherort der Dokumentation |
| docs.microsoft.com | Speicherort der Dokumentation |
| msdn.microsoft.com | Speicherort der Dokumentation |
| www.microsoft.com | Speicherort der Dokumentation |
| *.windows.net | Anmeldeort |
| *.microsoftonline.com | Anmeldeort |
| *.live.com | Anmeldeort |


## <a name="non-microsoft-domains"></a>Nicht-Microsoft-Domänen
| Domäne | Installieren dieser Workloads |
| ------ | ------- |
| archive.apache.org |  Mobile Entwicklung mit JavaScript <br />(Cordova) |
| cocos2d-x.org | Spieleentwicklung mit C++ <br />(Cocos) |
| download.epicgames.com | Spieleentwicklung mit C++ <br />(Unreal Engine) |
| download.oracle.com | Mobile Entwicklung mit JavaScript <br />(Java SDK) <br /><br />Mobile Entwicklung mit .NET <br />(Java SDK) |
| download.unity3d.com | Spieleentwicklung mit Unity <br />(Unity) |
| netstorage.unity3d.com | Spieleentwicklung mit Unity <br /> (Unity) |
| dl.google.com | Mobile Entwicklung mit JavaScript <br />(Android SDK und NDK, Emulator) <br /><br />Mobile Entwicklung mit .NET <br />(Android SDK und NDK, Emulator) |
| www.incredibuild.com | Spieleentwicklung mit C++ <br />(IncrediBuild) |
| incredibuildvs2017i.azureedge.net | Spieleentwicklung mit C++ <br />(IncrediBuild) |
| www.python.org | Python-Entwicklung <br />(Python) <br /><br />Data Science und analytische Anwendungen <br />(Python) |

## <a name="get-support"></a>Support aufrufen
Manchmal kann etwas schiefgehen. Wenn bei der Installation von Visual Studio ein Fehler auftritt, lesen Sie den Artikel [Problembehandlung bei Visual Studio 2017-Installations- und -Upgradefehlern](troubleshooting-installation-issues.md). Wenn keiner der Schritte zur Problembehandlung hilfreich ist, können Sie uns per Livechat kontaktieren, um Hilfe bei der Installation zu erhalten (nur in englischer Sprache). Einzelheiten finden Sie auf der [Visual Studio-Supportseite](https://www.visualstudio.com/vs/support/#talktous).

Hier sind einige weitere Supportoptionen:
* Sie können uns über Produktprobleme mit dem Tool [Problem melden](../ide/how-to-report-a-problem-with-visual-studio-2017.md) informieren, das sowohl im Visual Studio-Installer als auch in der Visual Studio-IDE angezeigt wird.
* Sie können uns einen Produktvorschlag unter [UserVoice](https://visualstudio.uservoice.com/forums/121579) mitteilen.
* Sie können Probleme mit Produkten im Portal [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) im Blick behalten, Fragen stellen und Antworten finden.
* Über die [Visual Studio-Unterhaltung in der Gitter-Community](https://gitter.im/Microsoft/VisualStudio) können Sie auch Kontakt zu uns oder zu anderen Visual Studio-Entwicklern aufnehmen.  (Diese Option erfordert ein [GitHub](https://github.com/)-Konto.)

## <a name="see-also"></a>Siehe auch
* [Installieren von Visual Studio 2017](install-visual-studio.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
  * [Beispiele für Befehlszeilenparameter](command-line-parameter-examples.md)
  * [Referenz der Arbeitsauslastungs- und Komponenten-IDs](workload-and-component-ids.md)
* [Erstellen einer Netzwerkinstallation von Visual Studio 2017](create-a-network-installation-of-visual-studio.md)
  * [Installieren der für eine Offlineinstallation von Visual Studio erforderlichen Zertifikate](install-certificates-for-visual-studio-offline.md)
* [Automatisieren der Visual Studio-Installation mit einer Antwortdatei](automated-installation-with-response-file.md)
* [Automatisches Anwenden von Produktschlüsseln bei der Bereitstellung von Visual Studio](automatically-apply-product-keys-when-deploying-visual-studio.md)
* [Festlegen von Standardeinstellungen für Unternehmensbereitstellungen von Visual Studio 2017](set-defaults-for-enterprise-deployments.md)
* [Deaktivieren oder Verschieben des Paketcaches](disable-or-move-the-package-cache.md)
* [Aktualisieren einer netzwerkbasierten Installation von Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Steuern von Updates für Visual Studio 2017-Bereitstellungen](controlling-updates-to-visual-studio-deployments.md)
* [Tools zum Erkennen und Verwalten von Visual Studio-Instanzen](tools-for-managing-visual-studio-instances.md)

---
title: Installieren von Visual Studio hinter einer Firewall oder einem Proxyserver | Microsoft-Dokumentation
description: 
ms.custom: 
ms.date: 07/18/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
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
ms.translationtype: HT
ms.sourcegitcommit: ddbbda1069749e2ce685507d55a070f1dec27c17
ms.openlocfilehash: 48fd143f917d6e13c18f6913bea625b2e8cf5ce8
ms.contentlocale: de-de
ms.lasthandoff: 07/19/2017

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
| msdn.microsoft.com | Speicherort der Dokumentation |
| www.microsoft.com | Speicherort der Dokumentation |

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

## <a name="see-also"></a>Siehe auch
* [Installieren von Visual Studio 2017](install-visual-studio.md)
* [Administratorhandbuch für Visual Studio](visual-studio-administrator-guide.md)
  * [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md)
    * [Beispiele für Befehlszeilenparameter](command-line-parameter-examples.md)
    * [Referenz der Arbeitsauslastungs- und Komponenten-IDs](workload-and-component-ids.md)
  * [Erstellen einer netzwerkbasierten Installation von Visual Studio](create-a-network-installation-of-visual-studio.md)
    * [Besonderheiten bei der Installation von Visual Studio in einer Offline-Umgebung](install-visual-studio-in-offline-environment.md)
  * [Automatisieren von Visual Studio mit einer Antwortdatei](automated-installation-with-response-file.md)
  * [Automatisches Anwenden von Produktschlüsseln bei der Bereitstellung von Visual Studio](automatically-apply-product-keys-when-deploying-visual-studio.md)
  * [Festlegen von Standardeinstellungen für Unternehmensbereitstellungen von Visual Studio](set-defaults-for-enterprise-deployments.md)
  * [Deaktivieren oder Verschieben des Paketcaches](disable-or-move-the-package-cache.md)
  * [Aktualisieren einer netzwerkbasierten Installation von Visual Studio](update-a-network-installation-of-visual-studio.md)
  * [Steuern von Updates für Visual Studio-Bereitstellungen](controlling-updates-to-visual-studio-deployments.md)
  * [Tools zum Erkennen und Verwalten von Visual Studio-Instanzen](tools-for-managing-visual-studio-instances.md)
  * [Melden eines Problems mit Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)


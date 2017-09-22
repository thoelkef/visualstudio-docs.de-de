---
title: "Administratorhandbuch für Visual Studio | Microsoft-Dokumentation"
description: Erfahren Sie mehr zur Bereitstellung von Visual Studio in einer Unternehmensumgebung.
ms.custom: 
ms.date: 05/15/2017
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
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d9de84bed187c62962a76424aabdc5f355dff4dc
ms.openlocfilehash: 220b41f44cdc91ea84bf08b8eec8181dc01c25c7
ms.contentlocale: de-de
ms.lasthandoff: 05/15/2017

---
# <a name="visual-studio-2017-administrator-guide"></a>Administratorhandbuch für Visual Studio 2017

In Unternehmensumgebungen ist es üblich, dass Systemadministratoren Installationen für Endbenutzer über eine Netzwerkfreigabe oder mithilfe von Systemverwaltungssoftware bereitstellen. Wir haben das Visual Studio-Setupprogramm so gestaltet, dass es die unternehmensweite Bereitstellung unterstützt. Systemadministratoren können einen Speicherort für die Netzwerkinstallation erstellen, Standardwerte für die Installation vorkonfigurieren, Product Keys während des Installationsvorgangs bereitstellen und nach erfolgreicher Einführung Produktupdates verwalten. Dieses Handbuch für Administratoren bietet vom jeweiligen Szenario abhängige Anleitungen für die Unternehmensbereitstellung in Netzwerkumgebungen.

## <a name="deploying-visual-studio-2017-in-an-enterprise-environment"></a>Bereitstellen von Visual Studio 2017 in einer Unternehmensumgebung

Sie können Visual Studio 2017 auf Clientarbeitsstationen bereitstellen, solange jeder Zielcomputer die [minimalen Installationsanforderungen](https://www.visualstudio.com/en-us/productinfo/vs2017-system-requirements-vs) erfüllt. Egal, ob Sie über Software, z.B. System Center oder über eine Batchdatei bereitstellen, Sie sollten in der Regel die folgenden Schritte durchlaufen:

1. [Erstellen Sie eine Netzwerkfreigabe, die Visual Studio-Produktdateien enthält](create-a-network-installation-of-visual-studio.md) an einem Speicherort im Netzwerk.

2. [Wählen Sie die Arbeitsauslastungen und Komponenten](workload-and-component-ids.md) aus, die installiert werden sollen.

3. [Erstellen Sie eine Antwortdatei](automated-installation-with-response-file.md), die Standardinstallationsoptionen enthält. [Erstellen Sie alternativ ein Installationsskript](use-command-line-parameters-to-install-visual-studio.md), das Befehlszeilenparametern zum Steuern der Installation verwendet.

4. [Wenden Sie optional einen Volumenlizenz-Produktschlüssel](automatically-apply-product-keys-when-deploying-visual-studio.md) als Teil des Installationsskripts an, damit Benutzer die Software nicht separat aktivieren müssen.

5. Aktualisieren Sie das Netzwerklayout, [um zu steuern, wann Produktupdates an Ihre Endbenutzer übermittelt werden](controlling-updates-to-visual-studio-deployments.md).

6. Legen Sie optional Registrierungsschlüssel fest, [um zu steuern, was auf Clientarbeitsstationen zwischengespeichert wird](set-defaults-for-enterprise-deployments.md).

7. Verwenden Sie zum Ausführen des Skripts auf der Ziel-Entwicklerarbeitsstationen die Bereitstellungstechnologie Ihrer Wahl.

8. [Aktualisieren Sie den Netzwerkspeicherort mit den neuesten Updates](update-a-network-installation-of-visual-studio.md) für Visual Studio durch regelmäßiges Ausführen des Befehls, den Sie in Schritt 1 verwendet haben, um aktualisierte Komponenten hinzuzufügen.

> [!IMPORTANT]
> Beachten Sie, dass sich Installationen über eine Netzwerkfreigabe den ursprünglichen Quellspeicherort „merken“. Dies bedeutet, dass Sie zur Reparatur eines Clients möglicherweise zur Netzwerkfreigabe zurückkehren müssen, über die der Client ursprünglich installiert wurde. Wählen Sie die Netzwerkadresse sorgfältig aus, sodass sie der Lebensdauer der Visual Studio 2017-Clients in Ihrer Organisation entspricht.

## <a name="visual-studio-tools"></a>Visual Studio Tools
Wir haben mehrere Tools zur Verfügung gestellt, mit denen Sie [installierte Instanzen von Visual Studio auf Clientcomputern erkennen und verwalten](tools-for-managing-visual-studio-instances.md) können:

> [!TIP]
> Zusätzlich zur Dokumentation im Administratorhandbuch ist der [Blog von Heath Stewart](https://blogs.msdn.microsoft.com/heaths/tag/vs2017/) eine gute Quelle für Informationen zum Setup von Visual Studio 2017.

## <a name="see-also"></a>Siehe auch
* [Installieren von Visual Studio 2017](install-visual-studio.md)
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


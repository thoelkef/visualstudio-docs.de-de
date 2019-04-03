---
title: Administratorhandbuch für Visual Studio
titleSuffix: ''
description: Erfahren Sie mehr zur Bereitstellung von Visual Studio in einer Unternehmensumgebung.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 0c12ae3e101f2f59f0f7f6560ea86f1e6161c6ff
ms.sourcegitcommit: d4bea2867a4f0c3b044fd334a54407c0fe87f9e8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/01/2019
ms.locfileid: "58790094"
---
# <a name="visual-studio-administrator-guide"></a>Administratorhandbuch für Visual Studio

In Unternehmensumgebungen ist es üblich, dass Systemadministratoren Installationen für Endbenutzer über eine Netzwerkfreigabe oder mithilfe von Systemverwaltungssoftware bereitstellen. Wir haben die Visual Studio-Setup-Engine so gestaltet, dass sie die unternehmensweite Bereitstellung unterstützt. Systemadministratoren können einen Speicherort für die Netzwerkinstallation erstellen, Standardwerte für die Installation vorkonfigurieren, Product Keys während des Installationsvorgangs bereitstellen und nach erfolgreicher Einführung Produktupdates verwalten. Dieses Handbuch für Administratoren bietet vom jeweiligen Szenario abhängige Anleitungen für die Unternehmensbereitstellung in Netzwerkumgebungen.

## <a name="deploy-visual-studio-in-an-enterprise-environment"></a>Bereitstellen von Visual Studio in einer Unternehmensumgebung

::: moniker range="vs-2017"

Sie können Visual Studio auf Clientarbeitsstationen bereitstellen, solange jeder Zielcomputer die [minimalen Installationsanforderungen](/visualstudio/productinfo/vs2017-system-requirements-vs/) erfüllt. Egal, ob Sie über Software, z.B. System Center oder über eine Batchdatei bereitstellen, Sie sollten in der Regel die folgenden Schritte durchlaufen:

::: moniker-end

::: moniker range="vs-2019"

Sie können Visual Studio auf Clientarbeitsstationen bereitstellen, solange jeder Zielcomputer die [minimalen Installationsanforderungen](/visualstudio/releases/2019/system-requirements/) erfüllt. Egal, ob Sie über Software, z.B. System Center oder über eine Batchdatei bereitstellen, Sie sollten in der Regel die folgenden Schritte durchlaufen:

::: moniker-end

1. [Erstellen Sie eine Netzwerkfreigabe, die Visual Studio-Produktdateien enthält](create-a-network-installation-of-visual-studio.md) an einem Speicherort im Netzwerk.

2. [Wählen Sie die Arbeitsauslastungen und Komponenten](workload-and-component-ids.md) aus, die installiert werden sollen.

3. [Erstellen Sie eine Antwortdatei](automated-installation-with-response-file.md), die Standardinstallationsoptionen enthält. [Erstellen Sie alternativ ein Installationsskript](use-command-line-parameters-to-install-visual-studio.md), das Befehlszeilenparametern zum Steuern der Installation verwendet.

4. [Wenden Sie optional einen Volumenlizenz-Produktschlüssel](automatically-apply-product-keys-when-deploying-visual-studio.md) als Teil des Installationsskripts an, damit Benutzer die Software nicht separat aktivieren müssen.

5. Aktualisieren Sie das Netzwerklayout, [um zu steuern, wann Produktupdates an Ihre Endbenutzer übermittelt werden](controlling-updates-to-visual-studio-deployments.md).

6. Legen Sie optional Registrierungsschlüssel fest, [um zu steuern, was auf Clientarbeitsstationen zwischengespeichert wird](set-defaults-for-enterprise-deployments.md).

7. Verwenden Sie zum Ausführen des Skripts auf der Ziel-Entwicklerarbeitsstationen die Bereitstellungstechnologie Ihrer Wahl.

8. [Aktualisieren Sie den Netzwerkspeicherort mit den neuesten Updates](update-a-network-installation-of-visual-studio.md) für Visual Studio durch regelmäßiges Ausführen des Befehls, den Sie in Schritt 1 verwendet haben, um aktualisierte Komponenten hinzuzufügen.

> [!IMPORTANT]
> Beachten Sie, dass sich Installationen über eine Netzwerkfreigabe den ursprünglichen Quellspeicherort „merken“. Dies bedeutet, dass Sie zur Reparatur eines Clients möglicherweise zur Netzwerkfreigabe zurückkehren müssen, über die der Client ursprünglich installiert wurde. Wählen Sie die Netzwerkadresse sorgfältig aus, sodass sie der Lebensdauer der Visual Studio-Clients in Ihrer Organisation entspricht.

## <a name="use-visual-studio-tools"></a>Verwenden von Visual Studio-Tools

Wir haben mehrere Tools zur Verfügung gestellt, mit denen Sie [installierte Instanzen von Visual Studio auf Clientcomputern erkennen und verwalten](tools-for-managing-visual-studio-instances.md) können:

> [!TIP]
> Neben der Dokumentation im Administratorhandbuch sind die [Archive zum Setup von Visual Studio](https://devblogs.microsoft.com/setup/tag/vs2017/) eine gute Quelle für Informationen zum Setup von Visual Studio.

## <a name="specify-customer-feedback-settings"></a>Festlegen von Kundenfeedbackeinstellungen

Standardmäßig ermöglicht die Visual Studio-Installation Kundenfeedback. Wenn Sie die Gruppenrichtlinie aktivieren, können Sie Visual Studio konfigurieren, um Kundenfeedback auf einzelnen Computern zu deaktivieren. Legen Sie hierzu eine registrierungsbasierte Richtlinie für den folgenden Schlüssel fest:

**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM**

Eintrag = **OptIn**

Wert = (DWORD)
* **0** = deaktiviert
* **1** = aktiviert

Weitere Informationen über Kundenfeedbackeinstellungen finden Sie auf der Seite [Programm zur Verbesserung der Benutzerfreundlichkeit von Visual Studio](../ide/visual-studio-experience-improvement-program.md).

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Siehe auch

* [Installieren von Visual Studio](install-visual-studio.md)
* [Verwenden von Befehlszeilenparametern zum Installieren von Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Beispiele für Befehlszeilenparameter](command-line-parameter-examples.md)
  * [Referenz der Arbeitsauslastungs- und Komponenten-IDs](workload-and-component-ids.md)
* [Erstellen einer netzwerkbasierten Installation von Visual Studio](create-a-network-installation-of-visual-studio.md)
  * [Installieren der für eine Offlineinstallation von Visual Studio erforderlichen Zertifikate](install-certificates-for-visual-studio-offline.md)
* [Automatisieren von Visual Studio mit einer Antwortdatei](automated-installation-with-response-file.md)
* [Automatisches Anwenden von Produktschlüsseln bei der Bereitstellung von Visual Studio](automatically-apply-product-keys-when-deploying-visual-studio.md)
* [Festlegen von Standardeinstellungen für Unternehmensbereitstellungen von Visual Studio](set-defaults-for-enterprise-deployments.md)
* [Deaktivieren oder Verschieben des Paketcaches](disable-or-move-the-package-cache.md)
* [Aktualisieren einer netzwerkbasierten Installation von Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Steuern von Updates für Visual Studio-Bereitstellungen](controlling-updates-to-visual-studio-deployments.md)
* [Tools zum Erkennen und Verwalten von Visual Studio-Instanzen](tools-for-managing-visual-studio-instances.md)

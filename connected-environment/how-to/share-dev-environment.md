---
title: Freigeben einer Entwicklungsumgebung | Microsoft-Dokumentation
author: johnsta
ms.author: johnsta
ms.date: 3/12/2018
ms.topic: article
ms.technology: vsce-kubernetes
description: Schnelle Kubernetes-Entwicklung mit Containern und Microservices in Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, Container
manager: ghogen
ms.openlocfilehash: 9808e1ac3a6d7b3381b807bc0ce209e15f3e97cf
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
---
# <a name="share-a-development-environment"></a>Freigeben einer Entwicklungsumgebung

Mithilfe von Connected Environment können Sie Ihre Entwicklungsumgebung mit anderen in Ihrem Team teilen. Jeder Entwickler kann in seinem eigenen Bereich arbeiten, ohne befürchten zu müssen, dass er den Bereich von jemand anderem beschädigt. Darüber hinaus kann die Zusammenarbeit in einer Umgebung Ihnen ermöglichen, End-to-End-Tests für den Code durchzuführen, ohne Abhängigkeiten imitieren oder simulieren zu müssen. Weitere Informationen finden Sie im Leitfaden [Informationen zur Entwicklung im Team](../get-started-nodejs-06.md).

Einrichten einer Umgebung für mehrere Entwickler:
1. [Erstellen einer Connected Environment-Umgebung in Azure](../get-started.md). Sie benötigen Besitzer- oder Mitwirkendenzugriff, um auf das ausgewählte Azure-Abonnement zuzugreifen.
1. Legen Sie die **Ressourcengruppe** der Umgebung für jedes Teammitglied auf [Zugriffsrechte für Mitwirkende gewähren](https://docs.microsoft.com/en-us/azure/active-directory/role-based-access-control-configure) fest. Sie können die Ressourcengruppe einer Umgebung überprüfen, indem Sie folgenden Befehl ausführen: `vsce env list`
1. Fordern Sie Ihre Teammitglieder dazu auf, **die Umgebung auszuwählen**, um in ihr zu entwickeln.
     * **Befehlszeile oder Visual Studio Code**: Zum Anzeigen der Connected Environment-Umgebungen, auf die Sie Zugriff haben: `vsce env list`. Zum Auswählen einer Umgebung: `vsce env select`.
     * **Visual Studio IDE**: Öffnen Sie ein Projekt in Visual Studio, und wählen Sie in der Dropdownliste der Starteinstellungen **Connected Environment for AKS** (Connected Environment für AKS) aus. Wählen Sie in dem geöffneten Dialogfeld eine vorhandene Entwicklungsumgebung aus.

![Dropdownliste der Starteinstellungen in Visual Studio](../images/LaunchSettings.png)
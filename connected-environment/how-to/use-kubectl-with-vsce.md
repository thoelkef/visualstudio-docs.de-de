---
title: Verwenden von kubectl mit Connected Environment | Microsoft-Dokumentation
author: johnsta
ms.author: johnsta
ms.date: 03/12/2018
ms.topic: article
ms.technology: vsce-kubernetes
description: Schnelle Kubernetes-Entwicklung mit Containern und Microservices in Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, Container
manager: ghogen
ms.openlocfilehash: 46c69f80e58a4265aa5e4320e731c3ad241a8116
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
---
# <a name="use-kubectl-with-a-connected-environment"></a>Verwenden Sie `kubectl` mit Connected Environment

Sie können auf den Kubernetes-Cluster in Connected Environment zugreifen und vorhandene Kubernetes-Tools verwenden, wie z.B. `kubectl`.

Durch das Ausführen von `vsce env create` oder `vsce env select` wird automatisch ein `kubectl`-Konfigurationskontext hinzugefügt, sodass kubectl bereits mit Ihrem VSCE Kubernetes-Cluster verbunden ist. Beispiele:
- Bestätigen des aktuellen Kontexts: `kubectl config current-context`
- Auflisten aller verfügbaren Kontexte: `kubectl config get-contexts` Ein von VSCE erstellter Kubernetes-Cluster wird mit einem Namen wie „vsce-<guid>“ benannt.
- Ändern des Kontexts: `kubectl config use-context <context-name>`
- Anzeigen des Kubernetes-Dashboards: Führen Sie `kubectl proxy` aus, öffnen Sie in Ihrem Browser die Adresse, die der Befehl ausgegeben hat (fügen Sie `/ui` an die URL an, um zum Kubernetes-Dashboard zu gelangen).
- Auflisten ausgeführter Dienste im VSCE-Bereich namens *mainline*: `kubectl get services --namespace=mainline`


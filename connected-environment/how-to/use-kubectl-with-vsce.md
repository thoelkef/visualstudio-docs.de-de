---
title: Verwenden von kubectl mit Connected Environment | Microsoft-Dokumentation
author: ghogen
ms.author: ghogen
ms.date: 03/12/2018
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-azure
description: Schnelle Kubernetes-Entwicklung mit Containern und Microservices in Azure
keywords: Docker, Kubernetes, Azure, AKS, Azure Container Service, Container
manager: douge
ms.openlocfilehash: 138dce09e0d53dc47703b9c6f56a7efda4adc255
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="use-kubectl-with-a-connected-environment"></a>Verwenden Sie `kubectl` mit Connected Environment

Sie können auf den Kubernetes-Cluster in Connected Environment zugreifen und vorhandene Kubernetes-Tools verwenden, wie z.B. `kubectl`.

Durch das Ausführen von `vsce env create` oder `vsce env select` wird automatisch ein `kubectl`-Konfigurationskontext hinzugefügt, sodass kubectl bereits mit Ihrem VSCE Kubernetes-Cluster verbunden ist. Beispiele:
- Bestätigen des aktuellen Kontexts: `kubectl config current-context`
- Auflisten aller verfügbaren Kontexte: `kubectl config get-contexts` Ein von VSCE erstellter Kubernetes-Cluster wird mit einem Namen wie „vsce-<guid>“ benannt.
- Ändern des Kontexts: `kubectl config use-context <context-name>`
- Anzeigen des Kubernetes-Dashboards: Führen Sie `kubectl proxy` aus, öffnen Sie in Ihrem Browser die Adresse, die der Befehl ausgegeben hat (fügen Sie `/ui` an die URL an, um zum Kubernetes-Dashboard zu gelangen).
- Auflisten ausgeführter Dienste im VSCE-Bereich namens *mainline*: `kubectl get services --namespace=mainline`


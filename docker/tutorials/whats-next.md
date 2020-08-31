---
title: 'Docker-Tutorial: Nächste Schritte'
description: Beschreibt Optionen zum Erweitern von Docker-apps mit Orchestrierung mithilfe von Cloud Native Computing Foundation-Projekten.
ms.date: 08/04/2020
author: nebuk89
ms.author: ghogen
manager: jillfra
ms.technology: vs-azure
ms.topic: conceptual
ms.workload:
- azure
ms.openlocfilehash: f93185641a0814797b66eae90714e04cac83f7e5
ms.sourcegitcommit: c4212f40df1a16baca1247cac2580ae699f97e4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176691"
---
# <a name="whats-next"></a>Nächste Schritte

Obwohl Sie mit Ihrem Lernprogramm fertig sind, gibt es noch viel mehr über Container!
Sie werden hier nicht ausführlich darauf eingehen, aber hier sind einige weitere Bereiche, die Sie als nächstes betrachten können.

## <a name="container-orchestration"></a>Containerorchestrierung

Die Ausführung von Containern in der Produktion ist schwierig. Sie möchten sich nicht bei einem Computer anmelden und einfach ein `docker run` oder Ausführen `docker-compose up` . Warum nicht? Was geschieht, wenn die Container? Wie Skalieren Sie auf mehreren Computern? Die Container Orchestrierung löst dieses Problem. Tools wie "Kubernetes", "Swarm", "Nomad" und "AKS" helfen Ihnen dabei, dieses Problem zu lösen.

Die allgemeine Idee ist, dass Sie über "Manager" verfügen, die den **erwarteten Zustand**erhalten. Dieser Status kann lauten: "Ich möchte zwei Instanzen meiner Web-App ausführen und Port 80 verfügbar machen." Die Vorgesetzten betrachten dann alle Computer im Cluster und delegieren die Arbeit an die Worker-Knoten. Die Manager überwachen Änderungen (z. b. einen Containerstatus) und stellen dann fest, dass der **tatsächliche Zustand** den erwarteten Zustand widerspiegelt.

## <a name="cloud-native-computing-foundation-projects"></a>Cloud Native Computing Foundation-Projekte

Cncf ist ein herstellerneutrales Zuhause für verschiedene Open Source-Projekte, einschließlich Kubernetes, Prometheus, Gesandter, linkerd, NATs und mehr! Hier können Sie die vollständig [gestaffelten und aufgestuften Projekte](https://www.cncf.io/projects/) und das gesamte [cncf-quer](https://landscape.cncf.io/)Format anzeigen. Es gibt viele Projekte, die Ihnen helfen, Probleme im Zusammenhang mit Überwachung, Protokollierung, Sicherheit, Abbild Registrierungen, Messaging und mehr zu lösen.

Wenn Sie also noch nicht mit der Container Landschaft und der cloudbasierten Anwendungsentwicklung vertraut sind, Willkommen! Stellen Sie eine Verbindung mit der Community her, stellen Sie Fragen, und halten Sie Ihr Lernen! Wir freuen uns auf Sie!

## <a name="working-with-docker-in-vs-code"></a>Arbeiten mit docker in vs Code

Weitere Informationen zur Verwendung der Docker-vs Code Erweiterung finden Sie hier:

- [Übersicht über die vs Code docker-Erweiterung](https://code.visualstudio.com/docs/containers/overview)
- [Beginnen Sie mit Node.js](https://code.visualstudio.com/docs/containers/quickstart-node)
- [Erste Schritte mit Python](https://code.visualstudio.com/docs/containers/quickstart-python)
- [Erste Schritte mit .NET Core](https://code.visualstudio.com/docs/containers/quickstart-aspnet-core)
- [Debuggen von containerisierten apps](https://code.visualstudio.com/docs/containers/debug-common)

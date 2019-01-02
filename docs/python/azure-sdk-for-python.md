---
title: Azure-SDK für Python
description: Mit dem Azure SDK für Python können Microsoft Azure-Dienste von Python-Anwendungen genutzt werden, die auf beliebigen Plattformen ausgeführt werden.
ms.date: 12/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: b9c8f5193e55d86ea4ff5e4d68fb7a66a1044d2e
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062883"
---
# <a name="consume-azure-services-using-the-azure-sdk-for-python"></a>Nutzen von Azure-Diensten mithilfe des Azure SDK für Python

Das Azure SDK für Python vereinfacht die Nutzung und Verwaltung von Microsoft Azure-Diensten in Anwendungen unter Windows, MacOS und Linux.

## <a name="installation"></a>Installation

Das Azure SDK wird über den [Python-Paketindex](https://pypi.python.org/pypi/azure) installiert.

Installieren Sie die **neueste stabile Version** (unterstützt Python 2.7 und 3.x) wie folgt:

```command
pip install azure
```

Sie können auch den entsprechenden Artikel der Azure-Dokumentation lesen: [Installieren von Python und SDK](https://docs.microsoft.com/azure/python-how-to-install/).

## <a name="documentation"></a>Dokumentation

Das [Python Developer Center](https://docs.microsoft.com/python/azure/?view=azure-python) umfasst ebenfalls eine Reihe nützlicher Ressourcen für das Azure SDK für Python, darunter eine Reihe von Tutorials:

- [Erstellen von Web-Apps für Azure App Service unter Linux](/azure/app-service/containers/quickstart-python)
- [Blobspeicher](/azure/storage/blobs/storage-quickstart-blobs-python)
- [Tabellenspeicher](/azure/cosmos-db/table-storage-how-to-use-python)
- [Warteschlangenspeicher](/azure/storage/storage-python-how-to-use-queue-storage)
- [Azure Cosmos DB](/azure/cosmos-db/sql-api-python-application)
- [Service Bus-Warteschlangen](/azure/service-bus-messaging/service-bus-python-how-to-use-queues)
- [Service Bus-Themen und -Abonnements](/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)
- [Dienstverwaltung](/azure/cloud-services/cloud-services-python-how-to-use-service-management)

Bei öffentlichen APIs ohne Dokumentation sind die Komponententests im [GitHub-Repository für das SDK](https://github.com/Azure/azure-sdk-for-python) eine gute Informationsquelle:

- [Komponententests für Speicher](https://github.com/Azure/azure-storage-python/tree/master/tests)
- [Komponententests für Service Bus](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicebus/tests)
- [Komponententests für die Dienstverwaltung](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicemanagement-legacy/tests)

## <a name="support"></a>Unterstützung

Das GitHub-Repository für das SDK befindet sich unter [https://github.com/Azure/azure-sdk-for-python](https://github.com/Azure/azure-sdk-for-python).

Wenn Ihnen Fehler auffallen oder Sie Fragen zur Verwendung des SDK haben, [melden Sie Probleme im Repository](https://github.com/Azure/azure-sdk-for-python/issues).

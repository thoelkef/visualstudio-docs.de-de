---
title: Azure SDK für Python | Microsoft-Dokumentation
description: Mit dem Azure SDK für Python können Microsoft Azure-Dienste von Python-Anwendungen genutzt werden, die auf beliebigen Plattformen ausgeführt werden.
ms.custom: ''
ms.date: 01/22/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: 3f03ca08dddb90f6eb86a439f7f92307df3b4335
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
---
# <a name="azure-sdk-for-python"></a>Azure-SDK für Python

Das Azure SDK für Python vereinfacht die Nutzung und Verwaltung von Microsoft Azure-Diensten in Anwendungen unter Windows, Mac OS X und Linux.

## <a name="installation"></a>Installation

Das Azure SDK wird über den [Python-Paketindex](https://pypi.python.org/pypi/azure) installiert.

Installieren Sie die **neueste stabile Version** (unterstützt Python 2.7 und 3.x) wie folgt:

```command
pip install azure
```

Sie können auch den entsprechenden Artikel der Azure-Dokumentation lesen: [Installieren von Python und SDK](https://docs.microsoft.com/azure/python-how-to-install/).

## <a name="documentation"></a>Dokumentation

Unter [azure-sdk-for-python.readthedocs.org](http://azure-sdk-for-python.readthedocs.org/en/latest/index.html) finden Sie die entsprechende Dokumentation.

Das [Python Developer Center](http://azure.microsoft.com/develop/python/) umfasst ebenfalls eine Reihe nützlicher Ressourcen für das Azure SDK für Python, darunter eine Reihe von Tutorials:

- Erstellen von Web-Apps mit [Django](/azure/app-service-web/web-sites-python-create-deploy-django-app) [Flask](/azure/app-service-web/web-sites-python-create-deploy-flask-app) und [Bottle](/azure/app-service-web/web-sites-python-create-deploy-bottle-app).
- [Blobspeicher](/azure/storage/storage-python-how-to-use-blob-storage)
- [Tabellenspeicher](/azure/storage/storage-python-how-to-use-table-storage)
- [Warteschlangenspeicher](/azure/storage/storage-python-how-to-use-queue-storage)
- [Azure Cosmos DB](/azure/cosmos-db/sql-api-python-application)
- [Service Bus-Warteschlangen](/azure/service-bus-messaging/service-bus-python-how-to-use-queues)
- [Service Bus-Themen/-Abonnements](/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)
- [Dienstverwaltung](/azure/cloud-services/cloud-services-python-how-to-use-service-management)

Bei öffentlichen APIs ohne Dokumentation sind die Komponententests im [GitHub-Repository für das SDK](https://github.com/Azure/azure-sdk-for-python) eine gute Informationsquelle:

- [Komponententests für Speicher](https://github.com/Azure/azure-storage-python/tree/master/tests)
- [Komponententests für Service Bus](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicebus/tests)
- [Komponententests für die Dienstverwaltung](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicemanagement-legacy/tests)
- [Komponententests für die Ressourcenverwaltung](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-mgmt/tests)

## <a name="support"></a>Unterstützung

Das Git-Repository für das SDK befindet sich unter [https://github.com/Azure/azure-sdk-for-python](https://github.com/Azure/azure-sdk-for-python).

Wenn Ihnen Fehler auffallen oder Sie Fragen zur Verwendung des SDK haben, [melden Sie Probleme im Repository](https://github.com/Azure/azure-sdk-for-python/issues).

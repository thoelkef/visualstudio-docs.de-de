---
title: Speichern von Daten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- DataRow.RowState
- DataSet.GetChanges
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- DBDirect methods
- updating data
- data [Visual Studio], saving
- TableAdapter DBDirect methods
- databases, updating
- TableAdapter.Update method
- data [Visual Studio], updating
- saving data
- updating databases
ms.assetid: 21d2b115-62e4-4ac9-a873-dcbb535b8af8
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 14ff0e62608c3e2ab0c72366d9544f1d1309737a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523347"
---
# <a name="saving-data"></a>Speichern von Daten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Speichern von Daten ist, dass der Vorgang der Daten im Datenmodell einer Anwendung an den ursprünglichen Datenspeicher, in der Regel einer relationalen Datenbank wie SQL Server geändert.  
  
 Aktualisieren einer Datenquelle über ein Datenmodell ist in der Regel ein zweistufiger Prozess. Der erste Schritt ist das Datenmodell mit neuen Informationen aktualisieren, neue Datensätze, geänderten oder gelöschten Datensätzen. Im zweite Schritt werden die Änderungen in Ihrem Datenmodell in der Datenbank zu speichern.  
  
 Die folgenden Themen beschreiben die Konzepte und Aufgaben im Zusammenhang mit Daten zu speichern.  
  
## <a name="related-topics"></a>Verwandte Themen  
 [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)  
 Bietet einen Überblick darüber, wie Änderungen in einem Dataset vorgenommen werden und wie das Dataset Informationen zu Änderungen nachverfolgt, um diese Änderungen in einer Datenbank zu speichern.  
  
 [Speichern von Entitätsdaten](../data-tools/saving-entity-data.md)  
 Beschreibt das Speichern von Änderungen in [ADO.NET Entity Framework](http://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205) und [WCF Data Services 4.5](http://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a) Anwendungen.
---
title: 'Vorgehensweise: Bearbeiten von TableAdapter-Abfragen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vbData.Microsoft.VSDesigner.DataSource.DbSource
- vbdata.Microsoft.VSDesigner.DataSource.DbSource
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- queries [Visual Basic], editing
- TableAdapters, editing queries
- data [Visual Studio], TableAdapters
- editing queries
ms.assetid: aac7b7b4-bd91-4225-95d4-a07643568c43
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 14157d10f105c6f3a1e95442edfe18bfd3aebd6e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513941"
---
# <a name="how-to-edit-tableadapter-queries"></a>Gewusst wie: Bearbeiten von TableAdapter-Abfragen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TableAdapter-Abfragen mit der Bearbeitung der [Bearbeiten von TableAdapters](../data-tools/editing-tableadapters.md) in die **Dataset-Designer**. Sie sollten eine TableAdapter-Abfrage ändern, wenn es nicht mehr die Anforderungen Ihrer Anwendung geeignet ist. (Alternativ können Sie zusätzliche Abfragen auf dem TableAdapter erstellen. Weitere Informationen zum Hinzufügen neuer Abfragen finden Sie unter [Vorgehensweise: Erstellen von TableAdapter-Abfragen](../data-tools/how-to-create-tableadapter-queries.md).)  
  
> [!NOTE]
>  Wenn die [TableAdapter-Konfigurations-Assistenten](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8) öffnet anstelle von der **Konfigurations-Assistenten für TableAdapter-Abfragen**, Sie haben die TableAdapter Main ausgewählt `Fill` Abfrage- und keiner der der Zusätzlichen des TableAdapter-Abfragen. Für Informationen zum Bearbeiten von TableAdapter-Hauptthread `Fill` abzufragen, finden Sie unter [Vorgehensweise: Bearbeiten von TableAdapters](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855).  
  
 ![TableAdapter mit mehreren Abfragen](../data-tools/media/tableadapter.gif "TableAdapter")  
  
### <a name="to-edit-a-tableadapter-query"></a>Bearbeiten eine TableAdapter-Abfrage  
  
1.  Öffnen Sie das Dataset in den **Dataset-Designer**. Weitere Informationen finden Sie unter [Vorgehensweise: Öffnen Sie ein Dataset im Dataset-Designer](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Wählen Sie die TableAdapter-Abfrage, die Sie bearbeiten möchten.  
  
3.  Mit der rechten Maustaste der TableAdapter-Abfrage, und wählen Sie **konfigurieren**.  
  
     Die **Konfigurations-Assistenten für TableAdapter-Abfragen** geöffnet wird, können Sie die Abfrage oder gespeicherte Prozedur für diese Abfrage zu ändern.  
  
4.  Abschließen der **Konfigurations-Assistenten für TableAdapter-Abfragen** mit den Änderungen, die Sie möchten. Weitere Informationen finden Sie unter [Bearbeiten von TableAdapters](../data-tools/editing-tableadapters.md).  
  
## <a name="see-also"></a>Siehe auch  
 [TableAdapters](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)   
 [Herstellen einer Verbindung mit Daten in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Vorbereiten der Anwendung zum Empfangen von Daten](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Abrufen von Daten für Ihre Anwendung](../data-tools/fetching-data-into-your-application.md)   
 [Binden von Steuerelementen an Daten in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Bearbeiten von Daten in Ihrer Anwendung](../data-tools/editing-data-in-your-application.md)   
 [Überprüfen von Daten](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Speichern von Daten](../data-tools/saving-data.md)   
 [Exemplarische Vorgehensweisen für Daten](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)
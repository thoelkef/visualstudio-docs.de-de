---
title: Erweitern der Funktionalität eines TableAdapter | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bbba71e6c1e636abe160036f10c1de1d11004a65
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58956696"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Erweitern der Funktionalität eines TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Sie können die Funktionalität eines TableAdapter erweitern, indem partiellen Klassendatei für die TableAdapter Code hinzufügen.  
  
 Der Code, der einen TableAdapter definiert wird erneut generiert, wenn Änderungen, um den TableAdapter im vorgenommen werden der **Dataset-Designer**, oder wenn ein Assistent ändert die Konfiguration eines TableAdapter. Um zu verhindern, dass Ihr Code beim erneuten Generieren eines TableAdapter gelöscht wird, fügen Sie Code zur Datei für die TableAdapter partielle Klasse.  
  
 Partielle Klassen können Sie Code für eine bestimmte Klasse auf mehrere physische Dateien unterteilt werden. Weitere Informationen finden Sie unter [teilweise](http://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) oder [Partial (Typ)](http://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).  
  
## <a name="locate-tableadapters-in-code"></a>Suchen Sie TableAdapters im code  
 Während TableAdapters mit entworfen werden die **Dataset-Designer**, die TableAdapter-Klassen, die generiert werden, sind nicht geschachtelten Klassen von <xref:System.Data.DataSet>. TableAdapters befinden sich in einem Namespace, die basierend auf den Namen des zugeordneten Datasets des TableAdapter. Wenn Ihre Anwendung ein Dataset Namens enthält, z. B. `HRDataSet`, befindet sich die TableAdapters in die `HRDataSetTableAdapters` Namespace. (Die Benennungskonvention folgt diesem Muster: *DatasetName* + `TableAdapters`).  
  
 Im folgende Beispiel wird davon ausgegangen, einen TableAdapter namens `CustomersTableAdapter`befindet sich in einem Projekt mit `NorthwindDataSet`.  
  
#### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Um eine partielle Klasse für einen TableAdapter zu erstellen.  
  
1.  Fügen Sie eine neue Klasse hinzu, indem Sie auf die **Projekt** Menü und auswählen**Klasse hinzufügen**.  
  
2.  Nennen Sie die Klasse `CustomersTableAdapterExtended`.  
  
3.  Wählen Sie **Hinzufügen** aus.  
  
4.  Ersetzen Sie den Code mit den richtigen Namespace und den Namen der partiellen Klasse für das Projekt wie folgt:  
  
     [!code-csharp[VbRaddataTableAdapters#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/CustomersTableAdapterExtended.cs#2)]
     [!code-vb[VbRaddataTableAdapters#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/CustomersTableAdapterExtended.vb#2)]  
  
## <a name="see-also"></a>Siehe auch  
 [Füllen von Datasets mit TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)

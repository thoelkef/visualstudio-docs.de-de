---
title: Eine oder mehrere der ausgewählten Elemente enthält einen Datentyp, der vom Designer nicht unterstützt | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 42a04d4f3eb75f8ca3a922094e9beb245e6c0ed9
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704945"
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Mindestens eines der ausgewählten Elemente enthält einen Datentyp, der nicht vom Designer unterstützt wird.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine oder mehrere Elemente aus gezogen **Server-Explorer**/**Datenbank-Explorer** auf die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] enthält einen Datentyp, der von nicht unterstützt wird die [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] (z. b. [CLR-benutzerdefinierte Typen](https://msdn.microsoft.com/library/9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2)).  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1. Erstellen Sie eine auf der gewünschten Tabelle basierende Ansicht, in der der nicht unterstützte Datentyp nicht enthalten ist.  
  
2. Ziehen Sie die Ansicht von **Server-Explorer**/**Datenbank-Explorer** in den Designer.  
  
## <a name="see-also"></a>Siehe auch  
 [LINQ to SQL-Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Exemplarische Vorgehensweise: Erstellen von LINQ to SQL-Klassen (O / R-Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)

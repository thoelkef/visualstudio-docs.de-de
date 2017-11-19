---
title: "Ein oder mehrere ausgewählte Elemente enthalten einen Datentyp, der vom Designer nicht unterstützt wird | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 31e42bfcaf8904932d4ea864a608c943f638428c
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2017
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Mindestens eines der ausgewählten Elemente enthält einen Datentyp, der nicht vom Designer unterstützt wird.
Eine oder mehrere Elemente aus gezogen **Server-Explorer**/**Datenbank-Explorer** auf die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] enthält einen Datentyp, der von nicht unterstützt wird die [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] (z. B. [Benutzerdefinierte CLR-Typen](http://msdn.microsoft.com/Library/9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2)).  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1.  Erstellen Sie eine auf der gewünschten Tabelle basierende Ansicht, in der der nicht unterstützte Datentyp nicht enthalten ist.  
  
2.  Ziehen Sie die Ansicht von **Server-Explorer**/**Datenbank-Explorer** in den Designer.  
  
## <a name="see-also"></a>Siehe auch
[O/R-Designer-Nachrichten](../data-tools/o-r-designer-messages.md)  
[LINQ to SQL-tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
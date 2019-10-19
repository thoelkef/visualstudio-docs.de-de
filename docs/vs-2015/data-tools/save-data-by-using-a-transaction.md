---
title: Speichern von Daten mithilfe einer Transaktion | Microsoft-Dokumentation
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
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85f3584073523e748168faf569aa918ba912fbf8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652837"
---
# <a name="save-data-by-using-a-transaction"></a>Speichern von Daten mithilfe von Transaktionen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie speichern Daten in einer Transaktion, indem Sie den <xref:System.Transactions>-Namespace verwenden. Verwenden Sie das <xref:System.Transactions.TransactionScope>-Objekt, um an einer Transaktion teilzunehmen, die automatisch für Sie verwaltet wird.

 Projekte werden nicht mit einem Verweis auf die System. Transactions-Assembly erstellt. Daher müssen Sie manuell einen Verweis auf Projekte hinzufügen, die Transaktionen verwenden.

> [!NOTE]
> Der <xref:System.Transactions>-Namespace wird in Windows 2000 oder höher unterstützt.

 Die einfachste Möglichkeit, eine Transaktion zu implementieren, besteht darin, ein <xref:System.Transactions.TransactionScope> Objekt in einer `using`-Anweisung zu instanziieren. (Weitere Informationen finden Sie unter [using-Anweisung](https://msdn.microsoft.com/library/665d1580-dd54-4e96-a9a9-6be2a68948f1)und [using-Anweisung](https://msdn.microsoft.com/library/afc355e6-f0b9-4240-94dd-0d93f17d9fc3).) Der Code, der in der `using`-Anweisung ausgeführt wird, nimmt an der Transaktion teil.

 Um einen Commit für die Transaktion durchzusetzen, wenden Sie die <xref:System.Transactions.TransactionScope.Complete%2A>-Methode als letzte Anweisung im Using-Block an.

 Um ein Rollback für die Transaktion auszuführen, lösen Sie eine Ausnahme aus, bevor Sie die <xref:System.Transactions.TransactionScope.Complete%2A>-Methode aufrufen.

 Weitere Informationen finden Sie unter [Speichern von Daten in einer Transaktion](../data-tools/save-data-in-a-transaction.md).

### <a name="to-add-a-reference-to-the-systemtransactions-dll"></a>So fügen Sie einen Verweis auf die System. Transactions-dll hinzu

1. Wählen Sie im Menü **Projekt** die Option **Verweis hinzufügen**aus.

2. Wählen Sie auf der Registerkarte **.net** (Registerkarte**SQL Server** für SQL Server Projekte) die Option **System. Transactions**aus, und klicken Sie dann auf **OK**.

     Dem Projekt wird ein Verweis auf "System. Transactions. dll" hinzugefügt.

### <a name="to-save-data-in-a-transaction"></a>So speichern Sie Daten in einer Transaktion

- Fügen Sie Code hinzu, um Daten in der using-Anweisung zu speichern, die die Transaktion enthält. Der folgende Code zeigt, wie ein <xref:System.Transactions.TransactionScope>-Objekt in einer using-Anweisung erstellt und instanziiert wird:

     [!code-csharp[VbRaddataSaving#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#11)]
     [!code-vb[VbRaddataSaving#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#11)]

## <a name="see-also"></a>Siehe auch
 [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)

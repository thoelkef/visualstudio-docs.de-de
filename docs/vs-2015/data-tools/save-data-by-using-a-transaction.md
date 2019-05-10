---
title: Speichern von Daten mithilfe von Transaktion | Microsoft-Dokumentation
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 260396123f806e7c37b91ff4aca643a05853676f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425087"
---
# <a name="save-data-by-using-a-transaction"></a>Speichern von Daten mithilfe von Transaktionen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Speichern Sie Daten in einer Transaktion mithilfe der <xref:System.Transactions> Namespace. Verwenden der <xref:System.Transactions.TransactionScope> Objekt, das an einer Transaktion teilnehmen, die automatisch für Sie verwaltet wird.  
  
 Projekte werden nicht mit einem Verweis auf die System.Transactions-Assembly erstellt, daher müssen Sie manuell einen Verweis zu Projekten hinzufügen, die Transaktionen verwenden.  
  
> [!NOTE]
> Die <xref:System.Transactions> Namespace wird in Windows 2000 oder höher unterstützt.  
  
 Die einfachste Möglichkeit zum Implementieren einer Transaktions ist die Instanziierung einer <xref:System.Transactions.TransactionScope> -Objekt in ein `using` Anweisung. (Weitere Informationen finden Sie unter [Using-Anweisung](http://msdn.microsoft.com/library/665d1580-dd54-4e96-a9a9-6be2a68948f1), und [using-Anweisung](http://msdn.microsoft.com/library/afc355e6-f0b9-4240-94dd-0d93f17d9fc3).) Der Code, in wird, der `using` Anweisung, die in der Transaktion beteiligt ist.  
  
 Aufrufen, um die Transaktion einen Commit auszuführen, die <xref:System.Transactions.TransactionScope.Complete%2A> Methode als die letzte Anweisung in der mit blockiert.  
  
 Um ein Rollback die Transaktion, eine Ausnahme vor dem Aufrufen der <xref:System.Transactions.TransactionScope.Complete%2A> Methode.  
  
 Weitere Informationen finden Sie unter [Speichern von Daten in einer Transaktion](../data-tools/save-data-in-a-transaction.md).  
  
### <a name="to-add-a-reference-to-the-systemtransactions-dll"></a>Einen Verweis auf die System.Transactions-Dll hinzufügen  
  
1. Auf der **Projekt** , wählen Sie im Menü **Verweis hinzufügen**.  
  
2. Auf der **.NET** Registerkarte (**SQL Server** Registerkarte für SQL Server-Projekte), wählen **System.Transactions**, und wählen Sie dann **OK**.  
  
     Ein Verweis auf "System.Transactions.dll" wird dem Projekt hinzugefügt.  
  
### <a name="to-save-data-in-a-transaction"></a>Zum Speichern von Daten in einer Transaktion  
  
- Fügen Sie Code zum Speichern von Daten innerhalb des using-Anweisung, die Transaktion enthält. Der folgende Code zeigt das Erstellen und Instanziieren einer <xref:System.Transactions.TransactionScope> Objekts in einer using Anweisung:  
  
     [!code-csharp[VbRaddataSaving#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#11)]
     [!code-vb[VbRaddataSaving#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#11)]  
  
## <a name="see-also"></a>Siehe auch  
 [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)

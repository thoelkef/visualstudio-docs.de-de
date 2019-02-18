---
title: 'Vorgehensweise: Speichern von Daten mithilfe einer Transaktion'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8d5d47cfc21b0aebef884fade422600be2beeb58
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55924369"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Vorgehensweise: Speichern von Daten mithilfe einer Transaktion

Speichern Sie Daten in einer Transaktion mithilfe der <xref:System.Transactions> Namespace. Verwenden der <xref:System.Transactions.TransactionScope> Objekt, das an einer Transaktion teilnehmen, die automatisch für Sie verwaltet wird.

Projekte werden nicht erstellt, mit einem Verweis auf die *System.Transactions* Assembly, daher müssen Sie manuell einen Verweis zu Projekten hinzufügen, die Transaktionen verwenden.

Die einfachste Möglichkeit zum Implementieren einer Transaktions ist die Instanziierung einer <xref:System.Transactions.TransactionScope> -Objekt in ein `using` Anweisung. (Weitere Informationen finden Sie unter [Using-Anweisung](/dotnet/visual-basic/language-reference/statements/using-statement), und [Using-Anweisung](/dotnet/csharp/language-reference/keywords/using-statement).) Der Code, in wird, der `using` Anweisung, die in der Transaktion beteiligt ist.

Aufrufen, um die Transaktion einen Commit auszuführen, die <xref:System.Transactions.TransactionScope.Complete%2A> Methode als die letzte Anweisung in der mit blockiert.

Um ein Rollback die Transaktion, eine Ausnahme vor dem Aufrufen der <xref:System.Transactions.TransactionScope.Complete%2A> Methode.

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>Einen Verweis auf die "System.Transactions.dll" hinzufügen

1.  Auf der **Projekt** , wählen Sie im Menü **Verweis hinzufügen**.

2.  Auf der **.NET** Registerkarte (**SQL Server** Registerkarte für SQL Server-Projekte), wählen **System.Transactions**, und wählen Sie dann **OK**.

     Ein Verweis auf *"System.Transactions.dll"* wird dem Projekt hinzugefügt.

## <a name="to-save-data-in-a-transaction"></a>Zum Speichern von Daten in einer Transaktion

-   Fügen Sie Code zum Speichern von Daten innerhalb des using-Anweisung, die Transaktion enthält. Der folgende Code zeigt das Erstellen und Instanziieren einer <xref:System.Transactions.TransactionScope> Objekts in einer using Anweisung:

     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]

## <a name="see-also"></a>Siehe auch

- [Rückspeichern von Daten in der Datenbank](../data-tools/save-data-back-to-the-database.md)
- [Exemplarische Vorgehensweise: Speichern von Daten im Rahmen einer Transaktion](../data-tools/save-data-in-a-transaction.md)
---
title: Beispielprojekt zum Erstellen von Komponententests in Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: sample
helpviewer_keywords:
- unit test sample [Visual Studio]
- unit tests, samples
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0f6ab04990292715932c652e2e275787447761ca
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="sample-project-for-creating-unit-tests"></a>Beispielprojekt zum Erstellen von Komponententests

Dieser Beispielcode wird zur Verwendung in den folgenden exemplarischen Vorgehensweisen bereitgestellt:

- [Exemplarische Vorgehensweise: Erstellen und Ausführen von Komponententests für verwalteten Code](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md). Diese exemplarische Vorgehensweise führt Sie durch die Schritte zum Erstellen und Anpassen von Komponententests, deren Ausführung und das Überprüfen der Testergebnisse.

- [Exemplarische Vorgehensweise: Verwenden des Befehlszeilen-Testhilfsprogramms](http://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867). In dieser exemplarischen Vorgehensweise verwenden Sie das Befehlszeilenhilfsprogramm MSTest.exe, um Tests auszuführen und Ergebnisse anzuzeigen.

## <a name="sample-code"></a>Beispielcode

Der einzige absichtliche Fehler in diesem Beispiel ist, dass die In-Debit-Methode „m_balance += amount“ ein Minuszeichen statt eines Pluszeichens vor dem Gleichheitszeichen haben sollte.

```csharp
using System;

namespace BankAccountNS
{
    /// <summary>
    /// Bank Account demo class.
    /// </summary>
    public class BankAccount
    {
        private string m_customerName;

        private double m_balance;

        private bool m_frozen = false;

        private BankAccount()
        {
        }

        public BankAccount(string customerName, double balance)
        {
            m_customerName = customerName;
            m_balance = balance;
        }

        public string CustomerName
        {
            get { return m_customerName; }
        }

        public double Balance
        {
            get { return m_balance; }
        }

        public void Debit(double amount)
        {
            if (m_frozen)
            {
                throw new Exception("Account frozen");
            }

            if (amount > m_balance)
            {
                throw new ArgumentOutOfRangeException("amount");
            }

            if (amount < 0)
            {
                throw new ArgumentOutOfRangeException("amount");
            }

            m_balance += amount; // intentionally incorrect code
        }

        public void Credit(double amount)
        {
            if (m_frozen)
            {
                throw new Exception("Account frozen");
            }

            if (amount < 0)
            {
                throw new ArgumentOutOfRangeException("amount");
            }

            m_balance += amount;
        }

        private void FreezeAccount()
        {
            m_frozen = true;
        }

        private void UnfreezeAccount()
        {
            m_frozen = false;
        }

        public static void Main()
        {
            BankAccount ba = new BankAccount("Mr. Bryan Walton", 11.99);

            ba.Credit(5.77);
            ba.Debit(11.22);
            Console.WriteLine("Current balance is ${0}", ba.Balance);
        }
    }
}
```

/* Die in den Beispielen genannten Unternehmen, Organisationen, Produkte, Domänennamen, E-Mail-Adressen, Logos, Personen, Orte und Ereignisse sind frei erfunden. Jede Ähnlichkeit mit tatsächlichen Firmen, Organisationen, Produkten, Domänen, Personen, Orten, Ereignissen, E-Mail-Adressen und Logos ist rein zufällig. \*/

## <a name="working-with-the-code"></a>Arbeiten mit dem Code

Um mit diesem Code zu arbeiten, müssen Sie dafür zuerst in Visual Studio ein Projekt erstellen. Führen Sie die Schritte im Abschnitt „Vorbereiten der exemplarischen Vorgehensweise“ unter [Exemplarische Vorgehensweise: Erstellen und Ausführen von Komponententests für verwalteten Code](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) aus.

## <a name="see-also"></a>Siehe auch

- [Exemplarische Vorgehensweise: Erstellen und Ausführen von Komponententests für verwalteten Code](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)
- [Exemplarische Vorgehensweise: Verwenden des Befehlszeilen-Testprogramms](http://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867)

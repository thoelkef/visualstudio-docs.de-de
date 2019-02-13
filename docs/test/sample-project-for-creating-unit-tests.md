---
title: Beispielcode zum Erstellen von Komponententests
description: Dieser Artikel enthält Beispielcode, der zum Testen von Komponententests in Visual Studio verwendet werden kann.
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- unit test sample [Visual Studio]
- unit tests, samples
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b914101a98f3eb40c479a3a39556e7e4138504c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55929725"
---
# <a name="sample-code-for-testing"></a>Beispielcode für Tests

Dieser Beispielcode enthält die Klasse *BankAccount* mit verschiedenen Methoden, die in Komponententests getestet werden können.

Der Code wird in den folgenden exemplarischen Vorgehensweisen verwendet:

- [Erstellen und Ausführen von Komponententests für verwalteten Code](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md): Diese exemplarische Vorgehensweise führt Sie durch die Schritte zum Erstellen und Anpassen von Komponententests, deren Ausführung und das Überprüfen der Testergebnisse.
- [Verwenden des Befehlszeilen-Testprogramms](https://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867): In dieser exemplarischen Vorgehensweise verwenden Sie das Befehlszeilenhilfsprogramm *MSTest.exe*, um Tests auszuführen und Ergebnisse anzuzeigen.

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

## <a name="create-the-project"></a>Erstellen eines Projekts

Erstellen Sie zum Arbeiten mit diesem Code zunächst ein Projekt dafür in Visual Studio. Führen Sie die Schritte zum Erstellen des Projekts unter [Exemplarische Vorgehensweise: Erstellen und Ausführen von Komponententests für verwalteten Code](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md#create-a-project-to-test) aus.

## <a name="see-also"></a>Siehe auch

- [Exemplarische Vorgehensweise: Erstellen und Ausführen von Komponententests für verwalteten Code](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)
- [Exemplarische Vorgehensweise: Verwenden des Befehlszeilen-Testprogramms](https://msdn.microsoft.com/Library/52c11992-9e94-4067-a4b7-59f19d69d867)

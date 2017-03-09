---
title: "Beispielprojekt zum Erstellen von Komponententests | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Komponententestbeispiel [Visual Studio]"
  - "Komponententests, Beispiele"
ms.assetid: db80aaf2-0652-4d3f-a8c5-2a98fd8502a2
caps.latest.revision: 30
caps.handback.revision: 30
ms.author: "mlearned"
manager: "douge"
---
# Beispielprojekt zum Erstellen von Komponententests
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieser Beispielcode wird zur Verwendung in den folgenden exemplarischen Vorgehensweisen bereitgestellt:  
  
-   [Exemplarische Vorgehensweise: Erstellen und Ausführen von Komponententests für verwalteten Code](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md).  Diese exemplarische Vorgehensweise führt Sie durch die Schritte zum Erstellen und Anpassen von Komponententests, deren Ausführung und das Überprüfen der Testergebnisse.  
  
-   [Walkthrough: Run tests and view code coverage](http://msdn.microsoft.com/de-de/d4aab8e2-2140-4975-b4e3-41ef3fa944c8).  Diese exemplarische Vorgehensweise veranschaulicht, wie Sie Codeabdeckungsdaten anzeigen, die den Anteil des Projektcodes zeigen, der getestet wird.  
  
-   [Exemplarische Vorgehensweise: Verwenden des Befehlszeilen\-Testprogramms](../Topic/Walkthrough:%20using%20the%20command-line%20test%20utility.md).  In dieser exemplarischen Vorgehensweise verwenden Sie das Befehlszeilenhilfsprogramm MSTest.exe, um Tests auszuführen und Ergebnisse anzuzeigen.  
  
## Beispielcode  
 Der einzige absichtliche Fehler in diesem Beispiel ist, dass die In\-Debit\-Methode „m\_balance \+\= amount“ ein Minuszeichen statt eines Pluszeichens vor dem Gleichheitszeichen haben sollte.  
  
```  
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
  
 \/\* Die in den Beispielen genannten Unternehmen, Organisationen, Produkte, Domänennamen, E\-Mail\-Adressen, Logos, Personen, Orte und Ereignisse sind frei erfunden.  Jede Ähnlichkeit mit tatsächlichen Firmen, Organisationen, Produkten, Domänen, Personen, Orten, Ereignissen, E\-Mail\-Adressen und Logos ist rein zufällig.  \*\/  
  
## Arbeiten mit dem Code  
 Um mit diesem Code zu arbeiten, müssen Sie dafür zuerst in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ein Projekt erstellen.  Führen Sie die Schritte im Abschnitt „Vorbereiten der exemplarischen Vorgehensweise“ unter [Exemplarische Vorgehensweise: Erstellen und Ausführen von Komponententests für verwalteten Code](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) aus.  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Erstellen und Ausführen von Komponententests für verwalteten Code](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)   
 [Walkthrough: Run tests and view code coverage](http://msdn.microsoft.com/de-de/d4aab8e2-2140-4975-b4e3-41ef3fa944c8)   
 [Exemplarische Vorgehensweise: Verwenden des Befehlszeilen\-Testprogramms](../Topic/Walkthrough:%20using%20the%20command-line%20test%20utility.md)
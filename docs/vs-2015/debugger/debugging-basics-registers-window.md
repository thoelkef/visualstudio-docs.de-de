---
title: 'Grundlagen des Debuggens: Fenster registriert | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Registers window, about Registers window
- debugging [Visual Studio], Registers window
ms.assetid: ab354047-053e-4f94-8ac1-26e761442b6f
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa204726632f55ad6aa1b79e0b9d071864a5dcaa
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210300"
---
# <a name="debugging-basics-registers-window"></a>Grundlagen des Debuggens: Fenster "Register"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die **registriert** Fenster ist nur verfügbar, wenn Debuggen auf Adressebene im aktiviert ist die **Optionen** Dialogfeld **Debuggen** Knoten.  
  
 Register sind bestimmte Speicherorte innerhalb des Prozessors (CPU), die verwendet werden, um kleine Mengen an Daten zu speichern, die der Prozessor gegenwärtig verarbeitet. Beim Kompilieren oder Interpretieren von Quellcode werden Anweisungen erzeugt, die Daten je nach Bedarf vom Arbeitsspeicher in die Register und wieder zurück verschieben. Im Vergleich zu Daten im Arbeitsspeicher ist der Zugriff auf Daten in Registern sehr viel schneller möglich. Demnach wird Code, der es dem Prozessor ermöglicht, Daten in Registern zu speichern und wiederholt darauf zuzugreifen, wesentlich schneller ausgeführt, als Code, bei dem der Prozessor gezwungen ist, die Register ständig zu laden bzw. zu entladen. Sie sollten die Verwendung von globalen Variablen nach Möglichkeit vermeiden und stattdessen lokale Variablen verwenden, um dem Compiler das Speichern von Daten in Registern sowie das Durchführen weiterer Optimierungen zu erleichtern. Code, der auf diese Weise geschrieben wird, ist für die gute Positionierung von Verweisen bekannt. In einigen Sprachen (beispielsweise C/C++) können Programmierer eine Registervariable deklarieren, die den Compiler anweist, die Variable nach Möglichkeit immer in einem Register zu speichern. Weitere Informationen finden Sie unter [Register-Schlüsselwort](http://msdn.microsoft.com/en-us/5b66905a-2f7f-4918-bb55-5e66d4bc50f9).  
  
 Register können in zwei Gruppen eingeteilt werden: Allzweckregister und spezielle Register für besondere Zwecke. Allzweckregister enthalten Daten für allgemeine Operationen, beispielsweise zum Addieren zweier Zahlen oder für den Verweis auf ein Element in einem Array. Spezielle Register haben einen besonderen Zweck und eine spezielle Bedeutung. Ein gutes Beispiel ist das Aufruflistenzeigerregister, das vom Prozessor verwendet wird, um die Aufrufliste des Programms zu verfolgen. Als Programmierer werden Sie den Stapelzeiger voraussichtlich nicht direkt bearbeiten. Allerdings ist der Stapelzeiger wichtig für eine fehlerfreie Funktionsweise des Programms. Ohne den Stapelzeiger könnte der Prozessor nicht wissen, an welche Position er nach einem Funktionsaufruf zurückkehren soll.  
  
 Die meisten Allzweckregister enthalten nur ein einzelnes Datenelement. Zum Beispiel eine einzelne ganze Zahl, eine einzelne Gleitkommazahl oder ein einzelnes Arrayelement. Einige neuere Prozessoren enthalten dagegen größere Register (Vektorregister), die ein kleines Datenarray enthalten können. Da Vektorregister so viele Daten enthalten, ermöglichen sie ein äußerst schnelles Durchführen von Operationen, die Arrays beinhalten. Vektorregister wurden anfänglich nur auf teuren, leistungsstarken Supercomputern verwendet, doch mittlerweile sind sie auch auf Mikroprozessoren erhältlich, wo sie insbesondere bei umfangreichen Grafikoperationen von großem Vorteil sind.  
  
 Ein Prozessor verfügt in der Regel über zwei Gruppen von Allzweckregistern, wobei eine für Gleitkommaoperationen und die andere für Ganzzahloperationen optimiert ist. Es ist daher nahe liegend, dass diese Register als Gleitkommaregister und als Ganzzahlregister bezeichnet werden.  
  
 Verwalteter Code wird zur Laufzeit in nativen Code kompiliert, der auf die physischen Register des Mikroprozessors zugreift. Die **registriert** diese physischen Register für common Language Runtime oder nativen Code angezeigt. Die **registriert** Fenster zeigt keine Registerinformationen für Skript- oder SQL-Anwendung, da Skriptsprachen und SQL Sprachen sind, die das Konzept der Register nicht unterstützen.  
  
 Weitere Informationen zum Anzeigen der **registriert** Fenster finden Sie unter [mithilfe des Fensters "Register"](../debugger/how-to-use-the-registers-window.md).  
  
 Bei näherer Betrachtung der **registriert** Fenster finden Sie Einträge wie in diesem Beispiel:  
  
```  
EAX = 003110D8  
```  
  
 Das Symbol auf der linken Seite des Gleichheitszeichens (=) ist der Registername (in diesem Fall EAX). Die Zahl auf der rechten Seite des Gleichheitszeichens stellt den Registerinhalt dar.  
  
 Die **registriert** Fenster können Sie mehr als nur View den Inhalt eines Registers zur Verfügung. Wenn Sie sich im Unterbrechungsmodus befinden, können Sie im nativen Code auf den Inhalt eines Registers klicken und den jeweiligen Wert bearbeiten. Dies sollten Sie jedoch nicht willkürlich machen. Solange Sie das zu bearbeitende Register und die darin enthaltenen Daten nicht vollständig verstehen, werden achtlose Bearbeitungen vermutlich einen Systemabsturz oder andere unerwünschte Konsequenzen zur Folge haben. Leider würden detailliertere Erklärungen der Registergruppen der verschiedenen Intel- bzw. Intel-kompatiblen Prozessoren den Rahmen dieser kurzen Einführung sprengen.  
  
## <a name="register-groups"></a>Registergruppen  
 Übersichtlichkeit der **registriert** in Gruppen organisiert Fenster. Wenn Sie mit der rechten Maustaste auf die **registriert** Fenster sehen Sie ein Kontextmenü mit einer Liste von Gruppen, die Sie anzeigen oder ausblenden, ganz nach Wunsch können.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Verwenden Sie das Fenster "Register"](../debugger/how-to-use-the-registers-window.md)   
 [Debugger – Grundlagen](../debugger/debugger-basics.md)






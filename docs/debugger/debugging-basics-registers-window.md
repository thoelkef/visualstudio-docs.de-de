---
title: Über das Fenster "Register" | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, about Registers window
- debugging [Visual Studio], Registers window
ms.assetid: ab354047-053e-4f94-8ac1-26e761442b6f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df01776b5a7f2437c704c2b389c7d0929be5901c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62852264"
---
# <a name="about-the-registers-window-in-visual-studio-c-c-visual-basic-f"></a>Über das Fenster "Register" in Visual Studio (C#, C++, Visual Basic F#)

Das Fenster **Register** ist nur verfügbar, wenn Debuggen auf Adressebene im Dialogfeld **Optionen** im Knoten **Debuggen** aktiviert ist.

 Register sind bestimmte Speicherorte innerhalb des Prozessors (CPU), die verwendet werden, um kleine Mengen an Daten zu speichern, die der Prozessor gegenwärtig verarbeitet. Beim Kompilieren oder Interpretieren von Quellcode werden Anweisungen erzeugt, die Daten je nach Bedarf vom Arbeitsspeicher in die Register und wieder zurück verschieben. Im Vergleich zu Daten im Arbeitsspeicher ist der Zugriff auf Daten in Registern sehr viel schneller möglich. Demnach wird Code, der es dem Prozessor ermöglicht, Daten in Registern zu speichern und wiederholt darauf zuzugreifen, wesentlich schneller ausgeführt, als Code, bei dem der Prozessor gezwungen ist, die Register ständig zu laden bzw. zu entladen. Sie sollten die Verwendung von globalen Variablen nach Möglichkeit vermeiden und stattdessen lokale Variablen verwenden, um dem Compiler das Speichern von Daten in Registern sowie das Durchführen weiterer Optimierungen zu erleichtern. Code, der auf diese Weise geschrieben wird, ist für die gute Positionierung von Verweisen bekannt. In einigen Sprachen (beispielsweise C/C++) können Programmierer eine Registervariable deklarieren, die den Compiler anweist, die Variable nach Möglichkeit immer in einem Register zu speichern. Weitere Informationen hierzu finden Sie unter [register-Schlüsselwort](https://msdn.microsoft.com/library/5b66905a-2f7f-4918-bb55-5e66d4bc50f9).

 Register können in zwei Gruppen eingeteilt werden: Allzweckregister und spezielle Register für besondere Zwecke. Allzweckregister enthalten Daten für allgemeine Operationen, beispielsweise zum Addieren zweier Zahlen oder für den Verweis auf ein Element in einem Array. Spezielle Register haben einen besonderen Zweck und eine spezielle Bedeutung. Ein gutes Beispiel ist das Aufruflistenzeigerregister, das vom Prozessor verwendet wird, um die Aufrufliste des Programms zu verfolgen. Als Programmierer werden Sie den Stapelzeiger voraussichtlich nicht direkt bearbeiten. Allerdings ist der Stapelzeiger wichtig für eine fehlerfreie Funktionsweise des Programms. Ohne den Stapelzeiger könnte der Prozessor nicht wissen, an welche Position er nach einem Funktionsaufruf zurückkehren soll.

 Die meisten Allzweckregister enthalten nur ein einzelnes Datenelement. Zum Beispiel eine einzelne ganze Zahl, eine einzelne Gleitkommazahl oder ein einzelnes Arrayelement. Einige neuere Prozessoren enthalten dagegen größere Register (Vektorregister), die ein kleines Datenarray enthalten können. Da Vektorregister so viele Daten enthalten, ermöglichen sie ein äußerst schnelles Durchführen von Operationen, die Arrays beinhalten. Vektorregister wurden anfänglich nur auf teuren, leistungsstarken Supercomputern verwendet, doch mittlerweile sind sie auch auf Mikroprozessoren erhältlich, wo sie insbesondere bei umfangreichen Grafikoperationen von großem Vorteil sind.

 Ein Prozessor verfügt in der Regel über zwei Gruppen von Allzweckregistern, wobei eine für Gleitkommaoperationen und die andere für Ganzzahloperationen optimiert ist. Es ist daher nahe liegend, dass diese Register als Gleitkommaregister und als Ganzzahlregister bezeichnet werden.

 Verwalteter Code wird zur Laufzeit in nativen Code kompiliert, der auf die physischen Register des Mikroprozessors zugreift. Diese physischen Register für die Common Language Runtime oder nativen Code werden im Fenster **Register** angezeigt. Im Fenster **Register** werden die Registerinformationen für Skript- oder SQL-Anwendungen jedoch nicht angezeigt, da Skriptsprachen und SQL das Konzept der Register nicht unterstützen.

 Weitere Informationen zum Anzeigen des Fensters **Register** finden Sie unter [Verwenden des Fensters „Register“](../debugger/how-to-use-the-registers-window.md).

 Bei näherer Betrachtung der **registriert** Fenster finden Sie Einträge wie z. B. `EAX = 003110D8`.

 Das Symbol links neben der `=` Anmeldung ist der Registername `EAX`, in diesem Fall. Die Zahl auf der rechten Seite des Gleichheitszeichens (`=`) stellt den Registerinhalt dar.

 Das Fenster **Register** bietet neben der Anzeige des Registerinhalts jedoch noch weitere Vorteile. Wenn Sie sich im Unterbrechungsmodus befinden, können Sie im nativen Code auf den Inhalt eines Registers klicken und den jeweiligen Wert bearbeiten. Dies sollten Sie jedoch nicht willkürlich machen. Solange Sie das zu bearbeitende Register und die darin enthaltenen Daten nicht vollständig verstehen, werden achtlose Bearbeitungen vermutlich einen Systemabsturz oder andere unerwünschte Konsequenzen zur Folge haben. Leider würden detailliertere Erklärungen der Registergruppen der verschiedenen Intel- bzw. Intel-kompatiblen Prozessoren den Rahmen dieser kurzen Einführung sprengen.

## <a name="register-groups"></a>Registergruppen

Aus Gründen der Übersichtlichkeit werden Register im Fenster **Register** in Gruppen organisiert. Wenn Sie mit der rechten Maustaste in das Fenster **Register** klicken, wird ein Kontextmenü mit einer Liste von Gruppen geöffnet, die Sie je nach Bedarf ein- oder ausblenden können.

## <a name="register-flags"></a>Registrieren von flags

X86-Intel-Prozessoren können finden Sie in der folgenden Flags der **registriert** Fenster. Während einer Debugsitzung können Sie auch diese Flags bearbeiten.

|Flag|Wert festlegen|
|-|-|
|Überlauf|OV = 1|
|Richtung|UP = 1|
|Interrupt|EI = 1|
|Sign|PL = 1|
|Zero|ZR = 1|
|Zusätzliche carry|AC = 1|
|Parität|PE = 1|
|Ausführen|CY = 1|

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Verwenden des Fensters „Register“](../debugger/how-to-use-the-registers-window.md)
- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
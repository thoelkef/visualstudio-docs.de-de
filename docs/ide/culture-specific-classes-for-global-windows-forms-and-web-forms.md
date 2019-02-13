---
title: Kulturspezifische Klassen für globale Windows Forms und Web Forms
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- globalization [Windows Forms], classes
- Web applications [.NET Framework], globalization
- culture, culture-specific classes
- numbers, international
- localization [Windows Forms], classes
- globalization [Visual Studio], culture-specific classes
- Windows Forms, localization
- international applications [Visual Studio], data formats
- time [Visual Studio], international
- dates [Visual Studio], international
- culture
- international characters
- currency formats
- ASP.NET, globalization
- classes [Visual Studio], culture-specific
- localization [Visual Studio], culture-specific classes
ms.assetid: 0d06a0a4-f887-4f7c-bde7-1d543c06f803
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3fdb46f79d6b300280c6743a368953bac5c5b02d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55933898"
---
# <a name="culture-specific-classes-for-global-windows-forms-and-web-forms"></a>Kulturspezifische Klassen für globale Windows Forms und Web Forms

Jede Kultur verfügt über unterschiedliche Konventionen für die Anzeige von Datumsangaben, Uhrzeiten, Zahlen, Währungen und sonstigen Informationen. Der Namespace <xref:System.Globalization> enthält Klassen, die zum Ändern der Anzeige kulturspezifischer Werte verwendet werden können, z.B.:
- <xref:System.Globalization.DateTimeFormatInfo>
- **Kalender**
- <xref:System.Globalization.NumberFormatInfo>

## <a name="using-the-culture-setting"></a>Verwenden der Kultureinstellung

Verwenden Sie die Kultureinstellung, die entweder in der App oder in der Systemsteuerung unter **Regionale Einstellungen** gespeichert ist, um die Kulturkonventionen zur Laufzeit zu ermitteln und die Informationen entsprechend zu formatieren. Weitere Informationen zum Festlegen der Kultur finden Sie unter [Vorgehensweise: Festlegen der Kultur und Benutzeroberflächenkultur für die Globalisierung von ASP.NET-Webseiten](https://msdn.microsoft.com/Library/76091f86-f967-4687-a40f-de87bd8cc9a0). Klassen, die die Informationen automatisch entsprechend der Kultureinstellung formatieren, werden als *kulturspezifisch* bezeichnet. Einige kulturspezifische Methoden sind
- <xref:System.IFormattable.ToString%2A?displayProperty=fullName>
- <xref:System.Console.WriteLine%2A?displayProperty=fullName>
- <xref:System.String.Format%2A?displayProperty=fullName>

Einige kulturspezifische Funktionen (in Visual Basic) sind `MonthName` und `WeekDayName`.

Zum Beispiel zeigt der folgende Code, wie Sie die Methode <xref:System.IFormattable.ToString%2A> zum Formatieren von Währungen für die aktuelle Kultur verwenden können:

```vb
' Put the Imports statements at the beginning of the code module
Imports System.Threading
Imports System.Globalization
' Display a number with the culture-specific currency formatting
Dim MyInt As Integer = 100
Console.WriteLine(MyInt.ToString("C", Thread.CurrentThread.CurrentCulture))
```

```csharp
// Put the using statements at the beginning of the code module
using System.Threading;
using System.Globalization;
// Display a number with the culture-specific currency formatting
int myInt = 100;
Console.WriteLine(myInt.ToString("C", Thread.CurrentThread.CurrentCulture));
```

Wenn die Kultur auf „fr-FR“ festgelegt ist, wird Folgendes im Ausgabefenster angezeigt:

`100,00`

Wenn die Kultur auf „en-US“ festgelegt ist, wird Folgendes im Ausgabefenster angezeigt:

`$100.00`

## <a name="see-also"></a>Siehe auch

- <xref:System.IFormattable.ToString%2A?displayProperty=fullName>
- <xref:System.Globalization.DateTimeFormatInfo>
- <xref:System.Globalization.NumberFormatInfo>
- <xref:System.Globalization.Calendar>
- <xref:System.Console.WriteLine%2A?displayProperty=fullName>
- <xref:System.String.Format%2A?displayProperty=fullName>
- [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)
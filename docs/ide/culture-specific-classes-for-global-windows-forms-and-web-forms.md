---
title: "Kulturspezifische Klassen für globale Windows Forms und Web Forms | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 3fb3b66548077a2f92289f1a2f02cc8ae77544cc
ms.contentlocale: de-de
ms.lasthandoff: 05/19/2017

---
# <a name="culture-specific-classes-for-global-windows-forms-and-web-forms"></a>Kulturspezifische Klassen für globale Windows Forms und Web Forms
Jede Kultur verfügt über unterschiedliche Konventionen für die Anzeige von Datumsangaben, Uhrzeiten, Zahlen, Währungen und sonstigen Informationen. Der Namespace <xref:System.Globalization> enthält Klassen, die zum Ändern der Anzeige kulturspezifischer Werte verwendet werden können, z.B. <xref:System.Globalization.DateTimeFormatInfo>, **Calendar** und <xref:System.Globalization.NumberFormatInfo>.  
  
## <a name="using-the-culture-setting"></a>Verwenden der Kultureinstellung  
 In den meisten Fällen werden Sie jedoch die Kultureinstellung verwenden, die entweder in der Anwendung oder in der Systemsteuerung unter **Regionale Einstellungen** gespeichert ist, um die Konventionen zur Laufzeit automatisch zu ermitteln und die Informationen entsprechend zu formatieren. Weitere Informationen zum Festlegen der Kultur finden Sie unter [Gewusst wie: Festlegen der Kultur und Benutzeroberflächenkultur für die Windows Forms-Globalisierung](http://msdn.microsoft.com/en-us/694e049f-0b91-474a-9789-d35124f248f0) oder [Gewusst wie: Festlegen der Kultur und Benutzeroberflächenkultur für die Globalisierung von ASP.NET-Webseiten](http://msdn.microsoft.com/Library/76091f86-f967-4687-a40f-de87bd8cc9a0). Klassen, die die Informationen automatisch entsprechend der Kultureinstellung formatieren, werden als kulturspezifisch bezeichnet. Einige kulturspezifische Methoden sind <xref:System.IFormattable.ToString%2A?displayProperty=fullName>, <xref:System.Console.WriteLine%2A?displayProperty=fullName> und <xref:System.String.Format%2A?displayProperty=fullName>. Einige kulturspezifische Funktionen (in Visual Basic) sind `MonthName` und `WeekDayName`.  
  
 Zum Beispiel zeigt der folgende Code, wie Sie die Methode <xref:System.IFormattable.ToString%2A> zum Formatieren von Währungen für die aktuelle Kultur verwenden können:  
  
```vb#  
' Put the Imports statements at the beginning of the code module  
Imports System.Threading  
Imports System.Globalization  
' Display a number with the culture-specific currency formatting  
Dim MyInt As Integer = 100  
Console.WriteLine(MyInt.ToString("C", Thread.CurrentThread.CurrentCulture))  
  
```  
  
```c#  
// Put the using statements at the beginning of the code module  
using System.Threading;  
using System.Globalization;  
// Display a number with the culture-specific currency formatting  
int myInt = 100;  
Console.WriteLine(myInt.ToString("C", Thread.CurrentThread.CurrentCulture));  
```  
  
 Wenn die Kultur „fr-FR“ festgelegt ist, wird Folgendes im Ausgabefenster angezeigt:  
  
 `100,00`  
  
 Wenn die Kultur „en-US“ festgelegt ist, wird Folgendes im Ausgabefenster angezeigt:  
  
 `$100.00`  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.IFormattable.ToString%2A?displayProperty=fullName>   
 <xref:System.Globalization.DateTimeFormatInfo>   
 <xref:System.Globalization.NumberFormatInfo>   
 <xref:System.Globalization.Calendar>   
 <xref:System.Console.WriteLine%2A?displayProperty=fullName>   
 <xref:System.String.Format%2A?displayProperty=fullName>   
 [Globalisieren und Lokalisieren von Anwendungen](../ide/globalizing-and-localizing-applications.md)

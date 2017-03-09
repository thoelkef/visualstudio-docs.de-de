---
title: "Problembehandlung bei Ausnahmen: System.FormatException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "FormatException-Klasse"
ms.assetid: b2a4f55e-da87-4915-a053-59eb1595993d
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.FormatException
Die <xref:System.FormatException>\-Ausnahme, die von einer Methode ausgelöst wird, die einen Typ analysiert oder formatiert, wenn das Format eines Arguments nicht den Parameterspezifikationen der Methode entspricht.  
  
## In diesem Artikel  
  
## Verursachen von Formatausnahmen  
  
### Formatierung  
 Bei der *Formatting*wird eine Instanz einer Klasse, Struktur oder eines Enumerationswerts in die entsprechende Zeichenfolgendarstellung konvertiert. Die resultierende Zeichenfolge kann dann häufig Benutzern angezeigt oder verwendet werden, um den Status des Objekts zu speichern.  
  
 Z. B. übernimmt <xref:System.Int32.ToString%28System.String%29?displayProperty=fullName> einen Zeichenfolgenparameter, der eine Standard\- oder benutzerdefinierte *Formatzeichenfolge* bestimmt und eine Zeichenfolgendarstellung der Zahl zurückgibt. Die Methode löst eine <xref:System.FormatException> aus. Wenn die Formatzeichenfolge ungültig ist oder nicht unterstützt wird, wird a ausgelöst.  
  
### Kombinierte Formatierung  
 *Kombinierte Formatierung* akzeptiert eine Liste von Objekten und eine kombinierte Formatzeichenfolge als Eingabe. Eine kombinierte Formatzeichenfolge besteht aus festgelegtem Text mit indizierten Platzhaltern, so genannten Formatelementen, die den Objekten in der Liste entsprechen. Der Formatierungsvorgang liefert eine Ergebniszeichenfolge, die sich aus dem ursprünglichen festgelegten Text und der Zeichenfolgendarstellung der Objekte in der Liste zusammensetzt.  
  
 <xref:System.String.Format%2A?displayProperty=fullName>und <xref:System.Console.WriteLine%2A?displayProperty=fullName> sind Beispiele für Methoden der kombinierten Formatierung. Methoden, die kombinierte Formatierung verwenden, lösen eine <xref:System.FormatException> aus, wenn die Formatzeichenfolge ungültig ist oder der Index eines Formatelements kleiner als 0 oder größer oder gleich der Anzahl der Argumente ist.  
  
### Analyse  
 *Analyse* ist der Prozess der Konvertierung einer Zeichenfolge, die einen.NET Framework\-Basistyp in diesen Basistyp darstellt. Beispielsweise wird ein Analysevorgang zum Konvertieren einer Zeichenfolge in eine Gleitkommazahl oder einen Wert für Datum und Uhrzeit verwendet.  
  
 Beispielsweise konvertiert <xref:System.Int32.Parse%28System.String%29?displayProperty=fullName><xref:System.DateTime.Parse%2A> die angegebene Zeichenfolgendarstellung einer Datums\- und Uhrzeitangabe in die entsprechende <xref:System.DateTime> mit kulturabhängigen Formatierungsinformationen im Parameter <xref:System.IformatProvider>. Wenn die Zeichenfolge nicht das richtige Format hat, wird <xref:System.FormatException> ausgelöst.  
  
## Vermeiden von FormatExceptions  
 Der Klassenreferenzartikel <xref:System.FormatException> enthält die gängigen Ursachen und Lösungen von <xref:System.FormatException>\-Fehlern.  
  
 Die MSDN Library\-Abschnitte [Formatierung von Typen](../Topic/Formatting%20Types%20in%20the%20.NET%20Framework.md) und [Analysieren von Zeichenfolgen](../Topic/Parsing%20Strings%20in%20the%20.NET%20Framework.md) enthalten Informationen über die ordnungsgemäße Formatierung und Analyse von Typen.  
  
 **Zusammengesetzte Formatierung**  
  
 [Kombinierte Formatierung](../Topic/Composite%20Formatting.md)  
  
 **Numerische Typen**  
  
|||  
|-|-|  
|[Standardmäßige Zahlenformatzeichenfolgen](../Topic/Standard%20Numeric%20Format%20Strings.md)|[Benutzerdefinierte Zahlenformatzeichenfolgen](../Topic/Custom%20Numeric%20Format%20Strings.md)|  
|[Verarbeiten numerischer Zeichenfolgen](../Topic/Parsing%20Numeric%20Strings%20in%20the%20.NET%20Framework.md)||  
  
 **Datum und Uhrzeit und Timespan\-Typen**  
  
|||  
|-|-|  
|[Standard\-Formatzeichenfolgen für Datum und Uhrzeit](../Topic/Standard%20Date%20and%20Time%20Format%20Strings.md)|[Benutzerdefinierte Formatzeichenfolgen für Datum und Uhrzeit](../Topic/Custom%20Date%20and%20Time%20Format%20Strings.md)|  
|[TimeSpan\-Standardformatzeichenfolgen](../Topic/Standard%20TimeSpan%20Format%20Strings.md)|[Benutzerdefinierte TimeSpan\-Formatzeichenfolgen](../Topic/Custom%20TimeSpan%20Format%20Strings.md)|  
|[Verarbeiten von Zeichenfolgen für Datum und Uhrzeit](../Topic/Parsing%20Date%20and%20Time%20Strings%20in%20the%20.NET%20Framework.md)||  
  
 **Andere Typen**  
  
|||  
|-|-|  
|[Enumerationsformatzeichenfolgen](../Topic/Enumeration%20Format%20Strings.md)|[Verarbeiten anderer Zeichenfolgen](../Topic/Parsing%20Other%20Strings%20in%20the%20.NET%20Framework.md)|
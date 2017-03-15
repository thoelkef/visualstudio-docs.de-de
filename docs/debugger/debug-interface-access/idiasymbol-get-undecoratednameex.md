---
title: "IDiaSymbol::get_undecoratedNameEx | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSymbol::get_undecoratedNameEx-Methode"
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IDiaSymbol::get_undecoratedNameEx
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ruft einen Teil des Ziels oder das gesamte nicht ergänzten Namen für die ergänzten Namen in C\-Format \+\+ \(Bindung\) ab oder legt diese fest.  
  
## Syntax  
  
```cpp#  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### Parameter  
 `undecoratedOptions`  
 \[in\]  Gibt eine Kombination von Flags an, die steuern, welche zurückgegeben wurde.  Weitere Informationen finden Sie im Abschnitt " Hinweise " für die spezifischen Werte und was sie dies tun.  
  
 `pRetVal`  
 \[out\]  Gibt den nicht ergänzten Namen für die ergänzten Namen in C\-Format \+\+ zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt `S_FALSE` oder einen Fehlercode zurück.  
  
> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft nicht für das Symbol verfügbar ist.  
  
## Hinweise  
 `undecorateOptions` kann eine Kombination der folgenden Flags handeln.  
  
> [!NOTE]
>  Die Namen von Flags sind nicht im DIA SDK definiert. Daher müssen Sie entweder die Deklarationen dem Code hinzufügen oder die Rohwerter verwenden.  
  
|Flag|Wert|Beschreibung|  
|----------|----------|------------------|  
|UNDNAME\_COMPLETE|0x0000|Aktiviert die vollständige undecoration.|  
|UNDNAME\_NO\_LEADING\_UNDERSCORES|0x0001|Entfernt führende Unterstriche von Microsoft erweiterte Schlüsselwörter.|  
|UNDNAME\_NO\_MS\_KEYWORDS|0x0002|Deaktiviert die Erweiterung von Microsoft erweiterte Schlüsselwörter.|  
|UNDNAME\_NO\_FUNCTION\_RETURNS|0x0004|Deaktiviert die Erweiterung des Rückgabetyps primäre Deklaration.|  
|UNDNAME\_NO\_ALLOCATION\_MODEL|0x0008|Deaktiviert die Erweiterung des Deklarationen modells.|  
|UNDNAME\_NO\_ALLOCATION\_LANGUAGE|0x0010|Deaktiviert die Erweiterung des spezifizierers Sprachen Deklaration.|  
|UNDNAME\_RESERVED1|0x0020|RESERVIERT.|  
|UNDNAME\_RESERVED2|0x0040|RESERVIERT.|  
|UNDNAME\_NO\_THISTYPE|0x0060|Deaktiviert alle Modifizierer für den `this`\-Typ.|  
|UNDNAME\_NO\_ACCESS\_SPECIFIERS|0x0080|Deaktiviert die Erweiterung von Zugriffsspezifizierern für Member.|  
|UNDNAME\_NO\_THROW\_SIGNATURES|0x0100|Deaktiviert die Erweiterung von „THROW Signaturen“ für Zeiger auf Funktionen und Funktionen.|  
|UNDNAME\_NO\_MEMBER\_TYPE|0x0200|Deaktiviert die Erweiterung von `static` oder `virtual`\-Member.|  
|UNDNAME\_NO\_RETURN\_UDT\_MODEL|0x0400|Deaktiviert die Erweiterung des Microsoft\-Modells für UDTs zurückgegeben wird.|  
|UNDNAME\_32\_BIT\_DECODE|0x0800|Legt die Ergänzung Namen 32\-Bit\-ergänzte rückgängig.|  
|UNDNAME\_NAME\_ONLY|0x1000|Ruft den Namen nur für primäre Deklaration ab. Bereich \[gibt derzeit::\] Namen zurück.  Erweitert Parameter Vorlagen.|  
|UNDNAME\_TYPE\_ONLY|0x2000|Typ ist lediglich eine Eingabe Codierung. verfasst einen abstrakten Deklarator.|  
|UNDNAME\_HAVE\_PARAMETERS|0x4000|In der Praxis Vorlagenparameter sind verfügbar.|  
|UNDNAME\_NO\_ECSU|0x8000|Unterdrückt Enumeration\/Klasse\/Struktur\/Union.|  
|UNDNAME\_NO\_IDENT\_CHAR\_CHECK|0x10000|Unterdrückt die Überprüfung für gültige Bezeichnerzeichen.|  
|UNDNAME\_NO\_PTR64|0x20000|Schließt ptr64 nicht in der Ausgabe ein.|  
  
## Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
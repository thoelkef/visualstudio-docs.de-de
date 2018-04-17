---
title: 'Idiasymbol:: Get_undecoratednameex | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d737ccfe9dbbcdf7a205fb847bb81344cd18ff0c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idiasymbolgetundecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
Ruft Teils oder aller eines nicht ergänzten Namens für eine C++ ergänzten Namen (Bindung).  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `undecoratedOptions`  
 [in] Gibt einer Kombination von Flags, die Rückgabe steuern. Finden Sie im Abschnitt "Hinweise" für die bestimmte Werte und was sie tun.  
  
 `pRetVal`  
 [out] Gibt zurück, der der nicht ergänzte Namen für eine C++ Name ergänzt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
> [!NOTE]
>  Ein Rückgabewert von `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.  
  
## <a name="remarks"></a>Hinweise  
 Die `undecorateOptions` kann eine Kombination der folgenden Flags sein.  
  
> [!NOTE]
>  Die Kennzeichen-Namen sind in DIA-SDK nicht definiert, daher müssen Sie entweder die Deklarationen in den Code hinzufügen, oder verwenden Sie die unformatierte Werte.  
  
|Flag|Wert|Beschreibung|  
|----------|-----------|-----------------|  
|UNDNAME_COMPLETE|0x0000|Aktiviert die vollständige Undecoration.|  
|UNDNAME_NO_LEADING_UNDERSCORES|0x0001|Entfernt führende Unterstriche von Microsoft-Schlüsselwörter erweitert.|  
|UNDNAME_NO_MS_KEYWORDS|0x0002|Deaktiviert die Erweiterung von Microsoft-Schlüsselwörter erweitert.|  
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|Deaktiviert die Erweiterung des Rückgabetyps für die primäre Deklaration.|  
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|Deaktiviert die Erweiterung des Modells Deklaration.|  
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|Deaktiviert die Erweiterung von der Sprache deklarationsspezifizierer.|  
|UNDNAME_RESERVED1|0x0020|RESERVIERT.|  
|UNDNAME_RESERVED2|0 x 0040|RESERVIERT.|  
|UNDNAME_NO_THISTYPE|0x0060|Deaktiviert alle Modifizierer auf der `this` Typ.|  
|UNDNAME_NO_ACCESS_SPECIFIERS|0 x 0080|Deaktiviert die Erweiterung der Zugriffsspezifizierer für Elemente.|  
|UNDNAME_NO_THROW_SIGNATURES|0x0100|Deaktiviert die Erweiterung "Throw-Signaturen" für Funktionen und Zeigern auf Funktionen.|  
|UNDNAME_NO_MEMBER_TYPE|0x0200|Deaktiviert die Erweiterung der `static` oder `virtual` Elemente.|  
|UNDNAME_NO_RETURN_UDT_MODEL|0 x 0400|Deaktiviert die Erweiterung von der Microsoft-Modell zur UDT zurückgibt.|  
|UNDNAME_32_BIT_DECODE|0x0800|Undecorates 32-Bit-ergänzte Namen an.|  
|UNDNAME_NAME_ONLY|0 x 1000|Ruft nur den Namen für die primäre Deklaration an; Gibt nur [Bereich::] Namen.  Wird erweitert, Vorlage Params.|  
|UNDNAME_TYPE_ONLY|0 x 2000|Eingabe ist nur ein Typ, die Codierung. kombiniert einen abstrakten Deklarator an.|  
|UNDNAME_HAVE_PARAMETERS|0 x 4000|Die tatsächlichen Vorlagenparameter sind verfügbar.|  
|UNDNAME_NO_ECSU|0 x 8000|Unterdrückt die Enum/Klasse/Struktur/Union.|  
|UNDNAME_NO_IDENT_CHAR_CHECK|0 x 10000|Unterdrückt die Kontrollkästchen für gültige Bezeichner.|  
|UNDNAME_NO_PTR64|0 x 20000|Umfasst nicht ptr64 in der Ausgabe.|  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
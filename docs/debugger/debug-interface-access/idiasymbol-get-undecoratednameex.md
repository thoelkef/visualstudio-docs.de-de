---
title: 'Idiasymbol:: Get_undecoratednameex | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_undecoratedNameEx method
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2a952c074e62e7fe999826882e382a552789f3a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63400561"
---
# <a name="idiasymbolgetundecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
Ruft teilweise oder vollständig einen nicht ergänzten Namen für eine C++ versehen (Bindung) Namen.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_undecoratedNameEx( 
   DWORD undecorateOptions,
   BSTR* pRetval
);
```

#### <a name="parameters"></a>Parameter
 `undecoratedOptions`

[in] Gibt einer Kombination von Flags, was zurückgegeben wird, die Steuern an. Finden Sie im Abschnitt "Hinweise" für die spezifischen Werte und was sie tun.

 `pRetVal`

[out] Gibt den nicht ergänzten Namen für eine C++ ergänzten Namen.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.

## <a name="remarks"></a>Hinweise
 Die `undecorateOptions` kann eine Kombination der folgenden Flags sein.

> [!NOTE]
> Die Flag-Namen sind nicht in die DIA-SDK definiert, daher müssen Sie Ihren Code die Deklarationen hinzu, oder verwenden Sie die unformatierte Werte.

|Flag|Wert|Beschreibung|
|----------|-----------|-----------------|
|UNDNAME_COMPLETE|0x0000|Aktiviert die vollständige Undecoration.|
|UNDNAME_NO_LEADING_UNDERSCORES|0x0001|Entfernt führende Unterstriche von Microsoft erweitert Schlüsselwörter.|
|UNDNAME_NO_MS_KEYWORDS|0x0002|Deaktiviert die Erweiterung der Microsoft-Schlüsselwörter erweitert.|
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|Deaktiviert die Erweiterung des Rückgabetyps für die primäre Deklaration.|
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|Deaktiviert die Erweiterung des Modells Deklaration.|
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|Deaktiviert die Erweiterung der Sprache deklarationsspezifizierer.|
|UNDNAME_RESERVED1|0x0020|RESERVIERT.|
|UNDNAME_RESERVED2|0x0040|RESERVIERT.|
|UNDNAME_NO_THISTYPE|0x0060|Deaktiviert alle Modifizierer auf der `this` Typ.|
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|Deaktiviert die Erweiterung der Zugriffsspezifizierer für Member.|
|UNDNAME_NO_THROW_SIGNATURES|0x0100|Deaktiviert die Erweiterung "Throw-Signaturen" für Funktionen und Zeigern auf Funktionen.|
|UNDNAME_NO_MEMBER_TYPE|0x0200|Deaktiviert die Erweiterung der `static` oder `virtual` Member.|
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|Deaktiviert die Erweiterung des Modells Microsoft zur UDT zurückgibt.|
|UNDNAME_32_BIT_DECODE|0x0800|Undecorates 32-Bit-ergänzte Namen.|
|UNDNAME_NAME_ONLY|0x1000|Ruft nur den Namen für die primäre Deklaration an; Gibt nur [Bereich::] Namen.  Wird die Vorlage Params erweitert.|
|UNDNAME_TYPE_ONLY|0x2000|Eingabe ist nur ein Typ, die Codierung. erstellt einen abstrakten Deklarator.|
|UNDNAME_HAVE_PARAMETERS|0x4000|Die tatsächlichen Vorlagenparameter sind verfügbar.|
|UNDNAME_NO_ECSU|0x8000|Unterdrückt die Enumeration/Klasse/Struktur/Union.|
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000|Unterdrückt die Überprüfung auf gültige Bezeichnerzeichen.|
|UNDNAME_NO_PTR64|0x20000|Umfasst keine ptr64 in der Ausgabe.|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
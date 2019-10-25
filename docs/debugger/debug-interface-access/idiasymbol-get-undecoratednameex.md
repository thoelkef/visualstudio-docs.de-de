---
title: 'Idiasymmetribol:: get_undecoratedNameEx | Microsoft-Dokumentation'
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
ms.openlocfilehash: 48efbc249d076853e12bc54d2e8a8d438570e740
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738993"
---
# <a name="idiasymbolget_undecoratednameex"></a>IDiaSymbol::get_undecoratedNameEx
Ruft einen Teil oder alle einen nicht ergänzten Namen für einen C++ ergänzten (Verknüpfungs-) Namen ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_undecoratedNameEx( 
   DWORD undecorateOptions,
   BSTR* pRetval
);
```

#### <a name="parameters"></a>Parameter
 `undecoratedOptions`

in Gibt eine Kombination von Flags an, die Steuern, was zurückgegeben wird. Weitere Informationen zu den jeweiligen Werten finden Sie im Abschnitt "Hinweise".

 `pRetVal`

vorgenommen Gibt den nicht ergänzten Namen für C++ einen ergänzten Namen zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK` zurückgegeben. Andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.

> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.

## <a name="remarks"></a>Hinweise
 Der `undecorateOptions` kann eine Kombination der folgenden Flags sein.

> [!NOTE]
> Die flagnamen sind nicht in der DIA SDK definiert, daher müssen Sie entweder die Deklarationen zum Code hinzufügen oder die Rohwerte verwenden.

|Flag|Wert|Beschreibung|
|----------|-----------|-----------------|
|UNDNAME_COMPLETE|0x0000|Ermöglicht die vollständige undekoration.|
|UNDNAME_NO_LEADING_UNDERSCORES|0x0001|Entfernt führende Unterstriche aus erweiterten Schlüsselwörtern von Microsoft.|
|UNDNAME_NO_MS_KEYWORDS|0x0002|Deaktiviert die Erweiterung von erweiterten Microsoft-Schlüsselwörtern.|
|UNDNAME_NO_FUNCTION_RETURNS|0x0004|Deaktiviert die Erweiterung des Rückgabe Typs für die primäre Deklaration.|
|UNDNAME_NO_ALLOCATION_MODEL|0x0008|Deaktiviert die Erweiterung des Deklarations Modells.|
|UNDNAME_NO_ALLOCATION_LANGUAGE|0x0010|Deaktiviert die Erweiterung des Deklarations sprach Spezifizierers.|
|UNDNAME_RESERVED1|0x0020|RESERVIERT.|
|UNDNAME_RESERVED2|0x0040|RESERVIERT.|
|UNDNAME_NO_THISTYPE|0x0060|Deaktiviert alle modifiziererer für den `this` Typ.|
|UNDNAME_NO_ACCESS_SPECIFIERS|0x0080|Deaktiviert die Erweiterung der Zugriffsspezifizierer für Member.|
|UNDNAME_NO_THROW_SIGNATURES|0x0100|Deaktiviert die Erweiterung von "throw-Signaturen" für Funktionen und Zeiger auf Funktionen.|
|UNDNAME_NO_MEMBER_TYPE|0x0200|Deaktiviert die Erweiterung von `static`-oder `virtual` Membern.|
|UNDNAME_NO_RETURN_UDT_MODEL|0x0400|Deaktiviert die Erweiterung des Microsoft-Modells für UDT-Rückgabe.|
|UNDNAME_32_BIT_DECODE|0x0800|Entfüllt die 32-Bit-ergänzten Namen.|
|UNDNAME_NAME_ONLY|0x1000|Ruft nur den Namen der primären Deklaration ab. gibt nur den Namen [Scope::] zurück.  Erweitert Vorlagen Parameter.|
|UNDNAME_TYPE_ONLY|0x2000|Die Eingabe ist nur eine typcodierung. verfasst einen abstrakten Deklarator.|
|UNDNAME_HAVE_PARAMETERS|0x4000|Die tatsächlichen Vorlagen Parameter sind verfügbar.|
|UNDNAME_NO_ECSU|0x8000|Unterdrückt Enumeration/class/struct/Union.|
|UNDNAME_NO_IDENT_CHAR_CHECK|0x10000|Unterdrückt die Prüfung auf gültige Bezeichnerzeichen.|
|UNDNAME_NO_PTR64|0x20000|Enthält ptr64 nicht in der Ausgabe.|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
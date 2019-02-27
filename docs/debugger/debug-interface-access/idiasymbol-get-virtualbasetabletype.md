---
title: 'Idiasymbol:: Get_virtualbasetabletype | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBaseTableType method
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3be75efa175e281378e722e3d10a36cf4b612f7e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56636696"
---
# <a name="idiasymbolgetvirtualbasetabletype"></a>IDiaSymbol::get_virtualBaseTableType
Ruft den Typ eines Zeigers virtuelle Basis-Tabelle ab.

## <a name="syntax"></a>Syntax

```C++
HRESULT get_virtualBaseTableType(
   IDiaSymbol *pRetVal
};
```

#### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|`pRetVal`|[out] Gibt eine [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt, das den Typ der Basistabelle angibt.|

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.

> [!NOTE]
>  Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft ist nicht verfügbar für das Symbol.

## <a name="remarks"></a>Anmerkungen
 Ein virtuelles Basistabelle Zeiger (`vbtptr`) ist ein ausgeblendeter Zeiger in einen [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Vtable, die Vererbung von virtuellen Basisklassen behandelt. Ein `vbtptr` können verschiedene Größen, abhängig von der geerbten Klassen haben.

 Diese Methode gibt ein [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) -Objekt, das verwendet werden kann, um zu bestimmen, die Größe der Vbtptr.

## <a name="requirements"></a>Anforderungen

|Anforderung|Beschreibung|
|-----------------|-----------------|
|Header:|dia2.h|
|Version:|DIA-SDK 8.0|

## <a name="see-also"></a>Siehe auch
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
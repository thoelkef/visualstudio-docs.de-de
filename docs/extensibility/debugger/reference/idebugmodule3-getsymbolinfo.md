---
title: IDebugModule3::GetSymbolInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3aafb28715f58eaba4499b47a2e1dee15b82ed14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726889"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
Ruft eine Liste der Pfade ab, die nach Symbolen durchsucht werden, sowie die Ergebnisse der Suche nach jedem Pfad.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetSymbolInfo(
    SYMBOL_SEARCH_INFO_FIELDS  dwFields,
    MODULE_SYMBOL_SEARCH_INFO* pInfo
);
```

```csharp
int GetSymbolInfo(
    enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,
    MODULE_SYMBOL_SEARCH_INFO[]    pinfo
);
```

## <a name="parameters"></a>Parameter
`dwFields`\
[in] Eine Kombination von Flags aus der SYMBOL_SEARCH_INFO_FIELDS-Enumeration, die angibt, welche [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) `pInfo` Felder ausgefüllt werden sollen.

`pInfo`\
[out] Eine [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) Struktur, deren Elemente mit den angegebenen Informationen ausgefüllt werden sollen. Wenn es sich um einen `E_INVALIDARG`NULL-Wert handelt, gibt diese Methode zurück.

## <a name="return-value"></a>Rückgabewert
Wenn die Methode erfolgreich `S_OK`ist, wird sie zurückgegeben ; Andernfalls wird ein Fehlercode zurückgegeben.

> [!NOTE]
> Die zurückgegebene Zeichenfolge `MODULE_SYMBOL_SEARCH_INFO` (in der Struktur) kann auch dann leer sein, wenn `S_OK` sie zurückgegeben wird. In diesem Fall gab es keine Suchinformationen zurückzugeben.

## <a name="remarks"></a>Bemerkungen
Wenn `bstrVerboseSearchInfo` das Feld `MODULE_SYMBOL_SEARCH_INFO` der Struktur nicht leer ist, enthält es eine Liste der gesuchten Pfade und die Ergebnisse dieser Suche. Die Liste wird mit einem Pfad formatiert, gefolgt von einer Auslassung ("..."), gefolgt vom Ergebnis. Wenn mehr als ein Pfadergebnispaar vorhanden ist, wird jedes Paar durch ein Paar "-r-n" (Carriage-Return/linefeed) getrennt. Das Muster sieht wie folgt aus:

\<Pfad>... \<Ergebnis> Pfad\<>... \<Ergebnis\<>-Pfad>... \<Ergebnis>

Beachten Sie, dass der letzte Eintrag keine Sequenz von .r.n.

## <a name="example"></a>Beispiel
In diesem Beispiel gibt diese Methode drei Pfade mit drei verschiedenen Suchergebnissen zurück. Jede Zeile wird mit einem Wagen-Rücklauf-/Zeileneinzugspaar beendet. Die Beispielausgabe druckt nur die Suchergebnisse als einzelne Zeichenfolge.

> [!NOTE]
> Ein Statusergebnis ist alles unmittelbar nach dem "..." bis zum Ende der Leitung.

```cpp
void ShowSymbolSearchResults(IDebugModule3 *pIDebugModule3)
{
    MODULE_SYMBOL_SEARCH_INFO ssi = { 0 };
    HRESULT hr;
    hr = pIDebugModule3->GetSymbolInfo(SSIF_VERBOSE_SEARCH_INFO,&ssi);
    if (SUCCEEDED(hr)) {
        CComBSTR searchInfo = ssi.bstrVerboseSearchInfo;
        if (searchInfo.Length() != 0) {
            std::wcout << (wchar_t *)(BSTR)searchInfo;
            std::wcout << std::endl;
        }
    }
}
```

**c:-Symbole-Benutzer32.pdb... Datei wurde nicht gefunden.** 
 **c:-winnt-Symbole-User32.pdb... Die Version stimmt nicht überein.** 
"Symbols" (Symbole) -Symbole,32.dll,0a8sd0ad8ad,32.pdb... ** \\ Symbole geladen.**

## <a name="see-also"></a>Weitere Informationen

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)
- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)

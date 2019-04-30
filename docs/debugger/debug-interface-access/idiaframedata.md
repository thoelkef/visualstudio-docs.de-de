---
title: IDiaFrameData | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData interface
ms.assetid: 2f1b4986-341b-4641-89a4-226e261e9d93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4e4adb0747ce569bc372daf0d36cfe1719a2ff61
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830294"
---
# <a name="idiaframedata"></a>IDiaFrameData
Stellt die Details zu einem Stapelrahmen.

## <a name="syntax"></a>Syntax

```
IDiaFrameData : IUnknown
```

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
Die folgende Tabelle zeigt die Methoden der `IDiaFrameData`.

|Methode|Beschreibung|
|------------|-----------------|
|[IDiaFrameData::get_addressSection](../../debugger/debug-interface-access/idiaframedata-get-addresssection.md)|Ruft den Abschnitt in der Codeadresse für den Frame ab.|
|[IDiaFrameData::get_addressOffset](../../debugger/debug-interface-access/idiaframedata-get-addressoffset.md)|Ruft den Zeitzonenoffset-Teil der Codeadresse für den Frame ab.|
|[IDiaFrameData::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiaframedata-get-relativevirtualaddress.md)|Ruft das Bild relative virtuelle Adresse (RVA) des Codes für den Frame ab.|
|[IDiaFrameData::get_virtualAddress](../../debugger/debug-interface-access/idiaframedata-get-virtualaddress.md)|Ruft die virtuelle Adresse (VA) des Codes für den Frame ab.|
|[IDiaFrameData::get_lengthBlock](../../debugger/debug-interface-access/idiaframedata-get-lengthblock.md)|Ruft die Länge in Bytes der Codeblock durch den Frame beschrieben ab.|
|[IDiaFrameData::get_lengthLocals](../../debugger/debug-interface-access/idiaframedata-get-lengthlocals.md)|Ruft die Anzahl der Bytes der lokalen Variablen, die auf dem Stapel abgelegt.|
|[IDiaFrameData::get_lengthParams](../../debugger/debug-interface-access/idiaframedata-get-lengthparams.md)|Ruft die Anzahl der Bytes von Parametern, die auf dem Stapel abgelegt.|
|[IDiaFrameData::get_maxStack](../../debugger/debug-interface-access/idiaframedata-get-maxstack.md)|Ruft die maximale Anzahl von Bytes, die auf dem Stapel im Frame abgelegt.|
|[IDiaFrameData::get_lengthProlog](../../debugger/debug-interface-access/idiaframedata-get-lengthprolog.md)|Ruft die Anzahl der Bytes der Prolog-Code im Block.|
|[IDiaFrameData::get_lengthSavedRegisters](../../debugger/debug-interface-access/idiaframedata-get-lengthsavedregisters.md)|Ruft die Anzahl der Bytes der gespeicherten Register, die auf dem Stapel abgelegt.|
|[IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)|Ruft ab, die Programm-Zeichenfolge, die zum Berechnen der Registrierung festlegen, bevor der Aufruf von der aktuellen Funktion verwendet wird.|
|[IDiaFrameData::get_systemExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-systemexceptionhandling.md)|Ruft wird ein Flag, das diese Ausnahmebehandlung System gibt an, in Kraft.|
|[IDiaFrameData::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md)|Ruft ein Flag, das angibt, C++-Ausnahmebehandlung verwendet wirksam wird.|
|[IDiaFrameData::get_functionStart](../../debugger/debug-interface-access/idiaframedata-get-functionstart.md)|Ruft ein Flag, das zeigt an, dass der Block den Einstiegspunkt einer Funktion enthält.|
|[IDiaFrameData::get_allocatesBasePointer](../../debugger/debug-interface-access/idiaframedata-get-allocatesbasepointer.md)|Ruft ein Flag, das zeigt an, dass der basiszeiger für Code in dieser Adressbereich zugeordnet ist. Diese Methode ist veraltet.|
|[IDiaFrameData::get_type](../../debugger/debug-interface-access/idiaframedata-get-type.md)|Ruft den compilerspezifischen Frametyp ab.|
|[IDiaFrameData::get_functionParent](../../debugger/debug-interface-access/idiaframedata-get-functionparent.md)|Ruft frame-Data-Schnittstelle für eine einschließende Funktion.|
|[IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)|Führt die stapelentladung und gibt den aktuellen Status von Registern in einer Stackwalk-Frame-Schnittstelle zurück.|

## <a name="remarks"></a>Hinweise
 Die Details für einen Frame verfügbar sind für die der Ausführungspunkte innerhalb des Adressbereichs, der durch die Adresse und Block-Länge angegeben.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Rufen Sie diese Schnittstelle durch Aufrufen der [idiaenumframedata:: Next](../../debugger/debug-interface-access/idiaenumframedata-next.md) oder [idiaenumframedata:: Item](../../debugger/debug-interface-access/idiaenumframedata-item.md) Methoden. Finden Sie unter den [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) Schnittstelle für Details.

## <a name="example"></a>Beispiel
 In diesem Beispiel gibt die Eigenschaften einer `IDiaFrameData` Objekt. Finden Sie unter den [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) Schnittstelle für ein Beispiel dafür, wie die `IDiaFrameData` Schnittstelle abgerufen wird.

```C++
void PrintFrameData(IDiaFrameData* pFrameData){
    DWORD dwSect;
    DWORD dwOffset;
    DWORD cbBlock;
    DWORD cbLocals; // Number of bytes reserved for the function locals
    DWORD cbParams; // Number of bytes reserved for the function arguments
    DWORD cbMaxStack;
    DWORD cbProlog;
    DWORD cbSavedRegs;
    BOOL  bSEH;
    BOOL  bEH;
    BOOL  bStart;
    BSTR  wszProgram;

    if(pFrameData->get_addressSection(&dwSect) == S_OK &&
       pFrameData->get_addressOffset(&dwOffset) == S_OK &&
       pFrameData->get_lengthBlock(&cbBlock) == S_OK &&
       pFrameData->get_lengthLocals(&cbLocals) == S_OK &&
       pFrameData->get_lengthParams(&cbParams) == S_OK &&
       pFrameData->get_maxStack(&cbMaxStack) == S_OK &&
       pFrameData->get_lengthProlog(&cbProlog) == S_OK &&
       pFrameData->get_lengthSavedRegisters(&cbSavedRegs) == S_OK &&
       pFrameData->get_systemExceptionHandling(&bSEH) == S_OK &&
       pFrameData->get_cplusplusExceptionHandling(&bEH) == S_OK &&
       pFrameData->get_functionStart(&bStart) == S_OK )
    {
        wprintf(L"Frame address  : %04X:%08X\n", dwSect, dwOffset);
        wprintf(L"Block size     : 0x%8X\n", cbBlock);
        wprintf(L"Locals size    : 0x%8X\n", cbLocals);
        wprintf(L"Parms size     : 0x%8X\n", cbParams);
        wprintf(L"Max stack used : 0x%8X\n", cbMaxStack);
        wprintf(L"Prolog size    : 0x%8X\n", cbProlog);
        wprintf(L"Saved regs size: 0x%8X\n", cbSavedRegs);
        wprintf(L"System Exception Handling: %c\n", bSEH ? L'Y' : L'N');
        wprintf(L"C++ Exception Handling   : %c\n", bEH ? L'Y' : L'N');
        wprintf(L"Function starts in block : %c\n", bStart ? L'Y' : L'N');

        if (pFrameData->get_program(&wszProgram) == S_OK)
        {
            wprintf(L"Program used for register set: %s\n", wszProgram);
            SysFreeString(wszProgram);
        }
        else
        {
            wprintf(L"\n");
        }
    }
}
```

## <a name="requirements"></a>Anforderungen
Header: Dia2.h

Bibliothek: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Siehe auch
- [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)
- [IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md)

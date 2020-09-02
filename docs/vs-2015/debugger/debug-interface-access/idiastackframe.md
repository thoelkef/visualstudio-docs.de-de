---
title: IDiaStackFrame | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame interface
ms.assetid: 486d25b8-a590-41c1-bdb5-faff3ae35632
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3199498f9e31f65045f7df44c4c6b6c39be18f56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144727"
---
# <a name="idiastackframe"></a>IDiaStackFrame
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Macht die Eigenschaften eines Stapel Rahmens verfügbar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaStackFrame : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgenden Methoden werden von dieser Schnittstelle unterstützt:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[IDiaStackFrame::get_allocatesBasePointer](../../debugger/debug-interface-access/idiastackframe-get-allocatesbasepointer.md)|Ruft ein Flag ab, das angibt, dass der Basis Zeiger für den Code in diesem Adressbereich zugeordnet wird. Diese Methode ist als veraltet markiert.|  
|[IDiaStackFrame::get_base](../../debugger/debug-interface-access/idiastackframe-get-base.md)|Ruft die Adress Basis des Frames ab.|  
|[IDiaStackFrame::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-cplusplusexceptionhandling.md)|Ruft ein Flag ab, das angibt, dass die C++-Ausnahmebehandlung wirksam ist.|  
|[IDiaStackFrame::get_functionStart](../../debugger/debug-interface-access/idiastackframe-get-functionstart.md)|Ruft ein Flag ab, das angibt, dass der-Block den Einstiegspunkt einer Funktion enthält.|  
|[IDiaStackFrame::get_lengthLocals](../../debugger/debug-interface-access/idiastackframe-get-lengthlocals.md)|Ruft die Anzahl der Bytes der lokalen Variablen ab, die auf dem Stapel abgelegt werden.|  
|[IDiaStackFrame::get_lengthParams](../../debugger/debug-interface-access/idiastackframe-get-lengthparams.md)|Ruft die Anzahl der Bytes von Parametern ab, die auf dem Stapel abgelegt werden.|  
|[IDiaStackFrame::get_lengthProlog](../../debugger/debug-interface-access/idiastackframe-get-lengthprolog.md)|Ruft die Anzahl der Bytes des prologcodes im-Block ab.|  
|[IDiaStackFrame::get_lengthSavedRegisters](../../debugger/debug-interface-access/idiastackframe-get-lengthsavedregisters.md)|Ruft die Anzahl der Bytes gespeicherter Register auf dem Stapel ab.|  
|[IDiaStackFrame::get_localsBase](../../debugger/debug-interface-access/idiastackframe-get-localsbase.md)|Ruft die Adress Basis der lokalen ab.|  
|[IDiaStackFrame::get_maxStack](../../debugger/debug-interface-access/idiastackframe-get-maxstack.md)|Ruft die maximale Anzahl von Bytes ab, die auf dem Stapel im Frame abgelegt werden.|  
|[IDiaStackFrame::get_rawLVarInstanceValue](../../debugger/debug-interface-access/idiastackframe-get-rawlvarinstancevalue.md)|Ruft den Wert der angegebenen lokalen Variablen als Rohdaten Bytes ab.|  
|[IDiaStackFrame::get_registerValue](../../debugger/debug-interface-access/idiastackframe-get-registervalue.md)|Ruft den Wert eines angegebenen Registers ab.|  
|[IDiaStackFrame::get_returnAddress](../../debugger/debug-interface-access/idiastackframe-get-returnaddress.md)|Ruft die Rückgabeadresse des Frames ab.|  
|[IDiaStackFrame::get_size](../../debugger/debug-interface-access/idiastackframe-get-size.md)|Ruft die Größe des Frames in Bytes ab.|  
|[IDiaStackFrame::get_systemExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-systemexceptionhandling.md)|Ruft ein Flag ab, das angibt, dass die System Ausnahmebehandlung wirksam ist.|  
|[IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)|Ruft den Rahmentyp ab.|  
  
## <a name="remarks"></a>Bemerkungen  
 Ein Stapel Rahmen ist eine Abstraktion eines Funktions Aufrufes während seiner Ausführung.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie diese Schnittstelle durch Aufrufen der [IDiaEnumStackFrames:: Next](../../debugger/debug-interface-access/idiaenumstackframes-next.md) -Methode ab. Ein Beispiel für das Abrufen der-Schnittstelle finden Sie unter [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) -Schnittstelle `IDiaStackFrame` .  
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel werden verschiedene Attribute eines Stapel Rahmens angezeigt.  
  
```cpp#  
void PrintStackFrame(IDiaStackFrame* pFrame)  
{  
    if (pFrame != NULL)  
    {  
        ULONGLONG bottom = 0;  
        ULONGLONG top    = 0;  
  
        if (pFrame->get_base(&bottom) == S_OK &&  
            pFrame->get_registerValue( CV_REG_ESP, &top ) == S_OK )  
        {  
             printf("range = 0x%08I64x - 0x%08I64x\n", bottom, top);  
        }  
  
        ULONGLONG returnAddress = 0;  
        if (pFrame->get_returnAddress(&returnAddress) == S_OK)  
        {  
             printf("return address = 0x%08I64x\n", returnAddress);  
        }  
  
        DWORD lengthFrame     = 0;  
        DWORD lengthLocals    = 0;  
        DWORD lengthParams    = 0;  
        DWORD lengthProlog    = 0;  
        DWORD lengthSavedRegs = 0;  
        if (pFrame->get_size(&lengthFrame) == S_OK &&  
            pFrame->get_lengthLocals(&lengthLocals) == S_OK &&  
            pFrame->get_lengthParams(&lengthParams) == S_OK &&  
            pFrame->get_lengthProlog(&lengthProlog) == S_OK &&  
            pFrame->get_lengthSavedRegisters(&lengthSavedRegs) == S_OK)  
        {  
            printf("stack frame size          = 0x%08lx bytes\n", lengthFrame);  
            printf("length of locals          = 0x%08lx bytes\n", lengthLocals);  
            printf("length of parameters      = 0x%08lx bytes\n", lengthParams);  
            printf("length of prolog          = 0x%08lx bytes\n", lengthProlog);  
            printf("length of saved registers = 0x%08lx bytes\n", lengthSavedRegs);  
        }  
    }  
}  
```  
  
## <a name="requirements"></a>Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Schnittstellen (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)   
 [IDiaEnumStackFrames:: Next](../../debugger/debug-interface-access/idiaenumstackframes-next.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)

---
title: "IDiaStackFrame | Microsoft Docs"
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
  - "IDiaStackFrame-Schnittstelle"
ms.assetid: 486d25b8-a590-41c1-bdb5-faff3ae35632
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# IDiaStackFrame
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Macht die Eigenschaften eines Stapelrahmens.  
  
## Syntax  
  
```  
IDiaStackFrame : IUnknown  
```  
  
## Methoden in die Vtable\-Reihenfolge  
 Im Folgenden sind die Methoden, die von dieser Schnittstelle unterstützt werden:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IDiaStackFrame::get\_allocatesBasePointer](../../debugger/debug-interface-access/idiastackframe-get-allocatesbasepointer.md)|Ruft ein Flag ab, das angibt, dass der Zeiger für den Code in diesem Adressbereich zugeordnet ist.  Diese Methode ist veraltet.|  
|[IDiaStackFrame::get\_base](../../debugger/debug-interface-access/idiastackframe-get-base.md)|Ruft die Adressen Seite des Rahmens ab.|  
|[IDiaStackFrame::get\_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-cplusplusexceptionhandling.md)|Ruft ein Flag ab, das angibt, dass die C\+\+\-Ausnahmebehandlung aktiviert.|  
|[IDiaStackFrame::get\_functionStart](../../debugger/debug-interface-access/idiastackframe-get-functionstart.md)|Ruft ein Flag ab, das angibt, dass der Block den Einstiegspunkt einer Funktion enthält.|  
|[IDiaStackFrame::get\_lengthLocals](../../debugger/debug-interface-access/idiastackframe-get-lengthlocals.md)|Ruft die Anzahl von Bytes lokalen Variablen ab, die auf dem Stapel abgelegt werden.|  
|[IDiaStackFrame::get\_lengthParams](../../debugger/debug-interface-access/idiastackframe-get-lengthparams.md)|Ruft die Anzahl von Bytes Parametern ab, die auf dem Stapel abgelegt werden.|  
|[IDiaStackFrame::get\_lengthProlog](../../debugger/debug-interface-access/idiastackframe-get-lengthprolog.md)|Ruft die Anzahl von Bytes des vorläufige Codes im Block ab|  
|[IDiaStackFrame::get\_lengthSavedRegisters](../../debugger/debug-interface-access/idiastackframe-get-lengthsavedregisters.md)|Ruft die Anzahl von Bytes ab, die gespeicherte Register auf dem Stapel abgelegt werden.|  
|[IDiaStackFrame::get\_localsBase](../../debugger/debug-interface-access/idiastackframe-get-localsbase.md)|Ruft die Adressen der Seite lokalen Variablen ab.|  
|[IDiaStackFrame::get\_maxStack](../../debugger/debug-interface-access/idiastackframe-get-maxstack.md)|Ruft die maximale Anzahl von Bytes ab, die in den Frames auf dem Stapel abgelegt werden.|  
|[IDiaStackFrame::get\_rawLVarInstanceValue](../../debugger/debug-interface-access/idiastackframe-get-rawlvarinstancevalue.md)|Ruft den Wert der angegebenen lokalen Variable als unformatierte Bytes ab.|  
|[IDiaStackFrame::get\_registerValue](../../debugger/debug-interface-access/idiastackframe-get-registervalue.md)|Ruft den Wert eines angegebenen Registers ab.|  
|[IDiaStackFrame::get\_returnAddress](../../debugger/debug-interface-access/idiastackframe-get-returnaddress.md)|Ruft die Rückgabeadresse des Rahmens ab.|  
|[IDiaStackFrame::get\_size](../../debugger/debug-interface-access/idiastackframe-get-size.md)|Ruft die Größe des Rahmens in Bytes ab.|  
|[IDiaStackFrame::get\_systemExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-systemexceptionhandling.md)|Ruft ein Flag ab, das angibt, dass diese System ausnahmebehandlung wirksam.|  
|[IDiaStackFrame::get\_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)|Ruft den Typ des Rahmens ab.|  
  
## Hinweise  
 Ein Stapelrahmen ist eine Abstraktion eines Funktionsaufrufs während ihrer Ausführung.  
  
## Hinweise für Aufrufer  
 Rufen Sie diese Schnittstelle, indem sie die [IDiaEnumStackFrames::Next](../../debugger/debug-interface-access/idiaenumstackframes-next.md)\-Methode aufruft.  Zeigen Sie die [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)\-Schnittstelle als Beispiel auf Abrufen der `IDiaStackFrame`\-Schnittstelle.  
  
## Beispiel  
 In diesem Beispiel werden verschiedene Attribute eines Stapelrahmens.  
  
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
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia80.dll  
  
## Siehe auch  
 [Schnittstellen \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)   
 [IDiaEnumStackFrames::Next](../../debugger/debug-interface-access/idiaenumstackframes-next.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
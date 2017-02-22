---
title: "IDiaFrameData | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaFrameData-Schnittstelle"
ms.assetid: 2f1b4986-341b-4641-89a4-226e261e9d93
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaFrameData
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Macht die Details eines Stapelrahmens.  
  
## Syntax  
  
```  
IDiaFrameData : IUnknown  
```  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDiaFrameData`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[IDiaFrameData::get\_addressSection](../../debugger/debug-interface-access/idiaframedata-get-addresssection.md)|Ruft den Teil der Code\-Adresse Abschnitts für den Rahmen ab.|  
|[IDiaFrameData::get\_addressOffset](../../debugger/debug-interface-access/idiaframedata-get-addressoffset.md)|Ruft den Offset Teil der Code\-Adresse für den Zielframe ab.|  
|[IDiaFrameData::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiaframedata-get-relativevirtualaddress.md)|Ruft die relative virtuelle Adresse des Bildes \(RVA\) des Codes für den Zielframe ab.|  
|[IDiaFrameData::get\_virtualAddress](../../debugger/debug-interface-access/idiaframedata-get-virtualaddress.md)|Ruft die virtuelle Adresse \(VA\) des Codes für den Zielframe ab.|  
|[IDiaFrameData::get\_lengthBlock](../../debugger/debug-interface-access/idiaframedata-get-lengthblock.md)|Ruft die Länge in Bytes des Codeblocks ab, der durch den Frame beschrieben wird.|  
|[IDiaFrameData::get\_lengthLocals](../../debugger/debug-interface-access/idiaframedata-get-lengthlocals.md)|Ruft die Anzahl von Bytes lokalen Variablen ab, die auf dem Stapel abgelegt werden.|  
|[IDiaFrameData::get\_lengthParams](../../debugger/debug-interface-access/idiaframedata-get-lengthparams.md)|Ruft die Anzahl von Bytes Parametern ab, die auf dem Stapel abgelegt werden.|  
|[IDiaFrameData::get\_maxStack](../../debugger/debug-interface-access/idiaframedata-get-maxstack.md)|Ruft die maximale Anzahl von Bytes ab, die in den Frames auf dem Stapel abgelegt werden.|  
|[IDiaFrameData::get\_lengthProlog](../../debugger/debug-interface-access/idiaframedata-get-lengthprolog.md)|Ruft die Anzahl von Bytes des vorläufige Codes im Block ab.|  
|[IDiaFrameData::get\_lengthSavedRegisters](../../debugger/debug-interface-access/idiaframedata-get-lengthsavedregisters.md)|Ruft die Anzahl von Bytes ab, die gespeicherte Register auf dem Stapel abgelegt werden.|  
|[IDiaFrameData::get\_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)|Ruft das Programm Zeichenfolge ab, die verwendet wird, um den Registern Gruppe vor dem Aufruf der aktuellen Funktion abzuleiten.|  
|[IDiaFrameData::get\_systemExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-systemexceptionhandling.md)|Ruft ein Flag ab, das diese System aktiv ist ausnahmebehandlung angibt.|  
|[IDiaFrameData::get\_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md)|Ruft ein Flag ab, das dieses C\+\+\-Ausnahmebehandlung ist wirksam angibt.|  
|[IDiaFrameData::get\_functionStart](../../debugger/debug-interface-access/idiaframedata-get-functionstart.md)|Ruft ein Flag ab, das angibt, dass der Block den Einstiegspunkt einer Funktion enthält.|  
|[IDiaFrameData::get\_allocatesBasePointer](../../debugger/debug-interface-access/idiaframedata-get-allocatesbasepointer.md)|Ruft ein Flag ab, das angibt, dass der Zeiger für den Code in diesem Adressbereich zugeordnet ist.  Diese Methode ist veraltet.|  
|[IDiaFrameData::get\_type](../../debugger/debug-interface-access/idiaframedata-get-type.md)|Ruft den Typ des Rahmens compilerspezifisch ab.|  
|[IDiaFrameData::get\_functionParent](../../debugger/debug-interface-access/idiaframedata-get-functionparent.md)|Ruft einen Rahmen bezugspunkt Oberfläche für das Einschließen der Funktion ab.|  
|[IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)|Führt Stapelentladung aus und gibt den aktuellen Zustand von Registern in einer Stackwalk Skinframes Oberfläche zurück.|  
  
## Hinweise  
 Die Details, die für Frames verfügbar sind, sind für zeigt bei der Ausführung innerhalb des Adressbereichs, der durch die Adresse und die Länge des Blocks angegeben wird.  
  
## Hinweise für Aufrufer  
 Rufen Sie diese Schnittstelle, indem sie die [IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md) oder [IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)\-Methoden aufgerufen werden.  Zeigen Sie die [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)\-Schnittstelle.  
  
## Beispiel  
 In diesem Beispiel werden die Eigenschaften eines `IDiaFrameData`\-Objekts aus.  Zeigen Sie die [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)\-Schnittstelle als ein Beispiel dafür, wie die `IDiaFrameData`\-Schnittstelle ermittelt wird.  
  
```cpp#  
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
  
## Anforderungen  
 Header: Dia2.h  
  
 Bibliothek: diaguids.lib  
  
 DLLs: msdia80.dll  
  
## Siehe auch  
 [Schnittstellen \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)   
 [IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md)
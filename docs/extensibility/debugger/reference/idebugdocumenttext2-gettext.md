---
title: "IDebugDocumentText2::GetText | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentText2::GetText"
helpviewer_keywords: 
  - "IDebugDocumentText2::GetText"
ms.assetid: f8c15a58-da77-473e-a721-7a094e306c63
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugDocumentText2::GetText
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Text der angegebenen Position im Dokument ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetText(   
   TEXT_POSITION pos,  
   ULONG         cMaxChars,  
   WCHAR*        pText,  
   ULONG*        pcNumChars  
);  
```  
  
```c#  
int GetText(   
   eumn_TEXT_POSITION pos,  
   uint               cMaxChars,  
   IntPtr             pText,  
   out uint           pcNumChars  
);  
```  
  
#### Parameter  
 `pos`  
 \[in\]  Eine [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) Struktur, die die Position des abzurufenden Texts angibt.  
  
 `cMaxChars`  
 \[in\]  Die maximale Anzahl von Zeichen des abzurufenden Texts.  
  
 `pText`  
 \[in, out\]  Ein Zeiger auf einen Puffer, der mit dem gewünschten Text ausgefüllt werden soll.  Dieser Puffer muss in der Lage sein, `cMaxChars` Anzahl von Breitzeichen mindestens enthalten soll.  
  
 `pcNumChars`  
 \[out\]  Gibt die Anzahl der tatsächlich abgerufenen Zeichen zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Beispiel  
 In diesem Beispiel wird veranschaulicht, wie diese Methode in C\# aufgerufen werden kann.  
  
```c#  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace Mynamespace  
{  
    class MyClass  
    {  
         string GetDocumentText(IDebugDocumentText2 pText, TEXT_POSITION pos)  
        {  
             string documentText = string.Empty;  
             if (pText != null)  
             {  
                  uint numLines = 0;  
                  uint numChars = 0;  
                  int hr;  
                  hr = pText.GetSize(ref numLines, ref numChars);  
                  if (ErrorHandler.Succeeded(hr))  
                  {  
                       IntPtr buffer = Marshal.AllocCoTaskMem((int)numChars * sizeof(char));  
                       uint actualChars = 0;  
                       hr = pText.GetText(pos, numChars, buffer, out actualChars);  
                       if (ErrorHandler.Succeeded(hr))  
                       {  
                            documentText = Marshal.PtrToStringUni(buffer, (int)actualChars);  
                       }  
                       Marshal.FreeCoTaskMem(buffer);  
                  }  
              }  
              return documentText;  
         }  
    }  
}  
```  
  
## Siehe auch  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)
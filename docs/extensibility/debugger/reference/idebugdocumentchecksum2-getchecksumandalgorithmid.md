---
title: IDebugDocumentChecksum2::GetChecksumAndAlgorithmId | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2::GetChecksumAndAlgorithmI
- GetChecksumAndAlgorithmI
ms.assetid: 25efef99-0ef3-4332-a752-607605fc6e67
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f1a00b34aa640f9198649552ad7f1620d9b026d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62875738"
---
# <a name="idebugdocumentchecksum2getchecksumandalgorithmid"></a>IDebugDocumentChecksum2::GetChecksumAndAlgorithmId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft die Prüfsumme und Algorithmus Dokumentbezeichner erhalten die maximale Anzahl von Bytes, die ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetChecksumAndAlgorithmId(   
   GUID  *pRetVal,  
   ULONG cMaxBytes,  
   BYTE  *pChecksum,  
   ULONG *pcNumBytes  
);  
```  
  
```csharp  
public int GetChecksumAndAlgorithmId(   
   out Guid pRetVal,  
   uint     cMaxBytes,  
   out byte pChecksum,  
   out uint pcNumBytes  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Eindeutiger Bezeichner für den Prüfsummenalgorithmus.  
  
 `cMaxBytes`  
 [in] Maximale Anzahl von Bytes, die für die Prüfsumme verwendet werden.  
  
 `pChecksum`  
 [out] Der Wert der Prüfsumme.  
  
 `pcNumBytes`  
 [out] Tatsächliche Anzahl von Bytes, die für die Prüfsumme verwendet.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird diese Methode, um die Prüfsumme und den Algorithmus für ein Dokument abzurufen.  
  
```cpp#  
HRESULT CDebugCodeContext::GetDocumentChecksumAndAlgorithmId(GUID *pguidAlgorithm, BYTE **ppChecksum, ULONG *pcNumBytes)  
{  
    HRESULT hRes = E_FAIL;  
  
    *ppChecksum = NULL;  
    *pcNumBytes = 0;  
  
    CComPtr<IDebugDocumentContext2> pDocContext;  
  
    hRes = this->GetDocumentContext(&pDocContext);  
  
    if ( HREVAL(S_OK, hRes) )  
    {  
        CComQIPtr<IDebugDocumentChecksum2> pDocChecksum(pDocContext);  
  
        if ( pDocChecksum != NULL )  
        {  
            // Figure out the size of the checksum buffer required  
            ULONG cNumBytes = 0;  
  
            hRes = pDocChecksum->GetChecksumAndAlgorithmId(pguidAlgorithm, 0, NULL, &cNumBytes);  
  
            if ( S_OK == hRes )  
            {  
                // check to see if we got back valid values  
                if ( cNumBytes && GUID_NULL != (*pguidAlgorithm) )  
                {  
                    // Alloc space for the checksum data  
                    BYTE *pChecksum = (BYTE*) CoTaskMemAlloc(cNumBytes);  
  
                    if ( pChecksum )  
                    {  
                        // Get the buffer containing the checksum info  
                        hRes = pDocChecksum->GetChecksumAndAlgorithmId(pguidAlgorithm, cNumBytes, pChecksum, &cNumBytes);  
  
                        if ( HREVAL(S_OK, hRes) )  
                        {  
                            *ppChecksum = pChecksum;  
                            *pcNumBytes = cNumBytes;  
                        }  
                        else  
                        {  
                            CoTaskMemFree(pChecksum);  
                        }  
                    }  
                    else  
                        hRes = E_OUTOFMEMORY;  
                }  
                else  
                    hRes = S_FALSE; // lang doesn't support checksums  
            }  
            else  
                hRes = S_FALSE; // failed to work out checksum info  
        }  
        else  
            hRes = S_FALSE; // SH doesn't support checksums  
    }  
  
    return ( hRes );  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)
